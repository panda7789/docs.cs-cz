---
title: "Atributy, které řídí serializace kódovaného protokolu SOAP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ae3193a2f9ef01f8e7f71235f15ed070e84ec11c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Atributy, které řídí serializace kódovaného protokolu SOAP 
Dokument World Wide Web Consortium (www.w3.org) s názvem "Simple Object Access Protocol (SOAP) 1.1" obsahuje volitelný oddíl (část 5), který popisuje, jak můžete zakódovat parametry protokolu SOAP. Tak, aby odpovídala část 5 specifikace, musíte použít speciální sadu atributů, které jsou součástí <xref:System.Xml.Serialization> oboru názvů. Tyto atributy v závislosti na třídy a členy třídy aplikovat a pak <xref:System.Xml.Serialization.XmlSerializer> k serializaci instancí třídy nebo tříd.  
  
 V následující tabulce jsou uvedeny atributy, kde je lze použít, a jejich význam. Další informace o použití těchto atributů k řízení serializace XML, najdete v části [postup: serializovat objekt jako protokolu SOAP-datový proud XML kódováno](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) a [postupy: přepsání kódovaný serializace XML protokolu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).  
  
 Další informace o atributech najdete v tématu [atributy](../../../docs/standard/attributes/index.md).  
  
|Atribut|Platí pro|Určuje|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.|Člen třídy bude serializována jako atribut XML.|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.|Třída bude serializována jako XML element.|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|Veřejné pole, které je identifikátor výčtu.|Název elementu člen výčtového typu.|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|Veřejné vlastnosti a pole.|Vlastnosti nebo pole mají být ignorovány, pokud je serializována třídu obsahující.|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|Veřejná odvozené třídy prohlášení a veřejné metody pro dokumenty služby popis jazyka WSDL (Web).|Typ by měly být zahrnuty při generování schémat (Chcete-li rozpoznán po serializován).|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|Deklarace veřejných tříd.|Třída by měla být serializován jako typ objektu XML.|  
  
## <a name="see-also"></a>Viz také  
 [Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [Postupy: Přepsání serializace XML zakódované v protokolu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [Atributy](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Postupy: Serializace objektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Postupy: Deserializace objektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
