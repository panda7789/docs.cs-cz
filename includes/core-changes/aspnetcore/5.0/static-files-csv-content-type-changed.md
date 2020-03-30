---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391179"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="326cb-101">Statické soubory: Typ obsahu CSV byl změněn na standardy</span><span class="sxs-lookup"><span data-stu-id="326cb-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="326cb-102">V ASP.NET jádrem Core `Content-Type` 5.0 se výchozí hodnota hlavičky odpovědi, kterou [middleware statického souboru](/aspnet/core/fundamentals/static-files) používá pro soubory *.csv,* změnila na hodnotu `text/csv`kompatibilní se standardy .</span><span class="sxs-lookup"><span data-stu-id="326cb-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="326cb-103">Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="326cb-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="326cb-104">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="326cb-104">Version introduced</span></span>

<span data-ttu-id="326cb-105">5.0 Náhled 1</span><span class="sxs-lookup"><span data-stu-id="326cb-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="326cb-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="326cb-106">Old behavior</span></span>

<span data-ttu-id="326cb-107">Byla `Content-Type` použita hodnota `application/octet-stream` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="326cb-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="326cb-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="326cb-108">New behavior</span></span>

<span data-ttu-id="326cb-109">Použije `Content-Type` se `text/csv` hodnota záhlaví.</span><span class="sxs-lookup"><span data-stu-id="326cb-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="326cb-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="326cb-110">Reason for change</span></span>

<span data-ttu-id="326cb-111">Shoda se standardem [RFC 7111.](https://tools.ietf.org/html/rfc7111#section-5.1)</span><span class="sxs-lookup"><span data-stu-id="326cb-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="326cb-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="326cb-112">Recommended action</span></span>

<span data-ttu-id="326cb-113">Pokud tato změna ovlivní vaši aplikaci, můžete přizpůsobit mapování typu přípona souboru na MIME.</span><span class="sxs-lookup"><span data-stu-id="326cb-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="326cb-114">Chcete-li se `application/octet-stream` vrátit k typu <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> MIME, upravte volání metody v `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="326cb-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="326cb-115">Například:</span><span class="sxs-lookup"><span data-stu-id="326cb-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="326cb-116">Další informace o přizpůsobení mapování naleznete v tématu [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="326cb-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="326cb-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="326cb-117">Category</span></span>

<span data-ttu-id="326cb-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="326cb-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="326cb-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="326cb-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
