---
title: Přehled oborů názvů (technologie LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 03451f50605adf6de0d43f19d220aaeed382f13c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="namespaces-overview-linq-to-xml"></a>Přehled oborů názvů (technologie LINQ to XML)
Toto téma představuje obory názvů, <xref:System.Xml.Linq.XName> třída a <xref:System.Xml.Linq.XNamespace> třídy.  
  
## <a name="xml-names"></a>Názvy XML  
 Názvy XML jsou často zdroj složitostí při programování XML. Název XML se skládá z oboru názvů XML (také nazývané identifikátor URI oboru názvů XML) a místní název. Je podobná oboru názvů v oboru názvů XML [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]– na základě programu. Umožňuje jednoznačně kvalifikovat názvy elementů a atributů. To pomáhá zabránit konflikty v názvech mezi různé části dokumentu XML. Pokud máte deklarován obor názvů XML, můžete vybrat místní název, který se musí být jedinečný v daném oboru názvů.  
  
 Další aspekt názvů XML je XML *předpony oboru názvů*. XML – předpony způsobit, že většina složitost názvů XML. Tyto předpony umožňují vytvořit zástupce pro obor názvů XML, který zkracují a nerozumí dokumentu XML. XML – předpony však závisí na jejich kontext, který má význam, který přidá složitost. Například předpona XML `aw` může být spojeny s jeden obor názvů XML v jedné části stromu XML a s jiný obor názvů XML v různých součástí stromové struktuře XML.  
  
 Jednou z výhod použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pomocí C# je, že není nutné používat XML – předpony. Když [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zatížení nebo analyzuje dokument XML, každý předpona XML je přeložen na jeho odpovídající obor názvů XML. Potom při práci s dokumentem, který používá obory názvů, téměř vždy přistupujete obory názvů pomocí identifikátoru URI oboru názvů a ne prostřednictvím Předpona oboru názvů. Když vývojářům pracovat s názvy XML v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vždy pracují s plně kvalifikovaný název XML (to znamená, obor názvů XML a místní název). Nicméně, pokud je to nezbytné, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňuje pracovat s a řídit předpony oboru názvů.  
  
 V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], je třída, která představuje názvy XML <xref:System.Xml.Linq.XName>. Často se názvy XML v průběhu zobrazit [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API, a bez ohledu na název XML je potřeba, najdete <xref:System.Xml.Linq.XName> parametr. Nicméně, občas pracovat přímo se <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> obsahuje implicitní převod z řetězce.  
  
 Další informace naleznete v tématu <xref:System.Xml.Linq.XNamespace> a <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Viz také  
 [Práce s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
