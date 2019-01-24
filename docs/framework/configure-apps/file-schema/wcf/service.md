---
title: '&lt;Služba&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: e91e04c602fd867e329477015fc0a8354ae26a05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535005"
---
# <a name="ltservicegt"></a>&lt;Služba&gt;
`service` Element obsahuje nastavení pro službu Windows Communication Foundation (WCF). Obsahuje také koncové body, které zpřístupňují služby.  
  
 \<system.ServiceModel>  
\<services>  
\<služby >  
  
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
|behaviorConfiguration|Řetězec obsahující název chování, jenž bude použit k vytvoření instance služby. Název musí být v rozsahu od bodu služby je definována. Výchozí hodnota je prázdný řetězec.|  
|name|Požadovaný atribut typu řetězec, který určuje typ služby, který má být vytvořena. Toto nastavení musí odpovídá platného typu. By měl být ve formátu `Namespace.Class.`|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|Kolekce `endpoint` prvky, které zpřístupňují této služby.|  
|[\<host>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Určuje řadu tato instance služby. Tento prvek je typu <xref:System.ServiceModel.Configuration.HostElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Kořenový element všechny elementy konfigurace WCF.|  
  
## <a name="remarks"></a>Poznámky  
 Služby jsou definovány v `services` oddílu konfiguračního souboru. Sestavení může obsahovat libovolný počet služeb. Každá služba má svůj vlastní `service` konfigurační oddíl. V této části a její obsah definování kontraktu služby, chování a koncové body konkrétní služby.  
  
 `behaviorConfiguration` Element je volitelné. Určuje chování služba používá. Chování určené v tomto atributu propojit chování v oboru ve stejném souboru konfigurace.  
  
 Každá služba zpřístupňuje jeden nebo více koncových bodů, který má svou vlastní adresu a vazbu. Všechny vazby používá v konfiguračním souboru musí být definován v rozsahu souboru. Vazby jsou propojeny do koncových bodů prostřednictvím kombinace atributů `name` a `bindingConfiguration`. `name` Atribut popisuje část vazby je definováno v. `bindingConfiguration` Atribut definuje, která konfigurace bude v rámci oddílu vazby se používá. Část vazby můžete definovat několik konfigurací.  
  
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
- [Konfigurace služeb](../../../../../docs/framework/wcf/configuring-services.md)
