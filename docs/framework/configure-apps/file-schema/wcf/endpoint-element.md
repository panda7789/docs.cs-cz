---
title: <endpoint> – element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855390"
---
# <a name="endpoint-element"></a>\<endpoint> – element
Určuje vazbu, kontrakt a vlastnosti adresy koncového bodu služby, který slouží k vystavení služeb.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
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
|adresa|Řetězec, který obsahuje adresu koncového bodu. Adresu lze zadat jako absolutní nebo relativní adresu. Pokud je zadána relativní adresa, očekává se, že hostitel poskytne základní adresu vhodnou pro přenosové schéma používané ve vazbě. Pokud není adresa nakonfigurovaná, předpokládá se, že základní adresa je adresa pro tento koncový bod.<br /><br /> Výchozí hodnota je prázdný řetězec.|  
|behaviorConfiguration|Řetězec obsahující název chování, které se má použít v koncovém bodě.|  
|vazba|Povinný atribut řetězce, který určuje typ vazby, která se má použít. Typ musí mít registrovaný konfigurační oddíl, aby na něj bylo odkazováno. Typ je zaregistrován podle názvu oddílu, nikoli podle názvu typu vazby.|  
|bindingConfiguration|Řetězec, který určuje název vazby vazby, která se má použít při vytvoření instance koncového bodu. Název vazby musí být v oboru v místě, kde je koncový bod definován. Výchozí hodnota je prázdný řetězec.<br /><br /> Tento atribut se používá ve spojení s `binding` pro odkazování na konkrétní konfiguraci vazby v konfiguračním souboru. Nastavte tento atribut, pokud se pokoušíte použít vlastní vazbu. V opačném případě může být vyvolána výjimka.|  
|Binding|Řetězec, který určuje jedinečný kvalifikovaný název vazby pro export definice prostřednictvím WSDL. Výchozí hodnota je prázdný řetězec.|  
|bindingNamespace|Řetězec, který určuje kvalifikovaný název oboru názvů vazby pro export definice prostřednictvím WSDL. Výchozí hodnota je prázdný řetězec.|  
|dodavatele|Řetězec označující kontrakt, který tento koncový bod vystavuje. Sestavení musí implementovat typ kontraktu. Pokud implementace služby implementuje jeden typ kontraktu, může být tato vlastnost vynechána. Výchozí hodnota je prázdný řetězec.|  
|endpointConfiguration|Řetězec, který určuje název standardního koncového bodu, který je nastaven `kind` atributem, který odkazuje na Další informace o konfiguraci tohoto standardního koncového bodu. V části se musí definovat stejný název `<standardEndpoints>` .|  
|isSystemEndpoint|Logická hodnota určující, zda je koncový bod koncovým bodem infrastruktury.|  
|plnění|Řetězec, který určuje typ použitého standardního koncového bodu. Typ musí být zaregistrován v `<extensions>` oddílu nebo v souboru Machine. config. Pokud není nic zadáno, vytvoří se běžný koncový bod služby.|  
|listenUriMode|Určuje, jak přenos zachází z `ListenUri` poskytované služby k naslouchání. Platné hodnoty jsou<br /><br /> – Explicitní<br />-Unique<br /><br /> Výchozí hodnota je explicitní.|  
|listenUri|Řetězec určující identifikátor URI, na kterém naslouchá koncový bod služby. Výchozí hodnota je prázdný řetězec.|  
|name|Nepovinný atribut. Řetězec, který určuje název koncového bodu služby. Výchozí hodnota je zřetězení názvu vazby a názvu popisu kontraktu. Služby mohou mít několik koncových bodů, takže atribut koncového bodu `name` se liší od názvu služby.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<headers>](headers.md)|Kolekce hlaviček adres.|  
|[\<identity>](identity.md)|Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<service>](service.md)|Konfigurační oddíl definující seznam koncových bodů, ke kterým se klient může připojit.|  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [Koncové body: adresy, vazby a kontrakty](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
