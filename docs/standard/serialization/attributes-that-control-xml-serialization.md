---
title: Atributy, které řídí serializaci XML
description: Tento článek obsahuje atributy, které lze použít na třídy a členy třídy pro řízení způsobu, jakým objekt XmlSerializer serializace nebo deserializace instance třídy.
ms.date: 03/30/2017
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
ms.openlocfilehash: 3a269e1f3e8fd6e982db3c241c113f471134f9d3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378451"
---
# <a name="attributes-that-control-xml-serialization"></a>Atributy, které řídí serializaci XML
Můžete použít atributy v následující tabulce do třídy a třídy členy lze řídit způsob, ve kterém <xref:System.Xml.Serialization.XmlSerializer> serializuje a deserializuje instance třídy. Informace o tom, jak tyto atributy řídí serializace XML, naleznete v tématu [řízení serializace XML pomocí atributů](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md).  
  
 Tyto atributy lze také použít k řízení zprávy protokolu SOAP literálu styl generovaných webové služby XML. Další informace o použití těchto atributů pro metodu XML Web Services naleznete v tématu [serializace XML s webovými službami XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md).  
  
 Další informace o atributech naleznete v tématu [Attributes](../../../docs/standard/attributes/index.md).  
  
|Atribut|Platí pro|Určuje|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu, která vrátí pole <xref:System.Xml.XmlAttribute> objekty.|Při deserializaci, pole bude vyplněn <xref:System.Xml.XmlAttribute> objekty, které představují všechny atributy ve formátu XML Neznámý schématu.|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu, která vrátí pole <xref:System.Xml.XmlElement> objekty.|Při deserializaci, je vyplněno pole <xref:System.Xml.XmlElement> objekty, které představují všechny prvky XML Neznámý schématu.|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu, která vrací pole komplexních objektů.|Členy pole bude generována jako členy do pole XML.|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu, která vrací pole komplexních objektů.|Odvozené typy, které mohou být zařazeny do pole. Obvykle se používá ve spojení s <xref:System.Xml.Serialization.XmlArrayAttribute>.|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.|Člen bude serializována jako atribut XML.|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.|Člen můžete dále jednoznačně rozlišit pomocí výčet.|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|Veřejné pole, vlastnost, parametr nebo návratovou hodnotu.|Pole nebo vlastnost bude serializována jako XML element.|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|Veřejné pole, které je identifikátor výčtu.|Název elementu člen výčtového typu.|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|Veřejné vlastnosti a pole.|Vlastnosti nebo pole mají být ignorovány, pokud je serializována třídu obsahující.|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|Veřejná odvozené třídy deklarací a návratovými hodnotami veřejné metody pro webové služby WSDL (Description Language) dokumenty.|Třída by měly být zahrnuty při generování schémat (Chcete-li rozpoznán po serializován).|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|Deklarace veřejných tříd.|Ovládací prvky XML serializace atribut cíle jako kořenový element XML. Použijte atribut dále zadejte název oboru názvů a element.|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|Veřejné vlastnosti a pole.|Vlastnost nebo pole by měl být serializován jako XML text.|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|Deklarace veřejných tříd.|Zadejte název a obor názvů XML.|  
  
 Kromě těchto atributů, které jsou všechny nalezené v <xref:System.Xml.Serialization> obor názvů, můžete také použít <xref:System.ComponentModel.DefaultValueAttribute> atributu na pole. **DefaultValueAttribute –** nastaví hodnotu, která bude automaticky přiřazena členu, pokud není zadána žádná hodnota.  
  
 Pro řízení kódované serializace XML protokolu SOAP, viz [atributy, které řídí serializaci kódovaných SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
## <a name="see-also"></a>Viz také

- [Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Řízení serializace XML pomocí atributů](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [Postupy: Zadání alternativního názvu elementu pro XML stream](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Postupy: Serializace objektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Postupy: Deserializace objektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
