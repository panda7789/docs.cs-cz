---
title: Přehled literálů XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: e889de4eefae6a943c70735f8a16474cb76d1149
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403288"
---
# <a name="xml-literals-overview-visual-basic"></a>Přehled literálů XML (Visual Basic)
*Literál XML* umožňuje začlenit XML přímo do kódu Visual Basic. Syntaxe literálu XML reprezentuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty a je podobná SYNTAXI XML 1,0. To usnadňuje vytváření elementů XML a dokumentů programově, protože váš kód má stejnou strukturu jako finální XML.  
  
 Visual Basic zkompiluje literály XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektů. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje jednoduchý objektový model pro vytváření a manipulaci s XML a tento model se dobře integruje s dotazem integrovaným na jazyk (LINQ). Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.  
  
 Výraz Visual Basic lze vložit do literálu XML. V době běhu aplikace vytvoří [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekt pro každý literál, který zahrnuje hodnoty vložených výrazů. To umožňuje zadat dynamický obsah uvnitř literálu XML. Další informace najdete v tématu [vložené výrazy v XML](embedded-expressions-in-xml.md).  
  
 Další informace o rozdílech mezi syntaxí literálu XML a syntaxí XML 1,0 naleznete v tématu [literály XML a specifikace xml 1,0](xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Jednoduché literály  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Objekt můžete v kódu Visual Basic vytvořit zadáním nebo vložením v platném formátu XML. Literál elementu XML vrací <xref:System.Xml.Linq.XElement> objekt. Další informace naleznete v tématu [literály elementu XML](../../../language-reference/xml-literals/xml-element-literal.md) a [literály XML a specifikace XML 1,0](xml-literals-and-the-xml-1-0-specification.md). Následující příklad vytvoří element XML, který má několik podřízených elementů.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Dokument XML můžete vytvořit spuštěním literálu XML pomocí `<?xml version="1.0"?>` , jak je znázorněno v následujícím příkladu. Literál dokumentu XML vrací <xref:System.Xml.Linq.XDocument> objekt. Další informace naleznete v tématu [literál dokumentu XML](../../../language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Syntaxe literálu XML v Visual Basic není shodná se syntaxí ve specifikaci XML 1,0. Další informace naleznete v tématu [literály XML a specifikace xml 1,0](xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Pokračování řádku  
 Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku (mezera-podtržítko-ENTER Sequence). Díky tomu je snazší porovnat literály XML v kódu s dokumenty XML.  
  
 Kompilátor zpracovává znaky pro pokračování řádku jako součást literálu XML. Proto byste měli použít sekvenci Space-podtržítko-ENTER pouze v případě, že patří do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektu.  
  
 Pokud ale máte víceřádkový výraz ve vloženém výrazu, budete potřebovat znaky pro pokračování řádku. Další informace najdete v tématu [vložené výrazy v XML](embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Vložení dotazů do literálů XML  
 Dotaz můžete použít ve vloženém výrazu. Když to uděláte, prvky vrácené dotazem jsou přidány do elementu XML. To umožňuje přidat dynamický obsah, jako je například výsledek dotazu uživatele, do literálu XML.  
  
 Například následující kód používá vložený dotaz k vytvoření prvků XML ze členů `phoneNumbers2` pole a poté tyto prvky přidat jako podřízené položky `contact2` .  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Jak kompilátor vytváří objekty z literálů XML  
 Kompilátor Visual Basic překládá literály XML do volání ekvivalentních [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstruktorů pro sestavení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektu. Například kompilátor Visual Basic přeloží následující příklad kódu do volání <xref:System.Xml.Linq.XProcessingInstruction> konstruktoru pro instrukci verze XML, volání <xref:System.Xml.Linq.XElement> konstruktoru pro `<contact>` `<name>` prvky, a a `<phone>` volání konstruktoru pro <xref:System.Xml.Linq.XAttribute> `type` atribut. Konkrétně při základě atributů v následující ukázce bude kompilátor Visual Basic volat <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> konstruktor dvakrát. První předáte hodnotu `type` `name` parametru a hodnotu `home` `value` parametru. Druhý bude také předávat hodnotu `type` `name` parametru, ale hodnotu `work` `value` parametru.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement>
- [Vytvoření XML v jazyce Visual Basic](creating-xml.md)
- [Vložené výrazy v XML](embedded-expressions-in-xml.md)
- [Literál dokumentu XML](../../../language-reference/xml-literals/xml-document-literal.md)
- [Literál XML elementu](../../../language-reference/xml-literals/xml-element-literal.md)
- [Literály XML](../../../language-reference/xml-literals/index.md)
