---
title: Element &lt;endpoint&gt;
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: ef436acca40eaac135a54042b62abd76ec55febf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749501"
---
# <a name="ltendpointgt-element"></a>Element &lt;endpoint&gt;
Určuje vazby, kontrakt a vlastnosti adresy pro koncový bod služby, který se používá ke zveřejnění služby.  
  
 \<system.ServiceModel>  
\<služby >  
\<koncový bod >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   bindingName="String"  
   bindingNamespace="String"  
   contract="String"  
   endpointConfiguration="String"   isSystemEndpoint="Boolean"   kind="String"   listenUriMode="Explicit/Unique"  
   listenUri="Uri"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|adresa|Řetězec, který obsahuje adresu koncového bodu. Adresu lze zadat jako absolutní nebo relativní adresa. Pokud je zadaný relativní adresa, hostitel se očekává poskytování základní adresu, která je vhodná pro používané vazba schéma přenosu. Pokud adresa není nakonfigurována, základní adresu se považuje za adresu pro tohoto koncového bodu.<br /><br /> Výchozí hodnota je prázdný řetězec.|  
|behaviorConfiguration|Řetězec, který obsahuje název chování, který se má použít v koncovém bodě.|  
|vazba|Vyžaduje atribut řetězce, který určuje typ vazby použít. Typ musí mít registrovaný konfigurační oddíl, aby na něj odkazovat. Typ je zaregistrovanou podle názvu části, nikoli název typu vazby.|  
|bindingConfiguration|Řetězec, který určuje název vazby vazby pro použití při vytváření instance koncový bod. Název vazby musí být v rozsahu na bod, který je definován koncový bod. Výchozí hodnota je prázdný řetězec.<br /><br /> Tento atribut se používá ve spojení s `binding` tak, aby odkazovaly konfigurace konkrétní vazeb v konfiguračním souboru. Tento atribut nastavte, pokud se pokoušíte použít vlastní vazby. Jinak může být vyvolána výjimka.|  
|bindingName|Řetězec, který určuje jedinečný název kvalifikovaný vazby pro export definice prostřednictvím WSDL. Výchozí hodnota je prázdný řetězec.|  
|bindingNamespace|Řetězec, který určuje kvalifikovaný název oboru názvů vazby pro definici exportovat prostřednictvím WSDL. Výchozí hodnota je prázdný řetězec.|  
|kontrakt|Řetězec, který určuje, které kontrakt tento koncový bod je vystavení. Sestavení musí implementovat typ smlouvy. Pokud implementace služby implementuje typu jeden kontrakt, můžete tuto vlastnost vynechat. Výchozí hodnota je prázdný řetězec.|  
|endpointConfiguration|Řetězec, který určuje název standardní koncového bodu, který se nastavuje pomocí `kind` atribut, který odkazuje na další konfigurační informace tohoto standardní koncového bodu. Se stejným názvem, musí být definován v `<standardEndpoints>` oddílu.|  
|isSystemEndpoint|Logická hodnota, která určuje, jestli koncový bod je koncový bod infrastruktury.|  
|Typ|Řetězec, který určuje typ standardní koncového bodu použít. Typ musí být zaregistrovaný ve `<extensions>` části nebo v souboru machine.config. Pokud není zadáno žádné umístění, vytvoří se běžné koncového bodu služby.|  
|listenUriMode|Určuje, jak zpracovává přenos `ListenUri` zadaný pro službu pro naslouchání. Platné hodnoty jsou<br /><br /> -Explicitní<br />-Jedinečné<br /><br /> Výchozí hodnota je explicitní.|  
|Adrese ListenUri|Řetězec, který určuje identifikátor URI, na kterém naslouchá koncový bod služby. Výchozí hodnota je prázdný řetězec.|  
|name|Nepovinný atribut. Řetězec, který určuje název koncového bodu služby. Výchozí hodnota je zřetězení vazby název a popis názvu kontraktu. Služby mohou mít několik koncových bodů, takže pro koncový bod `name` atributu se liší od názvu služby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<hlavičky >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Kolekce hlavičky adresy.|  
|[\<identity >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Identita, která umožňuje ověření koncový bod pomocí dalších koncových bodů výměna zpráv s ním.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Konfigurační oddíl, který definuje seznam koncových bodů, které klient může připojit k.|  
  
## <a name="example"></a>Příklad  
 Toto je příklad konfigurace koncového bodu služby.  
  
```xml  
<endpoint   
    address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    bindingName="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
    <Headers>  
       <Region xmlns="http://tempuri.org/">EastCoast</Region>  
       <Member xmlns="http://tempuri.org/">Gold</Member>  
    </Headers>  
</endpoint>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceEndpointElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.Description.ServiceEndpoint>  
 [Koncové body: adresy, vazby a kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
