# produtividade-ias-mcps_ai-weekend-2026-01
Slides e conteúdos da apresentação "Produtividade no Desenvolvimento com IAs: descomplicando tarefas do dia a dia com MCP Servers".

Exemplos utilizados:
- [MCP Server de geração de dados fake criado com .NET 10 (pacote NuGet)](https://github.com/renatogroffe/dotnet10-nuget-mcp-fakedata)
- [MCP Server de geração de dados fake criado com .NET 10 (container)](https://github.com/renatogroffe/dotnet10-consoleapp-mcp-fakedata)
- [k6 + Azure DevOps: exemplo de teste automatizado de um MCP Server](https://github.com/renatogroffe/k6-mcps-tests-azdevops-pipelines)
- [Exemplo de uso da ferramenta MCP Audit (APIsec) em um pipeline do Azure DevOps](https://github.com/renatogroffe/azdevops-apisec-mcp-audit_v1.0.0)

Configurações completas para simular um ambiente local de desenvolvimento com vários MCPs ativados no Visual Studio Code e integrados com GitHub Copilot: https://github.com/renatogroffe/vscode-mcp-dev-enviroment-2026-01

Exemplo incompleto de **mcp.json** (utilizado durante a demo):

```json
{
	"servers": {
		"nuget": {
			"type": "stdio",
			"command": "dnx",
			"args": [
				"NuGet.Mcp.Server@1.1.29",
				"--yes"
			]
		},
		"docker": {
			"command": "docker",
			"args": [
				"run",
				"-i",
				"--rm",
				"-e",
				"HUB_PAT_TOKEN=${input:hub_pat_token}",
				"mcp/dockerhub"
			],
			"type": "stdio"
		},
		"github": {
		  "type": "http",
		  "url": "https://api.githubcopilot.com/mcp/"
		}
	},
	"inputs": [
		{
			"id": "hub_pat_token",
			"type": "promptString",
			"description": "Docker Hub Personal Access Token",
			"password": true
		}
	]
}
```
