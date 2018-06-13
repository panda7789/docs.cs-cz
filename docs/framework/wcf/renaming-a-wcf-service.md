---
title: Přejmenování služby WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498984"
---
# <a name="renaming-a-wcf-service"></a>Přejmenování služby WCF
Toto téma popisuje, jak můžete přejmenovat služby Windows Communication Foundation (WCF).  
  
## <a name="renaming-a-wcf-service"></a>Přejmenování služby WCF  
 Proveďte následující kroky pro přejmenování služby v šabloně služby Windows Communication Foundation (WCF)  
  
-   Změňte název třídy, který implementuje službu.  
  
-   V konfiguračním souboru služby změňte název služby na nový název, který jste vybrali, jak je uvedeno v následujícím příkladu. Konfigurační soubor může být soubor app.config nebo web.config, v závislosti na hostování modelu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   Pokud je vaše služba webhosted, používá soubor *.svc. Otevřete soubor svc a změňte název vaší služby, jak je uvedeno v následujícím příkladu. Tento krok není nezbytné pro samoobslužné hostovaných aplikací, protože není dostupný žádný soubor svc.  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Přejmenování kontraktu služby WCF  
  
-   Proveďte následující kroky pro přejmenování kontrakt služby  
  
-   Změňte název kontraktu služby.  
  
-   V konfiguračním souboru služby změňte název kontraktu služby na nový název, který jste vybrali, jak je uvedeno v následujícím příkladu. Konfigurační soubor může být soubor app.config nebo web.config, v závislosti na hostování modelu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
