# escape=`

FROM microsoft/dotnet-framework:4.7.2-runtime AS base
EXPOSE 80

# configure web servers to bind to port 80 when present
ENV ASPNETCORE_URLS=http://+:80 `
    # Enable detection of running in a container
    DOTNET_RUNNING_IN_CONTAINERS=true `
    # ignore first time expierence
    DOTNET_SKIP_FIRST_TIME_EXPERIENCE=true

FROM microsoft/dotnet-framework:4.7.2-sdk AS build
WORKDIR /src
COPY ["Demo.API/Demo.API.csproj", "Demo.API/"]
RUN dotnet restore "Demo.API/Demo.API.csproj"
COPY . .
WORKDIR /src/Demo.API
RUN dotnet build "Demo.API.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "Demo.API.csproj" --no-build -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
# The csproj targets net472. This output produced by dotnet publish:
# * creates an EXE (Demo.API.exe) rather than the usual DLL (Demo.API.dll)
# * is NOT a self-contained deployment (SCD)
# * although being very close to being a SCD, it is missing Microsoft.DiaSymReader.Native.*.dll
ENTRYPOINT ["Demo.API.exe"]
# ENTRYPOINT ["dotnet", "Demo.API.dll"]