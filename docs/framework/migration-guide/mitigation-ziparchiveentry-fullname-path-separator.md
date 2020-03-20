---
title: 'Zmírnění: Oddělovač cesty ZipArchiveEntry.FullName'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 021d22e90ba39a4d01cf7d64588fab2d724b6640
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457732"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="e18e1-102">Zmírnění: Oddělovač cesty ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="e18e1-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="e18e1-103">Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.1, oddělovač cesty použitý ve <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnosti se změnil z zpětného lomítka ("\\") používaného v předchozích verzích rozhraní .NET Framework na lomítko ("/").</span><span class="sxs-lookup"><span data-stu-id="e18e1-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="e18e1-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>objekty jsou vytvořeny voláním jednoho <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> z přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="e18e1-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e18e1-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="e18e1-105">Impact</span></span>  
 <span data-ttu-id="e18e1-106">Změna uvede implementaci .NET do souladu s oddílem 4.4.17.1 [. SPECIFIKACE FORMÁTU SOUBORU ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje . ZIP archivy, které mají být dekomprimovány v systémech, které nejsou systémy Windows.</span><span class="sxs-lookup"><span data-stu-id="e18e1-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="e18e1-107">Dekomprese souboru ZIP vytvořeného aplikací, která cílí na předchozí verzi rozhraní .NET Framework v operačních systémech, například v systému Macintosh, nezachová adresářovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="e18e1-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="e18e1-108">Například na Macintosh vytvoří sadu souborů, jejichž název souboru zřetězí cestu k adresáři,\\spolu s případnými znaky zpětného lomítka (" a názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="e18e1-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="e18e1-109">V důsledku toho není zachována adresářová struktura dekomprimovaných souborů.</span><span class="sxs-lookup"><span data-stu-id="e18e1-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="e18e1-110">Dopad této změny na . Soubory ZIP, které jsou dekomprimovány v operačním systému <xref:System.IO> Windows pomocí rozhraní API v oboru názvů rozhraní .NET Framework, by měly\\být minimální, protože tato rozhraní API mohou bez problémů zpracovat lomítko ("/") nebo zpětné lomítko (" ") jako znak oddělovače cesty.</span><span class="sxs-lookup"><span data-stu-id="e18e1-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e18e1-111">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="e18e1-111">Mitigation</span></span>  
 <span data-ttu-id="e18e1-112">Pokud je toto chování nežádoucí, můžete se odhlásit přidáním nastavení konfigurace do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="e18e1-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="e18e1-113">V následujícím textu `<runtime>` je uveden oddíl i přepínač pro odhlášení.</span><span class="sxs-lookup"><span data-stu-id="e18e1-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="e18e1-114">Kromě toho aplikace, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6.1 a novějšíverze můžete přihlásit k tomuto chování přidáním nastavení konfigurace [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="e18e1-114">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="e18e1-115">V následujícím textu `<runtime>` je uveden oddíl i přepínač pro přihlášení.</span><span class="sxs-lookup"><span data-stu-id="e18e1-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e18e1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e18e1-116">See also</span></span>

- [<span data-ttu-id="e18e1-117">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="e18e1-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="e18e1-118">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="e18e1-118">Application compatibility</span></span>](application-compatibility.md)
