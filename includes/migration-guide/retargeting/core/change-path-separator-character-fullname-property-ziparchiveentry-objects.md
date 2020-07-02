---
ms.openlocfilehash: 148312743dd274728b178951548889dc3a680528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614468"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a><span data-ttu-id="cc950-101">Změna v znaku oddělovače cesty ve vlastnosti FullName objektů ZipArchiveEntry</span><span class="sxs-lookup"><span data-stu-id="cc950-101">Change in path separator character in FullName property of ZipArchiveEntry objects</span></span>

#### <a name="details"></a><span data-ttu-id="cc950-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="cc950-102">Details</span></span>

<span data-ttu-id="cc950-103">U aplikací, které cílí na .NET Framework 4.6.1 a novější verze, se znak oddělovače cesty změnil z zpětného lomítka (" \" ) na lomítko ("/") ve <xref:System.IO.Compression.ZipArchiveEntry.FullName> vlastnosti <xref:System.IO.Compression.ZipArchiveEntry> objektů vytvořených přetížením <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cc950-103">For apps that target the .NET Framework 4.6.1 and later versions, the path separator character has changed from a backslash ("\") to a forward slash ("/") in the <xref:System.IO.Compression.ZipArchiveEntry.FullName> property of <xref:System.IO.Compression.ZipArchiveEntry>  objects created by overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> method.</span></span> <span data-ttu-id="cc950-104">Tato změna přináší implementaci rozhraní .NET do souladu s oddílem 4.4.17.1 [. Specifikace formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. Archivy ZIP, které se mají dekomprimovat v systémech jiných než Windows</span><span class="sxs-lookup"><span data-stu-id="cc950-104">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span><br /><span data-ttu-id="cc950-105">Dekomprimace souboru ZIP vytvořeného aplikací, která cílí na předchozí verzi .NET Framework v operačních systémech jiných než Windows, jako je například Macintosh, se nepodařilo zachovat adresářovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="cc950-105">Decompressing a zip file created by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="cc950-106">Například v počítači Macintosh vytvoří sadu souborů, jejichž název souboru zřetězí cestu k adresáři, spolu se znakem zpětného lomítka ("") a názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="cc950-106">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("") characters, and the filename.</span></span> <span data-ttu-id="cc950-107">V důsledku toho není zachována adresářová struktura dekomprimovaných souborů.</span><span class="sxs-lookup"><span data-stu-id="cc950-107">As a result, the directory structure of decompressed files is not preserved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cc950-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="cc950-108">Suggestion</span></span>

<span data-ttu-id="cc950-109">Dopad této změny na. Soubory ZIP, které jsou v operačním systému Windows dekomprimovány pomocí rozhraní API v <xref:System.IO?displayProperty=nameWithType> oboru názvů .NET Framework, by měly být minimální, protože tato rozhraní API můžou hladě zpracovávat lomítka ("/") nebo zpětné lomítko (" \" ) jako znak oddělovače cesty.</span><span class="sxs-lookup"><span data-stu-id="cc950-109">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO?displayProperty=nameWithType> namespace should be minimal, since these APIs can seamlessly handle either a forward slash ("/") or a backslash ("\") as the path separator character.</span></span><br /><span data-ttu-id="cc950-110">Pokud je tato změna nežádoucí, můžete ji odhlásit přidáním nastavení konfigurace do [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc950-110">If this change is undesirable, you can opt out of it by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="cc950-111">Následující příklad ukazuje jak `<runtime>` oddíl, tak přepínač pro `Switch.System.IO.Compression.ZipFile.UseBackslash` výslovný souhlas:</span><span class="sxs-lookup"><span data-stu-id="cc950-111">The following example shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-out switch:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

<span data-ttu-id="cc950-112">Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 a novějších verzích se můžou k tomuto chování vyjádřit přidáním nastavení konfigurace do [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="cc950-112">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="cc950-113">Následující příklad ukazuje `<runtime>` oddíl i `Switch.System.IO.Compression.ZipFile.UseBackslash` přepínač pro výslovný souhlas.</span><span class="sxs-lookup"><span data-stu-id="cc950-113">The following shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-in switch.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| <span data-ttu-id="cc950-114">Name</span><span class="sxs-lookup"><span data-stu-id="cc950-114">Name</span></span>    | <span data-ttu-id="cc950-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cc950-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cc950-116">Rozsah</span><span class="sxs-lookup"><span data-stu-id="cc950-116">Scope</span></span>   | <span data-ttu-id="cc950-117">Edge</span><span class="sxs-lookup"><span data-stu-id="cc950-117">Edge</span></span>        |
| <span data-ttu-id="cc950-118">Verze</span><span class="sxs-lookup"><span data-stu-id="cc950-118">Version</span></span> | <span data-ttu-id="cc950-119">4.6.1</span><span class="sxs-lookup"><span data-stu-id="cc950-119">4.6.1</span></span>       |
| <span data-ttu-id="cc950-120">Typ</span><span class="sxs-lookup"><span data-stu-id="cc950-120">Type</span></span>    | <span data-ttu-id="cc950-121">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="cc950-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="cc950-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="cc950-122">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
