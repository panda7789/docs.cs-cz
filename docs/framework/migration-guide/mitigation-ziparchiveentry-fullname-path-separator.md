---
title: 'Zmírnění rizika: ZipArchiveEntry. FullName – oddělovač cest'
description: Přečtěte si, jak se oddělovač cest pro vlastnost ZipArchiveEntry. FullName změnil počínaje aplikacemi, které cílí na .NET Framework 4.6.1.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 8cd6362038ce0548681f3d3b44724f3ef9ff62cb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475291"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="b4330-103">Zmírnění rizika: ZipArchiveEntry. FullName – oddělovač cest</span><span class="sxs-lookup"><span data-stu-id="b4330-103">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="b4330-104">Počínaje aplikacemi, které cílí na .NET Framework 4.6.1, se oddělovač cest použitý ve <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnosti změnil z zpětného lomítka (" \\ ") používaného v předchozích verzích .NET Framework na lomítko ("/").</span><span class="sxs-lookup"><span data-stu-id="b4330-104">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="b4330-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>objekty jsou vytvořeny voláním jednoho z přetížení <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b4330-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b4330-106">Dopad</span><span class="sxs-lookup"><span data-stu-id="b4330-106">Impact</span></span>  
 <span data-ttu-id="b4330-107">Tato změna přináší implementaci rozhraní .NET do souladu s oddílem 4.4.17.1 [. Specifikace formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. Archivy ZIP, které se mají dekomprimovat v systémech jiných než Windows</span><span class="sxs-lookup"><span data-stu-id="b4330-107">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="b4330-108">Dekomprimace souboru ZIP vytvořeného aplikací, která cílí na předchozí verzi .NET Framework v operačních systémech jiných než Windows, jako je například MacOS, se nepodařilo zachovat adresářovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="b4330-108">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="b4330-109">Například v MacOS vytvoří sadu souborů, jejichž název souboru zřetězí cestu k adresáři, znak zpětného lomítka (" \\ ") a název souboru.</span><span class="sxs-lookup"><span data-stu-id="b4330-109">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="b4330-110">V důsledku toho není zachována adresářová struktura dekomprimovaných souborů.</span><span class="sxs-lookup"><span data-stu-id="b4330-110">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="b4330-111">Dopad této změny na. Soubory ZIP, které jsou v operačním systému Windows dekomprimovány pomocí rozhraní API v .NET Framework <xref:System.IO> obor názvů by měly být minimální, protože tato rozhraní API můžou hladě zpracovávat lomítko ("/") nebo zpětné lomítko (" \\ ") jako znak oddělovače cesty.</span><span class="sxs-lookup"><span data-stu-id="b4330-111">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b4330-112">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="b4330-112">Mitigation</span></span>  
 <span data-ttu-id="b4330-113">Pokud je toto chování nežádoucí, můžete se odhlásit přidáním nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4330-113">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="b4330-114">Následující příklad ukazuje `<runtime>` oddíl i přepínač pro odhlášení.</span><span class="sxs-lookup"><span data-stu-id="b4330-114">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="b4330-115">Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 a novějších verzích se můžou k tomuto chování vyjádřit přidáním nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4330-115">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="b4330-116">Následující příklad ukazuje `<runtime>` oddíl i přepínač pro výslovný souhlas.</span><span class="sxs-lookup"><span data-stu-id="b4330-116">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4330-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4330-117">See also</span></span>

- [<span data-ttu-id="b4330-118">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="b4330-118">Application compatibility</span></span>](application-compatibility.md)
