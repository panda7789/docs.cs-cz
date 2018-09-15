---
title: Seznam atributů řídících serializaci kódovaný protokol SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 7b5a48003ff9bfb398c05c8d70a9076d49ad83d6
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658324"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Seznam atributů řídících serializaci kódovaný protokol SOAP

World Wide Web Consortium (W3C) dokumentu s názvem [jednoduchý objekt přístup protokolu (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) obsahuje volitelný oddíl (oddíl 5), který popisuje, jak může být zakódován parametry protokolu SOAP. Tak, aby odpovídal pro oddíl 5 specifikace, musí používat speciální sadu atributů v nalezen <xref:System.Xml.Serialization> oboru názvů. Tyto atributy v závislosti na třídy a členy třídy aplikovat a pak <xref:System.Xml.Serialization.XmlSerializer> k serializaci instancí třídy nebo tříd.

V následující tabulce jsou uvedeny atributy, kde je lze použít, a jejich význam. Další informace o použití těchto atributů ovládacímu prvku serializace XML, naleznete v tématu [postupy: serializace objektu jako SOAP-Encoded XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) a [postupy: přepsání kódovaný protokol SOAP XML serializace](how-to-override-encoded-soap-xml-serialization.md).

Další informace o atributech najdete v tématu [atributy](../../../docs/standard/attributes/index.md).

|Atribut|Platí pro|Určuje|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.|Člen třídy bude serializována jako atribut XML.|
|<xref:System.Xml.Serialization.SoapElementAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.|Třída bude serializována jako XML element.|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|Veřejné pole, které je identifikátor výčtu.|Název elementu člen výčtového typu.|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|Veřejné vlastnosti a pole.|Vlastnosti nebo pole mají být ignorovány, pokud je serializována třídu obsahující.|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|Veřejná odvozené třídy prohlášení a veřejné metody pro dokumenty služby popis jazyka WSDL (Web).|Typ by měly být zahrnuty při generování schémat (Chcete-li rozpoznán po serializován).|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|Deklarace veřejných tříd.|Třída by měla být serializován jako typ objektu XML.|

## <a name="see-also"></a>Viz také:

- [Serializace XML a SOAP](xml-and-soap-serialization.md)  
- [Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
- [Postupy: Přepsání serializace XML zakódované v protokolu SOAP](how-to-override-encoded-soap-xml-serialization.md)  
- [Atributy](../../../docs/standard/attributes/index.md)  
- <xref:System.Xml.Serialization.XmlSerializer>  
- [Postupy: Serializace objektu](how-to-serialize-an-object.md)  
- [Postupy: Deserializace objektu](how-to-deserialize-an-object.md)
