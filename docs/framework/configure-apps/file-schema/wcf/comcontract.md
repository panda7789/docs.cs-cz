---
title: '&lt;comContract&gt;'
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: e2addbada7f55076ae919d93c897991a7ec0fcd8
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46507999"
---
# <a name="ltcomcontractgt"></a>&lt;comContract&gt;
Určuje kontrakt služby integrace modelu COM +.  
  
 \<system.ServiceModel>  
\<comContracts >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|kontrakt|Řetězec, který obsahuje typ kontraktu.|  
|name|Řetězec obsahující název kontraktu.|  
|– obor názvů|Řetězec, který obsahuje obor názvů kontraktu.|  
|Vlastnost requiresSession|Logická hodnota, která určuje, zda lze kontrakt použít pouze vazby s relacemi. Při inicializaci služby modulu runtime integrace zajišťuje, že toto nastavení je konzistentní s typem vazby který se má použít. Je vygenerována výjimka, pokud jeden nebo více vazeb pro kontrakt je v konfliktu. Pokud je tato vlastnost `false`a je jednosměrná kanál používá a [parametry out] existuje, je vygenerována výjimka.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|persistableTypes|Všechny trvalé typy.|  
|userDefinedTypes|Kolekce z uživateli definované typy (UDT), který je součástí kontraktu služby.|  
|exposedMethods|Kolekce metod modelu COM +, které jsou vystaveny při vystavení rozhraní komponenty COM + jako webovou službu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|comContracts|Obsahuje kolekci `comContract` elementy.|  
  
## <a name="remarks"></a>Poznámky  
 Kontrakty služby integrace modelu COM + jsou momentálně omezené jenom na `http://tempuri.org` oboru názvů a název smlouvy je odvozen z rozhraní COM podpůrné. Alternativy můžete však určit pomocí `comContracts` část, stejně jako `comContract` element v konfiguračním souboru. Například můžete použít následující konfigurace k určení oboru názvů, název kontraktu a uživatelsky definované typy, které mají být zahrnuty, jakož i další nastavení pro kontrakt služby.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 Při inicializaci služby zadaných oborů názvů trasy a názvy kontraktů se použijí na popis generované služeb.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [Integrace s aplikacemi modelu COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Postupy: Konfigurace nastavení služby modelu COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
