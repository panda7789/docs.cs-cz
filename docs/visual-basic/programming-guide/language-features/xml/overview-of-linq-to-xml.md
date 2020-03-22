---
title: Přehled technologie LINQ to XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 0481a140541a7f45c682c5150bc1c3d647de90bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266895"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Přehled technologie LINQ to XML v jazyce Visual Basic
Visual Basic poskytuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podporu pro přes XML literály a vlastnosti osy XML. To umožňuje použít známou a pohodlnou syntaxi pro práci s jazykem XML v kódu jazyka Visual Basic. *Literály XML* umožňují zahrnout XML přímo do kódu. *Vlastnosti osy XML* umožňují přístup k podřízeným uzlům, podřízeným uzlům a atributům literálu XML. Další informace naleznete v [tématu Přehled literálů XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) a [Přístup k XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je programovací rozhraní XML v paměti navržené speciálně pro využití výhod dotazu LINQ (Language-Integrated Query). Přestože můžete volat rozhraní API LINQ přímo, pouze visual basic umožňuje deklarovat literály XML a přímo přistupovat k vlastnostem osy XML.  
  
> [!NOTE]
> Literály XML a vlastnosti osy XML nejsou v deklarativním kódu na stránce ASP.NET podporovány. Chcete-li použít funkce jazyka Visual Basic XML, vložte kód do stránky s kódem na pozadí v aplikaci ASP.NET.  
  
 [Tlačítko Přehrát](./media/overview-of-linq-to-xml/play-video-icon-example.gif) Související ukázky videa najdete v [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml) [tématech Jak začít s LINQ na XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)
  
## <a name="creating-xml"></a>Vytváření XML  
 Existují dva způsoby, jak vytvořit stromy XML v jazyce Visual Basic. Literál XML můžete deklarovat přímo v kódu nebo můžete použít rozhraní LINQ API k vytvoření stromu. Oba procesy umožňují kódu odrážet konečnou strukturu stromu XML. Například následující příklad kódu vytvoří element XML:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Další informace naleznete [v tématu Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Přístup k xml a navigace  
 Visual Basic poskytuje vlastnosti osy XML pro přístup k strukturám XML a pro navigaci. Tyto vlastnosti umožňují přístup k prvkům a atributům XML zadáním názvů podřízených prvků XML. Alternativně můžete explicitně volat LINQ metody pro navigaci a vyhledávání prvků a atributů. Například následující příklad kódu používá vlastnosti osy XML k odkazování na atributy a podřízené prvky elementu XML. Příklad kódu používá dotaz LINQ k načtení podřízených prvků a jejich výstupu jako elementů XML, což efektivně provádí transformaci.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Další informace naleznete [v tématu Přístup k xml v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Obory názvů XML  
 Visual Basic umožňuje zadat alias globálního oboru názvů XML `Imports` pomocí příkazu. Následující příklad ukazuje, jak `Imports` použít příkaz k importu oboru názvů XML:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Alias oboru názvů XML můžete použít při přístupu k vlastnostem osy XML a deklarování literálů XML pro dokumenty a prvky XML.  
  
 Objekt pro <xref:System.Xml.Linq.XNamespace> určitou předponu oboru názvů můžete načíst pomocí [operátoru GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Další informace naleznete v [tématu Imports Statement (XML Namespace).](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Použití oborů názvů XML v literálech XML  
 Následující příklad ukazuje, jak <xref:System.Xml.Linq.XElement> vytvořit objekt, který `ns`používá globální obor názvů :  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Kompilátor jazyka Převádí literály XML, které obsahují aliasy oboru názvů XML, do `xmlns` ekvivalentního kódu, který používá zápis XML pro použití jmenných prostorů XML s atributem. Při kompilaci kód v příkladu předchozí části vytvoří v podstatě stejný spustitelný kód jako následující příklad:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Použití oborů názvů XML ve vlastnostech osy XML  
 Obory názvů XML deklarované v literálech XML nejsou k dispozici pro použití ve vlastnostech osy XML. Globální obory názvů však lze použít s vlastnostmi osy XML. Pomocí dvojtečky oddělte předponu oboru názvů XML od názvu místního prvku. Tady je příklad:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [Xml](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Přístup ke XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Zacházení s XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
