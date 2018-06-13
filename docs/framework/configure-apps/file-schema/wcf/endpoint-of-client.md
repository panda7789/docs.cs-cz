---
title: '&lt;endpoint&gt; – &lt;client&gt;'
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f9a69483ab058823fd419edc84868e801b91d2c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748058"
---
# <a name="ltendpointgt-of-ltclientgt"></a>&lt;endpoint&gt; – &lt;client&gt;
Určuje kontrakt, vazbu a vlastnosti adresy koncového bodu kanálu, který je používaný klienty pro připojení ke koncovým bodům služby na serveru.  
  
 \<system.ServiceModel>  
\<klient >  
\<koncový bod >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   contract="String"   endpointConfiguration="String"   kind="String"  
   name="String"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|adresa|Požadovaný atribut typu string.<br /><br /> Určuje adresu koncového bodu. Výchozí hodnota je prázdný řetězec. Tato adresa musí být absolutní identifikátor URI.|  
|behaviorConfiguration|Řetězec, který obsahuje název chování chování, který se má použít k vytváření instancí koncový bod. Název chování musí být v rozsahu na bod, který je definován službu. Výchozí hodnota je prázdný řetězec.|  
|vazba|Požadovaný atribut typu string.<br /><br /> Řetězec, který určuje typ vazby použít. Typ musí mít registrovaný konfigurační oddíl, aby na něj odkazovat. Typ je registrován podle názvu části místo název typu vazby.|  
|bindingConfiguration|Volitelné. Řetězec, který obsahuje název konfigurace vazby, který se má použít při vytváření instance koncový bod. Konfigurace vazeb musí být v rozsahu na bod, který je definován koncový bod. Výchozí hodnota je prázdný řetězec.<br /><br /> Tento atribut se používá ve spojení s `binding` tak, aby odkazovaly konfigurace konkrétní vazeb v konfiguračním souboru. Tento atribut nastavte, pokud se pokoušíte použít vlastní vazby. Jinak může být vyvolána výjimka.|  
|kontrakt|Požadovaný atribut typu string.<br /><br /> Řetězec, který určuje, které kontrakt tento koncový bod je vystavení. Sestavení musí implementovat typ smlouvy.|  
|endpointConfiguration|Řetězec, který určuje název standardní koncového bodu, který se nastavuje pomocí `kind` atribut, který odkazuje na další konfigurační informace tohoto standardní koncového bodu. Se stejným názvem, musí být definován v `<standardEndpoints>` oddílu.|  
|Typ|Řetězec, který určuje typ standardní koncového bodu použít. Typ musí být zaregistrovaný ve `<extensions>` části nebo v souboru machine.config. Pokud není zadáno žádné umístění, vytvoří se koncový bod běžné kanálu.|  
|name|Volitelný řetězec atributu. Tento atribut jednoznačně identifikuje koncový bod pro danou zakázku. Můžete definovat více klientů pro daný typ kontrakt. Každá definice musí rozlišené pomocí jedinečný název konfigurace. Pokud tento atribut je vynechán, odpovídající koncový bod se používá jako výchozí koncový bod spojená se zadaným typem kontrakt. Výchozí hodnota je prázdný řetězec.<br /><br /> `name` Atribut vazby se používá pro export definice prostřednictvím WSDL.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<hlavičky >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Kolekce hlavičky adresy.|  
|[\<identity >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Identita, která umožňuje ověření koncový bod pomocí dalších koncových bodů výměna zpráv s ním.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<klient >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Konfigurační oddíl, který definuje seznam koncových bodů, které klient může připojit k.|  
  
## <a name="example"></a>Příklad  
 Toto je příklad konfigurace koncového bodu kanálu.  
  
```xml  
<endpoint address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    name="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
</endpoint>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>  
 <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 [Konfigurace klienta WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienti](../../../../../docs/framework/wcf/feature-details/clients.md)
