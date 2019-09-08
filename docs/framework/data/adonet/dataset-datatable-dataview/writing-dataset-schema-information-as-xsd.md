---
title: Zápis informací o schématu datové sady jako XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f86e9100489ddf35d8ef5f98e386306a7dbfd4ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784176"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Zápis informací o schématu datové sady jako XSD
Schéma můžete zapsat <xref:System.Data.DataSet> jako schéma XML schématu definice jazyka (XSD), abyste ho mohli přenést s použitím nebo bez souvisejících dat v dokumentu XML. Schéma XML lze zapsat do souboru, datového proudu, <xref:System.Xml.XmlWriter>nebo řetězce; je užitečné pro vygenerování **datové sady**silného typu. Další informace o objektech **DataSet** se silnými typy najdete v tématu [typové datové sady](typed-datasets.md).  
  
 Můžete určit způsob reprezentace sloupce tabulky ve schématu XML pomocí vlastnosti <xref:System.Data.DataColumn> **ColumnMapping** objektu. Další informace naleznete v části "mapování sloupců na prvky XML, atributy a text" v článku [psaní obsahu datové sady jako XML data](writing-dataset-contents-as-xml-data.md).  
  
 Chcete-li zapsat schéma **datové sady** jako schématu XML, do souboru, datového proudu nebo **XmlWriter**, použijte metodu **WriteXmlSchema** **datové sady**. **WriteXmlSchema** přijímá jeden parametr, který určuje cíl výsledného schématu XML. Následující příklady kódu ukazují, jak zapsat schéma XML **datové sady** do souboru předáním řetězce obsahujícího název souboru a <xref:System.IO.StreamWriter> objektu.  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 Chcete-li získat schéma **datové sady** a zapsat je jako řetězec schématu XML, použijte metodu **GetXmlSchema** , jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Viz také:

- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Kopírování obsahu datové sady jako dat XML](writing-dataset-contents-as-xml-data.md)
- [Typové datové sady](typed-datasets.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
