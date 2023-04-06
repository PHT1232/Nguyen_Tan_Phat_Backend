FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build

WORKDIR /src
COPY ["src/Nguyen_Tan_Phat_Project.Web.Host/Nguyen_Tan_Phat_Project.Web.Host.csproj", "src/Nguyen_Tan_Phat_Project.Web.Host/"]
COPY ["src/Nguyen_Tan_Phat_Project.Web.Core/Nguyen_Tan_Phat_Project.Web.Core.csproj", "src/Nguyen_Tan_Phat_Project.Web.Core/"]
COPY ["src/Nguyen_Tan_Phat_Project.Application/Nguyen_Tan_Phat_Project.Application.csproj", "src/Nguyen_Tan_Phat_Project.Application/"]
COPY ["src/Nguyen_Tan_Phat_Project.Core/Nguyen_Tan_Phat_Project.Core.csproj", "src/Nguyen_Tan_Phat_Project.Core/"]
COPY ["src/Nguyen_Tan_Phat_Project.EntityFrameworkCore/Nguyen_Tan_Phat_Project.EntityFrameworkCore.csproj", "src/Nguyen_Tan_Phat_Project.EntityFrameworkCore/"]
WORKDIR "/src/src/Nguyen_Tan_Phat_Project.Web.Host"
RUN dotnet restore 

WORKDIR /src
COPY ["src/Nguyen_Tan_Phat_Project.Web.Host", "src/Nguyen_Tan_Phat_Project.Web.Host"]
COPY ["src/Nguyen_Tan_Phat_Project.Web.Core", "src/Nguyen_Tan_Phat_Project.Web.Core"]
COPY ["src/Nguyen_Tan_Phat_Project.Application", "src/Nguyen_Tan_Phat_Project.Application"]
COPY ["src/Nguyen_Tan_Phat_Project.Core", "src/Nguyen_Tan_Phat_Project.Core"]
COPY ["src/Nguyen_Tan_Phat_Project.EntityFrameworkCore", "src/Nguyen_Tan_Phat_Project.EntityFrameworkCore"]
WORKDIR "/src/src/Nguyen_Tan_Phat_Project.Web.Host"
RUN dotnet publish -c Release -o /publish --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:7.0
EXPOSE 80
WORKDIR /app
COPY --from=build /publish .
ENTRYPOINT ["dotnet", "Nguyen_Tan_Phat_Project.Web.Host.dll"]
