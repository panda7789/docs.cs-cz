---
title: 'Omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eba871215f33e4d3b50054e9ceaa92be090d0143
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871108"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="76146-102">Omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="76146-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="76146-103">Počínaje aplikací, které se zaměřují [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], cesta oddělovač použitý v <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnost se změnil z zpětné lomítko ("\\") používají v předchozích verzích rozhraní .NET Framework na dopředné lomítko ("/").</span><span class="sxs-lookup"><span data-stu-id="76146-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="76146-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objekty byly vytvořeny zavoláním jednoho z přetížení <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="76146-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="76146-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="76146-105">Impact</span></span>  
 <span data-ttu-id="76146-106">Tato změna přináší implementace .NET do souladu s část 4.4.17.1 [. Specifikaci formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. Na systémech než Windows dekomprimovat archivy ZIP.</span><span class="sxs-lookup"><span data-stu-id="76146-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="76146-107">Dekomprese souboru zip vytvořil aplikaci, který cílí předchozí verze rozhraní .NET Framework v operačních systémech než Windows například Macintosh selže zachovat adresářovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="76146-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="76146-108">Například na Macintosh, vytvoří sadu souborů, jejichž název souboru zřetězí cesta k adresáři, spolu s jakékoli zpětné lomítko ("\\") znaků a název souboru.</span><span class="sxs-lookup"><span data-stu-id="76146-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="76146-109">V důsledku toho se nezachová struktura adresářů dekomprimovaných souborů.</span><span class="sxs-lookup"><span data-stu-id="76146-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="76146-110">Dopad na tuto změnu. Soubory ZIP, které jsou v operačním systému Windows dekomprimovat rozhraní API v rozhraní .NET Framework <xref:System.IO> oborem názvů musí být minimální, protože tato rozhraní API bez problémů zvládne lomítko ("/") nebo zpětné lomítko ("\\") jako oddělovač cesty.</span><span class="sxs-lookup"><span data-stu-id="76146-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="76146-111">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="76146-111">Mitigation</span></span>  
 <span data-ttu-id="76146-112">Pokud toto chování nežádoucí, můžete se rozhodnout z přidáním nastavení konfigurace, které [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="76146-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="76146-113">Následující příklad zobrazuje i `<runtime>` části a výslovného nesouhlasu s přepínačem.</span><span class="sxs-lookup"><span data-stu-id="76146-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="76146-114">Kromě toho, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny na [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a novější verze můžete vyjádřit výslovný souhlas pro toto chování tak, že přidáte nastavení konfigurace, které [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="76146-114">In addition, apps that target previous versions of the .NET Framework but are running on the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="76146-115">Následující příklad zobrazuje i `<runtime>` části a přepínač opt-in.</span><span class="sxs-lookup"><span data-stu-id="76146-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76146-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76146-116">See also</span></span>

- [<span data-ttu-id="76146-117">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="76146-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="76146-118">Kompatibilita aplikací ve verzi 4.6.1</span><span class="sxs-lookup"><span data-stu-id="76146-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
