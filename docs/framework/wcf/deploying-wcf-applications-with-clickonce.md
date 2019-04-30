---
title: Nasazení aplikací služby WCF technologií ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 1820b00aa903633750f74f319f9cf8038ba2b043
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785087"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="92325-102">Nasazení aplikací služby WCF technologií ClickOnce</span><span class="sxs-lookup"><span data-stu-id="92325-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="92325-103">Klientským aplikacím pomocí služby Windows Communication Foundation (WCF) mohou být nasazeny pomocí technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="92325-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="92325-104">Tato technologie umožňuje využít modulu runtime zabezpečení poskytovanou zabezpečení přístupu kódu, za předpokladu, že jsou digitálně podepsané důvěryhodným certifikátem.</span><span class="sxs-lookup"><span data-stu-id="92325-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="92325-105">Certifikát použitý k podepsání aplikace ClickOnce se musí nacházet v úložišti důvěryhodné vydavatele a místních zásad zabezpečení v klientském počítači musí být nakonfigurovaný k udělení oprávnění plné důvěryhodnosti pro podepsané certifikátem pro vydavatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="92325-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="92325-106">Informace o konfiguraci aplikací ClickOnce a důvěryhodné vydavatele najdete v tématu [konfigurace Důvěryhodní vydavatelé ClickOnce](https://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="92325-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92325-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92325-107">See also</span></span>

- [<span data-ttu-id="92325-108">Přehled nasazení důvěryhodných aplikací</span><span class="sxs-lookup"><span data-stu-id="92325-108">Trusted Application Deployment Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=94775)
- [<span data-ttu-id="92325-109">ClickOnce – nasazení pro Windows Forms aplikací</span><span class="sxs-lookup"><span data-stu-id="92325-109">ClickOnce Deployment for Windows Forms Applications</span></span>](https://go.microsoft.com/fwlink/?LinkId=94776)
