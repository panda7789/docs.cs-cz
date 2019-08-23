---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 69f3c70514fc2bcab1b4ef6a45036de98d1af7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936515"
---
# <a name="service"></a>\<> služby
`service` Element obsahuje nastavení pro službu Windows Communication Foundation (WCF). Obsahuje také koncové body, které zpřístupňují službu.  
  
 \<system.ServiceModel>  
\<> služeb  
\<> služby  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|behaviorConfiguration|Řetězec obsahující název chování, který se má použít k vytvoření instance služby. Název chování musí být v oboru v místě, kde je služba definovaná. Výchozí hodnota je prázdný řetězec.|  
|name|Požadovaný atribut typu řetězec určující typ služby, pro kterou má být vytvořena instance. Toto nastavení musí být rovno platnému typu. Formát by měl být`Namespace.Class.`|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|Kolekce `endpoint` prvků, které zpřístupňují tuto službu.|  
|[\<host>](host.md)|Určuje hostitele této instance služby. Tento prvek je typu <xref:System.ServiceModel.Configuration.HostElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<services>](services.md)|Kořenový element všech elementů konfigurace služby WCF.|  
  
## <a name="remarks"></a>Poznámky  
 Služby jsou definovány v `services` části konfiguračního souboru. Sestavení může obsahovat libovolný počet služeb. Každá služba má vlastní `service` konfigurační oddíl. Tato část a její obsah definují kontrakt služby, chování a koncové body konkrétní služby.  
  
 `behaviorConfiguration` Prvek je také volitelný. Určuje chování, které služba používá. Chování zadané v tomto atributu musí být propojeno s chováním v oboru ve stejném konfiguračním souboru.  
  
 Každá služba zveřejňuje jeden nebo více koncových bodů, které mají svou vlastní adresu a vazbu. Všechny vazby používané v konfiguračním souboru musí být definovány v rozsahu souboru. Vazba je propojena s koncovými body prostřednictvím kombinace atributů `name` a `bindingConfiguration`. `name` Atribut popisuje oddíl, ve kterém je vazba definována. `bindingConfiguration` Atribut určuje, která konfigurace v rámci vazby je použita. Oddíl Binding může definovat několik konfigurací.  
  
## <a name="example"></a>Příklad  
 Toto je příklad konfigurace služby.  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [Konfigurace služeb](../../../wcf/configuring-services.md)
