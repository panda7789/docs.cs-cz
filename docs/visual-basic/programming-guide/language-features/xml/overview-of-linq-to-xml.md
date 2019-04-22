---
title: Přehled technologie LINQ to XML v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 91f622b9eecdd1aec8b9361493095e92a851988e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816171"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Přehled technologie LINQ to XML v jazyce Visual Basic
Visual Basic poskytuje podporu pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prostřednictvím literály XML a vlastnosti OS XML. To umožňuje používat známé a pohodlné syntaxe pro práci s XML v kódu jazyka Visual Basic. *Literály XML* umožňují zahrnout XML přímo v kódu. *Vlastnosti osy XML* umožňují přístup podřízené uzly, podřízených uzlů a atributů literálu XML. Další informace najdete v tématu [přehled literálů XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) a [přístup ke XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je XML v paměti programování API určené konkrétně pro využít výhod [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. I když můžete volat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] přímo rozhraní API, pouze Visual Basic umožňuje deklarovat literály XML a přímý přístup k vlastnosti osy XML.  
  
> [!NOTE]
>  Literály XML a vlastnosti OS XML nejsou podporovány v deklarativního kódu na stránce ASP.NET. Pokud chcete používat funkce XML v jazyce Visual Basic, ukládejte kód v modelu code-behind stránky v aplikaci ASP.NET.  
  
 ![odkaz na video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") související videa s ukázkami, naleznete v tématu [jak mám začít s LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) a [co a jak vytvářet tabulky aplikace Excel pomocí LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).  
  
## <a name="creating-xml"></a>Vytváření XML  
 Existují dva způsoby vytvoření stromů XML v jazyce Visual Basic. Je možné deklarovat XML literál přímo v kódu, nebo můžete použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] rozhraní API pro vytvoření stromu. Oba tyto procesy povolit kód tak, aby odrážely finální strukturu stromu XML. Například následující příklad kódu vytvoří XML element:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Další informace najdete v tématu [vytváření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Přístup k a procházení XML  
 Visual Basic poskytuje vlastnosti osy XML pro přístup k a navigace struktury XML. Tyto vlastnosti umožňují přístup k XML elementů a atributů tak, že zadáte názvy XML podřízených elementů. Alternativně můžete explicitně volat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] metody pro procházení a vyhledávání elementů a atributů. Například následující příklad kódu používá vlastnosti osy XML k odkazování na atributy a podřízené prvky prvku XML. Příklad kódu používá [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz pro načtení podřízené prvky a výstup jako prvky jazyka XML, efektivní provádění transformace.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Další informace najdete v tématu [přístup ke XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 Visual Basic umožňuje určit aliasu pro globální obor názvů XML s použitím `Imports` příkazu. Následující příklad ukazuje způsob použití `Imports` smlouvu pro import obor názvů XML:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Pokud přístup k vlastnosti osy XML a deklarace literálů XML dokumentů XML a prvků, můžete použít alias oboru názvů XML.  
  
 Můžete načíst <xref:System.Xml.Linq.XNamespace> objektu pro konkrétní obor názvů předponu pomocí [GetXmlNamespace operátor](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Použití oboru názvů XML v literálech XML  
 Následující příklad ukazuje, jak vytvořit <xref:System.Xml.Linq.XElement> objekt, který používá globální obor názvů `ns`:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Kompilátor jazyka Visual Basic přeloží literály XML, které obsahují aliasy oboru názvů XML do ekvivalentní kód, který se používá zápis XML pro použití s obory názvů XML `xmlns` atribut. Při kompilaci, vytvoří kód v předchozí části příkladu v podstatě stejný spustitelný kód jako v následujícím příkladu:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Použití oboru názvů XML ve vlastnosti osy XML  
 Obory názvů XML, které jsou deklarovány v literálech XML nejsou k dispozici pro použití ve vlastnosti osy XML. Globálními názvovými prostory je však možné pomocí vlastnosti osy XML. Pomocí dvojtečky k oddělení od názvu elementu místní předponu oboru názvů XML. Tady je příklad:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Přístup ke XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Manipulace s kódem XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
