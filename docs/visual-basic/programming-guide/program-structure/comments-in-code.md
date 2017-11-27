---
title: "Komentáře v kódu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cf1aa755c479c73c64951f80ab0b76985507da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="comments-in-code-visual-basic"></a>Komentáře v kódu (Visual Basic)
Při čtení ukázky kódu, často narazíte na symbol komentáře (`'`). Tento symbol informuje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru ignorovat, následující text nebo *komentář*. Komentáře jsou stručné vysvětlivky doplněné do kódu kvůli lepší orientaci těch, kteří si ho prohlížejí.  
  
 Při programování je dobrým zvykem začínat všechny procedury stručným komentářem, který popisuje funkční charakteristiky procedury (co dělá). Budete z toho mít prospěch jak vy, tak všichni ostatní, kteří tento kód prověřují. Podrobnosti implementace (jak to procedura dělá) byste měli oddělit od komentářů, které popisují funkční charakteristiky. Pokud do popisu zahrnete podrobnosti implementace, při úpravě funkce je nezapomeňte aktualizovat.  
  
 Komentáře mohou následovat za příkazem na stejném řádku, nebo obsazovat celý řádek. Obě varianty jsou znázorněny v následujícím kódu.  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 Pokud komentář vyžaduje více než jeden řádek, použijte symbol komentáře na každém řádku, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## <a name="commenting-guidelines"></a>Pokyny ke komentování  
 Následující tabulka obsahuje obecné pokyny k tomu, jaké typy komentářů mohou být před kódem. Jedná se o návrhy; [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nedokáže vynutit pravidla pro přidávání komentářů. Napište všechno, co má význam pro vás i pro kohokoli jiného, kdo si váš kód bude prohlížet.  
  
|||  
|---|---|  
|Typ komentáře|Popis komentáře|  
|Účel|Popisuje, co procedura dělá (ne jak to dělá).|  
|Předpoklady|Uvádí všechny externí proměnné, ovládací prvky, otevřené soubory nebo jiné prvky, ke kterým procedura přistupuje.|  
|Účinek|Uvádí všechny ovlivněné externí proměnné, ovládací prvky nebo soubory a účinek, který má (pouze pokud to není zřejmé).|  
|Vstupy|Určuje účel argumentu.|  
|Vrací|Vysvětluje hodnoty vrácené procedurou.|  
  
 Mějte na paměti následující body:  
  
-   Každou deklaraci důležité proměnné by měl předcházet komentář popisující použití této deklarované proměnné.  
  
-   Proměnné, ovládací prvky a procedury by měly být pojmenovány dostatečně výstižně, aby byly komentáře zapotřebí pouze pro složité podrobnosti implementace.  
  
-   Komentáře nemohou následovat za posloupností pokračování řádku na stejném řádku.  
  
 Můžete přidat nebo odebrat komentář symboly pro blok kódu výběrem jednoho nebo více řádků kódu a zvolením **komentář** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton ")) a **zrušte komentáře u** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) tlačítka na **upravit**  panelu nástrojů.  
  
> [!NOTE]
>  Komentáře můžete také přidat do kódu tak, že před textu pomocí `REM` – klíčové slovo. Ale `'` symbol a **komentář**/**zrušte komentáře u** tlačítka se snadněji používat a vyžadovat méně místa a paměti.  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace kódu s XML – komentáře](http://msdn.microsoft.com/magazine/dd722812.aspx)  
 [Postupy: vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [Struktura programu a pravidla týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [REM – příkaz](../../../visual-basic/language-reference/statements/rem-statement.md)
