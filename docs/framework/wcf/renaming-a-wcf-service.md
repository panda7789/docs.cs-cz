---
title: Přejmenování služby WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2ab3d780f85131fc7adf24c5f420bd5fe643d9e
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="renaming-a-wcf-service"></a>Přejmenování služby WCF
Toto téma popisuje, jak můžete přejmenovat [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby.  
  
## <a name="renaming-a-wcf-service"></a>Přejmenování služby WCF  
 Proveďte následující kroky pro přejmenování služby ve službě [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] šablony,  
  
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
