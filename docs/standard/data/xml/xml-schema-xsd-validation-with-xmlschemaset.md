---
title: Ověření schématu XML (XSD) s třídou XmlSchemaSet
description: Naučte se ověřovat dokumenty XML proti schématu XSD (XML Schema Definition Language) pomocí třídy XmlSchemaSet v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 995323d1882da13d45cdac516518d5b67845715a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594501"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Ověřování schématu XML (XSD) pomocí jazyka XmlSchemaSet

Dokumenty XML lze ověřit podle schématu XML schématu definice jazyka (XSD) v <xref:System.Xml.Schema.XmlSchemaSet> .  
  
## <a name="validate-xml-documents"></a>Ověřit dokumenty XML  
 Dokumenty XML jsou ověřovány <xref:System.Xml.XmlReader.Create%2A> metodou <xref:System.Xml.XmlReader> třídy. Chcete-li ověřit dokument XML, sestavte <xref:System.Xml.XmlReaderSettings> objekt, který obsahuje schéma XML schématu definice jazyk (XSD), pomocí kterého lze ověřit dokument XML.  
  
> [!NOTE]
> <xref:System.Xml.Schema>Obor názvů obsahuje metody rozšíření, které usnadňují ověření stromu XML proti souboru XSD při použití [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Další informace o ověřování dokumentů XML pomocí LINQ to XML naleznete v tématu [Jak ověřit pomocí XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) a [Postupy: ověřování pomocí XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).
  
 Jednotlivá schémata nebo sada schémat (jako <xref:System.Xml.Schema.XmlSchemaSet> ) lze přidat do prvku <xref:System.Xml.Schema.XmlSchemaSet> předáním jednoho jako parametru <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodě <xref:System.Xml.Schema.XmlSchemaSet> . Při ověřování dokumentu se cílový obor názvů dokumentu musí shodovat s cílovým oborem názvů schématu v sadě schémat.  
  
 Následuje příklad dokumentu XML.  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Následuje schéma, které ověřuje ukázkový dokument XML.  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 V následujícím příkladu kódu je schéma přidáno do <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti <xref:System.Xml.XmlReaderSettings> objektu. <xref:System.Xml.XmlReaderSettings>Objekt je předán jako parametr <xref:System.Xml.XmlReader.Create%2A> metodě <xref:System.Xml.XmlReader> objektu, který ověřuje dokument XML výše.  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A>Vlastnost <xref:System.Xml.XmlReaderSettings> objektu je nastavena na hodnotu `Schema` pro vymáhání ověřování dokumentu XML <xref:System.Xml.XmlReader.Create%2A> metodou <xref:System.Xml.XmlReader> objektu. A <xref:System.Xml.Schema.ValidationEventHandler> je přidán k <xref:System.Xml.XmlReaderSettings> objektu, který bude zpracovávat <xref:System.Xml.Schema.XmlSeverityType.Warning> události, které <xref:System.Xml.Schema.XmlSeverityType.Error> byly vyvolány chybami zjištěnými během procesu ověřování dokumentu XML i schématu.  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [XmlSchemaSet pro kompilaci schématu](xmlschemaset-for-schema-compilation.md)
- [Práce se schématy XML](working-with-xml-schemas.md)
