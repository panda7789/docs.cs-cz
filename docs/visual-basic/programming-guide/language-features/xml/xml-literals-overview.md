---
title: Přehled literálů XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: e5d2465d145f4059600121c6cef30bb2c74a8c1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346191"
---
# <a name="xml-literals-overview-visual-basic"></a>Přehled literálů XML (Visual Basic)
*Literál XML* umožňuje začlenit XML přímo do kódu Visual Basic. Syntaxe literálu XML představuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektů a je podobná syntaxi XML 1,0. To usnadňuje vytváření elementů XML a dokumentů programově, protože váš kód má stejnou strukturu jako finální XML.  
  
 Visual Basic zkompiluje literály XML do objektů [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje jednoduchý objektový model pro vytváření a manipulaci s XML a tento model se dobře integruje s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Další informace najdete v tématu <xref:System.Xml.Linq.XElement>.  
  
 Výraz Visual Basic lze vložit do literálu XML. V době běhu aplikace vytvoří objekt [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pro každý literál, který zahrnuje hodnoty vložených výrazů. To umožňuje zadat dynamický obsah uvnitř literálu XML. Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Další informace o rozdílech mezi syntaxí literálu XML a syntaxí XML 1,0 naleznete v tématu [literály XML a specifikace xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Jednoduché literály  
 Objekt [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete v kódu Visual Basic vytvořit zadáním nebo vložením v platném formátu XML. Literál XML elementu vrátí objekt <xref:System.Xml.Linq.XElement>. Další informace naleznete v tématu [literály elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) a [literály XML a specifikace XML 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Následující příklad vytvoří element XML, který má několik podřízených elementů.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Dokument XML můžete vytvořit spuštěním literálu XML pomocí `<?xml version="1.0"?>`, jak je znázorněno v následujícím příkladu. Literál dokumentu XML vrací objekt <xref:System.Xml.Linq.XDocument>. Další informace naleznete v tématu [literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Syntaxe literálu XML v Visual Basic není shodná se syntaxí ve specifikaci XML 1,0. Další informace naleznete v tématu [literály XML a specifikace xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Pokračování řádku  
 Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku (mezera-podtržítko-ENTER Sequence). Díky tomu je snazší porovnat literály XML v kódu s dokumenty XML.  
  
 Kompilátor zpracovává znaky pro pokračování řádku jako součást literálu XML. Proto byste měli použít sekvenci Space-podtržítko-ENTER pouze v případě, že patří do objektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Pokud ale máte víceřádkový výraz ve vloženém výrazu, budete potřebovat znaky pro pokračování řádku. Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Vložení dotazů do literálů XML  
 Dotaz můžete použít ve vloženém výrazu. Když to uděláte, prvky vrácené dotazem jsou přidány do elementu XML. To umožňuje přidat dynamický obsah, jako je například výsledek dotazu uživatele, do literálu XML.  
  
 Například následující kód používá vložený dotaz k vytvoření prvků XML ze členů pole `phoneNumbers2` a poté tyto prvky přidat jako podřízené položky `contact2`.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Jak kompilátor vytváří objekty z literálů XML  
 Kompilátor Visual Basic překládá literály XML do volání ekvivalentních [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ch konstruktorů pro sestavení objektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Například kompilátor Visual Basic převede následující příklad kódu do volání konstruktoru <xref:System.Xml.Linq.XProcessingInstruction> pro instrukci verze XML, volání konstruktoru <xref:System.Xml.Linq.XElement> pro prvky `<contact>`, `<name>`a `<phone>` a volání <xref:System.Xml.Linq.XAttribute>ho konstruktoru pro atribut `type`. Konkrétně při základě atributů v následující ukázce Visual Basic kompilátor volá <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> konstruktoru dvakrát. První předáte hodnotu `type` parametru `name` a hodnotu `home` pro parametr `value`. Druhá hodnota také předáte `type` hodnoty parametru `name`, ale hodnotu `work` pro parametr `value`.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- [Vytváření XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md)
