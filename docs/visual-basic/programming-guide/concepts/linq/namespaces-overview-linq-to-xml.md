---
title: "Přehled oborů názvů (technologie LINQ to XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 082172720abd39634f7183367d4d7b8d53d2bb7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces-overview-linq-to-xml"></a>Přehled oborů názvů (technologie LINQ to XML)
Toto téma představuje obory názvů, <xref:System.Xml.Linq.XName> třída a <xref:System.Xml.Linq.XNamespace> třídy.  
  
## <a name="xml-names"></a>Názvy XML  
 Názvy XML jsou často zdroj složitostí při programování XML. Název XML se skládá z oboru názvů XML (také nazývané identifikátor URI oboru názvů XML) a místní název. Je podobná oboru názvů v oboru názvů XML [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]– na základě programu. Umožňuje jednoznačně kvalifikovat názvy elementů a atributů. To pomáhá zabránit konflikty v názvech mezi různé části dokumentu XML. Pokud máte deklarován obor názvů XML, můžete vybrat místní název, který se musí být jedinečný v daném oboru názvů.  
  
 Další aspekt názvů XML je XML *předpony oboru názvů*. XML – předpony způsobit, že většina složitost názvů XML. Tyto předpony umožňují vytvořit zástupce pro obor názvů XML, který zkracují a nerozumí dokumentu XML. XML – předpony však závisí na jejich kontext, který má význam, který přidá složitost. Například předpona XML `aw` může být spojeny s jeden obor názvů XML v jedné části stromu XML a s jiný obor názvů XML v různých součástí stromové struktuře XML.  
  
 Při použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s Visual Basic a XML – literály, musíte použít předpony oboru názvů při práci s dokumenty v oborech názvů.  
  
 V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], je třída, která představuje názvy XML <xref:System.Xml.Linq.XName>. Často se názvy XML v průběhu zobrazit [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API, a bez ohledu na název XML je potřeba, najdete <xref:System.Xml.Linq.XName> parametr. Nicméně, občas pracovat přímo se <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName>obsahuje implicitní převod z řetězce.  
  
 Další informace naleznete v tématu <xref:System.Xml.Linq.XNamespace> a <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Viz také  
 [Práce s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
