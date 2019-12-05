---
title: Nasazení aplikací služby WCF technologií ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: b520931751bbba00d440b46657962ad3f1e41cd3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802231"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="eeadc-102">Nasazení aplikací služby WCF technologií ClickOnce</span><span class="sxs-lookup"><span data-stu-id="eeadc-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="eeadc-103">Klientské aplikace používající Windows Communication Foundation (WCF) se dají nasadit pomocí technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="eeadc-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="eeadc-104">Tato technologie umožňuje, aby mohli využít výhod ochrany zabezpečení za běhu poskytované zabezpečením přístupu kódu za předpokladu, že jsou digitálně podepsány důvěryhodným certifikátem.</span><span class="sxs-lookup"><span data-stu-id="eeadc-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="eeadc-105">Certifikát použitý k podepsání aplikace ClickOnce se musí nacházet v úložišti důvěryhodných vydavatelů a místní zásada zabezpečení na klientském počítači musí být nakonfigurovaná tak, aby udělila oprávnění úplný vztah důvěryhodnosti aplikacím podepsaným certifikátem vydavatele.</span><span class="sxs-lookup"><span data-stu-id="eeadc-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="eeadc-106">Informace o konfiguraci aplikací ClickOnce a důvěryhodných vydavatelů najdete v tématu [Konfigurace důvěryhodných vydavatelů ClickOnce](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="eeadc-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeadc-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eeadc-107">See also</span></span>

- [<span data-ttu-id="eeadc-108">Přehled nasazení důvěryhodných aplikací</span><span class="sxs-lookup"><span data-stu-id="eeadc-108">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)
- <span data-ttu-id="eeadc-109">[Nasazení ClickOnce pro aplikace model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="eeadc-109">[ClickOnce Deployment for Windows Forms Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span></span>
