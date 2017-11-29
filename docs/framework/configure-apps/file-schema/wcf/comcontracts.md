---
title: '&lt;comContracts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 168bd57652aca5f3c1b61c90abea5288bd1a6719
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
`comContracts` Konfigurační oddíl obsahuje prvky, které umožňují určit různé vlastnosti modelu COM + integrace kontraktu služby.  
  
## <a name="specifying-namespace-and-contract"></a>Určení Namespace a kontraktu  
 Kontrakty služeb integrace COM + jsou aktuálně omezeno na obor názvů "http://tempuri.org" a název smlouvy je odvozený od podpůrné rozhraní modelu COM. Můžete však zadat alternativy pomocí `comContracts` oddíl v konfiguračním souboru.  
  
 Například můžete použít následující konfigurace zadat obor názvů a kontrakt název kontraktu služby, stejně jako možnost vynutit využití na relacemi vazby.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 Při inicializaci služby zadaných oborů názvů a názvy kontraktu platí pro popis generovaného služby.  
  
 Když tato část je prázdná, inicializace služby se uplatní výchozí obor názvů a kontrakt název prováděné z podpůrné ID. rozhraní COM  
  
 Kromě toho můžete použít [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element k určení modelu COM + metody, které jsou zveřejněné, pokud je jako webovou službu vystavený rozhraní komponenty modelu COM +. Můžete také [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) k určení trvalá typy používané v integrace. Nakonec můžete použít [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) elementu, který chcete zahrnout uživatele definované typy (UDT), které mají být zahrnuty do kontrakt služby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [\<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [\<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [Integrace s aplikacemi modelu COM +](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Postupy: Konfigurace nastavení služby COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
