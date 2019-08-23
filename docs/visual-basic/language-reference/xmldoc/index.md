---
title: Doporučené značky XML pro dokumentační komentáře (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 2d6519af8ca1a0e2d59131eec4d63646dce7318b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913508"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Doporučené značky XML pro dokumentační komentáře (Visual Basic)
Kompilátor Visual Basic může zpracovat dokumentační komentáře ve vašem kódu do souboru XML. Pomocí dalších nástrojů můžete zpracovat soubor XML v dokumentaci.  
  
 Komentáře XML jsou povoleny v konstrukcích kódu, jako jsou typy a členy typu. U částečných typů může mít komentáře XML pouze jednu část typu, přestože neexistuje žádné omezení na komentování členů.  
  
> [!NOTE]
> Komentáře k dokumentaci nelze použít na obory názvů. Důvodem je, že jeden obor názvů může zahrnovat několik sestavení a nemusí být načtena všechna sestavení současně.  
  
 Kompilátor zpracovává všechny značky, které jsou platné XML. Následující značky poskytují běžně používané funkce v dokumentaci uživatele.  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<> kódu](../../../visual-basic/language-reference/xmldoc/code.md)|[\<Příklad >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|výjimka > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/exception.md)|zahrnout > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/include.md)|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|param > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/param.md)|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|> oprávnění <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/permission.md)|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|viz > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/see.md)|SeeAlso > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/seealso.md)|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|typeparam > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/typeparam.md)|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> kompilátor ověřuje syntaxi.)  
  
> [!NOTE]
> Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky `&lt;` , `&gt;`použijte a. Například řetězec `"&lt;text in angle brackets&gt;"` se zobrazí jako `<text in angle brackets>`.  
  
## <a name="see-also"></a>Viz také:

- [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Postupy: Vytvořit dokumentaci XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
