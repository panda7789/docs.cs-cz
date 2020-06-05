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
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400096"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Doporučené značky XML pro dokumentační komentáře (Visual Basic)
Kompilátor Visual Basic může zpracovat dokumentační komentáře ve vašem kódu do souboru XML. Pomocí dalších nástrojů můžete zpracovat soubor XML v dokumentaci.  
  
 Komentáře XML jsou povoleny v konstrukcích kódu, jako jsou typy a členy typu. U částečných typů může mít komentáře XML pouze jednu část typu, přestože neexistuje žádné omezení na komentování členů.  
  
> [!NOTE]
> Komentáře k dokumentaci nelze použít na obory názvů. Důvodem je, že jeden obor názvů může zahrnovat několik sestavení a nemusí být načtena všechna sestavení současně.  
  
 Kompilátor zpracovává všechny značky, které jsou platné XML. Následující značky poskytují běžně používané funkce v dokumentaci uživatele.  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|[\<exception>](exception.md)<sup>1</sup>|[\<include>](include.md)<sup>1</sup>|[\<list>](list.md)|  
|[\<para>](para.md)|[\<param>](param.md)<sup>1</sup>|[\<paramref>](paramref.md)|  
|[\<permission>](permission.md)<sup>1</sup>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|[\<see>](see.md)<sup>1</sup>|[\<seealso>](seealso.md)<sup>1</sup>|[\<summary>](summary.md)|  
|[\<typeparam>](typeparam.md)<sup>1</sup>|[\<value>](value.md)||  
  
 (<sup>1</sup> kompilátor ověřuje syntaxi.)  
  
> [!NOTE]
> Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, použijte `&lt;` a `&gt;` . Například řetězec se `"&lt;text in angle brackets&gt;"` zobrazí jako `<text in angle brackets>` .  
  
## <a name="see-also"></a>Viz také

- [Dokumentace kódu s XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../reference/command-line-compiler/doc.md)
- [Postupy: Vytvoření dokumentace XML](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
