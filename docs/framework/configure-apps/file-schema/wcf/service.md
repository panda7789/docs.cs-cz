---
title: '&lt;Služby&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: a73e4699e0998338f09e1ed0504f5b1cfd73b225
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicegt"></a>&lt;Služby&gt;
`service` Element obsahuje nastavení pro službu Windows Communication Foundation (WCF). Obsahuje taky koncových bodů, které službu vystavit.  
  
 \<system.ServiceModel>  
\<služby >  
\<služby >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|behaviorConfiguration|Řetězec, který obsahuje název chování chování, který se má použít k vytvoření instance služby. Název chování musí být v rozsahu na bod, který je definován službu. Výchozí hodnota je prázdný řetězec.|  
|name|Vyžaduje atribut řetězec, který určuje typ službu, kterou chcete vytvořit instanci. Toto nastavení musí rovnat platného typu. Musí být ve formátu `Namespace.Class.`|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|Kolekce `endpoint` elementy, které zveřejňují této služby.|  
|[\<hostitele >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Určuje hostitele této instance služby. Tento element je typu <xref:System.ServiceModel.Configuration.HostElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<služby >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Kořenový element všechny konfigurační prvky WCF.|  
  
## <a name="remarks"></a>Poznámky  
 Služby jsou definovány v `services` oddílu konfiguračního souboru. Sestavení může obsahovat libovolný počet služeb. Každá služba má svůj vlastní `service` konfigurační oddíl. V této části a jejího obsahu definovat kontrakt služby, chování a koncové body konkrétní služby.  
  
 `behaviorConfiguration` Prvek je volitelný. Určuje chování služba používá. Chování v tomto atributu musí propojit chování v oboru ve stejném souboru konfigurace.  
  
 Každá služba zpřístupní jeden nebo více koncových bodů, které má svou vlastní adresu a vazby. Všechny vazby používaných v rámci konfiguračního souboru musí být definován v oboru souboru. Vazba jsou propojeny s koncových bodů prostřednictvím kombinace atributů `name` a `bindingConfiguration`. `name` Atribut popisuje části vazba je definováno v. `bindingConfiguration` Atribut definuje, jakou konfiguraci v oddílu vazby se používá. Vazba části můžete definovat několik konfigurací.  
  
## <a name="example"></a>Příklad  
 Toto je příklad konfigurace služby.  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [Konfigurace služeb](../../../../../docs/framework/wcf/configuring-services.md)
