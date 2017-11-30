---
title: "Přehled technologie LINQ to XML v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: baa60939654857f40d323b6412978ed4ff918177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Přehled technologie LINQ to XML v jazyce Visual Basic
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]poskytuje podporu pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prostřednictvím literály XML a vlastnosti osy XML. To umožňuje používat známé a pohodlný syntaxe pro práci s XML v vaší [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu. *XML – literály* umožňují zahrnout přímo v kódu XML. *Vlastnosti osy XML* umožňují přístup podřízené uzly, podřízených uzlů a atributy literál XML. Další informace najdete v tématu [přehled literálů XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) a [přístup ke XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je v paměti XML programování navrženo konkrétně k využívat výhod API [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. I když můžete volat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] přímo, rozhraní API pouze [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] umožňuje deklarace literálů XML a přímý přístup k vlastnosti osy XML.  
  
> [!NOTE]
>  Literály XML a vlastnosti osy XML nejsou podporovány v deklarativní kódu na stránce technologie ASP.NET. Pokud chcete používat funkce jazyka Visual Basic XML, uveďte kódu do kódu stránky v aplikaci ASP.NET.  
  
 ![odkaz na video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") související videoukázky, najdete v části [Jak můžu začít pracovat s technologie LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143034) a [jak se dá vytvořit tabulky aplikace Excel pomocí technologie LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143536).  
  
## <a name="creating-xml"></a>Vytváření XML  
 Existují dva způsoby vytvoření stromy XML v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. XML můžou deklarovat literálu přímo v kódu, nebo můžete použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] rozhraní API pro vytvoření stromu. Oba tyto procesy povolit kód tak, aby odrážela konečné struktura stromu XML. Například následující příklad kódu vytvoří XML element:  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 Další informace najdete v tématu [vytváření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Přístup k informacím a navigace XML  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]poskytuje vlastnosti osy XML pro přístup k informacím a navigace struktury XML. Tyto vlastnosti umožňují přístup zadáním názvy XML podřízených elementů XML elementů a atributů. Alternativně můžete explicitně volat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] metody pro navigaci a vyhledávání elementů a atributů. Například následující příklad kódu používá vlastnosti osy XML k odkazování na atributy a podřízených elementů XML elementu. Příklad kódu používá [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz pro načtení podřízených elementů a jejich výstup jako elementy XML efektivní provádění transformace.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 Další informace najdete v tématu [přístup ke XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Umožňuje určit alias pro globální obor názvů XML s použitím `Imports` příkaz. Následující příklad ukazuje způsob použití `Imports` příkaz pro import obor názvů XML:  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 Alias oboru názvů XML můžete použít při přístup k vlastnosti osy XML a deklarace literálů XML pro dokumenty XML a elementy.  
  
 Můžete načíst <xref:System.Xml.Linq.XNamespace> objekt pro konkrétní obor názvů pomocí [getxmlnamespace – operátor](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Použití oboru názvů XML v literálech XML  
 Následující příklad ukazuje, jak vytvořit <xref:System.Xml.Linq.XElement> objekt, který používá obor názvů globální `ns`:  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru překládá literálů XML, které obsahují aliasy obor názvů XML do ekvivalentní kódu, který používá zápis XML pro obory názvů XML, pomocí `xmlns` atribut. Při kompilaci, vytvoří kód v předchozí části příkladu v podstatě stejný spustitelný kód jako v následujícím příkladu:  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Použití oboru názvů XML ve vlastnosti osy XML  
 Obory názvů XML, které jsou deklarované v literálech XML nejsou k dispozici pro použití v vlastnosti osy XML. Globální obory názvů však lze použít s vlastnosti osy XML. K oddělení Předpona oboru názvů XML od názvu místní element použijte středník. Tady je příklad:  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>Viz také  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Přístup XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [Zacházení s XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
