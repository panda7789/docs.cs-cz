---
title: Zmírnění ZipArchiveEntry. FullName – oddělovač cest
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
ms.openlocfilehash: b97436ca2f81fea139689c7c2c2348718827b90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778859"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="0de45-102">Zmírnění ZipArchiveEntry. FullName – oddělovač cest</span><span class="sxs-lookup"><span data-stu-id="0de45-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="0de45-103">Počínaje aplikacemi, které cílí na .NET Framework 4.6.1, se oddělovač cest použitý ve <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnosti změnil z zpětného lomítka\\("") používaného v předchozích verzích .NET Framework na lomítko ("/").</span><span class="sxs-lookup"><span data-stu-id="0de45-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="0de45-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>objekty jsou vytvořeny voláním jednoho z přetížení <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0de45-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0de45-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="0de45-105">Impact</span></span>  
 <span data-ttu-id="0de45-106">Tato změna přináší implementaci rozhraní .NET do souladu s oddílem 4.4.17.1 [. Specifikace formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. Archivy ZIP, které se mají dekomprimovat v systémech jiných než Windows</span><span class="sxs-lookup"><span data-stu-id="0de45-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="0de45-107">Dekomprimace souboru ZIP vytvořeného aplikací, která cílí na předchozí verzi .NET Framework v operačních systémech jiných než Windows, jako je například Macintosh, se nepodařilo zachovat adresářovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="0de45-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="0de45-108">Například v počítači Macintosh vytvoří sadu souborů, jejichž název souboru zřetězí cestu k adresáři, spolu se znakem zpětného lomítka ("\\") a názvem souboru.</span><span class="sxs-lookup"><span data-stu-id="0de45-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="0de45-109">V důsledku toho není zachována adresářová struktura dekomprimovaných souborů.</span><span class="sxs-lookup"><span data-stu-id="0de45-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="0de45-110">Dopad této změny na. Soubory zip, které jsou v operačním systému Windows dekomprimovány pomocí rozhraní API v <xref:System.IO> oboru názvů .NET Framework, by měly mít minimální hodnotu, protože tato rozhraní API můžou bez problémů zpracovávat lomítka ("/") nebo\\zpětné lomítko ("") jako znak oddělovače cesty.</span><span class="sxs-lookup"><span data-stu-id="0de45-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0de45-111">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="0de45-111">Mitigation</span></span>  
 <span data-ttu-id="0de45-112">Pokud je toto chování nežádoucí, můžete se odhlásit přidáním nastavení konfigurace do [ \<oddílu modulu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="0de45-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="0de45-113">Následující příklad ukazuje `<runtime>` oddíl i přepínač pro odhlášení.</span><span class="sxs-lookup"><span data-stu-id="0de45-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="0de45-114">Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží na .NET Framework 4.6.1 a novějších verzích, se můžou k tomuto chování vyjádřit přidáním nastavení konfigurace do [ \<části modulu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) aplikace. konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="0de45-114">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="0de45-115">Následující příklad ukazuje `<runtime>` oddíl i přepínač pro výslovný souhlas.</span><span class="sxs-lookup"><span data-stu-id="0de45-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0de45-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0de45-116">See also</span></span>

- [<span data-ttu-id="0de45-117">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="0de45-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
- [<span data-ttu-id="0de45-118">Kompatibilita aplikací v 4.6.1</span><span class="sxs-lookup"><span data-stu-id="0de45-118">Application Compatibility in 4.6.1</span></span>](application-compatibility-in-the-net-framework-4-6-1.md)
