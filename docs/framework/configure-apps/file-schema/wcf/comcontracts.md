---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: b44c09e7e32129ba21834f7fbb8dc4699904e46b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746407"
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
`comContracts` Konfigurační oddíl obsahuje prvky, které umožňují určit různé vlastnosti modelu COM + integrace kontraktu služby.  
  
## <a name="specifying-namespace-and-contract"></a>Určení Namespace a kontraktu  
 Kontrakty služeb integrace COM + aktuálně omezeny na "http://tempuri.org" oboru názvů a název smlouvy je odvozený od podpůrné rozhraní modelu COM. Můžete však zadat alternativy pomocí `comContracts` oddíl v konfiguračním souboru.  
  
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
 [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [Integrace s aplikacemi modelu COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Postupy: Konfigurace nastavení služby modelu COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
