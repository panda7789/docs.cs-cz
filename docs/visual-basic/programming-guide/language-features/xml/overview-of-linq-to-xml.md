---
title: Přehled technologie LINQ to XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 044aca634f5a0aa6e557a7dd9c0e1de64e35dc15
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374652"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Přehled technologie LINQ to XML v jazyce Visual Basic
Visual Basic poskytuje podporu pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prostřednictvím literálů XML a vlastností osy XML. To vám umožňuje používat známou a pohodlný Syntax pro práci s XML ve vašem kódu Visual Basic. *Literály XML* umožňují zahrnout XML přímo do kódu. *Vlastnosti osy XML* umožňují přístup k podřízeným uzlům, podřízeným uzlům a atributům literálu XML. Další informace naleznete v tématu [Přehled literálů XML](xml-literals-overview.md) a [přístup k XML v Visual Basic](accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je rozhraní API pro programování v paměti, které je navrženo speciálně pro využití LINQ (Language-Integrated Query). I když můžete volat rozhraní API LINQ přímo, umožňuje pouze Visual Basic deklarovat literály XML a přímo přistupovat k vlastnostem osy XML.  
  
> [!NOTE]
> Literály XML a vlastnosti OS XML nejsou podporovány v deklarativním kódu na stránce ASP.NET. Chcete-li použít funkce Visual Basic XML, vložte svůj kód do stránky s kódem na pozadí v aplikaci ASP.NET.  
  
 [Tlačítko Přehrát](./media/overview-of-linq-to-xml/play-video-icon-example.gif) Související video ukázky najdete v tématu [jak začít s LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) a [jak vytvořit excelové tabulky pomocí LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).
  
## <a name="creating-xml"></a>Vytváření XML  
 Existují dva způsoby, jak vytvořit stromy XML v Visual Basic. Literál XML můžete deklarovat přímo v kódu, nebo můžete použít rozhraní LINQ API k vytvoření stromu. Oba procesy umožňují kódu odrážet konečnou strukturu stromu XML. Například následující příklad kódu vytvoří element XML:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Další informace naleznete v tématu [CREATING XML in Visual Basic](creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Přístup a navigace v XML  
 Visual Basic poskytuje vlastnosti osy XML pro přístup k strukturám XML a jejich procházení. Tyto vlastnosti umožňují přístup k elementům a atributům XML zadáním názvů podřízených elementů XML. Alternativně můžete explicitně volat metody LINQ pro navigaci a hledání prvků a atributů. Například následující příklad kódu používá vlastnosti osy XML pro odkazování na atributy a podřízené prvky elementu XML. Příklad kódu používá dotaz LINQ k načtení podřízených elementů a jejich výstupu jako XML elementů a efektivně provádí transformaci.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Další informace najdete v tématu [přístup k XML v Visual Basic](accessing-xml.md).  
  
## <a name="xml-namespaces"></a>XML – obory názvů  
 Visual Basic umožňuje zadat alias do globálního oboru názvů XML pomocí `Imports` příkazu. Následující příklad ukazuje, jak použít `Imports` příkaz pro import oboru názvů XML:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Můžete použít alias oboru názvů XML, pokud přistupujete k vlastnostem osy XML a deklarujete literály XML pro dokumenty a elementy XML.  
  
 Můžete načíst <xref:System.Xml.Linq.XNamespace> objekt pro konkrétní předponu oboru názvů pomocí [operátoru GetXmlNamespace](../../../language-reference/operators/getxmlnamespace-operator.md).  
  
 Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../../../language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Použití oborů názvů XML v literálech XML  
 Následující příklad ukazuje, jak vytvořit <xref:System.Xml.Linq.XElement> objekt, který používá globální obor názvů `ns` :  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Kompilátor Visual Basic překládá literály XML, které obsahují aliasy oboru názvů XML, do ekvivalentního kódu, který používá zápis XML pro použití oborů názvů XML, s `xmlns` atributem. Při kompilaci kódu v příkladu předchozí části se v podstatě vytvoří stejný spustitelný kód jako v následujícím příkladu:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Použití oborů názvů XML ve vlastnostech osy XML  
 Obory názvů XML deklarované v literálech XML nejsou k dispozici pro použití ve vlastnostech osy XML. Globální obory názvů však lze použít s vlastnostmi osy XML. Použijte dvojtečku pro oddělení předpony oboru názvů XML z názvu místního elementu. Tady je příklad:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [XML](index.md)
- [Vytvoření XML v jazyce Visual Basic](creating-xml.md)
- [Přístup ke XML v jazyce Visual Basic](accessing-xml.md)
- [Zacházení s XML v jazyce Visual Basic](manipulating-xml.md)
