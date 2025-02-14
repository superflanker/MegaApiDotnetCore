Documente o projeto listado abaixo:

Uma api feito em dotnet, para listar os dados dos bosses do jogo megaman, que fornece jsons no formato abaixo:

```
{
  Id =1,
  Code = "DLN/DRN-003",
  Name = "Cutman",
  HP = 150,
  Picture = "https://vignette.wikia.nocookie.net/megaman/images/2/22/Cutman.png"
}
```

Projeto:

```
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.8" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="3.1.8">
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="3.1.8" />
    <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
  </ItemGroup>

</Project>
```

Endpoints:

```
{
    //api/v1/robots
    [ApiController]
    [Route("api/v1/robots")]
    public class RobotsController : ControllerBase
    {
        private readonly IRobotServices _services;
        public RobotsController(IRobotServices services)
        {
           _services = services;
        }

        //GET api/robots
        [HttpGet]
        public ActionResult<IEnumerable<RobotReadDTO>> GetAllRobots()
        {
            var robotItems = _services.SearchAll();
            return Ok(robotItems);
        }

        //GET api/v1/robots/{id}
        [HttpGet]
        [Route("{id:int}")]
        public object GetCommandById([FromRoute]int id)
        {
            var robot = _services.SearchById(id);

            if(robot != null)
                return Ok(robot);

                return NotFound(
                        new { message = "Nenhum robo encontrado" }
                );
        }

        //POST api/v1/robots
        [HttpPost]
        public ActionResult RobotSend(){
            return Ok();
        }


    }
}
```

orientações:

- Citar as dependências do projeto, no formato de tabela com hiperlinks para sua respectiva página inicial
- Criar lista de endpoints no formato de tabela
- Forneça exemplos de uso da API RESTful
- Criar a estrutura de projeto de acordo com a árvode de diretórios abaixo:

    .vs
    .vscode
    bin/
    Controllers/
    Database/
    middlewares/
    Models/
    obj/
    Properties/
    Services/
    appsettings.Development.json
    appsettings.json  
    global.json
    MegamanApi.csproj  
    MegamanApi.sln
    Program.cs
    Startup.cs

- Criar sessão explicativa das técnicas utilizadas, incluindo Dependenci Injection e Data Transfer Objects
