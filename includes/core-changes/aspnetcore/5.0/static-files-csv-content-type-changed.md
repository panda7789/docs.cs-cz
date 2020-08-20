---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391179"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Statické soubory: typ obsahu CSV se změnil na vyhovující standardům.

V ASP.NET Core 5,0 se výchozí `Content-Type` hodnota hlavičky odpovědi, kterou [middleware](/aspnet/core/fundamentals/static-files) pro soubory *. csv* používá, změnila na hodnotu kompatibilní se standardy `text/csv` .

Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 1

#### <a name="old-behavior"></a>Staré chování

`Content-Type` `application/octet-stream` Byla použita hodnota hlavičky.

#### <a name="new-behavior"></a>Nové chování

`Content-Type`Hodnota hlavičky `text/csv` se používá.

#### <a name="reason-for-change"></a>Důvod změny

Dodržování předpisů [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) Standard.

#### <a name="recommended-action"></a>Doporučená akce

Pokud tato změna ovlivní vaši aplikaci, můžete přizpůsobit mapování typu Přípona souboru na MIME. Chcete-li se vrátit k `application/octet-stream` typu MIME, upravte <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> volání metody v `Startup.Configure` . Příklad:

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Další informace o přizpůsobení mapování najdete v tématu [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
