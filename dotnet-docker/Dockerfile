
# Pull the mcr.microsoft.com/dotnet/sdk:8.0 image and name the image build.
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build


# Set the working directory within the image to /DataEntities.
WORKDIR /DataEntities

# Copy the file named DataEntities.csproj found locally to the /DataEntities directory that you created.
# COPY "DataEntities/DataEntities.csproj" .
# Copy everything in the local DataEntities directory to the image.
COPY DataEntities .
# Call dotnet restore on the project.
RUN dotnet restore
# Call dotnet publish on the project.
RUN dotnet publish -c release -o /app --no-restore

# Set the working directory within the image to /src.
WORKDIR /src
# Copy the file named Products.csproj found locally to the /src directory that you created.
# COPY Products/Products.csproj .
# Copy everything in the local DataEntities directory to the image.
COPY Products .

# Call dotnet restore on the project.
RUN dotnet restore
RUN dotnet publish -c release -o /app --no-restore

#Pull the mcr.microsoft.com/dotnet/aspnet:8.0 image.
#Set the working directory within the image to /app.
#Expose port 80 and 443.
#Copy everything from the app directory of the build image you created into the app directory of this image.
#Set the entry point of this image to dotnet and pass Products.dll as an argument.

 FROM mcr.microsoft.com/dotnet/aspnet:8.0
 WORKDIR /app
 EXPOSE 80
 EXPOSE 443
 COPY --from=build /app .
 ENTRYPOINT ["dotnet", "Products.dll"]
