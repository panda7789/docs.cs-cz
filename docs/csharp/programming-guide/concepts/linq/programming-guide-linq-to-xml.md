---
title: "Průvodce programováním (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4b1ffd10-ab81-4a0d-a0ca-e9876478d924
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7ee6ac9d13d265442e6d5b9f02c6d5788e75c50f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="programming-guide-linq-to-xml-c"></a>Průvodce programováním (technologie LINQ to XML) (C#)
Tato část obsahuje informace o programování s koncepční a postupy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="who-should-read-this-documentation"></a>Komu je tato dokumentace určen  
 Tato dokumentace cílem vývojáře, kteří již pochopit C# a některé základní aspekty [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Cílem této dokumentace je aby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] snadno použitelný pro všechny typy vývojářů. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]usnadňuje programování XML. Nemusíte být vývojář odborné ji použít.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]založena na obecných tříd. Je proto velmi důležité, abyste rozuměli tomu použití obecné třídy. Navíc je užitečné, pokud jste se seznámili s delegáti, které jsou deklarované jako parametrizované typy. Pokud nejste obeznámeni s C# obecné třídy, přečtěte si téma [obecné třídy](../../../../csharp/programming-guide/generics/generic-classes.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Technologie LINQ to XML přehled programování (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|Obsahuje přehled [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] třídy a podrobné informace o tři nejdůležitější tříd: <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, a <xref:System.Xml.Linq.XDocument>.|  
|[Vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)|Poskytuje informace o vytváření stromů XML koncepční a založený na úlohách. Stromy XML můžete vytvořit pomocí funkční konstrukce nebo analýzou textu XML z řetězce nebo souboru. Můžete použít také <xref:System.Xml.XmlReader> k naplnění strom XML.|  
|[Práce s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)|Poskytuje podrobné informace o vytváření stromů XML, které používají obory názvů.|  
|[Serializace XML stromů (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)|Popisuje více přístupy k serializaci strom XML a poskytuje pokyny k jaký přístup k použití.|  
|[Technologie LINQ to XML osy (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)|Uvádí a popisuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osy metody, které je třeba porozumět před zápisem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.|  
|[Dotazování stromy XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)|Obsahuje běžné příklady dotazování stromy XML.|  
|[Úprava XML stromů (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|Modelu DOM (Document Object), jako například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete upravit strom XML na místě.|  
|[Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|Poskytuje informace o poznámky, události, streamování a další pokročilé scénáře.|  
|[Technologie LINQ to XML zabezpečení (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-security.md)|Popisuje problémy se zabezpečením přidružené technologie LINQ to XML a obsahuje některé pokyny pro minimalizaci ohrožení zabezpečení.|  
|[Dokumenty XML ukázkové (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|Obsahuje ukázkové XML dokumenty, které jsou používány mnoho příklady v této dokumentaci.|  
  
## <a name="see-also"></a>Viz také  
 [Začínáme (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [Technologie LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
