---
title: Přehled literálů XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: c6d2600b590e01fff062828f8e0f48d9cfad0190
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681388"
---
# <a name="xml-literals-overview-visual-basic"></a>Přehled literálů XML (Visual Basic)
*Literál XML* umožňuje začlenit XML přímo do kódu jazyka Visual Basic. Syntaxe XML literál představuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty a je podobné syntaxi XML 1.0. To usnadňuje vytvořit XML elementů a dokumentů prostřednictvím kódu programu, protože váš kód má stejnou strukturu jako poslední XML.  
  
 Visual Basic zkompiluje literály XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje jednoduchý objektový model pro vytváření prostředků a manipulace s XML a tento model se integruje s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.  
  
 Výraz jazyka Visual Basic můžete vložit v literálu XML. V době běhu, vytvoří aplikaci [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekt pro každý literál obsahující hodnoty vložené výrazy. To vám umožní zadat dynamický obsah uvnitř literálu XML. Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Další informace o rozdílech mezi literálu syntaxe jazyka XML a syntaxe XML 1.0 najdete v tématu [literály XML a specifikace XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Jednoduché literály  
 Můžete vytvořit [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekt v kódu jazyka Visual Basic zadáním nebo vložením v platném formátu XML. Vrátí element XML literál <xref:System.Xml.Linq.XElement> objektu. Další informace najdete v tématu [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) a [literály XML a specifikace XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Následující příklad vytvoří element XML, který má několik podřízených elementů.  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 Dokument XML můžete vytvořit spuštěním literálu s XML `<?xml version="1.0"?>`, jak je znázorněno v následujícím příkladu. Literál dokumentu XML vrátí <xref:System.Xml.Linq.XDocument> objektu. Další informace najdete v tématu [literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  Literál syntaxe jazyka XML v jazyce Visual Basic není shodná se syntaxí ve specifikaci XML 1.0. Další informace najdete v tématu [literály XML a specifikace XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Pokračování řádku  
 Literál XML může zahrnovat více řádků bez použití znaky pokračování řádku (místo podtržítka zadejte pořadí). To usnadňuje porovnání literály XML v kódu s XML dokumenty.  
  
 Kompilátor zpracovává jako součást literál XML znaky pokračování řádku. Proto měli používat pořadí místo podtržítka zadejte pouze v případě, že patří [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektu.  
  
 Však nutné znaky pokračování řádku máte víceřádkového výrazu v vložený výraz. Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Vkládání dotazů v literálech XML  
 Dotaz můžete použít v vložený výraz. Když toto provedete, prvků vrácených dotazem se přidají do elementu XML. Tímto způsobem můžete přidat dynamický obsah, jako je například výsledek dotazu uživatele do literálů XML.  
  
 Například následující kód používá vložený dotaz k vytvoření elementy XML členů `phoneNumbers2` pole a pak přidejte tyto prvky jako podřízené objekty `contact2`.  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Jak kompilátor vytvoří objekty z literálů XML  
 Kompilátor jazyka Visual Basic přeloží literály XML do volání na ekvivalentní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstruktory Vybudujte [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektu. Například kompilátor jazyka Visual Basic přeloží následující příklad kódu do volání <xref:System.Xml.Linq.XProcessingInstruction> volání konstruktoru pro instrukci verze XML, <xref:System.Xml.Linq.XElement> konstruktor pro `<contact>`, `<name>`, a `<phone>` elementy a volání <xref:System.Xml.Linq.XAttribute> konstruktor pro `type` atribut. Konkrétně uvedené atributy v následující ukázce, zavolá kompilátor jazyka Visual Basic <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> konstruktor dvakrát. První předají hodnotu `type` pro `name` parametru a hodnota `home` pro `value` parametru. Druhá bude také předat hodnotu `type` pro `name` parametr, ale hodnota `work` pro `value` parametru.  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xml.Linq.XElement>
- [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md)
