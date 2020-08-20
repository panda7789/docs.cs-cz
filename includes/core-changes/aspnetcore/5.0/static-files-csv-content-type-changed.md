---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391179"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="4e2e3-101">Statické soubory: typ obsahu CSV se změnil na vyhovující standardům.</span><span class="sxs-lookup"><span data-stu-id="4e2e3-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="4e2e3-102">V ASP.NET Core 5,0 se výchozí `Content-Type` hodnota hlavičky odpovědi, kterou [middleware](/aspnet/core/fundamentals/static-files) pro soubory *. csv* používá, změnila na hodnotu kompatibilní se standardy `text/csv` .</span><span class="sxs-lookup"><span data-stu-id="4e2e3-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="4e2e3-103">Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="4e2e3-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4e2e3-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="4e2e3-104">Version introduced</span></span>

<span data-ttu-id="4e2e3-105">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="4e2e3-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4e2e3-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="4e2e3-106">Old behavior</span></span>

<span data-ttu-id="4e2e3-107">`Content-Type` `application/octet-stream` Byla použita hodnota hlavičky.</span><span class="sxs-lookup"><span data-stu-id="4e2e3-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4e2e3-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="4e2e3-108">New behavior</span></span>

<span data-ttu-id="4e2e3-109">`Content-Type`Hodnota hlavičky `text/csv` se používá.</span><span class="sxs-lookup"><span data-stu-id="4e2e3-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4e2e3-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="4e2e3-110">Reason for change</span></span>

<span data-ttu-id="4e2e3-111">Dodržování předpisů [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) Standard.</span><span class="sxs-lookup"><span data-stu-id="4e2e3-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4e2e3-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4e2e3-112">Recommended action</span></span>

<span data-ttu-id="4e2e3-113">Pokud tato změna ovlivní vaši aplikaci, můžete přizpůsobit mapování typu Přípona souboru na MIME.</span><span class="sxs-lookup"><span data-stu-id="4e2e3-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="4e2e3-114">Chcete-li se vrátit k `application/octet-stream` typu MIME, upravte <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> volání metody v `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="4e2e3-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="4e2e3-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4e2e3-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="4e2e3-116">Další informace o přizpůsobení mapování najdete v tématu [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="4e2e3-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="4e2e3-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4e2e3-117">Category</span></span>

<span data-ttu-id="4e2e3-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4e2e3-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4e2e3-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4e2e3-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
