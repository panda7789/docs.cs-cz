---
title: 'Postupy: Vytvoření sekvenčního pracovního postupu'
description: Tento článek vytvoří pracovní postup, který používá předdefinované aktivity, jako je například aktivita sekvence a vlastní aktivity.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: f80ac471fdcc425504b11b5fb17effa888aa9590
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419691"
---
# <a name="how-to-create-a-sequential-workflow"></a>Postupy: Vytvoření sekvenčního pracovního postupu

Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit. V tomto tématu se seznámíte s vytvořením pracovního postupu, který používá předdefinované aktivity, jako je <xref:System.Activities.Statements.Sequence> aktivita, a vlastní aktivity z předchozího tématu [Postupy: vytvoření aktivity](how-to-create-an-activity.md) . Pracovní postup modeluje číslo odhadující hru.

> [!NOTE]
> Každé téma v kurzu Začínáme závisí na předchozích tématech. Chcete-li dokončit toto téma, je nutné nejprve dokončit [Postupy: vytvoření aktivity](how-to-create-an-activity.md).

> [!NOTE]
> Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** a vyberte **Přidat**, **Nová položka**.

2. V uzlu **nainstalované**, **běžné položky** vyberte **pracovní postup**. V seznamu **pracovních postupů** vyberte **aktivita** .

3. `SequentialNumberGuessWorkflow`Do pole **název** zadejte a klikněte na **Přidat**.

4. Přetáhněte aktivitu **sekvence** z části **tok řízení** v **sadě nástrojů** a přetáhněte ji na popisek sem přetáhněte **aktivitu** na návrhové ploše pracovního postupu.

## <a name="to-create-the-workflow-variables-and-arguments"></a>Postup vytvoření proměnných a argumentů pracovního postupu

1. Dvojím kliknutím na **SequentialNumberGuessWorkflow. XAML** v **Průzkumník řešení** zobrazíte pracovní postup v návrháři, pokud ještě není zobrazený.

2. Kliknutím na **argumenty** v levé dolní části návrháře pracovních postupů zobrazíte podokno **argumenty** .

3. Klikněte na **vytvořit argument**.

4. `MaxNumber`Do pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v vyberte v** rozevíracím seznamu **typ argumentu** možnost **Int32** a potom stiskněte klávesu ENTER a argument uložte.

5. Klikněte na **vytvořit argument**.

6. `Turns`Do pole **název** , které se nachází pod nově přidaným `MaxNumber` argumentem, vyberte **out** v rozevíracím seznamu **směr** , v rozevíracím seznamu **typ argumentu** vyberte **Int32** a potom stiskněte klávesu ENTER.

7. Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .

8. Kliknutím na **proměnné** v levém dolním rohu návrháře pracovních postupů zobrazíte podokno **proměnné** .

9. Klikněte na **vytvořit proměnnou**.

    > [!TIP]
    > Pokud se nezobrazí žádné pole **vytvořit proměnnou** , vyberte ji kliknutím na aktivitu **sekvence** na ploše návrháře pracovního postupu.

10. `Guess`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.

11. Klikněte na **vytvořit proměnnou**.

12. `Target`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.

13. Kliknutím na **proměnné** v levém dolním rohu návrháře aktivit zavřete podokno **proměnné** .

## <a name="to-add-the-workflow-activities"></a>Přidání aktivit pracovního postupu

1. Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji na aktivitu **sekvence** . Do `Target` pole **do** vložte a následující výraz zadejte do **výrazu zadejte výraz jazyka C#** nebo **Zadejte pole výrazu VB** .

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .

2. Přetáhněte aktivitu **DoWhile** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do pracovního postupu tak, aby byla pod aktivitou **přiřazení** .

3. Do pole hodnota vlastnosti **podmínky** aktivity **DoWhile** zadejte následující výraz.

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <xref:System.Activities.Statements.DoWhile>Aktivita spustí své podřízené aktivity a pak vyhodnotí její <xref:System.Activities.Statements.DoWhile.Condition%2A> . Pokud se <xref:System.Activities.Statements.DoWhile.Condition%2A> vyhodnotí jako `True` , pak se aktivity v <xref:System.Activities.Statements.DoWhile> znovu spustí. V tomto příkladu je vyhodnocen odhad uživatele a <xref:System.Activities.Statements.DoWhile> pokračuje, dokud není odhad správný.

4. Přetáhněte aktivitu **prompt** z části **NumberGuessWorkflowActivities** sady **nástrojů** a přetáhněte ji do aktivity **DoWhile** z předchozího kroku.

5. V **okně Vlastnosti**zadejte `"EnterGuess"` včetně uvozovek do pole hodnota vlastnosti **Bookmark** pro aktivitu **výzvy** . `Guess`Do pole hodnota vlastnosti **výsledek** zadejte a do pole vlastnost **text** zadejte následující výraz.

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .

6. Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji do aktivity **DoWhile** , aby se protáhla jako aktivita **výzvy** .

    > [!NOTE]
    > Když vyřadíte aktivitu **přiřazení** , Všimněte si, jak Návrhář pracovního postupu automaticky přidá aktivitu **sekvence** , která bude obsahovat aktivitu **výzvy** i nově přidanou aktivitu **přiřazení** .

7. Do `Turns` pole **do** zadejte do a vložte `Turns + 1` **výraz jazyka C#** nebo zadejte pole **výrazu VB** .

8. Přetáhněte aktivitu **if** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do aktivity **sekvence** tak, aby se doplnila nově přidaným aktivitou **přiřazení** .

9. Do pole hodnota vlastnosti **Podmínka** pro aktivitu **if** aktivity zadejte následující výraz.

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. Přetáhněte jinou položku **if** Activity z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do části **then** první aktivity **if** .

11. Do pole nově **přidaná hodnota** vlastnosti **Condition podmínky** aktivity zadejte následující výraz.

    ```text
    Guess < Target
    ```

12. Přetáhněte dvě aktivity **WriteLine** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte je tak, aby jedna byla v oddílu **potom** nově přidané aktivity **if** a jedna je v části **Else** .

13. Kliknutím na aktivitu **WriteLine** v části **pak** ji vyberete a do pole hodnota vlastnosti **text** zadejte následující výraz.

    ```text
    "Your guess is too low."
    ```

14. Kliknutím na aktivitu **WriteLine** v části **Else** ji vyberte a do pole hodnota vlastnosti **text** zadejte následující výraz.

    ```text
    "Your guess is too high."
    ```

     Následující příklad znázorňuje dokončený pracovní postup:

     ![Snímek obrazovky zobrazující dokončený sekvenční pracovní postup](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a>Postup sestavení pracovního postupu

1. Stisknutím kláves CTRL+SHIFT+B řešení sestavíte.

     Pokyny ke spuštění pracovního postupu najdete v dalším tématu [Postup: spuštění pracovního postupu](how-to-run-a-workflow.md). Pokud jste již dokončili [Postup: spuštění kroku pracovního postupu](how-to-run-a-workflow.md) s jiným stylem pracovního postupu a chcete jej spustit pomocí sekvenčního pracovního postupu z tohoto kroku, přeskočte dopředu na [sestavení a spusťte aplikaci v](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) tématu [Postupy: spuštění pracovního postupu](how-to-run-a-workflow.md).

## <a name="see-also"></a>Viz také

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programování Windows Workflow Foundation](programming.md)
- [Návrh pracovních postupů](designing-workflows.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvoření aktivity](how-to-create-an-activity.md)
- [Postupy: Spuštění pracovního postupu](how-to-run-a-workflow.md)
