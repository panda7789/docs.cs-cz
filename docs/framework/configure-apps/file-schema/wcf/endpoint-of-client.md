---
title: <endpoint> z <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855317"
---
# <a name="endpoint-of-client"></a>\<koncový bod > \<> klienta
Určuje kontrakt, vazbu a vlastnosti adresy koncového bodu kanálu, který používají klienti pro připojení ke koncovým bodům služby na serveru.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> koncového bodu**  
  
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
|adresa|Požadovaný atribut typu string.<br /><br /> Určuje adresu koncového bodu. Výchozí hodnota je prázdný řetězec. Adresa musí být absolutním identifikátorem URI.|  
|behaviorConfiguration|Řetězec obsahující název chování, který se má použít k vytvoření instance koncového bodu. Název chování musí být v oboru v místě, kde je služba definovaná. Výchozí hodnota je prázdný řetězec.|  
|vazba|Požadovaný atribut typu string.<br /><br /> Řetězec, který určuje typ vazby, která se má použít. Typ musí mít registrovaný konfigurační oddíl, aby na něj bylo odkazováno. Typ je zaregistrován podle názvu oddílu namísto názvu typu vazby.|  
|bindingConfiguration|Volitelný parametr. Řetězec obsahující název konfigurace vazby, která má být použita při vytvoření instance koncového bodu. Konfigurace vazby musí být v oboru v místě, kde je koncový bod definován. Výchozí hodnota je prázdný řetězec.<br /><br /> Tento atribut se používá ve spojení s `binding` pro odkazování na konkrétní konfiguraci vazby v konfiguračním souboru. Nastavte tento atribut, pokud se pokoušíte použít vlastní vazbu. V opačném případě může být vyvolána výjimka.|  
|Dodavatele|Požadovaný atribut typu string.<br /><br /> Řetězec označující kontrakt, který tento koncový bod vystavuje. Sestavení musí implementovat typ kontraktu.|  
|endpointConfiguration|Řetězec, který určuje název standardního koncového bodu, který je nastaven `kind` atributem, který odkazuje na Další informace o konfiguraci tohoto standardního koncového bodu. V `<standardEndpoints>` části se musí definovat stejný název.|  
|plnění|Řetězec, který určuje typ použitého standardního koncového bodu. Typ musí být zaregistrován v `<extensions>` oddílu nebo v souboru Machine. config. Pokud není zadán žádný obsah, je vytvořen běžný koncový bod kanálu.|  
|name|Volitelný atribut řetězce. Tento atribut jednoznačně identifikuje koncový bod pro daný kontrakt. Pro daný typ kontraktu můžete definovat více klientů. Každá definice musí být odlišena jedinečným názvem konfigurace. Pokud je tento atribut vynechán, použije se jako výchozí koncový bod přidružený k zadanému typu kontraktu odpovídající koncový bod. Výchozí hodnota je prázdný řetězec.<br /><br /> `name` Atribut vazby se používá pro export definice prostřednictvím WSDL.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<headers>](headers.md)|Kolekce hlaviček adres.|  
|[\<identity>](identity.md)|Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<client>](client.md)|Konfigurační oddíl definující seznam koncových bodů, ke kterým se klient může připojit.|  
  
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
- [Konfigurace klienta WCF](../../../wcf/feature-details/client-configuration.md)
- [Klienti](../../../wcf/feature-details/clients.md)
