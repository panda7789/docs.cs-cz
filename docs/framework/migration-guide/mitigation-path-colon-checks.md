---
title: 'Omezení rizik: Path Colon Checks'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6799e36ec312bf857a12293dc0be15e9cc21f55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648459"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="27e2b-102">Omezení rizik: Path Colon Checks</span><span class="sxs-lookup"><span data-stu-id="27e2b-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="27e2b-103">Počínaje aplikací, které se zaměřují [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], počet změn byly provedeny na podporu dříve nepodporované cesty (jak z hlediska délku a formátu).</span><span class="sxs-lookup"><span data-stu-id="27e2b-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="27e2b-104">Konkrétně kontroly syntaxe správná jednotka oddělovač (dvojtečka) byly provedeny více správné.</span><span class="sxs-lookup"><span data-stu-id="27e2b-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="27e2b-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="27e2b-105">Impact</span></span>  
 <span data-ttu-id="27e2b-106">Tyto změny blokovat některé cesty identifikátoru URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody dříve podporovány.</span><span class="sxs-lookup"><span data-stu-id="27e2b-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="27e2b-107">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="27e2b-107">Mitigation</span></span>  
 <span data-ttu-id="27e2b-108">Chcete-li vyřešit problém dříve přijatelné cestu, která je již nejsou podporovány <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody, můžete provádět následující:</span><span class="sxs-lookup"><span data-stu-id="27e2b-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="27e2b-109">Schéma ručně odeberte z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="27e2b-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="27e2b-110">Například odebrat `file://` z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="27e2b-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="27e2b-111">Předat identifikátor URI <xref:System.Uri> konstruktoru a načtení hodnoty <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="27e2b-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="27e2b-112">Vyjádřit výslovný nesouhlas nové normalizace cestu tak, že nastavíte `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> přepnout na `true`.</span><span class="sxs-lookup"><span data-stu-id="27e2b-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="27e2b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27e2b-113">See also</span></span>

- [<span data-ttu-id="27e2b-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="27e2b-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
