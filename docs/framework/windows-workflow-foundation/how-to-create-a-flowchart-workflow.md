---
title: 'Postupy: Vytvoření pracovního postupu vývojového diagramu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 15cf94d5ea191435723f754f35e43d65632142e2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311198"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Postupy: Vytvoření pracovního postupu vývojového diagramu
Pracovní postupy lze zkonstruovat z předdefinovaných aktivit a také z vlastních aktivit. Toto téma se provede vytvořením pracovního postupu, který používá obě integrované aktivity, jako <xref:System.Activities.Statements.Flowchart> aktivity a vlastní aktivity z předchozího [jak: Vytvořit aktivitu](how-to-create-an-activity.md) tématu. Pracovní postup modely číslo rozluštění hru.  
  
> [!NOTE]
>  Každé téma v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív Dokončit [jak: Vytvořit aktivitu](how-to-create-an-activity.md).  
  
> [!NOTE]
>  Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu  
  
1. Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníka řešení** a vyberte **přidat**, **nová položka**.  
  
2. V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivity** z **pracovního postupu** seznamu.  
  
3. Typ `FlowchartNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.  
  
4. Přetáhněte **vývojový diagram** aktivita z **vývojový diagram** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek pracovní postup návrhovou plochu.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Chcete-li vytvořit pracovní postup proměnné a argumenty  
  
1. Dvakrát klikněte na panel **FlowchartNumberGuessWorkflow.xaml** v **Průzkumníka řešení** zobrazíte pracovního postupu v návrháři, pokud se už nezobrazí.  
  
2. Klikněte na tlačítko **argumenty** v levém dolním rohu návrháře postupu provádění zobrazit **argumenty** podokně.  
  
3. Klikněte na tlačítko **vytvořit Argument**.  
  
4. Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.  
  
5. Klikněte na tlačítko **vytvořit Argument**.  
  
6. Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte  **Datový typ Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.  
  
7. Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.  
  
8. Klikněte na tlačítko **proměnné** v levém dolním rohu návrháře postupu provádění zobrazit **proměnné** podokně.  
  
9. Klikněte na tlačítko **vytvořit proměnnou**.  
  
    > [!TIP]
    >  Pokud ne **vytvořit proměnnou** pole se zobrazí, klikněte na tlačítko <xref:System.Activities.Statements.Flowchart> aktivity na plochu návrháře pracovního postupu a vyberte ji.  
  
10. Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
11. Klikněte na tlačítko **vytvořit proměnnou**.  
  
12. Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
13. Klikněte na tlačítko **proměnné** v levého dolního rohu návrháře aktivit, zavřete **proměnné** podokně.  
  
### <a name="to-add-the-workflow-activities"></a>Přidání aktivit pracovního postupu  
  
1. Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a najeďte myší **spustit** uzlu, který je v horní části Vývojový diagram. Při **přiřadit** činnost je nad **Start** uzlu kolem se zobrazí tři trojúhelníky **Start** uzlu. Vyřadit **přiřadit** aktivitu na trojúhelník, který je přímo pod **Start** uzlu. To se propojit dvě položky a označí **přiřadit** aktivitu jako první aktivitu ve vývojovém diagramu.  
  
    > [!NOTE]
    >  Aktivity mohou také uvedené jako spouštěcí aktivitu v pracovním postupu ručně jejich propojením aktivit k počáteční uzel. K tomu, najeďte myší **Start** uzel, klikněte na některou obdélníky, které se zobrazí, když je myš **Start** uzel a přetáhněte připojení řádek dolů požadovanou aktivitu a umístěte ho na jednom z obdélníky, které se zobrazí. Můžete taky určit aktivity jako spouštěcí aktivitu tak, že kliknete pravým tlačítkem it a zvolíte **nastavit jako spuštění uzlu**.  
  
2. Typ `Target` do **k** pole a následující výraz, který **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.  
  
3. Přetáhněte **výzvy** aktivita z **NumberGuessWorkflowActivities** část **nástrojů**, vyřaďte níže **přiřadit** aktivity z předchozího kroku a připojit **výzvy** aktivitu **přiřadit** aktivity. Existují tři způsoby, jak připojit dvěma aktivitami. První způsob je jejich připojení, jako je vyřadit **výzvy** aktivity v pracovním postupu. Jak přetahujete **výzvy** aktivitu do pracovního postupu, najeďte myší **přiřadit** aktivity a umístěte ho na jednu ze čtyř trojúhelníků, které se objeví **výzvy** Aktivita je přes **přiřadit** aktivity. Druhý způsob je vyřadit **výzvy** aktivitu do pracovního postupu do požadovaného umístění. Poté najeďte myší **přiřadit** aktivity a přetáhněte jeden z obdélníky, které se zobrazí dolů na **výzvy** aktivity. Přetáhněte myší tak, aby připojení řádek z **přiřadit** aktivity se připojí k jedné obdélníků z **výzvy** aktivitu a pak uvolněte tlačítko myši. Třetí způsob je velmi podobně jako první, s výjimkou, že místo přetažení **výzvy** aktivita z **nástrojů**, přetáhněte ho z umístění na povrchu návrhu pracovního postupu, najeďte myší  **Přiřadit** aktivitu a umístěte ho na jeden z trojúhelníků, které se zobrazí.  
  
4. V **okno vlastností** pro **výzvy** aktivity, typ `"EnterGuess"` včetně uvozovek do **BookmarkName** pole s hodnotou vlastnosti. Typ `Guess` do **výsledek** vlastnost hodnotu pole a zadejte následující výraz do **Text** vlastnosti.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.  
  
5. Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a připojte ho pomocí jedné z metod popsaných v předchozím kroku, tak, aby se níže  **Příkazový řádek** aktivity.  
  
6. Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.  
  
7. Přetáhněte **FlowDecision** z **vývojový diagram** část **nástrojů** a připojte ho níže **přiřadit** aktivity. V **okno vlastností**, zadejte následující výraz do **podmínku** pole s hodnotou vlastnosti.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. Přetáhněte další **FlowDecision** aktivita z **nástrojů** a klesne pod první z nich. Propojení dvou aktivit přetažením z obdélník, který je označen **False** nahoře **FlowDecision** aktivity obdélníku, který v horní části druhý **FlowDecision**aktivity.  
  
    > [!TIP]
    >  Pokud se nezobrazí **True** a **False** popisků na **FlowDecision**, najeďte myší **FlowDecision**.  
  
9. Klikněte na druhé **FlowDecision** aktivitu a vyberte ji. V **okno vlastností**, zadejte následující výraz do **podmínku** pole s hodnotou vlastnosti.  
  
    ```
    Guess < Target  
    ```  
  
10. Přetáhněte dva **WriteLine** aktivity **primitiv** část **nástrojů** a umístit je tak, že jsou vedle sebe dva **FlowDecision**  aktivity. Připojit **True** akce dolní **FlowDecision** první aktivitu **WriteLine** aktivitu a **False** akce úplně vpravo **WriteLine** aktivity.  
  
11. Klikněte na první **WriteLine** aktivity ho vyberte a zadejte následující výraz do **Text** hodnota vlastnosti pole **okno vlastností**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Připojení **WriteLine** na levé straně **výzvy** aktivitu, která je nad ním.  
  
13. Klikněte na tlačítko úplně vpravo **WriteLine** aktivity ho vyberte a zadejte následující výraz do **Text** hodnota vlastnosti pole **okno vlastností**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Připojit **WriteLine** aktivity na pravé straně **výzvy** aktivity nad ním.  
  
     Následující příklad ukazuje dokončený pracovní postup.  
  
     ![Dokončení Windows Workflow Foundation](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### <a name="to-build-the-workflow"></a>K vytvoření pracovního postupu  
  
1. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
     Návod, jak spustit workflow, najdete dalším tématu s názvem [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md). Pokud jste už dokončili [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md) krok s jiným stylem pracovního postupu a chcete ji spustit pomocí pracovního postupu vývojového diagramu z tohoto kroku, přeskočte k části [sestavíte a spustíte aplikaci](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) část [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programování ve Windows Workflow Foundation](programming.md)
- [Návrh pracovních postupů](designing-workflows.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvoření aktivity](how-to-create-an-activity.md)
- [Postupy: Spuštění pracovního postupu](how-to-run-a-workflow.md)
