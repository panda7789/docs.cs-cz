---
title: ServiceDescription and WSDL Reference
ms.date: 03/30/2017
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
ms.openlocfilehash: 6690bea3d3df0f39a5581c3a6c14723c0f30f40c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748160"
---
# <a name="servicedescription-and-wsdl-reference"></a>ServiceDescription and WSDL Reference
Toto téma popisuje, jak Windows Communication Foundation (WCF) mapuje dokumenty služby popis jazyka WSDL (Web) do a z <xref:System.ServiceModel.Description.ServiceDescription> instancí.  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>Jak ServiceDescription mapuje WSDL 1.1  
 Export dokumenty WSDL z můžou využít WCF <xref:System.ServiceModel.Description.ServiceDescription> instanci pro vaši službu. Při publikování koncové body metadat, dokumenty WSDL jsou automaticky generovány pro vaši službu.  
  
 Můžete také importovat <xref:System.ServiceModel.Description.ServiceEndpoint> instancí, <xref:System.ServiceModel.Description.ContractDescription> instancí, a <xref:System.ServiceModel.Channels.Binding> instancí z pomocí dokumenty WSDL `WsdlImporter` typu.  
  
 Dokumenty WSDL, exportované sadou WCF, importovat všechny definice schématu XML používá z externí schéma XML dokumentů. Pro každý cílový obor názvů, které typy dat použít ve službě se exportuje samostatný dokument schématu XML. Podobně se exportuje samostatný dokumentu WSDL pro každý cílový obor názvů služby smluv týkajících se použití.  
  
### <a name="servicedescription"></a>Popis ServiceDescription  
 A <xref:System.ServiceModel.Description.ServiceDescription> instance se mapuje `wsdl:service` elementu. A <xref:System.ServiceModel.Description.ServiceDescription> instance obsahuje kolekci <xref:System.ServiceModel.Description.ServiceEndpoint> instance každé namapovat jednotlivé `wsdl:port` elementy.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@name Hodnota pro službu.|  
|`Namespace`|Cílový obor názvů pro `wsdl:service` definice služby.|  
|`Endpoints`|`wsdl:port` Definic pro službu.|  
  
### <a name="serviceendpoint"></a>ServiceEndpoint  
 A <xref:System.ServiceModel.Description.ServiceEndpoint> instance se mapuje `wsdl:port` elementu. A <xref:System.ServiceModel.Description.ServiceEndpoint> instance obsahuje adresy, vazby a kontrakt.  
  
 Chování koncového bodu, které implementují <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní můžete změnit `wsdl:port` – element pro koncový bod, jsou připojeny k.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:port` /@name Hodnotu pro koncový bod a `wsdl:binding` /@name hodnotu vazba koncového bodu.|  
|`Address`|Adresa pro `wsdl:port` definice koncového bodu.<br /><br /> Přenos pro koncový bod Určuje formát adresy. Pro přenosy WCF nepodporuje se třeba může být SOAP adresu nebo odkazem na koncový bod.|  
|`Binding`|`wsdl:binding` Definice koncového bodu.<br /><br /> Na rozdíl od `wsdl:binding` definic vazeb ve službě WCF, které nejsou vázány na jakékoli jeden kontrakt.|  
|`Contract`|`wsdl:portType` Definice koncového bodu.|  
|`Behaviors`|Chování koncového bodu, které implementují <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní můžete změnit `wsdl:port` pro koncový bod.|  
  
### <a name="bindings"></a>Vazby  
 Instanci vazby pro `ServiceEndpoint` instance se mapuje `wsdl:binding` definice. Na rozdíl od `wsdl:binding` definice, které musí být přidružen konkrétní `wsdl:portType` definice, vazby WCF nezávisí na žádné smlouvy.  
  
 Vazba se skládá z kolekce elementů vazby. Každý prvek popisuje určitý aspekt jak koncový bod komunikuje s klienty. Kromě toho má vazbu <xref:System.ServiceModel.Channels.MessageVersion> , která indikuje, <xref:System.ServiceModel.EnvelopeVersion> a <xref:System.ServiceModel.Channels.AddressingVersion> pro koncový bod.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|Použít výchozí název koncového bodu, což je název vazby s názvem kontraktu připojí oddělené podtržítkem.|  
|`Namespace`|`targetNamespace` Pro `wsdl:binding` definice.<br /><br /> Při importu, pokud zásady je připojená k portu WSDL, obor názvů importované vazby mapuje `targetNamespace` pro `wsdl:port` definice.|  
|`BindingElementCollection`, vrácené `CreateBindingElements`() – metoda|Různá rozšíření specifické pro doménu `wsdl:binding` definice, obvykle kontrolní výrazy zásad.|  
|`MessageVersion`|`EnvelopeVersion` a `AddressingVersion` pro koncový bod.<br /><br /> Když `MessageVersion.None` není zadána, Vazba WSDL neobsahuje vazbu protokolu SOAP a WSDL port neobsahuje WS-Addressing obsah. Toto nastavení se obvykle používá pro standardní koncové body staré XML (POX).|  
  
#### <a name="bindingelements"></a>Třídy BindingElements  
 Mapování elementů vazby pro vazbu koncového bodu na různých rozšíření WSDL `wsdl:binding`, jako jsou kontrolní výrazy zásad.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement> Pro vazbu určuje přenos identifikátor URI (Uniform Resource) pro vazbu protokolu SOAP.  
  
#### <a name="addressingversion"></a>AddressingVersion  
 `AddressingVersion` u vazby se mapuje na verzi adresování používané `wsd:port`. Podporuje WCF SOAP 1.1 a SOAP 1.2 adresy a WS-Addressing 08/2004 a odkazy na koncový bod WS-Addressing 1.0.  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  
 `EnvelopeVersion` u vazby mapuje na verzi protokolu SOAP používané `wsdl:binding`. WCF podporuje vazby SOAP 1.1 a SOAP 1.2.  
  
### <a name="contracts"></a>Kontrakty  
 <xref:System.ServiceModel.Description.ContractDescription> Instanci `ServiceEndpoint` instance se mapuje `wsdl:portType`. A `ContractDescription` instance popisuje všechny operace pro daný kontrakt.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@name Hodnoty pro kontrakt.|  
|`Namespace`|Cílový obor názvů pro `wsdl:portType` definice.|  
|`SessionMode`|`wsdl:portType` /@msc:usingSession Hodnoty pro kontrakt. Tento atribut je rozšíření WCF pro WSDL 1.1.|  
|`Operations`|`wsdl:operation` Definice pro kontrakt.|  
  
### <a name="operations"></a>Operace  
 <xref:System.ServiceModel.Description.OperationDescription> Instance se mapuje `wsdl:portType` / `wsdl:operation`. `OperationDescription` Obsahuje kolekci `MessageDescription` instancí, které popisují zprávy pro operaci.  
  
 Dvě operace chování silně účastnit jak `OperationDescription` se mapuje na dokument WSDL: `DataContractSerializerOperationBehavior` a `XmlSerializerOperationBehavior`.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name Hodnota pro operaci.|  
|`ProtectionLevel`|Kontrolní výrazy ochrany v zásadách zabezpečení připojené k `wsdl:binding/wsdl:operation` zprávy pro tuto operaci.|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating Hodnota pro operaci. Tento atribut je rozšíření WCF pro WSDL 1.1.|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating Hodnota pro operaci. Tento atribut je rozšíření WCF pro WSDL 1.1.|  
|`Messages`|`wsdl:portType` / `wsdl:operation` / `wsdl:input` a `wsdl:portType` / `wsdl:operation` / `wsdl:output` zprávy pro operaci.|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` Definice pro operaci.|  
|`Behaviors`|`DataContractSerializerOperationBehavior` a `XmlSerializerOperationBehavior` operace vazby a zpráv operace.|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>DataContractSerializerOperationBehavior  
 `DataContractSerializerOperationBehavior` Je operace `IWsdlExportExtension` implementace, která se exportuje zprávy WSDL a vazbu pro danou operaci. Typ schématu XML jsou exportovány pomocí `XsdDataContractExporter`. `DataContractSerializerOperationBehavior` Také určuje použití, styl a schéma Exportér a programu pro import pro danou operaci.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`DataContractFormatAttribute`|`Style` Vlastnost pro tento atribut mapuje `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style hodnota pro operaci.<br /><br /> `DataContractSerializerOperationBehavior` Podporuje pouze literál použití schématu typy ve schématu WSDL.|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>XmlSerializerOperationBehavior  
 `XmlSerializerOperationBehavior` Je operace `IWsdlExportExtension` implementace, která se exportuje zprávy WSDL a vazbu pro danou operaci. Typ schématu XML jsou exportovány pomocí `XmlSchemaExporter`. `XmlSerializerOperationBehavior` Také určuje použití, styl a schéma Exportér a programu pro import pro danou operaci.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|`Style` Vlastnost pro tento atribut mapuje `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style hodnota pro operaci.<br /><br /> `Use` Vlastnost pro tento atribut mapuje `wsdl:binding` / `wsdl:operation` / `soap:operation`/ */@use hodnoty pro všechny zprávy v operaci.|  
  
### <a name="messages"></a>Zprávy  
 A `MessageDescription` instance se mapuje `wsdl:message` , na který odkazuje `wsdl:portType` / `wsdl:operation` / `wsdl:input` nebo `wsdl:portType` / `wsdl:operation` / `wsdl:output`zprávy v operaci. A `MessageDescription` má záhlaví a text.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Action`|Akce SOAP nebo WS-Adressing zprávy.<br /><br /> Poznámka: této operace, které používají řetězec akcí "*" nejsou reprezentovány v jazyce WSDL.|  
|`Direction`|`MessageDirection.Input` mapuje `wsdl:input`.<br /><br /> `MessageDirection.Output` mapuje `wsdl:output`.|  
|`ProtectionLevel`|Kontrolní výrazy ochrany v zásadách zabezpečení připojené k `wsdl:message` definice pro tuto zprávu.|  
|`Body`|Text zprávy pro zprávu.|  
|`Headers`|Záhlaví zprávy.|  
|`ContractDescription.Name`, `OperationContract.Name`|Při exportu, použít k odvození `wsdl:message` /@name hodnotu.|  
  
#### <a name="message-body"></a>Text zprávy  
 A `MessageBodyDescription` instance se mapuje `wsdl:message` / `wsdl:part` definice těla zprávy. Tělo zprávy může být zabaleny nebo úplné.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`WrapperName`|Pokud styl není RPC, pak bude `WrapperName` mapuje na název elementu odkazuje `wsdl:message` / `wsdl:part` s @name nastavena na "parametrů".|  
|`WrapperNamespace`|Pokud styl není RPC, pak bude `WrapperNamespace` mapuje na obor názvů elementu pro `wsdl:message` / `wsdl:part` s @name nastavena na "parametrů".|  
|`Parts`|Části zprávy pro tento text zprávy.|  
|`ReturnValue`|Podřízený prvek element obálky, pokud existuje element obálky, a (styl zabalena dokumentem nebo stylu RPC), jinak první `wsdl:message` / `wsdl:part` ve zprávě.|  
  
#### <a name="message-parts"></a>Části zprávy  
 A `MessagePartDescription` instance se mapuje `wsdl:message` / `wsdl:part` a typ schématu XML nebo element odkazující na část zprávy.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsd:message` / `wsdl:part` /@name Hodnotu pro část zprávy a název elementu, který odkazuje část zprávy.|  
|`Namespace`|Obor názvů elementu, který odkazuje část zprávy.|  
|`Index`|Index `wsdl:message` / `wsdl:part` zprávy.|  
|`ProtectionLevel`|Kontrolní výrazy ochrany v zásadách zabezpečení připojené k `wsdl:message` definice pro tuto část zprávy. Zásady se parametry tak, aby odkazoval na část konkrétní zprávu.|  
|`MessageType`|Typ schématu XML element odkazující na část zprávy.|  
  
#### <a name="message-headers"></a>Záhlaví zpráv  
 A `MessageHeaderDescription` instance je součástí zprávy, která se také mapuje `soap:header` vazby pro část zprávy.  
  
### <a name="faults"></a>Chyby  
 A `FaultDescription` instance se mapuje `wsdl:portType` / `wsdl:operation` / `wsdl:fault` definice spolu s přidruženými `wsdl:message` definice. `wsdl:message` Se přidá do stejný cílový obor názvů jako jeho přidruženého port typu WSDL. `wsdl:message` Má jedna zpráva část s názvem "podrobností", který odkazuje na element schématu XML, který odpovídá `DefaultType` hodnota vlastnosti pro `FaultDescription` instance.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name Hodnotou chyby.|  
|`Namespace`|Obor názvů část chybové zprávy podrobností odkazující na element schématu XML.|  
|`Action`|Akce SOAP nebo WS-Addressing chyby.|  
|`ProtectionLevel`|Kontrolní výrazy ochrany v zásadách zabezpečení připojené k `wsdl:message` definici pro toto selhání.|  
|`DetailType`|Typ schématu XML element odkazující na podrobná část zprávy.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|Použít k odvození `wsdl:message` /@name hodnotu chybová zpráva.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description>
