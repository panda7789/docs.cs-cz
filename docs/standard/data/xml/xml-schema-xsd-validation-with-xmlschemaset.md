---
title: Ověření schématu XML (XSD) s třídou XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 6bd7525b77d4154193b57f8e6589cb865ace5fd6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709878"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Ověření schématu XML (XSD) s třídou XmlSchemaSet
Dokumenty XML lze ověřit podle schématu XML schématu definice jazyka (XSD) v <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Ověřování dokumentů XML  
 Dokumenty XML jsou ověřovány metodou <xref:System.Xml.XmlReader.Create%2A> třídy <xref:System.Xml.XmlReader>. Chcete-li ověřit dokument XML, Sestavte objekt <xref:System.Xml.XmlReaderSettings>, který obsahuje schéma XML Schema Definition Language (XSD), pomocí kterého lze ověřit dokument XML.  
  
> [!NOTE]
> Obor názvů <xref:System.Xml.Schema> obsahuje metody rozšíření, které usnadňují ověřování stromu XML proti souboru XSD při použití [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Další informace o ověřování dokumentů XML pomocí LINQ to XML naleznete v tématu [Jak ověřit pomocí XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) a [Postupy: ověřování pomocí XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).
  
 Jednotlivé schéma nebo sadu schémat (jako <xref:System.Xml.Schema.XmlSchemaSet>) lze přidat do <xref:System.Xml.Schema.XmlSchemaSet> předáním jednoho jako parametru <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodě <xref:System.Xml.Schema.XmlSchemaSet>. Všimněte si, že při ověřování dokumentu se cílový obor názvů dokumentu musí shodovat s cílovým oborem názvů schématu v sadě schémat.  
  
 Následuje příklad dokumentu XML.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Následuje schéma, které ověřuje ukázkový dokument XML.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 V následujícím příkladu kódu je schéma přidáno do vlastnosti <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> objektu <xref:System.Xml.XmlReaderSettings>. Objekt <xref:System.Xml.XmlReaderSettings> je předán jako parametr metodě <xref:System.Xml.XmlReader.Create%2A> objektu <xref:System.Xml.XmlReader>, který ověřuje dokument XML výše.  
  
 Vlastnost <xref:System.Xml.XmlReaderSettings.ValidationType%2A> objektu <xref:System.Xml.XmlReaderSettings> je nastavena na hodnotu `Schema` pro vymáhání ověřování dokumentu XML metodou <xref:System.Xml.XmlReader.Create%2A> objektu <xref:System.Xml.XmlReader>. Do objektu <xref:System.Xml.XmlReaderSettings> je přidána <xref:System.Xml.Schema.ValidationEventHandler>, která bude zpracovávat jakékoli <xref:System.Xml.Schema.XmlSeverityType.Warning> nebo <xref:System.Xml.Schema.XmlSeverityType.Error> události vyvolané chybami nalezenými během procesu ověřování dokumentu XML i schématu.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Práce se schématy XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
