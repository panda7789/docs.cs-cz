---
title: 'Postupy: vytvoření vývojový diagram pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: c483a79a234d175fca63f27b4303b3f087c84e59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519322"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Postupy: vytvoření vývojový diagram pracovního postupu
Pracovní postupy lze sestavit z předdefinovaných aktivit a také z vlastních aktivit. Kroky v tomto tématu procesem vytvoření pracovního postupu, který používá obě zabudované aktivity, jako <xref:System.Activities.Statements.Flowchart> aktivity a vlastní aktivity z předchozí [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu. Pracovní postup modelů číslo hádání hru.  
  
> [!NOTE]
>  Každého tématu v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníku řešení** a vyberte **přidat**, **novou položku**.  
  
2.  V **nainstalovaná**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivity** z **pracovního postupu** seznamu.  
  
3.  Typ `FlowchartNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.  
  
4.  Přetažení **vývojový diagram** aktivity z **vývojový diagram** části **sada nástrojů** a umístěte jej do **aktivity sem umístěte** v popisek pracovní postup návrhovou plochu.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Vytvoření proměnné pracovního postupu a argumenty  
  
1.  Klikněte dvakrát na **FlowchartNumberGuessWorkflow.xaml** v **Průzkumníku řešení** zobrazíte pracovního postupu v návrháři, pokud již není zobrazen.  
  
2.  Klikněte na tlačítko **argumenty** na straně dolním Návrháře pracovního postupu pro zobrazení **argumenty** podokně.  
  
3.  Klikněte na tlačítko **vytvořit Argument**.  
  
4.  Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení argument.  
  
5.  Klikněte na tlačítko **vytvořit Argument**.  
  
6.  Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **Out** z **směr** rozevíracího seznamu, vyberte  **Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.  
  
7.  Klikněte na tlačítko **argumenty** v levém dolním straně Návrhář aktivity zavřete **argumenty** podokně.  
  
8.  Klikněte na tlačítko **proměnné** na straně dolním Návrháře pracovního postupu pro zobrazení **proměnné** podokně.  
  
9. Klikněte na tlačítko **vytvořit proměnnou**.  
  
    > [!TIP]
    >  Pokud žádné **vytvoření proměnné** políčko se zobrazí, klikněte na tlačítko <xref:System.Activities.Statements.Flowchart> aktivity na plochu návrháře pracovního postupu a vyberte ji.  
  
10. Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
11. Klikněte na tlačítko **vytvořit proměnnou**.  
  
12. Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
13. Klikněte na tlačítko **proměnné** v levém dolním straně Návrhář aktivity zavřete **proměnné** podokně.  
  
### <a name="to-add-the-workflow-activities"></a>Chcete-li přidat aktivit pracovního postupu  
  
1.  Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a ukazatel myši přesunete **spustit** uzlu, který je v horní části Vývojový diagram. Při **přiřadit** aktivity je nad **spustit** uzlu kolem se zobrazí tři trojúhelníčky **spustit** uzlu. Vyřaďte **přiřadit** aktivity na trojúhelníček, který je přímo pod **spustit** uzlu. To bude propojit dvě položky společně a označí **přiřadit** aktivitu jako první aktivitu v vývojový diagram.  
  
    > [!NOTE]
    >  Aktivity můžete také zadat jako výchozí aktivity v pracovním postupu ručně jejich spojením aktivity s počáteční uzel. K tomu, najeďte myší **spustit** uzel, klikněte na jednu z obdélníky, které se zobrazí při přesunutí myši **spustit** uzel a přetáhněte připojení řádek dolů požadované aktivity a umístěte jej na jednom z obdélníky, které se zobrazují. Můžete také určit a aktivitu jako spouštěcí aktivitu tak, že kliknete pravým tlačítkem na it a výběr **nastavit jako spuštění uzlu**.  
  
2.  Typ `Target` do **k** pole a následující výraz do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Pokud **sada nástrojů** se nezobrazí okno, vyberte **sada nástrojů** z **zobrazení** nabídky.  
  
3.  Přetažení **výzva** aktivity z **NumberGuessWorkflowActivities** části **sada nástrojů**, vyřaďte níže **přiřadit** aktivity z předchozího kroku a připojte **výzva** aktivitu **přiřadit** aktivity. Existují tři způsoby, jak připojit dvěma aktivitami. První způsob je je připojení, jako je vyřadit **výzva** aktivity pro pracovní postup. Jako přetahování **výzva** aktivitu do pracovního postupu, najeďte myší **přiřadit** aktivity a umístěte jej do jednoho čtyři trojúhelníčky, které se objeví **výzva** Aktivita je přes **přiřadit** aktivity. Druhý způsob je odpojení **výzva** aktivitu do pracovního postupu v požadovaném umístění. Potom najeďte myší **přiřadit** aktivity a přetáhněte jeden obdélníky, které se zobrazí dolů na **výzva** aktivity. Přetažení myší tak, aby připojení řádek z **přiřadit** aktivity připojen k jednomu z obdélníků z **výzva** aktivity a pak uvolnění tlačítka myši. Třetí způsob, jakým je velmi podobně jako první, vyjma toho, že existuje několik způsobů **výzva** aktivity z **sada nástrojů**, přetáhněte ji z jeho umístění na návrhovou plochu pracovního postupu, najeďte myší  **Přiřadit** aktivitu a umístěte jej do jednoho trojúhelníčky, které se zobrazí.  
  
4.  V **vlastnosti – okno** pro **výzva** aktivity, typ `"EnterGuess"` včetně uvozovek do **NázevZáložky** pole hodnotu vlastnosti. Typ `Guess` do **výsledek** vlastnost hodnotu pole a zadejte následující výraz do **Text** pole vlastnosti.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Pokud **vlastnosti – okno** není zobrazený, vyberte **vlastnosti – okno** z **zobrazení** nabídky.  
  
5.  Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a připojte ho pomocí jedné z metod popsaných v předchozím kroku, tak, aby se níže  **Výzva** aktivity.  
  
6.  Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.  
  
7.  Přetáhněte **FlowDecision** z **vývojový diagram** části **sada nástrojů** a připojte ho níže **přiřadit** aktivity. V **vlastnosti – okno**, zadejte následující výraz do **podmínku** pole hodnotu vlastnosti.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  Přetáhněte další **FlowDecision** aktivity z **sada nástrojů** a umístěte jej pod první z nich. Připojení dvě aktivity přetažením z obdélníku, které je označeno **False** nahoře **FlowDecision** aktivitu rámeček v horní části druhý **FlowDecision**aktivity.  
  
    > [!TIP]
    >  Pokud se nezobrazí **True** a **False** popisků na **FlowDecision**, najeďte myší **FlowDecision**.  
  
9. Klikněte na druhý **FlowDecision** aktivity ji vyberte. V **vlastnosti – okno**, zadejte následující výraz do **podmínku** pole hodnotu vlastnosti.  
  
    ```
    Guess < Target  
    ```  
  
10. Přetáhněte dva **WriteLine** aktivity z **primitiv** části **sada nástrojů** a jejich umístění, aby se vedle sebe níže dva **FlowDecision**  aktivity. Připojení **True** akce dolní **FlowDecision** aktivitu levou krajní **WriteLine** aktivitu a **False** akce úplně vpravo **WriteLine** aktivity.  
  
11. Klikněte levou krajní **WriteLine** aktivitu vyberte ho a zadejte následující výraz do **Text** hodnota vlastnosti pole **vlastnosti – okno**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Připojení **WriteLine** na levé straně **výzva** aktivity, který je nad ním.  
  
13. Klikněte pravou krajní **WriteLine** aktivitu vyberte ho a zadejte následující výraz do **Text** hodnota vlastnosti pole **vlastnosti – okno**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Připojení **WriteLine** aktivity na pravé straně **výzva** aktivity nad ním.  
  
     Následující příklad ilustruje dokončené pracovního postupu.  
  
     ![Dokončit modelu Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### <a name="to-build-the-workflow"></a>K vytvoření pracovního postupu  
  
1.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
     Pokyny o tom, jak spustit workflow, naleznete v tématu Další [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Pokud jste již dokončili [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) krok s jiný styl pracovního postupu a chcete spustit pomocí vývojový diagram pracovního postupu z tohoto kroku, přeskočit na [sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)část [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programování Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Návrh pracovních postupů](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Postupy: Vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Postupy: Spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
