---
title: Přejmenování služby WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 1179e7b235130e1967c79843b7a11f55622a01fb
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052049"
---
# <a name="renaming-a-wcf-service"></a>Přejmenování služby WCF
Toto téma popisuje, jak lze přejmenovat službu Windows Communication Foundation (WCF).  
  
## <a name="renaming-a-wcf-service"></a>Přejmenování služby WCF  
 Provedením následujících kroků přejmenujete službu v šabloně Windows Communication Foundation (WCF),  
  
- Změňte název třídy, která implementuje službu.  
  
- V konfiguračním souboru služby změňte název služby na nový název, který jste zvolili, jak je uvedeno v následujícím příkladu. Konfigurační soubor může být buď app.config, nebo web.config soubor v závislosti na modelu hostování.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- Pokud je vaše služba hostitelem webhostovaná, používá soubor * \* . svc* . Otevřete soubor svc a upravte název vaší služby, jak je uvedeno v následujícím příkladu. Tento krok není nutný pro samoobslužné aplikace, protože není k dispozici žádný soubor svc.  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Přejmenování kontraktu služby WCF  
  
- Chcete-li přejmenovat kontrakt služby, proveďte následující kroky.  
  
- Změňte název kontraktu služby.  
  
- V konfiguračním souboru služby změňte název kontraktu služby na nový název, který jste zvolili, jak je uvedeno v následujícím příkladu. Konfigurační soubor může být buď app.config, nebo web.config soubor v závislosti na modelu hostování.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
