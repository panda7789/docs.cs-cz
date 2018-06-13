---
title: 'Postupy: Vytvoření sekvenčního pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: d7379e6e4d24ccc23d57486c3271c482a7f17edd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519399"
---
# <a name="how-to-create-a-sequential-workflow"></a>Postupy: Vytvoření sekvenčního pracovního postupu
Pracovní postupy lze sestavit z předdefinovaných aktivit a také z vlastních aktivit. Kroky v tomto tématu procesem vytvoření pracovního postupu, který používá obě zabudované aktivity, jako <xref:System.Activities.Statements.Sequence> aktivity a vlastní aktivity z předchozí [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu. Pracovní postup modelů číslo hádání hru.  
  
> [!NOTE]
>  Každého tématu v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníku řešení** a vyberte **přidat**, **novou položku**.  
  
2.  V **nainstalovaná**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivity** z **pracovního postupu** seznamu.  
  
3.  Typ `SequentialNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.  
  
4.  Přetažení **pořadí** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej do **aktivity sem umístěte** v popisek pracovní postup návrhovou plochu.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Vytvoření proměnné pracovního postupu a argumenty  
  
1.  Klikněte dvakrát na **SequentialNumberGuessWorkflow.xaml** v **Průzkumníku řešení** zobrazíte pracovního postupu v návrháři, pokud již není zobrazen.  
  
2.  Klikněte na tlačítko **argumenty** na straně dolním Návrháře pracovního postupu pro zobrazení **argumenty** podokně.  
  
3.  Klikněte na tlačítko **vytvořit Argument**.  
  
4.  Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení argument.  
  
5.  Klikněte na tlačítko **vytvořit Argument**.  
  
6.  Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **Out** z **směr** rozevíracího seznamu, vyberte  **Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.  
  
7.  Klikněte na tlačítko **argumenty** v levém dolním straně Návrhář aktivity zavřete **argumenty** podokně.  
  
8.  Klikněte na tlačítko **proměnné** na straně dolním Návrháře pracovního postupu pro zobrazení **proměnné** podokně.  
  
9. Klikněte na tlačítko **vytvořit proměnnou**.  
  
    > [!TIP]
    >  Pokud žádné **vytvoření proměnné** políčko se zobrazí, klikněte na tlačítko **pořadí** aktivity na plochu návrháře pracovního postupu a vyberte ji.  
  
10. Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
11. Klikněte na tlačítko **vytvořit proměnnou**.  
  
12. Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
13. Klikněte na tlačítko **proměnné** v levém dolním straně Návrhář aktivity zavřete **proměnné** podokně.  
  
### <a name="to-add-the-workflow-activities"></a>Chcete-li přidat aktivit pracovního postupu  
  
1.  Přetažení **přiřadit** aktivity z **primitiv** části **sada nástrojů** a umístěte jej do **pořadí** aktivity. Typ `Target` do **k** pole a následující výraz do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Pokud **sada nástrojů** se nezobrazí okno, vyberte **sada nástrojů** z **zobrazení** nabídky.  
  
2.  Přetáhněte **DoWhile** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej pro pracovní postup tak, aby se níže **přiřadit** aktivita.  
  
3.  Zadejte následující výraz do **DoWhile** aktivity **podmínku** pole hodnotu vlastnosti.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     A <xref:System.Activities.Statements.DoWhile> aktivita provede jeho podřízené aktivity a vyhodnocuje jeho <xref:System.Activities.Statements.DoWhile.Condition%2A>. Pokud <xref:System.Activities.Statements.DoWhile.Condition%2A> vyhodnotí jako `True`, pak aktivity v <xref:System.Activities.Statements.DoWhile> provést znovu. V tomto příkladu je odhad uživatele vyhodnotit a <xref:System.Activities.Statements.DoWhile> pokračuje, dokud odhad je správný.  
  
4.  Přetáhněte **výzva** aktivity z **NumberGuessWorkflowActivities** části **sada nástrojů** a umístěte jej do **DoWhile** aktivity v předchozím kroku.  
  
5.  V **vlastnosti – okno**, typ `"EnterGuess"` včetně uvozovek do **NázevZáložky** hodnota vlastnosti pole pro **výzva** aktivity. Typ `Guess` do **výsledek** vlastnost hodnotu pole a zadejte následující výraz do **Text** pole vlastnosti.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Pokud **vlastnosti – okno** není zobrazený, vyberte **vlastnosti – okno** z **zobrazení** nabídky.  
  
6.  Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a umístěte jej do **DoWhile** aktivity, které se řídí **Výzva** aktivity.  
  
    > [!NOTE]
    >  Když vyřadíte **přiřadit** aktivity, Všimněte si, jak automaticky přidá návrháře pracovních postupů **pořadí** aktivity tak, aby obsahovala i **výzva** aktivity a nově přidaný **Přiřadit** aktivity.  
  
7.  Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.  
  
8.  Přetáhněte **Pokud** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej do **pořadí** aktivity, které se řídí Nově přidaná **přiřadit** aktivity.  
  
9. Zadejte následující výraz do **Pokud** aktivity **podmínku** pole hodnotu vlastnosti.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Přetáhněte další **Pokud** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej do **pak** část první **Pokud** aktivity.  
  
11. Zadejte následující výraz do nově přidaný **Pokud** aktivity **podmínku** pole hodnotu vlastnosti.  
  
    ```
    Guess < Target  
    ```  
  
12. Přetáhněte dva **WriteLine** aktivity z **primitiv** části **sada nástrojů** a vyřadit je tak, aby jeden **pak** část nově přidaný **Pokud** aktivitu a jeden, je v **Else** části.  
  
13. Klikněte na tlačítko **WriteLine** aktivity v **pak** části ji vyberte a zadejte následující výraz do **Text** pole hodnotu vlastnosti.  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. Klikněte na tlačítko **WriteLine** aktivity v **Else** části ji vyberte a zadejte následující výraz do **Text** pole hodnotu vlastnosti.  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     Následující příklad ilustruje dokončené pracovního postupu.  
  
     ![Dokončit sekvenční pracovní postup](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>K vytvoření pracovního postupu  
  
1.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
     Pokyny o tom, jak spustit workflow, naleznete v tématu Další [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Pokud jste již dokončili [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) krok s jiný styl pracovního postupu a chcete spustit pomocí sekvenčního pracovního postupu z tohoto kroku, přeskočit na [sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)část [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programování Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Návrh pracovních postupů](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Postupy: Vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Postupy: Spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
