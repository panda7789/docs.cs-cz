---
title: Zmírnění Kontroly dvojtečky cest
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a74c25a9bf4dd8b9ab86bd280881fe1a7999e1d5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789994"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="4609b-102">Zmírnění Kontroly dvojtečky cest</span><span class="sxs-lookup"><span data-stu-id="4609b-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="4609b-103">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, byl proveden určitý počet změn pro podporu dříve nepodporovaných cest (z hlediska délky i formátu).</span><span class="sxs-lookup"><span data-stu-id="4609b-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="4609b-104">Konkrétně jsou zkontrolovány správné syntaxe oddělovače jednotek (dvojtečka).</span><span class="sxs-lookup"><span data-stu-id="4609b-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="4609b-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="4609b-105">Impact</span></span>  
 <span data-ttu-id="4609b-106">Tyto změny blokují některé cesty identifikátorů <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> URI <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> , které dříve podporovaly metody a.</span><span class="sxs-lookup"><span data-stu-id="4609b-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="4609b-107">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="4609b-107">Mitigation</span></span>  
 <span data-ttu-id="4609b-108">Chcete-li se vyhnout problému dříve přijatelné cesty, která již není podporována <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> metodami a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> , můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="4609b-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="4609b-109">Ručně odeberte schéma z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="4609b-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="4609b-110">Například odeberte `file://` z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="4609b-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="4609b-111">Předejte identifikátor URI <xref:System.Uri> konstruktoru a načtěte hodnotu <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4609b-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="4609b-112">Odhlášení od nové normalizace `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> cest nastavením přepínače na `true`.</span><span class="sxs-lookup"><span data-stu-id="4609b-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4609b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4609b-113">See also</span></span>

- [<span data-ttu-id="4609b-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="4609b-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-2.md)
