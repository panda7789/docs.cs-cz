---
title: "RaiseEvent – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6ba5ce4b009e0d8c675db07b56b9811c595ae2f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="raiseevent-statement"></a>RaiseEvent – příkaz
Aktivuje událost deklarovat na úrovni modulu v rámci třídy, formulář nebo dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Součásti  
 `eventname`  
 Požadováno. Název události k aktivaci.  
  
 `argumentlist`  
 Volitelné. Čárkami oddělený seznam proměnných, pole nebo výrazy. `argumentlist` Argument musí být uzavřena v závorkách. Pokud neexistují žádné argumenty, musí být vynechána závorkách.  
  
## <a name="remarks"></a>Poznámky  
 Požadované `eventname` je název události deklarované v rámci modulu. Postupuje proměnné zásady vytváření názvů jazyka Visual Basic.  
  
 Pokud událost nebyla deklarována v rámci modul, ve kterém se vyvolá, dojde k chybě. Následující fragment kódu ukazuje deklaraci události a postup, ve které je událost vyvolána.  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 Nemůžete použít `RaiseEvent` umožňuje aktivovat události, které nejsou výslovně deklarované v modulu. Například zdědí všechny formuláře <xref:System.Windows.Forms.Control.Click> událost z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, nelze zvýšit, pomocí `RaiseEvent` v odvozených formuláře. Pokud je deklarovat `Click` událostí v modulu formuláře ho shadows formuláře vlastní <xref:System.Windows.Forms.Control.Click> událostí. Přesto můžete vyvolat formuláře <xref:System.Windows.Forms.Control.Click> událostí voláním <xref:System.Windows.Forms.Control.OnClick%2A> metoda.  
  
 Ve výchozím nastavení vyvolá událost definované v jazyce Visual Basic jeho obslužné rutiny událostí v pořadí, že jsou navázat připojení. Protože události může mít `ByRef` parametry, proces, který se připojuje pozdní obdržet parametry, které se změnily starší obslužné rutiny události. Po spuštění obslužné rutiny události, ovládací prvek se vrátí k podprogramu, který vyvolal událost.  
  
> [!NOTE]
>  Pro nesdílené události by neměly být vyvolány v konstruktoru třídy, ve které jsou deklarované. I když tyto události nezpůsobí běhové chyby, se nemusí být zachytila obslužné rutiny související události. Použití `Shared` modifikátor vytvoření sdíleného události, pokud je nutné vyvolat událost z konstruktoru.  
  
> [!NOTE]
>  Výchozí chování události můžete změnit tak, že definujete vlastní události. Pro vlastní události `RaiseEvent` příkaz volá události `RaiseEvent` přistupujícího objektu. Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá události počítat dolů sekund z 10 na hodnotu 0. Kód ukazuje několik událostí související metody, vlastnosti a příkazy, včetně `RaiseEvent` příkaz.  
  
 Třída, která vyvolá událost, je zdroj události a jsou metody, které zpracovat událost obslužné rutiny událostí. Zdroje událostí může mít více obslužných rutin pro události, které generuje. Pokud třída vyvolá událost, že událost se vyvolá při každou třídu, která se rozhodl zpracovat události pro tuto instanci objektu.  
  
 V příkladu se rovněž používá formulář (`Form1`) s tlačítkem na (`Button1`) a textového pole (`TextBox1`). Když kliknete na tlačítko, textové pole první zobrazí odpočítávání z 10 na 0 sekund. Po uplynutí doby úplné (10 sekund), zobrazí první textové pole, "Hotovo".  
  
 Kód pro `Form1` Určuje počáteční a terminálu stavy formuláře. Obsahuje taky kód spustit, když jsou vyvolány události.  
  
 Chcete-li použít tento příklad, otevřete nový projekt aplikace Windows, přidat tlačítko s názvem `Button1` a textové pole s názvem `TextBox1` hlavní formulář s názvem `Form1`. Klikněte pravým tlačítkem formuláři a klikněte na tlačítko **kód zobrazení** otevření editoru kódu.  
  
 Přidat `WithEvents` do části deklarace proměnné `Form1` třídy.  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 Přidejte následující kód pro kód pro `Form1`. Nahraďte všechny duplicitní postupy, které mohou existovat, jako například `Form_Load`, nebo `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 Stisknutím klávesy F5 spusťte v předchozím příkladu a klikněte na tlačítko s názvem bez přípony **spustit**. První textové pole začne počítat dolů sekundách. Po uplynutí doby úplné (10 sekund), zobrazí první textové pole, "Hotovo".  
  
> [!NOTE]
>  `My.Application.DoEvents` Metoda nezpracovává události stejným způsobem, jak to dělá formuláře. Chcete-li povolit formuláře pro zpracování událostí přímo, můžete použít více vláken. Další informace najdete v tématu [zřetězení](../../programming-guide/concepts/threading/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)
