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
ms.openlocfilehash: 29d878afbe3669fc88e62b1fec98b306918c303d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405077"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Návod: Zpracování událostí (Visual Basic)
Jedná se o druhý ze dvou témat, která ukazují, jak pracovat s událostmi. První téma, [Návod: deklarace a vyvolávání událostí](walkthrough-declaring-and-raising-events.md), ukazuje, jak deklarovat a vyvolat události. V této části se používá formulář a třída z tohoto návodu k zobrazení, jak zpracovávat události, když dojde k jejich provedení.  
  
 `Widget`Příklad třídy používá tradiční příkazy pro zpracování událostí. Visual Basic poskytuje další techniky pro práci s událostmi. Jako cvičení můžete tento příklad upravit tak, aby používal `AddHandler` `Handles` příkazy a.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Zpracování události PercentDone třídy widgetu  
  
1. Vložte následující kód do `Form1` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents`Klíčové slovo určuje, že proměnná `mWidget` slouží ke zpracování událostí objektu. Typ objektu určíte zadáním názvu třídy, ze které bude objekt vytvořen.  
  
     Proměnná `mWidget` je deklarována v, `Form1` protože `WithEvents` proměnné musí být na úrovni třídy. To platí bez ohledu na typ třídy, ve které je umístíte.  
  
     Proměnná `mblnCancel` slouží ke zrušení `LongTask` metody.  
  
## <a name="writing-code-to-handle-an-event"></a>Psaní kódu pro zpracování události  
 Jakmile deklarujete proměnnou pomocí `WithEvents` , bude název proměnné zobrazen v levém rozevíracím seznamu **editoru kódu**třídy. Když vyberete `mWidget` , zobrazí se `Widget` události třídy v pravém rozevíracím seznamu. Výběrem události se zobrazí odpovídající procedura události s předponou `mWidget` a podtržítkem. Všem procedurám události přidruženým k `WithEvents` proměnné je dán název proměnné jako předpona.  
  
#### <a name="to-handle-an-event"></a>Postup zpracování události  
  
1. `mWidget`V **editoru kódu**vyberte v rozevíracím seznamu vlevo.  
  
2. `PercentDone`V rozevíracím seznamu vyberte událost. **Editor kódu** otevře `mWidget_PercentDone` proceduru události.  
  
    > [!NOTE]
    > **Editor kódu** je užitečný, ale není povinný pro vkládání nových obslužných rutin událostí. V tomto návodu je jednodušší pouze kopírovat obslužné rutiny událostí přímo do kódu.  
  
3. Do `mWidget_PercentDone` obslužné rutiny události přidejte následující kód:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Při každém `PercentDone` vyvolání události zobrazuje procedura události v ovládacím prvku procentuální hodnotu dokončení `Label` . `DoEvents`Metoda umožňuje popisku překreslit a také uživateli nabízí možnost kliknout na tlačítko **Storno** .  
  
4. Přidejte následující kód pro `Button2_Click` obslužnou rutinu události:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Pokud uživatel klikne na tlačítko **Storno** `LongTask` , když je spuštěn, `Button2_Click` událost se spustí, jakmile `DoEvents` příkaz umožní, aby bylo provedeno zpracování události. Proměnná na úrovni třídy `mblnCancel` je nastavena na hodnotu `True` a `mWidget_PercentDone` událost pak otestuje a nastaví `ByRef Cancel` argument na `True` .  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Připojení proměnné WithEvents k objektu  
 `Form1`je nyní nastaveno na zpracování `Widget` událostí objektu. Vše, co zbývá, je najít `Widget` někde.  
  
 Pokud deklarujete proměnnou `WithEvents` v době návrhu, k ní není přidružen žádný objekt. `WithEvents`Proměnná je stejně jako jakákoli jiná proměnná objektu. Musíte vytvořit objekt a přiřadit k němu odkaz s `WithEvents` proměnnou.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Vytvoření objektu a přiřazení odkazu na něj  
  
1. Z levého rozevíracího seznamu v **editoru kódu**vyberte **(události Form1)** .  
  
2. `Load`V rozevíracím seznamu vyberte událost. **Editor kódu** otevře `Form1_Load` proceduru události.  
  
3. Přidejte následující kód pro `Form1_Load` proceduru události pro vytvoření `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Když se spustí tento kód, Visual Basic vytvoří `Widget` objekt a připojí své události k procedurám události přidruženým k `mWidget` . Od tohoto okamžiku, kdykoli `Widget` vyvolá `PercentDone` událost, `mWidget_PercentDone` je provedena procedura události.  
  
#### <a name="to-call-the-longtask-method"></a>Volání metody LongTask  
  
- Do `Button1_Click` obslužné rutiny události přidejte následující kód:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Před `LongTask` voláním metody musí být inicializován popisek, který zobrazuje procento dokončení, a příznak na úrovni třídy `Boolean` pro zrušení metody musí být nastaven na `False` .  
  
 `LongTask`je volána s dobou trvání úlohy 12,2 sekund. `PercentDone`Událost se vyvolá jednou za každou třetinu sekundy. Při každém vyvolání události se `mWidget_PercentDone` spustí procedura události.  
  
 V případě, že je `LongTask` provedena, `mblnCancel` je Testováno pro zjištění, zda `LongTask` skončila normálně nebo pokud bylo zastaveno, protože `mblnCancel` bylo nastaveno na `True` . Procentuální hodnota dokončení je aktualizována pouze v bývalém případě.  
  
#### <a name="to-run-the-program"></a>Spuštění programu  
  
1. Stisknutím klávesy F5 vložte projekt do režimu spuštění.  
  
2. Klikněte na tlačítko **Spustit úlohu** . Pokaždé `PercentDone` , když se událost vyvolá, popisek se aktualizuje o procento dokončené úlohy.  
  
3. Kliknutím na tlačítko **Storno** úlohu zastavte. Všimněte si, že se vzhled tlačítka **Zrušit** nemění hned po kliknutí na něj. `Click`Událost nemůže nastat, dokud `My.Application.DoEvents` příkaz nepovolí zpracování událostí.  
  
    > [!NOTE]
    > `My.Application.DoEvents`Metoda nezpracovává události přesně stejným způsobem jako formulář. Například v tomto návodu musíte dvakrát kliknout na tlačítko **Zrušit** . Chcete-li, aby formulář mohl zpracovávat události přímo, můžete použít multithreading. Další informace najdete v tématu [spravovaná vlákna](../../../../standard/threading/index.md).
  
 Může se stát, že vám dá pokyn spustit program pomocí klávesy F11 a krokovat kód po řádku. Můžete zřetelně vidět, jak se spuštění spouští `LongTask` , a pak krátce znovu zadat `Form1` pokaždé, když `PercentDone` se událost vyvolá.  
  
 Co se stane, když při provádění bylo vráceno v kódu `Form1` , `LongTask` metoda byla volána znovu? V nejhorším případě může dojít k přetečení zásobníku, pokud `LongTask` bylo voláno při každém vyvolání události.  
  
 Můžete způsobit, že proměnná `mWidget` zpracovává události pro jiný `Widget` objekt přiřazením odkazu k novému `Widget` `mWidget` . V takovém případě můžete vytvořit kód `Button1_Click` pokaždé, když kliknete na tlačítko.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Zpracování událostí pro různé pomůcky  
  
- Do procedury přidejte následující řádek kódu `Button1_Click` , bezprostředně před řádek, který čte `mWidget.LongTask(12.2, 0.33)` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Výše uvedený kód vytvoří nové `Widget` pokaždé, když se klikne na tlačítko. Jakmile se `LongTask` Metoda dokončí, odkaz na se `Widget` uvolní a dojde k jejímu `Widget` zničení.  
  
 `WithEvents`Proměnná může současně obsahovat pouze jeden odkaz na objekt, takže pokud přiřadíte jiný `Widget` objekt k `mWidget` , `Widget` události předchozího objektu již nebudou zpracovány. Pokud `mWidget` je jedinou proměnnou objektu obsahující odkaz na starou `Widget` , je objekt zničen. Pokud chcete zpracovávat události z několika `Widget` objektů, použijte `AddHandler` příkaz pro zpracování událostí z každého objektu samostatně.  
  
> [!NOTE]
> Můžete deklarovat tolik `WithEvents` proměnných, kolik potřebujete, ale pole `WithEvents` proměnných nejsou podporována.  
  
## <a name="see-also"></a>Viz také

- [Návod: Deklarace a vyvolávání událostí](walkthrough-declaring-and-raising-events.md)
- [Události](index.md)
