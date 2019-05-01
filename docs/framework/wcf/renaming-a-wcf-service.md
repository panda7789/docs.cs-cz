---
title: Přejmenování služby WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955139"
---
# <a name="renaming-a-wcf-service"></a>Přejmenování služby WCF
Toto téma popisuje, jak můžete přejmenovat služby Windows Communication Foundation (WCF).  
  
## <a name="renaming-a-wcf-service"></a>Přejmenování služby WCF  
 Proveďte následující kroky pro přejmenování služby v šabloně služby Windows Communication Foundation (WCF)  
  
- Změňte název třídy, která implementuje služby.  
  
- V konfiguračním souboru služby změňte název služby na nový název, který jste zvolili, jak je uvedeno v následujícím příkladu. Konfigurační soubor může být soubor app.config nebo web.config v závislosti na modelu hostingu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- Pokud je služba webhosted, používá soubor *.svc. Otevřete soubor svc file a změnit název vaší služby, jak je uvedeno v následujícím příkladu. Tento krok není nezbytné pro aplikace v místním prostředí, protože není dostupný žádný soubor svc.  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Přejmenování kontraktu služby WCF  
  
- Proveďte následující kroky pro přejmenování kontrakt služby  
  
- Změňte název kontraktu služby.  
  
- V konfiguračním souboru služby změňte název kontraktu služby na nový název, který jste zvolili, jak je uvedeno v následujícím příkladu. Konfigurační soubor může být soubor app.config nebo web.config v závislosti na modelu hostingu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
