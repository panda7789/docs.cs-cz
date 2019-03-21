---
title: 'Postupy: Vytvoření sekvenčního pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: d924d684561a2dd90ff18c803c3b12e8ac3581ce
ms.sourcegitcommit: e994e47d3582bf09ae487ecbd53c0dac30aebaf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2019
ms.locfileid: "58262566"
---
# <a name="how-to-create-a-sequential-workflow"></a>Postupy: Vytvoření sekvenčního pracovního postupu
Pracovní postupy lze zkonstruovat z předdefinovaných aktivit a také z vlastních aktivit. Toto téma se provede vytvořením pracovního postupu, který používá obě integrované aktivity, jako <xref:System.Activities.Statements.Sequence> aktivity a vlastní aktivity z předchozího [jak: Vytvořit aktivitu](how-to-create-an-activity.md) tématu. Pracovní postup modely číslo rozluštění hru.  
  
> [!NOTE]
>  Každé téma v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív Dokončit [jak: Vytvořit aktivitu](how-to-create-an-activity.md).  
  
> [!NOTE]
>  Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníka řešení** a vyberte **přidat**, **nová položka**.  
  
2.  V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivity** z **pracovního postupu** seznamu.  
  
3.  Typ `SequentialNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.  
  
4.  Přetáhněte **pořadí** aktivita z **tok řízení** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek pracovní postup návrhovou plochu.  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a>Chcete-li vytvořit pracovní postup proměnné a argumenty  
  
1.  Dvakrát klikněte na panel **SequentialNumberGuessWorkflow.xaml** v **Průzkumníka řešení** zobrazíte pracovního postupu v návrháři, pokud se už nezobrazí.  
  
2.  Klikněte na tlačítko **argumenty** v levém dolním rohu návrháře postupu provádění zobrazit **argumenty** podokně.  
  
3.  Klikněte na tlačítko **vytvořit Argument**.  
  
4.  Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.  
  
5.  Klikněte na tlačítko **vytvořit Argument**.  
  
6.  Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte  **Datový typ Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.  
  
7.  Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.  
  
8.  Klikněte na tlačítko **proměnné** v levém dolním rohu návrháře postupu provádění zobrazit **proměnné** podokně.  
  
9. Klikněte na tlačítko **vytvořit proměnnou**.  
  
    > [!TIP]
    >  Pokud ne **vytvořit proměnnou** pole se zobrazí, klikněte na tlačítko **pořadí** aktivity na plochu návrháře pracovního postupu a vyberte ji.  
  
10. Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
11. Klikněte na tlačítko **vytvořit proměnnou**.  
  
12. Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
13. Klikněte na tlačítko **proměnné** v levého dolního rohu návrháře aktivit, zavřete **proměnné** podokně.  
  
## <a name="to-add-the-workflow-activities"></a>Přidání aktivit pracovního postupu  
  
1.  Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a umístěte ho do **pořadí** aktivity. Typ `Target` do **k** pole a následující výraz, který **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.  
  
2.  Přetáhněte **DoWhile** aktivita z **tok řízení** část **nástrojů** a umístěte ho na pracovní postup tak, aby byl pod **přiřadit** aktivita.  
  
3.  Zadejte následující výraz do **DoWhile** aktivity **podmínku** pole s hodnotou vlastnosti.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     A <xref:System.Activities.Statements.DoWhile> aktivita spustí jeho podřízených aktivit a vyhodnocuje jeho <xref:System.Activities.Statements.DoWhile.Condition%2A>. Pokud <xref:System.Activities.Statements.DoWhile.Condition%2A> vyhodnotí jako `True`, pak aktivity <xref:System.Activities.Statements.DoWhile> proveďte znovu. V tomto příkladu je vyhodnocen odhad uživatele a <xref:System.Activities.Statements.DoWhile> pokračuje, dokud je odhad správný.  
  
4.  Přetáhněte **výzvy** aktivita z **NumberGuessWorkflowActivities** část **nástrojů** a umístěte jej do **DoWhile** aktivity v předchozím kroku.  
  
5.  V **okno vlastností**, typ `"EnterGuess"` včetně uvozovek do **BookmarkName** pole s hodnotou pro vlastnost **výzvy** aktivity. Typ `Guess` do **výsledek** vlastnost hodnotu pole a zadejte následující výraz do **Text** vlastnosti.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.  
  
6.  Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a umístěte jej do **DoWhile** aktivitu tak, že následuje **Výzvy** aktivity.  
  
    > [!NOTE]
    >  Když přetáhnete **přiřadit** aktivita, Všimněte si, jak automaticky přidá návrháře postupu provádění **pořadí** aktivitu tak, aby obsahovala obě **výzvy** aktivity a nově přidané **Přiřadit** aktivity.  
  
7.  Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.  
  
8.  Přetáhněte **Pokud** aktivita z **tok řízení** část **nástrojů** a umístěte jej do **pořadí** aktivitu tak, že následuje nově přidané **přiřadit** aktivity.  
  
9. Zadejte následující výraz do **Pokud** aktivity **podmínku** pole s hodnotou vlastnosti.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Přetáhněte další **Pokud** aktivita z **tok řízení** část **nástrojů** a umístěte jej do **pak** část první **Pokud** aktivity.  
  
11. Zadejte následující výraz do nově přidaný **Pokud** aktivity **podmínku** pole s hodnotou vlastnosti.  
  
    ```
    Guess < Target  
    ```  
  
12. Přetáhněte dva **WriteLine** aktivity z **primitiv** část **nástrojů** a umístit je tak, že jeden je v **pak** část nově přidaný **Pokud** aktivity a jeden je v **Else** oddílu.  
  
13. Klikněte na tlačítko **WriteLine** aktivity v **pak** části jej vyberte a zadejte následující výraz do **Text** pole s hodnotou vlastnosti.  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. Klikněte na tlačítko **WriteLine** aktivity v **Else** části jej vyberte a zadejte následující výraz do **Text** pole s hodnotou vlastnosti.  
  
    ```text
    "Your guess is too high."  
    ```  
  
     Následující příklad ukazuje dokončený pracovní postup.  
  
     ![Dokončení sekvenčního pracovního postupu](./media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
## <a name="to-build-the-workflow"></a>K vytvoření pracovního postupu  
  
1.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
     Návod, jak spustit workflow, najdete dalším tématu s názvem [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md). Pokud jste už dokončili [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md) krok s jiným stylem pracovního postupu a chcete ji spustit pomocí sekvenčního pracovního postupu v tomto kroku, přeskočte k části [sestavíte a spustíte aplikaci](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) část [jak: Spuštění pracovního postupu](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programování Windows Workflow Foundation](programming.md)
- [Návrh pracovních postupů](designing-workflows.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvoření aktivity](how-to-create-an-activity.md)
- [Postupy: Spuštění pracovního postupu](how-to-run-a-workflow.md)
