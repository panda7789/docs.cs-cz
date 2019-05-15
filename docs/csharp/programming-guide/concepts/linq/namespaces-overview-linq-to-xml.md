---
title: Přehled názvových prostorů (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: e4be7ae398d69145ad8d22e5618a47c70db4fe5f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585754"
---
# <a name="namespaces-overview-linq-to-xml"></a>Přehled názvových prostorů (LINQ to XML)
Toto téma představuje obory názvů, <xref:System.Xml.Linq.XName> třídy a <xref:System.Xml.Linq.XNamespace> třídy.  
  
## <a name="xml-names"></a>Názvy XML  
 Názvy XML jsou často zdroj složitosti XML programování. Název XML obsahuje obor názvů XML (také nazývané identifikátor URI oboru názvů XML) a místní název. Obor názvů XML je podobný oboru názvů v aplikaci založené na rozhraní .NET Framework. Umožňuje vám k vyfiltrování jedinečné názvy prvků a atributů. To pomáhá předejít název je v konfliktu mezi různé části dokumentu XML. Když je deklarován obor názvů XML, můžete vybrat místní název, který se musí být jedinečný v rámci tohoto oboru názvů.  
  
 Dalším aspektem názvy XML je XML *předpony oboru názvů*. XML předpony způsobit, že většina složitost názvy XML. Tyto předpony umožňují vytvořit zástupce pro obor názvů XML, který vytvoří dokument XML, výstižný a srozumitelný. XML předpony však závisí na jejich kontextu má význam, který zvyšuje složitost. Například, předpona XML `aw` asociované s jeden obor názvů XML v jedné části stromu XML a jiný obor názvů XML v jiné části stromu XML.  
  
 Jednou z výhod používání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pomocí jazyka C# je, že není nutné použít XML předpony. Když [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zatížení nebo analyzuje dokument XML, každý předpona XML je přeložen na jeho odpovídající obor názvů XML. Poté při práci s dokumentem, který používá obory názvů, téměř vždy přistupujete obory názvů pomocí oboru názvů URI a ne prostřednictvím předponu oboru názvů. Když vývojáři pracovat s názvy XML v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vždy pracovat plně kvalifikovaný název XML (to znamená, obor názvů XML a místní název). Nicméně, pokud je to nezbytné, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňuje pracovat a řízení předpon názvového prostoru.  
  
 V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], je třída, která představuje názvy XML <xref:System.Xml.Linq.XName>. Názvy XML se zobrazí často v průběhu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API, a bez ohledu na to se vyžaduje název XML, najdete <xref:System.Xml.Linq.XName> parametru. Ale zřídka pracovat přímo se <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> obsahuje implicitní převod z řetězce.  
  
 Další informace naleznete v tématu <xref:System.Xml.Linq.XNamespace> a <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Viz také:

- [Práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
