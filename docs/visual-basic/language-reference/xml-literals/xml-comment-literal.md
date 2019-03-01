---
title: Literál komentáře XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 1f8526c4b67b7d975b11f6ef5dada2b45bb6b1df
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964176"
---
# <a name="xml-comment-literal-visual-basic"></a>Literál komentáře XML (Visual Basic)
Literál představující <xref:System.Xml.Linq.XComment> objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`<!--`|Povinný parametr. Označuje začátek komentáře XML.|  
|`content`|Povinný parametr. Text, který se zobrazí v komentáři XML. Nesmí obsahovat dvě pomlčky (-) nebo končit pomlčkou za uzavírací značku.|  
|`-->`|Povinný parametr. Označuje konec komentáře XML.|  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XComment> Objektu.  
  
## <a name="remarks"></a>Poznámky  
 Literály XML komentář neobsahují obsah dokumentu obsahují informace o dokumentu. Část Komentář XML se končí pořadí "-->". Z toho vyplývá následující body:  
  
-   Vložený výraz v literál komentáře XML nejde použít, protože vložený výraz oddělovače jsou platný obsah komentáře XML.  
  
-   Oddíly Komentář XML nemůže být vnořena, protože `content` nemůže obsahovat hodnotu "-->".  
  
 Literál komentáře XML můžete přiřadit k proměnné nebo je můžete zahrnout do literálů XML element.  
  
> [!NOTE]
>  Literál XML může zahrnovat více řádků bez použití znaků pokračování řádku. Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.  
  
 Kompilátor jazyka Visual Basic převede literál komentáře XML na volání <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří komentáře XML, který obsahuje text "Toto je komentář".  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xml.Linq.XComment>
- [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
