---
title: "Ověření schématu (XSD) XML s XmlSchemaSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a6cf857ccecbdac88453fd1fba6e93d609196b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Ověření schématu (XSD) XML s XmlSchemaSet
Dokumenty XML můžete ověřit pomocí schématu XML schéma definition language (XSD) v <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Ověření XML – dokumenty  
 Dokumenty XML ověřuje <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídy. K ověření dokument XML, vytvořit <xref:System.Xml.XmlReaderSettings> objekt, který obsahuje schématu XML schématu definition language (XSD) ke které má být ověření v dokumentu XML.  
  
> [!NOTE]
>  <xref:System.Xml.Schema> Obor názvů obsahuje rozšiřující metody, které usnadňují ověření strom XML proti soubor XSD při použití [technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). Další informace o ověřování dokumentů XML pomocí LINQ to XML, najdete v části [postupy: ověření pomocí XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).  
  
 Jednotlivé schéma nebo sadu schémata (jako <xref:System.Xml.Schema.XmlSchemaSet>) mohou být přidány do <xref:System.Xml.Schema.XmlSchemaSet> předáním buď jeden jako parametr, který se <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>. Všimněte si, že při ověřování dokumentu se musí shodovat cílový obor názvů dokumentu cílový obor názvů schématu v sadě schématu.  
  
 Následuje příklad XML dokumentu.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Toto je schématu, která ověřuje ukázkový dokument XML.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 V následujícím příkladu kódu je do výše uvedeného schématu <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu. <xref:System.Xml.XmlReaderSettings> Objekt je předán jako parametr, který se <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> objekt, který ověří výše dokumentu XML.  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> Vlastnost <xref:System.Xml.XmlReaderSettings> objektu na hodnotu `Schema` k vynucení ověřování dokumentu XML pomocí <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> objektu. A <xref:System.Xml.Schema.ValidationEventHandler> je přidán do <xref:System.Xml.XmlReaderSettings> objekt zpracována <xref:System.Xml.Schema.XmlSeverityType.Warning> nebo <xref:System.Xml.Schema.XmlSeverityType.Error> události vyvolané službou chyby nalezené během procesu ověřování v dokumentu XML a schéma.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Práce s XML schémata](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
