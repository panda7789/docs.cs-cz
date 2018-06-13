---
title: Nasazení aplikací služby WCF technologií ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: ceb652eed1a7cc377538f5d693dcb85ed99da4b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456693"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="4d6ee-102">Nasazení aplikací služby WCF technologií ClickOnce</span><span class="sxs-lookup"><span data-stu-id="4d6ee-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="4d6ee-103">Klientským aplikacím pomocí služby Windows Communication Foundation (WCF) mohou být nasazeny pomocí technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="4d6ee-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="4d6ee-104">Tato technologie umožňuje, aby využít výhod modulu runtime ochranu zabezpečení poskytované zabezpečení přístupu kódu, za předpokladu, že jsou digitálně podepsané důvěryhodným certifikátem.</span><span class="sxs-lookup"><span data-stu-id="4d6ee-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="4d6ee-105">Certifikát použitý k podepsání aplikace ClickOnce se musí nacházet v úložišti důvěryhodné vydavatele a místních zásad zabezpečení v klientském počítači musí být nakonfigurován pro udělení oprávnění úplné důvěryhodnosti pro aplikace podepsaný pomocí certifikátu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="4d6ee-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="4d6ee-106">Informace o konfiguraci aplikace ClickOnce a důvěryhodné vydavatele najdete v tématu [konfigurace Důvěryhodní vydavatelé ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="4d6ee-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d6ee-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d6ee-107">See Also</span></span>  
 [<span data-ttu-id="4d6ee-108">Přehled nasazení důvěryhodných aplikací</span><span class="sxs-lookup"><span data-stu-id="4d6ee-108">Trusted Application Deployment Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=94775)  
 [<span data-ttu-id="4d6ee-109">Aplikace ClickOnce – nasazení pro systém Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4d6ee-109">ClickOnce Deployment for Windows Forms Applications</span></span>](http://go.microsoft.com/fwlink/?LinkId=94776)
