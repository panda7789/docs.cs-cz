---
title: Ověření schématu XML (XSD) s třídou XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bdcfe785d6f5f81d721acd45eebb580b08b2d14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916074"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Ověření schématu XML (XSD) s třídou XmlSchemaSet
Dokumenty XML lze ověřit podle schématu XML schématu definice jazyka (XSD) v <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Ověřování dokumentů XML  
 Dokumenty XML jsou ověřovány <xref:System.Xml.XmlReader.Create%2A> metodou <xref:System.Xml.XmlReader> třídy. Chcete-li ověřit dokument XML, sestavte <xref:System.Xml.XmlReaderSettings> objekt, který obsahuje schéma XML schématu definice jazyk (XSD), pomocí kterého lze ověřit dokument XML.  
  
> [!NOTE]
> Obor názvů obsahuje metody rozšíření, které usnadňují ověření stromu XML proti souboru XSD při použití [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic).](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <xref:System.Xml.Schema> Další informace o ověřování dokumentů XML pomocí LINQ to XML naleznete v tématu [How to: Ověřte pomocí XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) a [postupy: Ověřte pomocí XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).  
  
 Jednotlivá schémata nebo sada <xref:System.Xml.Schema.XmlSchemaSet>schémat (jako) lze přidat do prvku <xref:System.Xml.Schema.XmlSchemaSet> předáním jednoho <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> jako <xref:System.Xml.Schema.XmlSchemaSet>parametru metodě. Všimněte si, že při ověřování dokumentu se cílový obor názvů dokumentu musí shodovat s cílovým oborem názvů schématu v sadě schémat.  
  
 Následuje příklad dokumentu XML.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Následuje schéma, které ověřuje ukázkový dokument XML.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 V následujícím příkladu kódu je schéma přidáno do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti <xref:System.Xml.XmlReaderSettings> objektu. Objekt je předán jako parametr <xref:System.Xml.XmlReader.Create%2A> metodě <xref:System.Xml.XmlReader> objektu, který ověřuje dokument XML výše. <xref:System.Xml.XmlReaderSettings>  
  
 `Schema` <xref:System.Xml.XmlReader.Create%2A> Vlastnost objektu je nastavena na hodnotu pro vymáhání ověřování dokumentu XML metodou <xref:System.Xml.XmlReader> objektu. <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReaderSettings.ValidationType%2A> A <xref:System.Xml.Schema.ValidationEventHandler> je přidán <xref:System.Xml.XmlReaderSettings> k objektu, který bude zpracovávat <xref:System.Xml.Schema.XmlSeverityType.Warning> události <xref:System.Xml.Schema.XmlSeverityType.Error> , které byly vyvolány chybami zjištěnými během procesu ověřování dokumentu XML i schématu.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Práce se schématy XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
