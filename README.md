# PdfReport

## RotativaPDF

###### 01. Adicionar [Pacote nuget](https://www.nuget.org/packages/Rotativa.AspNetCore/1.2.0-beta)

###### 02. Copiar o conteúdo do diretório: _wwwroot/rotativa/

###### 03. Adicionar a seguinte linha de código no método _Configure_ em _Startup_:
```
RotativaConfiguration.Setup(env);
```
###### 04. Substituir a seguinte linha de código:
```
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
```
por esta:
```
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
```
Obs: mudou apenas o _IIWebHostEnvironment

###### 05. No Controller retornar o tipo _ViewAsPdf_:
```
public IActionResult RotativaPDF()
{
    Person person = new Person()
    {
        Id = Guid.NewGuid(),
        Name = "Primeiro",
        LastName = "Ultimo"
    };

    var pdf = new ViewAsPdf(person);

    return pdf;
}
```
###### 06. Na View não muda nada do que estamos acostumados:
```
@model PdfReport.Models.Person

@{
    ViewData["Title"] = "RotativaPDF";
}

<h2>RotativaPDF</h2>

<ul>
    <li>@Model.Id</li>
    <li>@Model.Name</li>
    <li>@Model.LastName</li>
</ul>
```
