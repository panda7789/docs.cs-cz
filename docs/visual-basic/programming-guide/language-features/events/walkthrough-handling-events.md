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
ms.openlocfilehash: 0ac3514505ca42870d77317feec30a27e4384e6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655111"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Návod: Zpracování událostí (Visual Basic)
Toto je druhý dvě témata, která ukazují, jak pracovat s událostmi. První téma [návod: deklarující a aktivaci událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), ukazuje, jak deklarace a vyvolávání událostí. Tato část používá formulář a třídy z tohoto návodu jak ke zpracování událostí při jejich provádění.  
  
 `Widget` Třída příklad používá tradiční příkazy zpracování událostí. Visual Basic poskytuje další metody pro práci s událostmi. Jako cvičení, můžete upravit tento příklad pro použití `AddHandler` a `Handles` příkazy.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Zpracování události PercentDone třídy pomůcky  
  
1.  Vložte následující kód v `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     `WithEvents` – Klíčové slovo určuje, že proměnná `mWidget` slouží ke zpracování události objektu. Určují druh objektu zadáním názvu třídy, ze kterého bude vytvořen objekt.  
  
     Proměnná `mWidget` deklarovaného v souboru `Form1` protože `WithEvents` proměnných musí být na úrovni třídy. To platí bez ohledu na typ třídy, které je v umístění.  
  
     Proměnná `mblnCancel` je sloužící ke zrušení `LongTask` metoda.  
  
## <a name="writing-code-to-handle-an-event"></a>Psaní kódu pro zpracování událostí  
 Jakmile deklarovat proměnnou pomocí `WithEvents`, název proměnné se zobrazí v levém rozevíracím seznamu třídy **Editor kódu**. Když vyberete `mWidget`, `Widget` třídy události se zobrazí v pravém rozevíracího seznamu. Výběr událost zobrazí odpovídající postup událostí s předponou `mWidget` a podtržítka. Všechny postupy události související s `WithEvents` proměnná zadána název proměnné jako předponu.  
  
#### <a name="to-handle-an-event"></a>Zpracovat události  
  
1.  Vyberte `mWidget` v levém rozevíracím seznamu v **Editor kódu**.  
  
2.  Vyberte `PercentDone` událost z pravé rozevíracího seznamu. **Editor kódu** otevře `mWidget_PercentDone` procedury události.  
  
    > [!NOTE]
    >  **Editor kódu** je užitečné, ale není požadováno pro vkládání nové obslužné rutiny událostí. V tomto návodu je více přímo do obslužné rutiny událostí jednoduše zkopírujete přímo do kódu.  
  
3.  Přidejte následující kód, který `mWidget_PercentDone` obslužné rutiny události:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     Vždy, když `PercentDone` událost se vyvolá, postup událostí zobrazuje procento dokončení v `Label` ovládacího prvku. `DoEvents` Metoda umožňuje štítek, který chcete překreslit a klikněte na možnost také umožňuje uživateli **zrušit** tlačítko.  
  
4.  Přidejte následující kód pro `Button2_Click` obslužné rutiny události:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 Pokud uživatel klikne **zrušit** tlačítko při `LongTask` běží, `Button2_Click` událost se spustí co nejrychleji `DoEvents` příkaz umožňuje zpracování událostí proběhnout. Proměnná úrovni třídy `mblnCancel` je nastaven na `True`a `mWidget_PercentDone` událostí pak ho testuje a nastaví `ByRef Cancel` argument `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Připojení proměnnou WithEvents k objektu  
 `Form1` je teď nastavená pro zpracování `Widget` události objektu. Zbývá k vyhledání `Widget` místo.  
  
 Když je deklarovat proměnnou `WithEvents` žádný objekt v době návrhu, je k ní přidružena. A `WithEvents` proměnná je stejně jako jakoukoli jinou proměnnou objektu. Máte-li vytvořit objekt a přiřadit odkaz na její `WithEvents` proměnné.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>K vytvoření objektu a odkaz na jeho přiřazení  
  
1.  Vyberte **(Form1 událostí)** v levém rozevíracím seznamu v **Editor kódu**.  
  
2.  Vyberte `Load` událost z pravé rozevíracího seznamu. **Editor kódu** otevře `Form1_Load` procedury události.  
  
3.  Přidejte následující kód pro `Form1_Load` události postupu vytvořte `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 Když tento kód provede, vytvoří jazyka Visual Basic `Widget` objektu a události se připojí k události postupy související s `mWidget`. Od této chvíle, vždy, když `Widget` vyvolá jeho `PercentDone` událostí, `mWidget_PercentDone` procedury událostí.  
  
#### <a name="to-call-the-longtask-method"></a>K volání metody LongTask  
  
-   Přidejte následující kód, který `Button1_Click` obslužné rutiny události:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 Před `LongTask` metoda je volána, štítky, musí být inicializován zobrazí procento dokončení a úrovni třídy `Boolean` příznak pro zrušení metodu, musí být nastavené na `False`.  
  
 `LongTask` je volána s určitou dobou trvání úloh 12.2 sekund. `PercentDone` Událost se vyvolá po každé třetinu sekundy. Pokaždé, když událost se vyvolá, `mWidget_PercentDone` procedury událostí.  
  
 Když `LongTask` probíhá, `mblnCancel` je testován pro případ, `LongTask` skončila normálně, nebo pokud je zastavena, protože `mblnCancel` byla nastavena na `True`. Procento dokončení je aktualizovat jenom v prvním případě.  
  
#### <a name="to-run-the-program"></a>Ke spuštění programu  
  
1.  Stisknutím klávesy F5 projekt uvést do režimu spuštění.  
  
2.  Klikněte **spustit úlohu** tlačítko. Pokaždé, když `PercentDone` událost se vyvolá, aktualizuje popisek s procento dokončení úkolu.  
  
3.  Klikněte **zrušit** tlačítko Ukončit úlohu. Všimněte si, že vzhled **zrušit** tlačítko nezmění okamžitě po kliknutí. `Click` Událostí je skutečnost, dokud `My.Application.DoEvents` příkaz umožňuje zpracování událostí.  
  
    > [!NOTE]
    >  `My.Application.DoEvents` Metoda nezpracovává události stejným způsobem, jak to dělá formuláře. Například v tomto návodu, musíte kliknout na **zrušit** tlačítko dvakrát. Chcete-li povolit formuláře pro zpracování událostí přímo, můžete použít více vláken. Další informace najdete v tématu [zřetězení](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
 Možná bude významné lze spustit program s F11 a procházet kód řádku najednou. Jasně uvidíte, jak provádění zadá `LongTask`a pak stručně znovu zadá `Form1` pokaždé, když `PercentDone` událost se vyvolá.  
  
 Co by mohlo dojít v případě, při spuštění zpět v kódu `Form1`, `LongTask` byla volána metoda znovu? V nejhorším případě může dojít k přetečení zásobníku, pokud `LongTask` měla volat pokaždé, když byla vyvolána událost.  
  
 Proměnná může způsobit `mWidget` zpracovat události pro jiné `Widget` objekt přiřazením odkaz na nové `Widget` k `mWidget`. Ve skutečnosti můžete použít kód v `Button1_Click` tomu pokaždé, když kliknete na tlačítko.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Zpracování událostí pro různé pomůcky  
  
-   Přidejte následující řádek kódu `Button1_Click` postupu přímo předchází řádku, který čte `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 Výše uvedený kód vytvoří novou `Widget` pokaždé, když po kliknutí na tlačítko. Jakmile `LongTask` metoda dokončí, odkaz na `Widget` vydání a `Widget` zničena.  
  
 A `WithEvents` proměnná může obsahovat pouze jeden objekt odkaz najednou, chcete-li přiřadit jinou `Widget` do objektu `mWidget`, předchozí `Widget` už zpracování události objektu. Pokud `mWidget` je proměnnou pouze objekt obsahující odkaz na starý `Widget`, objekt zničena. Pokud chcete zpracovat události z několika `Widget` objekty, používají `AddHandler` příkaz zpracovat události z každý objekt odděleně.  
  
> [!NOTE]
>  Je možné deklarovat tolik `WithEvents` proměnné jako budete potřebovat, ale pole `WithEvents` proměnné nejsou podporovány.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Deklarace a vyvolávání událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
