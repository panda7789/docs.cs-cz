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
ms.openlocfilehash: 3b2dec4224006d35fb9add11e170b9dcbeeafcf3
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368559"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Doporučené značky XML pro dokumentační komentáře (Visual Basic)
Kompilátor jazyka Visual Basic můžete zpracovat dokumentační komentáře v kódu do souboru XML. Další nástroje můžete použít ke zpracování souboru XML do dokumentace ke službě.  
  
 Komentáře XML jsou povolené konstrukcí jako jsou typy a členy typu. Pro částečné typy mají pouze jednu část typu komentáře XML, ačkoli neexistuje žádné omezení komentování jejích členů.  
  
> [!NOTE]
>  Dokumentační komentáře nelze použít pro obory názvů. Důvodem je, že jeden obor názvů může zahrnovat několik sestavení, a ne všechna sestavení mají být načteny současně.  
  
 Kompilátor zpracovává všechny značky, který je platný kód XML. Následující značky poskytuje běžně používané funkce v dokumentaci pro uživatele.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<kód >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<Příklad >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<Výjimka >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<Zahrnout >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<Seznam >](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<Param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<oprávnění >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<REMARKS >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<Vrátí >](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<Zobrazit >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<Summary >](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<Hodnota >](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> kompilátor ověří syntaxi.)  
  
> [!NOTE]
>  Pokud chcete ostré závorky se zobrazí v textu Dokumentační komentář, použijte `&lt;` a `&gt;`. Například řetězec `"&lt;text in angle brackets&gt;"` se zobrazí jako `<text in angle brackets>`.  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
