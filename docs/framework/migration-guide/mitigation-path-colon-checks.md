---
title: 'Zmírnění: Kontrola dvojtečky cesty'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: c6e1106b6f5d8457417992941b9f28712d484442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181249"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="a577f-102">Zmírnění: Kontrola dvojtečky cesty</span><span class="sxs-lookup"><span data-stu-id="a577f-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="a577f-103">Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.2, byla provedena řada změn pro podporu dříve nepodporovaných cest (z hlediska délky i formátu).</span><span class="sxs-lookup"><span data-stu-id="a577f-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="a577f-104">Zejména kontroly správné syntaxe oddělovače jednotky (dvojtečka) byly provedeny správnější.</span><span class="sxs-lookup"><span data-stu-id="a577f-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a577f-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="a577f-105">Impact</span></span>  
 <span data-ttu-id="a577f-106">Tyto změny blokují některé <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> cesty URI a dříve podporované metody.</span><span class="sxs-lookup"><span data-stu-id="a577f-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a577f-107">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="a577f-107">Mitigation</span></span>  
 <span data-ttu-id="a577f-108">Chcete-li obejít problém dříve přijatelné cesty, která <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> již není podporována a metody, můžete provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="a577f-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="a577f-109">Ručně odeberte schéma z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="a577f-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="a577f-110">Můžete například `file://` odebrat z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="a577f-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="a577f-111">Předajuridu uri konstruktoru <xref:System.Uri> a <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> načtěte hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a577f-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="a577f-112">Odhlásit se z nové normalizace `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> cesty `true`nastavením přepínače na .</span><span class="sxs-lookup"><span data-stu-id="a577f-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a577f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a577f-113">See also</span></span>

- [<span data-ttu-id="a577f-114">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="a577f-114">Application compatibility</span></span>](application-compatibility.md)
