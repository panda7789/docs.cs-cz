---
title: Zpracování událostí (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: aa3c1f00922cda46d3ce5a788b606a6f5da52636
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64604044"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Návod: Zpracování událostí (Visual Basic)
Toto je druhá dvou tématech, které ukazují, jak pracovat s událostmi. První téma [názorný postup: Deklarující a vyvolání události](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), ukazuje, jak deklarace a vyvolávání událostí. Tato část používá formulář opravdu zavřít a třídy v tomto návodu k ukazují, jak zpracovávat události, když se provedou.  
  
 `Widget` Třídy příkladu tradiční příkazy pro zpracování událostí. Visual Basic obsahuje jiné techniky pro práci s událostmi. Jako cvičení, můžete upravit tento příkladu pro použití `AddHandler` a `Handles` příkazy.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Zpracování události PercentDone třídy widgetu  
  
1. Umístěte následující kód v `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents` – Klíčové slovo určuje, že proměnné `mWidget` se používá ke zpracování událostí objektu. Zadejte typ objektu zadáním názvu třídy, ze kterého se vytvoří objekt.  
  
     Proměnná `mWidget` je deklarován v `Form1` protože `WithEvents` proměnné musí být na úrovni třídy. To platí bez ohledu na typ třídy, které je v umístit.  
  
     Proměnná `mblnCancel` se používá pro zrušení `LongTask` metody.  
  
## <a name="writing-code-to-handle-an-event"></a>Psaní kódu pro zpracování událostí  
 Poté, co můžete deklarovat proměnné pomocí `WithEvents`, název proměnné se zobrazí v levém rozevírací seznam třídy **Editor kódu**. Když vyberete `mWidget`, `Widget` třídy události se zobrazí v pravém rozevíracího seznamu. Výběr události zobrazí odpovídající postup událostí s předponou `mWidget` a podtržítka. Všechny přidružené procedury `WithEvents` proměnné jsou předána název proměnné jako předponu.  
  
#### <a name="to-handle-an-event"></a>Zpracování události  
  
1. Vyberte `mWidget` z levé rozevíracího seznamu v **Editor kódu**.  
  
2. Vyberte `PercentDone` událost z přímo rozevíracího seznamu. **Editor kódu** otevře `mWidget_PercentDone` proceduru události.  
  
    > [!NOTE]
    >  **Editor kódu** je užitečné, ale nejsou vyžadovány, pro vkládání nové obslužné rutiny událostí. V tomto návodu je přímější stačí jen zkopírovat přímo do kódu obslužné rutiny událostí.  
  
3. Přidejte následující kód, který `mWidget_PercentDone` obslužné rutiny události:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Pokaždé, když `PercentDone` událost se vyvolá, zobrazí se postup události dokončení v procentech `Label` ovládacího prvku. `DoEvents` Metoda umožňuje tento popisek repaint a klikněte na možnost také umožňuje uživateli **zrušit** tlačítko.  
  
4. Přidejte následující kód `Button2_Click` obslužné rutiny události:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Pokud uživatel klikne **zrušit** tlačítka při `LongTask` běží, `Button2_Click` provedla událost poté, co `DoEvents` příkaz umožňuje zpracování událostí na výskyt. Proměnnou na úrovni `mblnCancel` je nastavena na `True`a `mWidget_PercentDone` události poté jej ověří a nastaví `ByRef Cancel` argument `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Připojování k objektu proměnnou WithEvents  
 `Form1` je nyní nastaveno pro zpracování `Widget` objektu události. Už jen zbývá k vyhledání `Widget` jinde.  
  
 Pokud deklarujete proměnnou `WithEvents` v době návrhu, je k ní přidružen žádný objekt. A `WithEvents` proměnnou je stejně jako jakoukoli jinou proměnnou objektu. Je nutné vytvořit objekt a přiřaďte přes odkaz `WithEvents` proměnné.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>K vytvoření objektu a přiřazení na ni odkaz  
  
1. Vyberte **(Form1 události)** z levé rozevíracího seznamu v **Editor kódu**.  
  
2. Vyberte `Load` událost z přímo rozevíracího seznamu. **Editor kódu** otevře `Form1_Load` proceduru události.  
  
3. Přidejte následující kód `Form1_Load` události postupu vytvořte `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Když tento kód spustí, Visual Basic vytvoří `Widget` objektu a jeho události se připojí k přidružené procedury `mWidget`. Od této chvíle, vždy, když `Widget` vyvolá jeho `PercentDone` událostí, `mWidget_PercentDone` procedury události.  
  
#### <a name="to-call-the-longtask-method"></a>Volání metody LongTask  
  
- Přidejte následující kód, který `Button1_Click` obslužné rutiny události:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Před `LongTask` metoda je volána, označení, že zobrazuje procento dokončení musí být inicializován a úrovni třídy `Boolean` příznak pro zrušení metoda musí být nastaveno na `False`.  
  
 `LongTask` je volána s určitou dobou trvání úkolu 12.2 sekund. `PercentDone` Událost je aktivována jednou každých 1 / 3 sekundy. Pokaždé, když se vyvolá událost, `mWidget_PercentDone` procedury události.  
  
 Když `LongTask` se provádí, `mblnCancel` je testován a zjistěte, jestli `LongTask` skončil normálně, nebo pokud je zastavena, protože `mblnCancel` byl nastaven na `True`. Procento dokončení se aktualizuje jenom v prvním případě.  
  
#### <a name="to-run-the-program"></a>Chcete-li spustit program  
  
1. Stisknutím klávesy F5 projekt uvést do režimu běhu.  
  
2. Klikněte na tlačítko **spustit úlohu** tlačítko. Pokaždé, když `PercentDone` událost se vyvolá, popisek se aktualizuje s procento dokončení úkolu.  
  
3. Klikněte na tlačítko **zrušit** tlačítko Zastavit úlohy. Všimněte si, že vzhled **zrušit** ihned po kliknutí nezmění tlačítko. `Click` Událostí nemůže dojít až `My.Application.DoEvents` příkaz umožňuje zpracování událostí.  
  
    > [!NOTE]
    >  `My.Application.DoEvents` Metoda nezpracovává události stejným způsobem, stejně jako formulář. Například v tomto podrobném návodu, musíte kliknout na **zrušit** dvakrát na tlačítko. Povolit formulář pro zpracování událostí přímo, můžete použít multithreadingu. Další informace najdete v tématu [dělení na spravovaná vlákna](../../../../standard/threading/index.md).
  
 Může být pro vás poučné spusťte program s F11 a krokovat kód řádku najednou. Jasně vidíte, jak provádění zadá `LongTask`a potom stručně znovu zadá `Form1` pokaždé, když `PercentDone` událost se vyvolá.  
  
 Co by se stalo if, při spuštění zpět do kódu `Form1`, `LongTask` byla znovu volána metoda? V nejhorším případě může dojít k přetečení zásobníku, pokud `LongTask` byly volány pokaždé, když byla vyvolána událost.  
  
 Proměnná může způsobit `mWidget` zpracování událostí pro jiný `Widget` objektu tak, že přiřadíte odkaz na nové `Widget` k `mWidget`. Ve skutečnosti můžete vytvořit kód v `Button1_Click` to pokaždé, když kliknete na tlačítko.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Zpracování událostí pro různé pomůcky  
  
- Přidejte následující řádek kódu, který `Button1_Click` postupu bezprostředně předchází řádku, který čte `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Výše uvedený kód vytvoří novou `Widget` pokaždé, když dojde ke kliknutí na tlačítko. Poté, co `LongTask` metoda dokončí, odkaz na `Widget` vydání a `Widget` zničen.  
  
 A `WithEvents` proměnná může obsahovat pouze jeden objekt odkazu v době, takže pokud přiřaďte jiný `Widget` objektu `mWidget`, předchozí `Widget` události objektu už se zpracuje. Pokud `mWidget` je pouze objekt proměnnou obsahující odkaz na původní `Widget`, objekt je zničen. Pokud chcete zpracovávat události z několika `Widget` objekty, použijte `AddHandler` příkaz pro zpracování událostí z každý objekt odděleně.  
  
> [!NOTE]
>  Lze deklarovat libovolný počet `WithEvents` proměnné, jako je třeba, ale pole `WithEvents` proměnné nejsou podporovány.  
  
## <a name="see-also"></a>Viz také:

- [Návod: Deklarace a vyvolávání událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
