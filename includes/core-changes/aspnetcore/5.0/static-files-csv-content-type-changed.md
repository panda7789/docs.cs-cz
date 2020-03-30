---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391179"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Statické soubory: Typ obsahu CSV byl změněn na standardy

V ASP.NET jádrem Core `Content-Type` 5.0 se výchozí hodnota hlavičky odpovědi, kterou [middleware statického souboru](/aspnet/core/fundamentals/static-files) používá pro soubory *.csv,* změnila na hodnotu `text/csv`kompatibilní se standardy .

Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).

#### <a name="version-introduced"></a>Zavedená verze

5.0 Náhled 1

#### <a name="old-behavior"></a>Staré chování

Byla `Content-Type` použita hodnota `application/octet-stream` záhlaví.

#### <a name="new-behavior"></a>Nové chování

Použije `Content-Type` se `text/csv` hodnota záhlaví.

#### <a name="reason-for-change"></a>Důvod změny

Shoda se standardem [RFC 7111.](https://tools.ietf.org/html/rfc7111#section-5.1)

#### <a name="recommended-action"></a>Doporučená akce

Pokud tato změna ovlivní vaši aplikaci, můžete přizpůsobit mapování typu přípona souboru na MIME. Chcete-li se `application/octet-stream` vrátit k typu <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> MIME, upravte volání metody v `Startup.Configure`. Například:

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Další informace o přizpůsobení mapování naleznete v tématu [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
