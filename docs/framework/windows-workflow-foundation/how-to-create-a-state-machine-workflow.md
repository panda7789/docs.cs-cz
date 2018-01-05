---
title: "Postupy: vytvoření pracovního postupu stavu počítače"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 95ba37b123b57ba9f86fefb55a860fb2122ccd3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a>Postupy: vytvoření pracovního postupu stavu počítače
Pracovní postupy lze sestavit z předdefinovaných aktivit a také z vlastních aktivit. Kroky v tomto tématu procesem vytvoření pracovního postupu, který používá obě zabudované aktivity, jako <xref:System.Activities.Statements.StateMachine> aktivity a vlastní aktivity z předchozí [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu. Pracovní postup modelů číslo hádání hru.  
  
> [!NOTE]
>  Každého tématu v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníku řešení** a vyberte **přidat**, **novou položku**.  
  
2.  V **nainstalovaná**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivity** z **pracovního postupu** seznamu.  
  
3.  Typ `StateMachineNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.  
  
4.  Přetažení **StateMachine** aktivity z **stavu počítače** části **sada nástrojů** a umístěte jej do **aktivity sem umístěte** v popisek návrhové ploše pracovního postupu.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Vytvoření proměnné pracovního postupu a argumenty  
  
1.  Klikněte dvakrát na **StateMachineNumberGuessWorkflow.xaml** v **Průzkumníku řešení** zobrazíte pracovního postupu v návrháři, pokud již není zobrazen.  
  
2.  Klikněte na tlačítko **argumenty** na straně dolním Návrháře pracovního postupu pro zobrazení **argumenty** podokně.  
  
3.  Klikněte na tlačítko **vytvořit Argument**.  
  
4.  Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení argument.  
  
5.  Klikněte na tlačítko **vytvořit Argument**.  
  
6.  Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **Out** z **směr** rozevíracího seznamu, vyberte  **Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.  
  
7.  Klikněte na tlačítko **argumenty** v levém dolním straně Návrhář aktivity zavřete **argumenty** podokně.  
  
8.  Klikněte na tlačítko **proměnné** na straně dolním Návrháře pracovního postupu pro zobrazení **proměnné** podokně.  
  
9. Klikněte na tlačítko **vytvořit proměnnou**.  
  
    > [!TIP]
    >  Pokud žádné **vytvoření proměnné** políčko se zobrazí, klikněte na tlačítko <xref:System.Activities.Statements.StateMachine> aktivity na plochu návrháře pracovního postupu a vyberte ji.  
  
10. Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
11. Klikněte na tlačítko **vytvořit proměnnou**.  
  
12. Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
13. Klikněte na tlačítko **proměnné** v levém dolním straně Návrhář aktivity zavřete **proměnné** podokně.  
  
### <a name="to-add-the-workflow-activities"></a>Chcete-li přidat aktivit pracovního postupu  
  
1.  Klikněte na tlačítko **State1** ji vyberte. V **vlastnosti – okno**, změnit **DisplayName** k `Initialize Target`.  
  
    > [!TIP]
    >  Pokud **vlastnosti – okno** není zobrazený, vyberte **vlastnosti – okno** z **zobrazení** nabídky.  
  
2.  Klikněte dvakrát na nově pojmenovaném **inicializovat cíl** stavu v Návrháři pracovních postupů a rozbalte ji.  
  
3.  Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a umístěte jej do **položka** části stavu. Typ `Target` do **k** pole a následující výraz do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Pokud **sada nástrojů** se nezobrazí okno, vyberte **sada nástrojů** z **zobrazení** nabídky.  
  
4.  Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.  
  
5.  Přetažení **stavu** aktivity z **stavový stroj** části **sada nástrojů** do návrháře pracovních postupů a pozastavte ukazatel myši nad **inicializovat cíl** stavu. Všimněte si, že kolem se zobrazí čtyři trojúhelníčky **inicializovat cíl** stav, když nový stav je nad ním. Vyřaďte nový stav na trojúhelníček, která se nachází bezprostředně pod **inicializovat cíl** stavu. To umístí nový stav do pracovního postupu a vytvoří přechod z **inicializovat cíl** do nového stavu stavu.  
  
6.  Klikněte na tlačítko **State1** ji vyberte Změnit **DisplayName** k `Enter Guess`a potom dvakrát klikněte na stav v Návrháři pracovních postupů a rozbalte ji.  
  
7.  Přetáhněte **WriteLine** aktivity z **primitiv** části **sada nástrojů** a umístěte jej do **položka** části stavu.  
  
8.  Zadejte následující výraz do **Text** vlastnost pole **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Přetáhněte **přiřadit** aktivity z **primitiv** části **sada nástrojů** a umístěte na **ukončení** části stavu.  
  
10. Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole.  
  
11. Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.  
  
12. Přetažení **FinalState** aktivity z **stavový stroj** části **sada nástrojů**, najeďte myší na **zadejte uhodnout** stavu a umístěte jej na trojúhelníček, který se zobrazí napravo **zadejte uhodnout** stavu tak, aby se vytvoří přechod mezi **zadejte uhodnout** a **FinalState**.  
  
13. Výchozí název přechodu je **T2**. Klikněte na tlačítko přechodu v Návrháři pracovních postupů, vyberte ho a nastavit jeho **DisplayName** k **uhodnout správné**. Potom klikněte na tlačítko a vyberte **FinalState**a přetáhněte jej do právo tak, aby bylo místo pro úplné přechod název zobrazený bez překrytí buď dva stavy. To bude usnadňují dokončit zbývající kroky v tomto kurzu.  
  
14. Klikněte dvakrát na nově pojmenovaném **uhodnout správné** přechod v Návrháři pracovních postupů a rozbalte ji.  
  
15. Přetáhněte **readint –** aktivity z **NumberGuessWorkflowActivities** části **sada nástrojů** a umístěte jej do **aktivační událost** části přechodu.  
  
16. V **vlastnosti – okno** pro **readint –** aktivity, typ `"EnterGuess"` včetně uvozovek do **NázevZáložky** vlastnost hodnota pole a zadejte `Guess`do **výsledek** vlastnost hodnota pole  
  
17. Zadejte následující výraz do **uhodnout správné** přechod na **podmínku** pole hodnotu vlastnosti.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.  
  
    > [!NOTE]
    >  Přechod nastane, když je obdržena aktivační událost a <xref:System.Activities.Statements.Transition.Condition%2A>, pokud existuje, jehož výsledkem `True`. Pro tento přechod Pokud uživatele `Guess` odpovídá náhodně generované `Target`, pak předá řízení **FinalState** a dokončení pracovního postupu.  
  
19. V závislosti na tom, jestli odhad je správná, měli přechod pracovního postupu k **FinalState** nebo zpět do **zadejte odhad** stavu pro jiné opakujte. Obě přechody sdílet stejnou aktivační událost čekání odhad uživatele k přijetí prostřednictvím **readint –** aktivity. Tomu se říká sdílené přechod. Vytvoření sdílené přechodu, klikněte na kruh označující začátek **uhodnout správné** přechod a přetáhněte ji do požadovaného stavu. V takovém případě je přechod vlastní přechodu, takže přetáhněte počáteční bod **uhodnout správné** přechod a umístěte jej zpět na konci **zadejte uhodnout** stavu. Po vytvoření přechodu, vyberte ho v Návrháři pracovních postupů a nastavit jeho **DisplayName** vlastnost **uhodnout nesprávné**.  
  
    > [!NOTE]
    >  Sdílené přechody můžete také vytvořit z v Návrháři přechod kliknutím **přidat sdílený aktivační událost přechod** v dolní části návrháře přechod a pak vybrat požadovanou cílového stavu z  **Dostupné stavy připojení** rozevíracího seznamu.  
  
    > [!NOTE]
    >  Všimněte si, že pokud <xref:System.Activities.Statements.Transition.Condition%2A> přechodu se vyhodnocuje `false` (nebo všechny podmínky přechod sdílené aktivační událost vyhodnocení `false`), přechod nedojde a budou všechny aktivační události pro všechny přechody ze stavu znovu naplánován. V tomto kurzu, nemůže tato situace nastat z důvodu způsob, jak jsou nakonfigurované podmínky (máme konkrétní akce na tom, jestli odhad správný nebo nesprávné).  
  
20. Dvakrát klikněte **uhodnout nesprávné** přechod v Návrháři pracovních postupů a rozbalte ji. Všimněte si, že **aktivační událost** už je nastavené na stejné **readint –** aktivity, která byla používána **uhodnout správné** přechod.  
  
21. Zadejte následující výraz do **podmínku** pole hodnotu vlastnosti.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Přetáhněte **Pokud** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej do **akce** části přechodu.  
  
23. Zadejte následující výraz do **Pokud** aktivity **podmínku** pole hodnotu vlastnosti.  
  
    ```
    Guess < Target  
    ```  
  
24. Přetáhněte dva **WriteLine** aktivity z **primitiv** části **sada nástrojů** a vyřadit je tak, aby jeden **pak** část **Pokud** aktivitu a jeden, je v **Else** části.  
  
25. Klikněte na tlačítko **WriteLine** aktivity v **pak** části ji vyberte a zadejte následující výraz do **Text** pole hodnotu vlastnosti.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Klikněte na tlačítko **WriteLine** aktivity v **Else** části ji vyberte a zadejte následující výraz do **Text** pole hodnotu vlastnosti.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. Vrátí k celkovému stavu počítače zobrazení v Návrháři pracovních postupů kliknutím **StateMachine** v zobrazení cesty zobrazí v horní části návrháře pracovních postupů.  
  
     Následující příklad ilustruje dokončené pracovního postupu.  
  
     ![Dokončit pracovní postup stavového stroje](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>K vytvoření pracovního postupu  
  
1.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
     Pokyny o tom, jak spustit workflow, naleznete v tématu Další [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Pokud jste již dokončili [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) krok s jiný styl pracovního postupu a chcete spustit pomocí pracovní postup stavu počítače z tohoto kroku, přeskočit na [sestavení a spuštění aplikace](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) části [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programování Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Návrh pracovních postupů](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Postupy: Vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Postupy: Spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
