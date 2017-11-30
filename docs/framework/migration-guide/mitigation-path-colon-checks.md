---
title: "Omezení rizik: Cesta dvojtečkou kontroly"
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
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a387e02c9d754db6af7fa2d2ba5f2ea6d96d4301
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="b14d8-102">Omezení rizik: Cesta dvojtečkou kontroly</span><span class="sxs-lookup"><span data-stu-id="b14d8-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="b14d8-103">Počínaje aplikací cílených [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], počet změn, byly provedeny na podporu dříve nepodporované cesty (jak z hlediska délku a format).</span><span class="sxs-lookup"><span data-stu-id="b14d8-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="b14d8-104">Konkrétně byly provedeny kontroly syntaxe oddělovače správné jednotky (dvojtečkou) více správné.</span><span class="sxs-lookup"><span data-stu-id="b14d8-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b14d8-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="b14d8-105">Impact</span></span>  
 <span data-ttu-id="b14d8-106">Tyto změny blokovat některé cesty identifikátoru URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody dřív podporované.</span><span class="sxs-lookup"><span data-stu-id="b14d8-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b14d8-107">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="b14d8-107">Mitigation</span></span>  
 <span data-ttu-id="b14d8-108">Chcete-li vyřešit problém dříve přijatelné cestu, která se už nepodporuje <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> a <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metod, můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="b14d8-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
-   <span data-ttu-id="b14d8-109">Schéma ručně odeberte z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="b14d8-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="b14d8-110">Například odebrat `file://` z adresy URL.</span><span class="sxs-lookup"><span data-stu-id="b14d8-110">For example, remove `file://` from a URL.</span></span>  
  
-   <span data-ttu-id="b14d8-111">Identifikátor URI pro předávání <xref:System.Uri> konstruktoru a načíst hodnotu <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b14d8-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
-   <span data-ttu-id="b14d8-112">Vyjádření výslovného nesouhlasu s novou cestu normalizaci nastavením `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> přepnout `true`.</span><span class="sxs-lookup"><span data-stu-id="b14d8-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b14d8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b14d8-113">See Also</span></span>  
 [<span data-ttu-id="b14d8-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="b14d8-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
