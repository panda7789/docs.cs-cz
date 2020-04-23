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
ms.openlocfilehash: 3f6c7f258fd5dbf01db4d79b73b88ddd7484f9b2
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102616"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="f7386-102">Zmírnění: Oddělovač cesty ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="f7386-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="f7386-103">Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.1, se oddělovač cesty použitý ve <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> vlastnosti změnil z zpětného lomítka ("\\") používaného v předchozích verzích rozhraní .NET Framework na lomítko ("/").</span><span class="sxs-lookup"><span data-stu-id="f7386-103">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="f7386-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>objekty jsou vytvořeny voláním jednoho <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> z přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="f7386-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f7386-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="f7386-105">Impact</span></span>  
 <span data-ttu-id="f7386-106">Změna uvede implementaci .NET do souladu s oddílem 4.4.17.1 [. SPECIFIKACE FORMÁTU SOUBORU ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje . ZIP archivy, které mají být dekomprimovány v systémech, které nejsou systémy Windows.</span><span class="sxs-lookup"><span data-stu-id="f7386-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="f7386-107">Dekomprese souboru ZIP vytvořeného aplikací, která cílí na předchozí verzi rozhraní .NET Framework v operačních systémech mimo windows, jako je MacOS, nezachová adresářovou strukturu.</span><span class="sxs-lookup"><span data-stu-id="f7386-107">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="f7386-108">Například v systému MacOS vytvoří sadu souborů, jejichž název souboru zřetězí cestu\\k adresáři, všechny znaky zpětného lomítka (") a název souboru.</span><span class="sxs-lookup"><span data-stu-id="f7386-108">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="f7386-109">V důsledku toho není zachována adresářová struktura dekomprimovaných souborů.</span><span class="sxs-lookup"><span data-stu-id="f7386-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="f7386-110">Dopad této změny na . Soubory ZIP, které jsou dekomprimovány v operačním systému Windows pomocí rozhraní API v oboru názvů rozhraní .NET Framework, <xref:System.IO> by měly\\být minimální, protože tato rozhraní API mohou bez problémů zpracovat lomítko ("/") nebo zpětné lomítko (") jako znak oddělovače cesty.</span><span class="sxs-lookup"><span data-stu-id="f7386-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f7386-111">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="f7386-111">Mitigation</span></span>  
 <span data-ttu-id="f7386-112">Pokud je toto chování nežádoucí, můžete se odhlásit přidáním nastavení konfigurace do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7386-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="f7386-113">V následujícím textu `<runtime>` je uveden oddíl i přepínač pro odhlášení.</span><span class="sxs-lookup"><span data-stu-id="f7386-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="f7386-114">Kromě toho se aplikace, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6.1 a novějších verzích, mohou přihlásit k tomuto chování přidáním nastavení konfigurace do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7386-114">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="f7386-115">V následujícím textu `<runtime>` je uveden oddíl i přepínač pro přihlášení.</span><span class="sxs-lookup"><span data-stu-id="f7386-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7386-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7386-116">See also</span></span>

- [<span data-ttu-id="f7386-117">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="f7386-117">Application compatibility</span></span>](application-compatibility.md)
