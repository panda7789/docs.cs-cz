---
title: Komentáře v kódu
ms.date: 07/20/2015
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
ms.openlocfilehash: 189810393db42c54cb8a0f97b22b3d1514d9a7c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346172"
---
# <a name="comments-in-code-visual-basic"></a>Komentáře v kódu (Visual Basic)
Při čtení příkladů kódu často narazíte na symbol komentáře (`'`). Tento symbol instruuje kompilátor Visual Basic, že má ignorovat text, který následuje, nebo *Komentář*. Komentáře jsou stručné vysvětlivky doplněné do kódu kvůli lepší orientaci těch, kteří si ho prohlížejí.  
  
 Při programování je dobrým zvykem začínat všechny procedury stručným komentářem, který popisuje funkční charakteristiky procedury (co dělá). Budete z toho mít prospěch jak vy, tak všichni ostatní, kteří tento kód prověřují. Podrobnosti implementace (jak to procedura dělá) byste měli oddělit od komentářů, které popisují funkční charakteristiky. Pokud do popisu zahrnete podrobnosti implementace, při úpravě funkce je nezapomeňte aktualizovat.  
  
 Komentáře mohou následovat za příkazem na stejném řádku, nebo obsazovat celý řádek. Obě varianty jsou znázorněny v následujícím kódu.  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 Pokud komentář vyžaduje více než jeden řádek, použijte symbol komentáře na každém řádku, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a>Pokyny ke komentování  
 Následující tabulka obsahuje obecné pokyny k tomu, jaké typy komentářů mohou být před kódem. Jedná se o návrhy; Visual Basic nevynutila pravidla pro přidávání komentářů. Napište všechno, co má význam pro vás i pro kohokoli jiného, kdo si váš kód bude prohlížet.  
  
|||  
|---|---|  
|Typ komentáře|Popis komentáře|  
|Účel|Popisuje, co procedura dělá (ne jak to dělá).|  
|Předpoklady|Uvádí všechny externí proměnné, ovládací prvky, otevřené soubory nebo jiné prvky, ke kterým procedura přistupuje.|  
|Účinek|Uvádí všechny ovlivněné externí proměnné, ovládací prvky nebo soubory a účinek, který má (pouze pokud to není zřejmé).|  
|Vstupy|Určuje účel argumentu.|  
|Vrací|Vysvětluje hodnoty vrácené procedurou.|  
  
 Mějte na paměti následující body:  
  
- Každou deklaraci důležité proměnné by měl předcházet komentář popisující použití této deklarované proměnné.  
  
- Proměnné, ovládací prvky a procedury by měly být pojmenovány dostatečně výstižně, aby byly komentáře zapotřebí pouze pro složité podrobnosti implementace.  
  
- Komentáře nemohou následovat za posloupností pokračování řádku na stejném řádku.  
  
 Chcete-li přidat nebo odebrat symboly komentářů pro blok kódu, vyberte jeden nebo více řádků kódu a zvolte **Komentář** (![tlačítko Visual Basic komentář v sadě Visual studio.](./media/comments-in-code/visual-basic-comment-button.gif)) a **zrušte komentář** (![tlačítko Visual Basic odkomentovat v sadě Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) na panelu nástrojů **Úpravy** .  
  
> [!NOTE]
> Komentáře můžete do kódu přidat také tak, že před text vložíte klíčové slovo `REM`. Nicméně symbol `'` a tlačítka **komentář**/zrušit **Komentář** se snadněji používají a vyžadují méně místa a paměti.  
  
## <a name="see-also"></a>Viz také:

- [Základní instinkty – dokumentování kódu pomocí komentářů XML](https://docs.microsoft.com/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Příkaz REM](../../../visual-basic/language-reference/statements/rem-statement.md)
