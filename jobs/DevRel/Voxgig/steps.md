1. Go to the parent folder
cd C:\Users\pablo\DEV\projects
2. Download the spec
Invoke-WebRequest https://developer.themoviedb.org/openapi/tmdb-api.json -OutFile .\tmdb-api.json
3. Install the scaffolder (so bare create-sdkgen works)
npm install -g @voxgig/create-sdkgen
4. Scaffold
create-sdkgen tmdb -d .\tmdb-api.json -o .\tmdb-sdk
5. Enter the build folder
cd .\tmdb-sdk\.sdk
6. Add the TypeScript target
npx voxgig-sdkgen target add ts
7. Add the offline test feature
npx voxgig-sdkgen feature add test
8. Generate the SDK
npm run generate
9. Move to the generated SDK
cd ..\ts
10. Install dependencies
npm install
11. Build
npm run build
12. Test
npm test