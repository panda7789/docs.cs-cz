---
title: Přejmenování služby WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 8cb86621972423f55bfa18c60c1d4eb60cacb205
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651047"
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
