---
title: "Nasazení aplikací služby WCF technologií ClickOnce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e87e01c39c5f50ff3f4d4e9479a68e19cceb90f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="aa27c-102">Nasazení aplikací služby WCF technologií ClickOnce</span><span class="sxs-lookup"><span data-stu-id="aa27c-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="aa27c-103">Klientským aplikacím pomocí [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] dá nasadit pomocí technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="aa27c-103">Client applications using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="aa27c-104">Tato technologie umožňuje, aby využít výhod modulu runtime ochranu zabezpečení poskytované zabezpečení přístupu kódu, za předpokladu, že jsou digitálně podepsané důvěryhodným certifikátem.</span><span class="sxs-lookup"><span data-stu-id="aa27c-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="aa27c-105">Certifikát použitý k podepsání aplikace ClickOnce se musí nacházet v úložišti důvěryhodné vydavatele a místních zásad zabezpečení v klientském počítači musí být nakonfigurován pro udělení oprávnění úplné důvěryhodnosti pro aplikace podepsaný pomocí certifikátu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="aa27c-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="aa27c-106">Informace o konfiguraci aplikace ClickOnce a důvěryhodné vydavatele najdete v tématu [konfigurace Důvěryhodní vydavatelé ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="aa27c-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa27c-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa27c-107">See Also</span></span>  
 [<span data-ttu-id="aa27c-108">Přehled nasazení důvěryhodných aplikací</span><span class="sxs-lookup"><span data-stu-id="aa27c-108">Trusted Application Deployment Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=94775)  
 [<span data-ttu-id="aa27c-109">Aplikace ClickOnce – nasazení pro systém Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa27c-109">ClickOnce Deployment for Windows Forms Applications</span></span>](http://go.microsoft.com/fwlink/?LinkId=94776)
