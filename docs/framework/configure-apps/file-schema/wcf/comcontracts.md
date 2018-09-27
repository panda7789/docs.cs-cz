---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 297a28181de8ce6ed658afad950f25cced9f9cb7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47402786"
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
`comContracts` Oddíl konfigurace obsahuje prvky, které vám umožňují určit různé vlastnosti kontraktu služby integrace modelu COM +.  
  
## <a name="specifying-namespace-and-contract"></a>Určení Namespace a smlouvy  
 Kontrakty služby integrace modelu COM + jsou momentálně omezené jenom na `http://tempuri.org` oboru názvů a název smlouvy je odvozen z rozhraní COM podpůrné. Můžete však určit alternativy pomocí `comContracts` oddílu v konfiguračním souboru.  
  
 Například můžete použít následující konfigurace k určení oboru názvů a kontrakt název kontraktu služby, stejně jako možnost vynutit použití vazby s relacemi.  
  
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
  
 Při inicializaci služby zadaných oborů názvů trasy a názvy kontraktů se použijí na popis generované služeb.  
  
 Když tato část je prázdná, inicializace služby se uplatní výchozí obor názvů a kontrakt název z podpůrné ID modelu COM rozhraní.  
  
 Kromě toho můžete použít [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementu k určení modelu COM + metody, které jsou vystaveny při vystavení rozhraní komponenty COM + jako webovou službu. Můžete také použít [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) k určení trvalé typy používané v integraci. Nakonec můžete použít [ \<typu userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element patří uživateli definované typy (UDT), které se mají být součástí kontraktu služby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [\<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [Integrace s aplikacemi modelu COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Postupy: Konfigurace nastavení služby modelu COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
