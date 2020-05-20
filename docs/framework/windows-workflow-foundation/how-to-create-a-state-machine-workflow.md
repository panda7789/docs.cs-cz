---
title: 'Postupy: Vytvoření pracovního postupu stavového stroje'
description: Tento článek vytvoří pracovní postup, který používá předdefinované aktivity, jako je například aktivita StateMachine, a vlastní aktivity.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8a9342c07c15d65df0310c0cb35b4b2c6f2ba686
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419652"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Postupy: Vytvoření pracovního postupu stavového stroje
Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit. V tomto tématu se seznámíte s vytvořením pracovního postupu, který používá předdefinované aktivity, jako je <xref:System.Activities.Statements.StateMachine> aktivita, a vlastní aktivity z předchozího tématu [Postupy: vytvoření aktivity](how-to-create-an-activity.md) . Pracovní postup modeluje číslo odhadující hru.  
  
> [!NOTE]
> Každé téma v kurzu Začínáme závisí na předchozích tématech. Chcete-li dokončit toto téma, je nutné nejprve dokončit [Postupy: vytvoření aktivity](how-to-create-an-activity.md).  
  
> [!NOTE]
> Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu  
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** a vyberte **Přidat**, **Nová položka**.  
  
2. V uzlu **nainstalované**, **běžné položky** vyberte **pracovní postup**. V seznamu **pracovních postupů** vyberte **aktivita** .  
  
3. `StateMachineNumberGuessWorkflow`Do pole **název** zadejte a klikněte na **Přidat**.  
  
4. Přetáhněte aktivitu **StateMachine** z části **Stavový počítač** v **sadě nástrojů** a přetáhněte ji na popisek **sem přetáhněte aktivitu** na návrhové ploše pracovního postupu.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Postup vytvoření proměnných a argumentů pracovního postupu  
  
1. Dvojím kliknutím na **StateMachineNumberGuessWorkflow. XAML** v **Průzkumník řešení** zobrazíte pracovní postup v návrháři, pokud ještě není zobrazený.  
  
2. Kliknutím na **argumenty** v levé dolní části návrháře pracovních postupů zobrazíte podokno **argumenty** .  
  
3. Klikněte na **vytvořit argument**.  
  
4. `MaxNumber`Do pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v vyberte v** rozevíracím seznamu **typ argumentu** možnost **Int32** a potom stiskněte klávesu ENTER a argument uložte.  
  
5. Klikněte na **vytvořit argument**.  
  
6. `Turns`Do pole **název** , které se nachází pod nově přidaným `MaxNumber` argumentem, vyberte **out** v rozevíracím seznamu **směr** , v rozevíracím seznamu **typ argumentu** vyberte **Int32** a potom stiskněte klávesu ENTER.  
  
7. Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .  
  
8. Kliknutím na **proměnné** v levém dolním rohu návrháře pracovních postupů zobrazíte podokno **proměnné** .  
  
9. Klikněte na **vytvořit proměnnou**.  
  
    > [!TIP]
    > Pokud se nezobrazí žádné pole **vytvořit proměnnou** , klikněte na <xref:System.Activities.Statements.StateMachine> aktivitu na ploše návrháře pracovního postupu a vyberte ji.  
  
10. `Guess`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.  
  
11. Klikněte na **vytvořit proměnnou**.  
  
12. `Target`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.  
  
13. Kliknutím na **proměnné** v levém dolním rohu návrháře aktivit zavřete podokno **proměnné** .  
  
### <a name="to-add-the-workflow-activities"></a>Přidání aktivit pracovního postupu  
  
1. Klikněte na **State1** a vyberte ji. V **okně Vlastnosti**změňte **Zobrazovaný** název na `Initialize Target` .  
  
    > [!TIP]
    > Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .  
  
2. Dvakrát klikněte na nově přejmenovaný **cílový stav inicializace** v Návrháři pracovních postupů a rozbalte ho.  
  
3. Přetáhněte aktivitu **přiřazení** z oddílu **primitivních** prvků v **sadě nástrojů** a přetáhněte ji do části pro **zadání** daného stavu. Do `Target` pole **do** vložte a následující výraz zadejte do **výrazu zadejte výraz jazyka C#** nebo **Zadejte pole výrazu VB** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .  
  
4. Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.  
  
5. Přetáhněte aktivitu **stavu** z části **Stavový počítač** v **sadě nástrojů** do návrháře pracovních postupů a najeďte myší na **cílový stav inicializace** . Všimněte si, že kolem **cílového stavu inicializace** se zobrazí čtyři trojúhelníky, když je tento nový stav nad ním. Nový stav umístěte na trojúhelník, který je hned pod **cílovým** stavem inicializace. Tím se nový stav umístí do pracovního postupu a vytvoří se přechod z **cílového stavu Initialize** do nového stavu.  
  
6. Kliknutím na **State1** ho vyberte, změňte **Zobrazovaný** název na `Enter Guess` a pak dvakrát klikněte na stav v Návrháři pracovních postupů a rozbalte ho.  
  
7. Přetáhněte aktivitu **WriteLine** z oddílu **primitivních** prvků v **sadě nástrojů** a přetáhněte ji do části pro **zadání** daného stavu.  
  
8. Do pole vlastnost **text** v poli **WriteLine**zadejte následující výraz.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji do části **Exit** (stav).  
  
10. Do `Turns` pole **do** zadejte do a vložte `Turns + 1` **výraz jazyka C#** nebo zadejte pole **výrazu VB** .  
  
11. Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.  
  
12. Přetáhněte aktivitu **FinalState** z části **Stavový počítač** v **sadě nástrojů**, najeďte ji na stav **odhadu ENTER** a přetáhněte ji na trojúhelník, který se zobrazí napravo od stavu " **zadejte odhad** ", takže se vytvoří přechod mezi **ENTER odhad** a **FinalState**.  
  
13. Výchozí název přechodu je **T2**. Kliknutím na přechod v Návrháři pracovního postupu ho vyberte a nastavte jeho **Zobrazovaný** název na **správný odhad**. Potom klikněte na **FinalState**a vyberte ho a přetáhněte ho na pravé straně, aby se zobrazil prostor pro zobrazení úplného názvu přechodu bez překryvu obou stavů. To usnadňuje dokončení zbývajících kroků v tomto kurzu.  
  
14. Dvojitým kliknutím na nově přejmenovaný **odhad správného** přechodu v Návrháři pracovního postupu ho rozbalte.  
  
15. Přetáhněte aktivitu **ReadInt** z oddílu **NumberGuessWorkflowActivities** **panelu nástrojů** a přetáhněte ji do oddílu **triggeru** přechodu.  
  
16. V **okně Vlastnosti** aktivity **ReadInt** zadejte `"EnterGuess"` včetně uvozovek do pole hodnota vlastnosti **Bookmark** a do `Guess` pole hodnota vlastnosti **výsledku** zadejte.  
  
17. Do pole **odhad správné** hodnoty vlastnosti **podmínky** přechodu zadejte následující výraz.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.  
  
    > [!NOTE]
    > K přechodu dojde v případě, že událost triggeru je přijata a je- <xref:System.Activities.Statements.Transition.Condition%2A> li k dispozici, je vyhodnocena jako `True` . V případě tohoto přechodu se v případě, že uživatel `Guess` odpovídá náhodně generovanému objektu `Target` , řídí průchod **FinalState** a pracovní postup se dokončí.  
  
19. V závislosti na tom, zda je odhad správný, by měl pracovní postup přejít buď na **FinalState** , nebo zpět do stavu **zadejte odhad** pro jiný pokus. Oba přechody sdílejí stejnou aktivační událost, která čeká na přijetí odhadu uživatele prostřednictvím aktivity **ReadInt** . Označuje se jako sdílený přechod. Chcete-li vytvořit sdílený přechod, klikněte na kroužek, který indikuje začátek **odhadu správného** přechodu a přetáhněte ho do požadovaného stavu. V tomto případě je přechodem Automatický přechod, takže přetáhněte počáteční bod pro **správný** přechod a přetáhněte ho zpátky do dolní části stavu **zadejte odhad** . Po vytvoření přechodu ho vyberte v Návrháři pracovních postupů a nastavte jeho vlastnost **DisplayName** na hodnotu **nesprávného odhadu**.  
  
    > [!NOTE]
    > Sdílené přechody je také možné vytvořit v Návrháři přechodu kliknutím na **přidat přechod sdílené triggery** v dolní části návrháře přechodu a pak výběrem požadovaného cílového stavu z rozevíracího seznamu **dostupné stavy pro připojení** .  
  
    > [!NOTE]
    > Všimněte si, že pokud je <xref:System.Activities.Statements.Transition.Condition%2A> z přechodu vyhodnocen `false` (nebo všechny podmínky přechodu na sdílený Trigger vyhodnoceny na hodnotu `false` ), přechod nebude proveden a všechny aktivační události pro všechny přechody ze stavu budou přeplánovány. V tomto kurzu nemůžete k této situaci dojít kvůli způsobu konfigurace podmínek (máme konkrétní akce, ať už je odhad správný nebo nesprávný).  
  
20. Poklikejte na **odhad nesprávného** přechodu v Návrháři pracovních postupů a rozbalte ho. Všimněte si, že **Trigger** je již nastaven na stejnou aktivitu **ReadInt** , jakou používal správný přechod **odhad** .  
  
21. Do pole hodnota vlastnosti **podmínky** zadejte následující výraz.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Přetáhněte aktivitu **if** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do části **Akce** přechodu.  
  
23. Do pole hodnota vlastnosti **Podmínka** pro aktivitu **if** aktivity zadejte následující výraz.  
  
    ```text
    Guess < Target
    ```  
  
24. Přetáhněte dvě aktivity **WriteLine** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte je tak, aby jedna byla v oddílu **then** aktivity **if** a jedna je v části **Else** .  
  
25. Kliknutím na aktivitu **WriteLine** v části **pak** ji vyberete a do pole hodnota vlastnosti **text** zadejte následující výraz.  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. Kliknutím na aktivitu **WriteLine** v části **Else** ji vyberte a do pole hodnota vlastnosti **text** zadejte následující výraz.  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. Kliknutím na položku **StateMachine** v horní části návrháře pracovních postupů se vrátíte do zobrazení celkového stavového počítače v Návrháři pracovního postupu.  
  
     Následující příklad znázorňuje dokončený pracovní postup.  
  
     ![Obrázek zobrazující pracovní postup dokončeného stavového počítače.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a>Postup sestavení pracovního postupu  
  
1. Stisknutím kláves CTRL+SHIFT+B řešení sestavíte.  
  
     Pokyny ke spuštění pracovního postupu najdete v dalším tématu [Postup: spuštění pracovního postupu](how-to-run-a-workflow.md). Pokud jste již dokončili [Postup: spuštění kroku pracovního postupu](how-to-run-a-workflow.md) s jiným stylem pracovního postupu a chcete jej spustit pomocí pracovního postupu stavového stroje z tohoto kroku, přeskočte dopředu na [sestavení a spusťte aplikaci v](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) tématu [Postupy: spuštění pracovního postupu](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programování Windows Workflow Foundation](programming.md)
- [Návrh pracovních postupů](designing-workflows.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvoření aktivity](how-to-create-an-activity.md)
- [Postupy: Spuštění pracovního postupu](how-to-run-a-workflow.md)
