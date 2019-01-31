---
title: <endpoint> – element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 94b6cc6225171d90164e6d6880e1095513f16ece
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254454"
---
# <a name="endpoint-element"></a>\<koncový bod > – element
Určuje vazbu, kontrakt a vlastnosti adresy koncového bodu služby, který se používá k vystavení služby.  
  
 \<system.ServiceModel>  
\<služby >  
\<endpoint>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|adresa|Řetězec, který obsahuje adresu koncového bodu. Adresa se dá nastavit jako absolutní nebo relativní adresu. Pokud je zadána relativní adresa, hostitel se očekává poskytování vhodné pro schéma přenosu ve vazbě používá základní adresu. Pokud není konfigurována adresa, základní adresa je považován za adresu pro tento koncový bod.<br /><br /> Výchozí hodnota je prázdný řetězec.|  
|behaviorConfiguration|Řetězec obsahující název chování pro koncový bod.|  
|vazba|Požadovaný atribut typu řetězec, který určuje typ použité vazby. Typ musí mít registrované konfigurační oddíl pro odkazovat. Typ je zapsané podle názvu oddílu, nikoli podle názvu typu vazby.|  
|bindingConfiguration|Řetězec určující název vazby, použita při vytvoření instance koncového bodu. Název vazby musí být v rozsahu od bodu na koncový bod je definována. Výchozí hodnota je prázdný řetězec.<br /><br /> Tento atribut se používá ve spojení s `binding` odkazovat konfigurace konkrétní vazby v konfiguračním souboru. Tento atribut nastavte, pokud se pokoušíte použít vlastní vazby. V opačném případě může být vyvolána výjimka.|  
|bindingName|Řetězec určující jedinečný kvalifikovaný název vazby pro export definice prostřednictvím WSDL. Výchozí hodnota je prázdný řetězec.|  
|bindingNamespace|Řetězec určující kvalifikovaný název oboru názvů vazby pro definice prostřednictvím WSDL exportu Výchozí hodnota je prázdný řetězec.|  
|kontrakt|Řetězec označující kontrakt, který tento koncový bod vystavuje. Sestavení musí implementovat typ kontraktu. Pokud implementace služby implementuje typ jeden kontrakt, lze tuto vlastnost vynechat. Výchozí hodnota je prázdný řetězec.|  
|endpointConfiguration|Řetězec určující název standardního koncového bodu, který je nastaven podle `kind` atribut, který odkazuje na další konfigurační informace tohoto standardního koncového bodu. Se stejným názvem musí být definován v `<standardEndpoints>` oddílu.|  
|isSystemEndpoint|Logická hodnota určující, zda je koncový bod koncovým bodem infrastruktury.|  
|Typ|Řetězec, který určuje typ standardně použitého koncového bodu. Typ musí být zaregistrovaný ve `<extensions>` části nebo v souboru machine.config. Pokud není zadáno žádné umístění, je vytvořen společný koncový bod služby.|  
|listenUriMode|Určuje, jak přenos zachází `ListenUri` poskytnutým službě k naslouchání. Platné hodnoty jsou<br /><br /> -Explicitní<br />-Jedinečné<br /><br /> Výchozí hodnota je explicitní.|  
|listenUri|Řetězec určující identifikátor URI, na kterém naslouchá koncový bod služby. Výchozí hodnota je prázdný řetězec.|  
|name|Nepovinný atribut. Řetězec určující název koncového bodu služby. Výchozí hodnota je zřetězení vazby název a popis název kontraktu. Služby mohou mít několik koncových bodů, proto koncový bod `name` atributu se liší od názvu služby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Kolekce záhlaví adres.|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Identita, která umožňuje ověřování z koncového bodu jiné koncové body výměna zpráv s ním.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Konfigurační oddíl, který definuje seznam koncových bodů, které se klient může připojit k.|  
  
## <a name="example"></a>Příklad  
 Toto je příklad konfigurace koncového bodu služby.  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [Koncové body: Adresy, vazby a kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
