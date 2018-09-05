---
title: RaiseEvent – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: ef4dce290a7a7f6340b15aa4083cd40518e37d0d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507389"
---
# <a name="raiseevent-statement"></a>RaiseEvent – příkaz
Spustí událost deklarovanou na úrovni modulu uvnitř třídy, formuláře nebo dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Součásti  
 `eventname`  
 Požadováno. Název události k aktivaci.  
  
 `argumentlist`  
 Volitelné. Čárkami oddělený seznam proměnných, pole nebo výrazy. `argumentlist` Argument musí být uzavřen v závorkách. Pokud neexistují žádné argumenty, musí být vynechána závorky.  
  
## <a name="remarks"></a>Poznámky  
 Požadované `eventname` je název události deklarované v rámci modulu. Splňuje zásady vytváření názvů proměnných jazyka Visual Basic.  
  
 Pokud událost nebyla deklarována v rámci modulu, ve kterém se vyvolá, dojde k chybě. Následující fragment kódu ukazuje deklaraci události a postup vyvolání události.  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 Nemůžete použít `RaiseEvent` vyvolávat události, které nejsou explicitně deklarovány v modulu. Například zdědí všechny formuláře <xref:System.Windows.Forms.Control.Click> událost z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, nelze vyvolat, pomocí `RaiseEvent` ve formě odvozené. Pokud deklarujete `Click` událostí v modulu formuláře je zastiňuje formuláře vlastní <xref:System.Windows.Forms.Control.Click> událostí. Stále můžete vyvolat formuláře <xref:System.Windows.Forms.Control.Click> události voláním <xref:System.Windows.Forms.Control.OnClick%2A> metody.  
  
 Ve výchozím nastavení události definované v jazyce Visual Basic vyvolá jeho obslužné rutiny událostí v pořadí, že se vytvoří připojení. Vzhledem k tomu, že události můžou mít `ByRef` parametry, proces, který se připojuje pozdní mohou přijímat parametry, které se změnily předchozí obslužnou rutinou události. Po spuštění obslužné rutiny událostí, ovládací prvek se vrátí do podprogram, který vyvolal událost.  
  
> [!NOTE]
>  Pro nesdílené události by neměla být vyvolána v rámci konstruktoru třídy, ve kterém jsou deklarovány. I když tyto události nezpůsobí chyby za běhu, se nemusí podařit ji zachytit obslužnými rutinami související události. Použití `Shared` modifikátor vytvořit sdílené událost, pokud je potřeba vyvolat událost v konstruktoru.  
  
> [!NOTE]
>  Výchozí chování událostí můžete změnit tak, že definujete vlastní událost. Pro vlastní události `RaiseEvent` příkaz volá události `RaiseEvent` přistupujícího objektu. Další informace o vlastních událostech najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá události k počet sekund od 10 do 0. Kód ukazuje několik událostí související metody, vlastnosti a příkazy, včetně `RaiseEvent` příkazu.  
  
 Třída, která vyvolá událost, je zdroj události a metody, které zpracovávají události jsou obslužné rutiny událostí. Zdroj událostí může mít více obslužných rutin událostí, který generuje. Pokud třída vyvolá událost, této události je vyvoláno na každé třídy, která je se rozhodli zpracovávat události pro tuto instanci objektu.  
  
 V příkladu se také používá formuláře (`Form1`) s tlačítkem (`Button1`) a textové pole (`TextBox1`). Když kliknete na tlačítko, prvního textového pole zobrazuje odpočítávání z 10 na 0 sekund. Po uplynutí doby úplné (10 sekund), se zobrazí "Hotovo" prvního textového pole.  
  
 Kód pro `Form1` Určuje počáteční a terminálu stavy formuláře. Také obsahuje kód, spustí se, když jsou vyvolány události.  
  
 Pokud chcete použít tento příklad, otevřete nový projekt aplikace Windows, přidejte tlačítko s názvem `Button1` a textové pole s názvem `TextBox1` hlavní formulář s názvem `Form1`. Klikněte pravým tlačítkem myši na formuláři a klikněte na tlačítko **zobrazit kód** otevřete Editor kódu.  
  
 Přidat `WithEvents` do části deklarace proměnných `Form1` třídy.  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující kód přidejte kód pro `Form1`. Nahraďte všechny duplicitní postupy, které mohou existovat, jako například `Form_Load`, nebo `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 Stisknutím klávesy F5 spusťte v předchozím příkladu a klikněte na tlačítko s popiskem **Start**. Prvního textového pole spustí odpočet sekundy. Po uplynutí doby úplné (10 sekund), se zobrazí "Hotovo" prvního textového pole.  
  
> [!NOTE]
>  `My.Application.DoEvents` Metoda nezpracovává události stejným způsobem, stejně jako formulář. Povolit formulář pro zpracování událostí přímo, můžete použít multithreadingu. Další informace najdete v tématu [zřetězení](../../programming-guide/concepts/threading/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)
