---
title: 'Zmírnění rizika: kontroly středních cest'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: e88643fea3bd507289436f41880a2de34117884f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457906"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="b36e1-102">Zmírnění rizika: kontroly středních cest</span><span class="sxs-lookup"><span data-stu-id="b36e1-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="b36e1-103">Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, byl proveden určitý počet změn pro podporu dříve nepodporovaných cest (z hlediska délky i formátu).</span><span class="sxs-lookup"><span data-stu-id="b36e1-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="b36e1-104">Konkrétně jsou zkontrolovány správné syntaxe oddělovače jednotek (dvojtečka).</span><span class="sxs-lookup"><span data-stu-id="b36e1-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b36e1-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="b36e1-105">Impact</span></span>  
 <span data-ttu-id="b36e1-106">Tyto změny blokují některé cesty identifikátorů URI, které byly dříve podporovány metodami <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b36e1-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b36e1-107">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="b36e1-107">Mitigation</span></span>  
 <span data-ttu-id="b36e1-108">Chcete-li se vyhnout problému dříve přijatelné cesty, která již není podporována <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>mi metodami, můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="b36e1-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="b36e1-109">Ručně odeberte schéma z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="b36e1-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="b36e1-110">Odeberte například `file://` z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="b36e1-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="b36e1-111">Předejte identifikátor URI konstruktoru <xref:System.Uri> a načtěte hodnotu vlastnosti <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b36e1-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="b36e1-112">Odhlášení od nové normalizace cest nastavením `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> přepínač na `true`.</span><span class="sxs-lookup"><span data-stu-id="b36e1-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b36e1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b36e1-113">See also</span></span>

- [<span data-ttu-id="b36e1-114">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="b36e1-114">Application compatibility</span></span>](application-compatibility.md)
