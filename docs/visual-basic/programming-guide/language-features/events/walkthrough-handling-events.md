---
title: Zpracování událostí
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: cb42f2e41e366cf8765cb9395d1a5641434bab40
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345072"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Návod: Zpracování událostí (Visual Basic)
Jedná se o druhý ze dvou témat, která ukazují, jak pracovat s událostmi. První téma, [Návod: deklarace a vyvolávání událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), ukazuje, jak deklarovat a vyvolat události. V této části se používá formulář a třída z tohoto návodu k zobrazení, jak zpracovávat události, když dojde k jejich provedení.  
  
 Příklad `Widget` třídy používá tradiční příkazy pro zpracování událostí. Visual Basic poskytuje další techniky pro práci s událostmi. Jako cvičení můžete tento příklad upravit tak, aby používal příkazy `AddHandler` a `Handles`.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Zpracování události PercentDone třídy widgetu  
  
1. Do `Form1`vložte následující kód:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     Klíčové slovo `WithEvents` určuje, že se proměnná `mWidget` používá ke zpracování událostí objektu. Typ objektu určíte zadáním názvu třídy, ze které bude objekt vytvořen.  
  
     Proměnná `mWidget` je deklarována v `Form1`, protože `WithEvents` proměnné musí být na úrovni třídy. To platí bez ohledu na typ třídy, ve které je umístíte.  
  
     Proměnná `mblnCancel` slouží ke zrušení metody `LongTask`.  
  
## <a name="writing-code-to-handle-an-event"></a>Psaní kódu pro zpracování události  
 Jakmile deklarujete proměnnou pomocí `WithEvents`, název proměnné se zobrazí v levém rozevíracím seznamu **editoru kódu**třídy. Když vyberete možnost `mWidget`, v pravém rozevíracím seznamu se zobrazí události `Widget` třídy. Výběrem události se zobrazí odpovídající procedura události s předponou `mWidget` a podtržítkem. Všem procedurám události přidruženým k `WithEvents` proměnné se předává název proměnné jako předpona.  
  
#### <a name="to-handle-an-event"></a>Postup zpracování události  
  
1. V **editoru kódu**vyberte `mWidget` v levém rozevíracím seznamu.  
  
2. V rozevíracím seznamu vyberte událost `PercentDone`. **Editor kódu** otevře proceduru události `mWidget_PercentDone`.  
  
    > [!NOTE]
    > **Editor kódu** je užitečný, ale není povinný pro vkládání nových obslužných rutin událostí. V tomto návodu je jednodušší pouze kopírovat obslužné rutiny událostí přímo do kódu.  
  
3. Do obslužné rutiny události `mWidget_PercentDone` přidejte následující kód:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Při každém vyvolání události `PercentDone` zobrazí procedura události procentuální hodnotu dokončení v ovládacím prvku `Label`. Metoda `DoEvents` umožňuje popisku překreslit a také uživateli dává možnost kliknout na tlačítko **Storno** .  
  
4. Přidejte následující kód pro obslužnou rutinu události `Button2_Click`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Pokud uživatel klikne na tlačítko **Storno** , když je spuštěný `LongTask`, událost `Button2_Click` se spustí, jakmile příkaz `DoEvents` umožní, aby se vykonalo zpracování událostí. Proměnná na úrovni třídy `mblnCancel` je nastavená na `True`a událost `mWidget_PercentDone` potom testuje a nastaví argument `ByRef Cancel` na `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Připojení proměnné WithEvents k objektu  
 `Form1` je teď nastavená tak, aby zpracovávala události `Widget` objektu. Vše, co zbývá, je najít `Widget` někam.  
  
 Pokud deklarujete proměnnou `WithEvents` v době návrhu, k ní není přidružen žádný objekt. `WithEvents` proměnná je stejně jako jakákoli jiná proměnná objektu. Musíte vytvořit objekt a přiřadit k němu odkaz s proměnnou `WithEvents`.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Vytvoření objektu a přiřazení odkazu na něj  
  
1. Z levého rozevíracího seznamu v **editoru kódu**vyberte **(události Form1)** .  
  
2. V rozevíracím seznamu vyberte událost `Load`. **Editor kódu** otevře proceduru události `Form1_Load`.  
  
3. Přidejte následující kód pro proceduru `Form1_Load` události a vytvořte `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Když se spustí tento kód, Visual Basic vytvoří objekt `Widget` a připojí své události k procedurám událostí přidruženým k `mWidget`. Od tohoto okamžiku, kdykoli `Widget` vyvolá událost `PercentDone`, je provedena procedura události `mWidget_PercentDone`.  
  
#### <a name="to-call-the-longtask-method"></a>Volání metody LongTask  
  
- Do obslužné rutiny události `Button1_Click` přidejte následující kód:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Před voláním metody `LongTask` musí být inicializován popisek, který zobrazuje procento dokončení, a příznak `Boolean` na úrovni třídy pro zrušení metody musí být nastaven na `False`.  
  
 `LongTask` se volá s dobou trvání úlohy 12,2 sekund. Událost `PercentDone` je vyvolána jednou třetinou sekundy. Pokaždé, když je událost vyvolána, je provedena procedura události `mWidget_PercentDone`.  
  
 Po dokončení `LongTask` `mblnCancel` testována, zda `LongTask` skončila normálně nebo pokud byla zastavena, protože `mblnCancel` byla nastavena na `True`. Procentuální hodnota dokončení je aktualizována pouze v bývalém případě.  
  
#### <a name="to-run-the-program"></a>Spuštění programu  
  
1. Stisknutím klávesy F5 vložte projekt do režimu spuštění.  
  
2. Klikněte na tlačítko **Spustit úlohu** . Pokaždé, když se aktivuje událost `PercentDone`, se popisek aktualizuje o procento dokončeného úkolu.  
  
3. Kliknutím na tlačítko **Storno** úlohu zastavte. Všimněte si, že se vzhled tlačítka **Zrušit** nemění hned po kliknutí na něj. Událost `Click` nemůže nastat, dokud příkaz `My.Application.DoEvents` nepovolí zpracování události.  
  
    > [!NOTE]
    > Metoda `My.Application.DoEvents` nezpracovává události přesně stejným způsobem jako formulář. Například v tomto návodu musíte dvakrát kliknout na tlačítko **Zrušit** . Chcete-li, aby formulář mohl zpracovávat události přímo, můžete použít multithreading. Další informace najdete v tématu [spravovaná vlákna](../../../../standard/threading/index.md).
  
 Může se stát, že vám dá pokyn spustit program pomocí klávesy F11 a krokovat kód po řádku. Můžete jasně zjistit, jak se spuštění zadává `LongTask`a pak krátce znovu zadá `Form1` pokaždé, když se vyvolá událost `PercentDone`.  
  
 K čemu dojde v případě, že při provádění bylo vráceno v kódu `Form1`byla metoda `LongTask` volána znovu? V nejhorším případě může dojít k přetečení zásobníku, pokud `LongTask` bylo voláno při každém vyvolání události.  
  
 Můžete způsobit, že proměnná `mWidget` zpracovávat události pro jiný objekt `Widget` přiřazením odkazu na nový `Widget` k `mWidget`. Ve skutečnosti můžete vytvořit kód v `Button1_Click` to udělat pokaždé, když kliknete na tlačítko.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Zpracování událostí pro různé pomůcky  
  
- Do `Button1_Click` postupu přidejte následující řádek kódu, který bezprostředně před řádek, který čte `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Výše uvedený kód vytvoří novou `Widget` pokaždé, když se klikne na tlačítko. Jakmile se `LongTask` metoda dokončí, odkaz na `Widget` se uvolní a `Widget` se zničí.  
  
 `WithEvents` proměnná může současně obsahovat pouze jeden odkaz na objekt, takže pokud přiřadíte jiným objektům `Widget` `mWidget`, již nebudou zpracovány předchozí události `Widget` objektu. Pokud je `mWidget` jedinou proměnnou objektu obsahující odkaz na starou `Widget`, je objekt zničen. Chcete-li zpracovávat události z několika objektů `Widget`, použijte příkaz `AddHandler` pro zpracování událostí z každého objektu samostatně.  
  
> [!NOTE]
> Můžete deklarovat tolik `WithEvents` proměnných, kolik potřebujete, ale pole `WithEvents` proměnných nejsou podporována.  
  
## <a name="see-also"></a>Viz také:

- [Návod: Deklarace a vyvolávání událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
