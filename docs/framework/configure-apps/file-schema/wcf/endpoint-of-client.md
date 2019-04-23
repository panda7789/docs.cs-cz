---
title: <endpoint> z <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 3af41ad5b5681b08aac44d984372ab5ac66caf5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231198"
---
# <a name="endpoint-of-client"></a>\<koncový bod > z \<klienta >
Určuje kontrakt vazby a vlastnosti adresy koncového bodu kanálu, který používají klienti pro připojení ke koncovým bodům služby na serveru.  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|adresa|Požadovaný atribut typu string.<br /><br /> Určuje adresu koncového bodu. Výchozí hodnota je prázdný řetězec. Tato adresa musí být absolutní identifikátor URI.|  
|behaviorConfiguration|Řetězec obsahující název chování, jenž bude použit k vytvoření instance koncového bodu. Název musí být v rozsahu od bodu služby je definována. Výchozí hodnota je prázdný řetězec.|  
|vazba|Požadovaný atribut typu string.<br /><br /> Řetězec, který označuje typ použité vazby. Typ musí mít registrované konfigurační oddíl pro odkazovat. Název oddílu, zaregistrován typ místo podle názvu typu vazby.|  
|bindingConfiguration|Volitelné. Řetězec, který obsahuje název konfigurace vazby, která se použije při vytvoření instance koncového bodu. Konfigurace vazby musí být v rozsahu od bodu na koncový bod je definována. Výchozí hodnota je prázdný řetězec.<br /><br /> Tento atribut se používá ve spojení s `binding` odkazovat konfigurace konkrétní vazby v konfiguračním souboru. Tento atribut nastavte, pokud se pokoušíte použít vlastní vazby. V opačném případě může být vyvolána výjimka.|  
|kontrakt|Požadovaný atribut typu string.<br /><br /> Řetězec označující kontrakt, který tento koncový bod vystavuje. Sestavení musí implementovat typ kontraktu.|  
|endpointConfiguration|Řetězec určující název standardního koncového bodu, který je nastaven podle `kind` atribut, který odkazuje na další konfigurační informace tohoto standardního koncového bodu. Se stejným názvem musí být definován v `<standardEndpoints>` oddílu.|  
|Typ|Řetězec, který určuje typ standardně použitého koncového bodu. Typ musí být zaregistrovaný ve `<extensions>` části nebo v souboru machine.config. Pokud není zadáno žádné umístění, vytvoří se běžné koncového bodu kanálu.|  
|name|Volitelný atribut řetězce. Tento atribut jednoznačně identifikuje koncový bod pro daný kontrakt. Můžete definovat více klientů pro daný typ kontraktu. Každá definice musí možné odlišit použitím jedinečný název konfigurace. Pokud tento atribut je vynechán, odpovídající koncový bod se používá jako výchozí koncový bod spojený se zadaným typem kontraktu. Výchozí hodnota je prázdný řetězec.<br /><br /> `name` Atribut vazby se používá pro export definice prostřednictvím WSDL.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Kolekce záhlaví adres.|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Identita, která umožňuje ověřování z koncového bodu jiné koncové body výměna zpráv s ním.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<client>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Konfigurační oddíl, který definuje seznam koncových bodů, které se klient může připojit k.|  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [Konfigurace klienta WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [Klienti](../../../../../docs/framework/wcf/feature-details/clients.md)
