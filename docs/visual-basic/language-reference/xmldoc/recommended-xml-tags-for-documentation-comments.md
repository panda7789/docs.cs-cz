---
title: Doporučené značky XML pro dokumentační komentáře (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7815d4c9fddc4e760c7495ef7a2509c55141e96e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Doporučené značky XML pro dokumentační komentáře (Visual Basic)
Visual Basic – kompilátor může zpracovat dokumentační komentáře v kódu do souboru XML. Další nástroje můžete používat ke zpracování souboru XML do dokumentace.  
  
 XML – komentáře na kód konstruktory, jako jsou typy jsou povoleny a zadejte členy. Pro částečné typy pouze jednu část typu může mít komentáře XML, i když neexistuje žádné omezení na komentářů její členy.  
  
> [!NOTE]
>  Dokumentační komentáře nelze použít na obory názvů. Důvodem je, že několik sestavení může mít rozsah jeden obor názvů, a ne všechny sestavení musí být načíst ve stejnou dobu.  
  
 Kompilátor zpracovává všechny značky, který je platný kód XML. Následující značky poskytují běžně používané funkce v dokumentaci pro uživatele.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<kód >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<Příklad >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<Výjimka >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<Zahrnout >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<Seznam >](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<Param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<oprávnění >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<Poznámky >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<Vrátí >](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<v tématu >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<Viz také >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<Souhrn >](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<Hodnota >](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> kompilátor ověří syntaxi.)  
  
> [!NOTE]
>  Pokud chcete lomené závorky, než se objeví v text komentáře dokumentace, použijte `<` a `>`. Například řetězec `"<text in angle brackets>"` se zobrazí jako `<text in angle``brackets>`.  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
