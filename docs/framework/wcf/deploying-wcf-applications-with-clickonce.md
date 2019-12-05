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
# <a name="deploying-wcf-applications-with-clickonce"></a>Nasazení aplikací služby WCF technologií ClickOnce
Klientské aplikace používající Windows Communication Foundation (WCF) se dají nasadit pomocí technologie ClickOnce. Tato technologie umožňuje, aby mohli využít výhod ochrany zabezpečení za běhu poskytované zabezpečením přístupu kódu za předpokladu, že jsou digitálně podepsány důvěryhodným certifikátem. Certifikát použitý k podepsání aplikace ClickOnce se musí nacházet v úložišti důvěryhodných vydavatelů a místní zásada zabezpečení na klientském počítači musí být nakonfigurovaná tak, aby udělila oprávnění úplný vztah důvěryhodnosti aplikacím podepsaným certifikátem vydavatele.  
  
 Informace o konfiguraci aplikací ClickOnce a důvěryhodných vydavatelů najdete v tématu [Konfigurace důvěryhodných vydavatelů ClickOnce](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).  
  
## <a name="see-also"></a>Viz také:

- [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview)
- [Nasazení ClickOnce pro aplikace model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))
