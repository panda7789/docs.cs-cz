---
title: "Omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ca43e4952f7ff457cf61c2c36334ab6213e50ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="9e775-102">Omezení rizik: Oddělovač cesty ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="9e775-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="9e775-103">Počínaje aplikací cílených [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], cesta oddělovač použitý v <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnost bylo změněno z zpětné lomítko ("\\") používají v předchozích verzích rozhraní .NET Framework na dopředné lomítko ("/").</span><span class="sxs-lookup"><span data-stu-id="9e775-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="9e775-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>objekty jsou vytvořené pomocí jednoho z přetížení volání <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="9e775-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9e775-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="9e775-105">Impact</span></span>  
 <span data-ttu-id="9e775-106">Tato změna přináší implementace rozhraní .NET do souladu s části 4.4.17.1 [. Specifikace formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. ZIP archivy k dekomprimaci na jiné operační systémy.</span><span class="sxs-lookup"><span data-stu-id="9e775-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="9e775-107">Dekompresi soubor zip vytvořené aplikace s cílem předchozí verzi rozhraní .NET Framework na jiný systém než Windows operační systémy, třeba Macintosh nepodaří zachovat strukturu adresáře.</span><span class="sxs-lookup"><span data-stu-id="9e775-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="9e775-108">Například na Macintosh, vytvoří sadu souborů, jejichž název souboru zřetězí cesta k adresáři, společně s žádné zpětné lomítko ("\\") znaků a název souboru.</span><span class="sxs-lookup"><span data-stu-id="9e775-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="9e775-109">V důsledku toho není zachován struktura adresářů dekomprimovaných souborů.</span><span class="sxs-lookup"><span data-stu-id="9e775-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="9e775-110">Dopad na tuto změnu. Soubory ZIP, které jsou dekomprimovat operačního systému Windows pomocí rozhraní API v rozhraní .NET Framework <xref:System.IO> oboru názvů musí být minimální, protože tato rozhraní API může bezproblémově zpracovat lomítko ("/") ani zpětné lomítko ("\\") jako cesta oddělovací znak.</span><span class="sxs-lookup"><span data-stu-id="9e775-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9e775-111">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="9e775-111">Mitigation</span></span>  
 <span data-ttu-id="9e775-112">Pokud je toto chování žádoucí, můžete zvolit z přidáním nastavení konfigurace, pro které [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddíl konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e775-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="9e775-113">Následující příklad zobrazuje i `<runtime>` části a vyjádření výslovného nesouhlasu s přepínačem.</span><span class="sxs-lookup"><span data-stu-id="9e775-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="9e775-114">Kromě toho aplikace, které cílí na předchozích verzích rozhraní .NET Framework, ale jsou spuštěny na [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a novější verze můžete vyjádřit výslovný souhlas pro toto chování přidáním nastavení konfigurace, pro které [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e775-114">In addition, apps that target previous versions of the .NET Framework but are running on the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="9e775-115">Následující příklad zobrazuje i `<runtime>` části a přepínače přihlášení.</span><span class="sxs-lookup"><span data-stu-id="9e775-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e775-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e775-116">See Also</span></span>  
 [<span data-ttu-id="9e775-117">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="9e775-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)  
 [<span data-ttu-id="9e775-118">Kompatibilita aplikací v 4.6.1</span><span class="sxs-lookup"><span data-stu-id="9e775-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
