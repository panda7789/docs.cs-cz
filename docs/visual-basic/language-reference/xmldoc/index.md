---
title: Doporučené značky XML pro dokumentační komentáře
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 093c967557b899c8661fdec348d421996e948b94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352336"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Doporučené značky XML pro dokumentační komentáře (Visual Basic)
Kompilátor Visual Basic může zpracovat dokumentační komentáře ve vašem kódu do souboru XML. Pomocí dalších nástrojů můžete zpracovat soubor XML v dokumentaci.  
  
 Komentáře XML jsou povoleny v konstrukcích kódu, jako jsou typy a členy typu. U částečných typů může mít komentáře XML pouze jednu část typu, přestože neexistuje žádné omezení na komentování členů.  
  
> [!NOTE]
> Komentáře k dokumentaci nelze použít na obory názvů. Důvodem je, že jeden obor názvů může zahrnovat několik sestavení a nemusí být načtena všechna sestavení současně.  
  
 Kompilátor zpracovává všechny značky, které jsou platné XML. Následující značky poskytují běžně používané funkce v dokumentaci uživatele.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[kód \<>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<příklad >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[výjimka\<>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<zahrnout >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[seznam \<>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<oprávnění >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<poznámky >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<zobrazit >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> kompilátor ověřuje syntaxi.)  
  
> [!NOTE]
> Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, použijte `&lt;` a `&gt;`. Například řetězec `"&lt;text in angle brackets&gt;"` se zobrazí jako `<text in angle brackets>`.  
  
## <a name="see-also"></a>Viz také:

- [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
