---
title: ServiceDescription and WSDL Reference
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 26babd473ca78d6b55ada6c0505ec2f94214448b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="servicedescription-and-wsdl-reference"></a>ServiceDescription and WSDL Reference
Toto téma popisuje, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mapuje webové služby popis Language (WSDL) dokumenty do a z <xref:System.ServiceModel.Description.ServiceDescription> instance.  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>Jak ServiceDescription mapuje WSDL 1.1  
 Můžete použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] export WSDL dokumenty z <xref:System.ServiceModel.Description.ServiceDescription> instanci pro vaši službu. WSDL dokumenty jsou pro vaši službu automaticky generovány při publikování kocových bodů metadat.  
  
 Můžete také importovat <xref:System.ServiceModel.Description.ServiceEndpoint> instancí <xref:System.ServiceModel.Description.ContractDescription> instance, a <xref:System.ServiceModel.Channels.Binding> instancí z WSDL dokumentů pomocí `WsdlImporter` typu.  
  
 Dokumenty WSDL exportované sadou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], importovat všechny definice schématu XML použité z externí dokumentů schématu XML. Pro každý cílový obor názvů, které typy dat použít v rámci služby se exportuje samostatný dokument schématu XML. Podobně se exportuje samostatný dokument WSDL pro každý cílový obor názvů služby měnící použití.  
  
### <a name="servicedescription"></a>ServiceDescription  
 A <xref:System.ServiceModel.Description.ServiceDescription> instance se mapuje `wsdl:service` elementu. A <xref:System.ServiceModel.Description.ServiceDescription> instance obsahuje kolekci <xref:System.ServiceModel.Description.ServiceEndpoint> instance, která každý mapování na jednotlivé `wsdl:port` elementy.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@name Hodnotu pro službu.|  
|`Namespace`|Cílový obor názvů pro `wsdl:service` definice pro službu.|  
|`Endpoints`|`wsdl:port` Definice pro službu.|  
  
### <a name="serviceendpoint"></a>Koncového bodu služby  
 A <xref:System.ServiceModel.Description.ServiceEndpoint> instance se mapuje `wsdl:port` elementu. A <xref:System.ServiceModel.Description.ServiceEndpoint> instance obsahuje adresy, vazby a kontraktu.  
  
 Koncový bod chování, které implementují <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní můžete upravit `wsdl:port` element pro koncový bod jsou připojené k.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:port` /@name Hodnotu pro koncový bod a `wsdl:binding` /@name hodnotu pro vazbu koncového bodu.|  
|`Address`|Adresy pro `wsdl:port` definice pro koncový bod.<br /><br /> Přenos pro koncový bod Určuje formát adresy. Například pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-podporované přenosy ho může být adresa protokolu SOAP nebo odkaz na koncový bod.|  
|`Binding`|`wsdl:binding` Definice pro koncový bod.<br /><br /> Na rozdíl od `wsdl:binding` definice, vazeb v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nejsou vázané na všechny jeden kontrakt.|  
|`Contract`|`wsdl:portType` Definice pro koncový bod.|  
|`Behaviors`|Koncový bod chování, které implementují <xref:System.ServiceModel.Description.IWsdlExportExtension> rozhraní můžete upravit `wsdl:port` pro koncový bod.|  
  
### <a name="bindings"></a>Vazby  
 Instance vazby pro `ServiceEndpoint` instance se mapuje `wsdl:binding` definice. Na rozdíl od `wsdl:binding` definice, které musí být přidružen konkrétní `wsdl:portType` definice [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby jsou nezávislé na jakékoli smlouvy.  
  
 Vazba se skládá z kolekce elementů vazby. Každý prvek popisuje určitý aspekt jak koncový bod komunikuje s klienty. Kromě toho má vazbu <xref:System.ServiceModel.Channels.MessageVersion> určující <xref:System.ServiceModel.EnvelopeVersion> a <xref:System.ServiceModel.Channels.AddressingVersion> pro koncový bod.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|Použije v názvu výchozí koncový bod, který je název vazby se připojí název kontraktu oddělených podtržítkem.|  
|`Namespace`|`targetNamespace` Pro `wsdl:binding` definice.<br /><br /> Při importu, pokud zásady je připojen k portu WSDL, obor názvů importované vazby mapuje `targetNamespace` pro `wsdl:port` definice.|  
|`BindingElementCollection`, jak ho vrátila `CreateBindingElements`() – metoda|Různá rozšíření specifické pro doménu `wsdl:binding` definice, obvykle výrazy zásad.|  
|`MessageVersion`|`EnvelopeVersion` a `AddressingVersion` pro koncový bod.<br /><br /> Když `MessageVersion.None` je zadán, Vazba WSDL neobsahuje vazbu protokolu SOAP a WSDL port neobsahuje WS-Addressing obsah. Toto nastavení se obvykle používá pro prostý staré koncové body XML (POX).|  
  
#### <a name="bindingelements"></a>Třídy BindingElements  
 Prvky vazeb pro vazbu koncového bodu mapování na různých rozšíření WSDL v `wsdl:binding`, jako jsou výrazy zásad.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement> Pro vazbu určuje přenos identifikátor URI (Uniform Resource) pro vazbu protokolu SOAP.  
  
#### <a name="addressingversion"></a>Třídu AddressingVersion  
 `AddressingVersion` Na vazbu se mapuje na verzi adresování používány `wsd:port`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje SOAP 1.1 a SOAP 1.2 adresy a adresování WS 08/2004 a odkazy na koncový bod služby WS-Addressing 1.0.  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  
 `EnvelopeVersion` u vazby mapy na verzi protokolu SOAP používány `wsdl:binding`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje SOAP 1.1 a SOAP 1.2 vazby.  
  
### <a name="contracts"></a>Kontrakty  
 <xref:System.ServiceModel.Description.ContractDescription> Instanci pro `ServiceEndpoint` instance se mapuje `wsdl:portType`. A `ContractDescription` instance popisuje všechny operace pro danou zakázku.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@name Hodnotu pro daný kontrakt.|  
|`Namespace`|Cílový obor názvů pro `wsdl:portType` definice.|  
|`SessionMode`|`wsdl:portType` /@msc:usingSession Hodnotu pro daný kontrakt. Tento atribut je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozšíření pro WSDL 1.1.|  
|`Operations`|`wsdl:operation` Definice pro kontrakt.|  
  
### <a name="operations"></a>Operace  
 <xref:System.ServiceModel.Description.OperationDescription> Instance se mapuje `wsdl:portType` / `wsdl:operation`. `OperationDescription` Obsahuje kolekci `MessageDescription` instancí, které popisují zprávy pro operaci.  
  
 Dvě operace chování výraznou účastnit postupy `OperationDescription` se mapuje na dokument WSDL: `DataContractSerializerOperationBehavior` a `XmlSerializerOperationBehavior`.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name Hodnotu pro operaci.|  
|`ProtectionLevel`|Kontrolní výrazy ochrany v zásadách zabezpečení připojené k `wsdl:binding/wsdl:operation` zpráv pro tuto operaci.|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating Hodnotu pro operaci. Tento atribut je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozšíření pro WSDL 1.1.|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating Hodnotu pro operaci. Tento atribut je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozšíření pro WSDL 1.1.|  
|`Messages`|`wsdl:portType` / `wsdl:operation` / `wsdl:input` a `wsdl:portType` / `wsdl:operation` / `wsdl:output` zprávy pro operaci.|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` Definice pro operaci.|  
|`Behaviors`|`DataContractSerializerOperationBehavior` a `XmlSerializerOperationBehavior` řešit vazby operace a zprávy operace.|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>DataContractSerializerOperationBehavior  
 `DataContractSerializerOperationBehavior` Pro operace je `IWsdlExportExtension` implementace, který exportuje WSDL zpráv a vazbu pro danou operaci. Typy schémat XML exportují se pomocí `XsdDataContractExporter`. `DataContractSerializerOperationBehavior` Také určuje použití, styl a schéma exportu a program pro import, které chcete použít pro tuto operaci.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`DataContractFormatAttribute`|`Style` Vlastnost pro tento atribut se mapuje `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style hodnotu pro operaci.<br /><br /> `DataContractSerializerOperationBehavior` Podporuje pouze literál použití typy schémat ve schématu WSDL.|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>XmlSerializerOperationBehavior  
 `XmlSerializerOperationBehavior` Pro operace je `IWsdlExportExtension` implementace, který exportuje WSDL zpráv a vazbu pro danou operaci. Typy schémat XML exportují se pomocí `XmlSchemaExporter`. `XmlSerializerOperationBehavior` Také určuje použití, styl a schéma exportu a program pro import, které chcete použít pro tuto operaci.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|`Style` Vlastnost pro tento atribut se mapuje `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style hodnotu pro operaci.<br /><br /> `Use` Vlastnost pro tento atribut se mapuje `wsdl:binding` / `wsdl:operation` / `soap:operation`/ */@use hodnoty pro všechny zprávy ve operaci.|  
  
### <a name="messages"></a>Zprávy  
 A `MessageDescription` instance se mapuje `wsdl:message` který odkazuje `wsdl:portType` / `wsdl:operation` / `wsdl:input` nebo `wsdl:portType` / `wsdl:operation` / `wsdl:output`zpráva v operaci. A `MessageDescription` má text a hlavičky.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Action`|Akce protokolu SOAP nebo WS-Addressing pro zprávu.<br /><br /> Poznámka: této operace, které používají řetězce akce "*" nenachází v jazyce WSDL.|  
|`Direction`|`MessageDirection.Input`se mapuje na `wsdl:input`.<br /><br /> `MessageDirection.Output`se mapuje na `wsdl:output`.|  
|`ProtectionLevel`|Kontrolní výrazy ochrany v zásadách zabezpečení připojené k `wsdl:message` definice pro tuto zprávu.|  
|`Body`|Text zprávy pro zprávu.|  
|`Headers`|Hlavičky pro zprávu.|  
|`ContractDescription.Name`, `OperationContract.Name`|Na exportu, použít k odvození `wsdl:message` /@name hodnotu.|  
  
#### <a name="message-body"></a>Tělo zprávy  
 A `MessageBodyDescription` instance se mapuje `wsdl:message` / `wsdl:part` definice pro tělo zprávy. Tělo zprávy může být uzavřen nebo úplné.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`WrapperName`|Pokud je styl není RPC, pak se `WrapperName` mapuje název elementu, který odkazuje `wsdl:message` / `wsdl:part` s @name nastavena na "parametry".|  
|`WrapperNamespace`|Pokud je styl není RPC, pak se `WrapperNamespace` se mapuje na element obor názvů pro `wsdl:message` / `wsdl:part` s @name nastavena na "parametry".|  
|`Parts`|Části zprávy pro tento text zprávy.|  
|`ReturnValue`|O podřízený prvek elementu obálky, pokud existuje element obálky (styl dokumentu zabalená, nebo styl RPC), jinak první `wsdl:message` / `wsdl:part` ve zprávě.|  
  
#### <a name="message-parts"></a>Části zprávy  
 A `MessagePartDescription` instance se mapuje `wsdl:message` / `wsdl:part` a typ schématu XML nebo element odkazující na část zprávy.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsd:message` / `wsdl:part` /@name Hodnotu pro část zprávy a název elementu, odkazující na část zprávy.|  
|`Namespace`|Obor názvů elementu, který bodů část zprávy.|  
|`Index`|Index `wsdl:message` / `wsdl:part` pro zprávu.|  
|`ProtectionLevel`|Kontrolní výrazy ochrany v zásadách zabezpečení připojené k `wsdl:message` definice pro tuto část zprávy. Zásady je parametry tak, aby odkazoval na část konkrétní zprávy.|  
|`MessageType`|Typ schématu XML element odkazující na část zprávy.|  
  
#### <a name="message-headers"></a>Hlavičky zpráv  
 A `MessageHeaderDescription` instance je část zprávy, která mapuje také `soap:header` vazba pro část zprávy.  
  
### <a name="faults"></a>Chyb  
 A `FaultDescription` instance se mapuje `wsdl:portType` / `wsdl:operation` / `wsdl:fault` definice a jeho přidružený `wsdl:message` definice. `wsdl:message` Se přidá do stejné cílový obor názvů jako typ přidružené portu WSDL. `wsdl:message` Má část jedné zprávy s názvem "podrobností", který odkazuje na element schématu XML, který odpovídá `DefaultType` hodnota vlastnosti pro `FaultDescription` instance.  
  
|Vlastnosti|Mapování WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name Hodnotu poruchy.|  
|`Namespace`|Obor názvů část podrobné chybové zprávy se odkazuje na element schématu XML.|  
|`Action`|Akce protokolu SOAP nebo WS-Addressing poruchy.|  
|`ProtectionLevel`|Kontrolní výrazy ochrany v zásadách zabezpečení připojené k `wsdl:message` definice této chyby.|  
|`DetailType`|Typ schématu XML elementu, který část podrobné zprávy se odkazuje na.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|Použít k odvození `wsdl:message` /@name hodnotu pro zprávu chyby.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description>
