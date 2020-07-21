---
title: 'Zmírnění rizika: kontroly středních cest'
description: Přečtěte si o změnách provedených v .NET Framework 4.6.2 pro podporu kontrol správné syntaxe oddělovače jednotek (dvojtečka).
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: f32ee54f88bc4747fd0d8065b0dce06b151d1d9a
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475447"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="05c95-103">Zmírnění rizika: kontroly středních cest</span><span class="sxs-lookup"><span data-stu-id="05c95-103">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="05c95-104">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, byl proveden určitý počet změn pro podporu dříve nepodporovaných cest (z hlediska délky i formátu).</span><span class="sxs-lookup"><span data-stu-id="05c95-104">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="05c95-105">Konkrétně jsou zkontrolovány správné syntaxe oddělovače jednotek (dvojtečka).</span><span class="sxs-lookup"><span data-stu-id="05c95-105">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="05c95-106">Dopad</span><span class="sxs-lookup"><span data-stu-id="05c95-106">Impact</span></span>  
 <span data-ttu-id="05c95-107">Tyto změny blokují některé cesty identifikátorů URI, které <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> dříve podporovaly metody a.</span><span class="sxs-lookup"><span data-stu-id="05c95-107">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="05c95-108">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="05c95-108">Mitigation</span></span>  
 <span data-ttu-id="05c95-109">Chcete-li se vyhnout problému dříve přijatelné cesty, která již není podporována <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metodami a, můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="05c95-109">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="05c95-110">Ručně odeberte schéma z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="05c95-110">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="05c95-111">Například odeberte `file://` z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="05c95-111">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="05c95-112">Předejte identifikátor URI <xref:System.Uri> konstruktoru a načtěte hodnotu <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="05c95-112">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="05c95-113">Odhlášení od nové normalizace cest nastavením `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> přepínače na `true` .</span><span class="sxs-lookup"><span data-stu-id="05c95-113">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="05c95-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="05c95-114">See also</span></span>

- [<span data-ttu-id="05c95-115">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="05c95-115">Application compatibility</span></span>](application-compatibility.md)
