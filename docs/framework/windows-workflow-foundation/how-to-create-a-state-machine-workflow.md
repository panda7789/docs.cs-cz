---
title: 'Postupy: vytvoření pracovního postupu stavového stroje'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8098ab4b056ad6375c248e803134c35d67e3f27b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397710"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Postupy: vytvoření pracovního postupu stavového stroje
Pracovní postupy lze zkonstruovat z předdefinovaných aktivit a také z vlastních aktivit. V tomto tématu se provede vytvořením pracovního postupu, který používá obě integrované aktivity, jako <xref:System.Activities.Statements.StateMachine> aktivity a vlastní aktivity z předchozího [jak: vytvořit aktivitu](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu. Pracovní postup modely číslo rozluštění hru.  
  
> [!NOTE]
>  Každé téma v kurzu Začínáme závisí na předchozí témata. K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu  
  
1.  Klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** v **Průzkumníka řešení** a vyberte **přidat**, **nová položka**.  
  
2.  V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivity** z **pracovního postupu** seznamu.  
  
3.  Typ `StateMachineNumberGuessWorkflow` do **název** pole a klikněte na tlačítko **přidat**.  
  
4.  Přetáhněte **stavový stroj StateMachine** aktivita z **stavového stroje** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek pracovní postup návrhovou plochu.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Chcete-li vytvořit pracovní postup proměnné a argumenty  
  
1.  Dvakrát klikněte na panel **StateMachineNumberGuessWorkflow.xaml** v **Průzkumníka řešení** zobrazíte pracovního postupu v návrháři, pokud se už nezobrazí.  
  
2.  Klikněte na tlačítko **argumenty** v levém dolním rohu návrháře postupu provádění zobrazit **argumenty** podokně.  
  
3.  Klikněte na tlačítko **vytvořit Argument**.  
  
4.  Typ `MaxNumber` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **Int32** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.  
  
5.  Klikněte na tlačítko **vytvořit Argument**.  
  
6.  Typ `Turns` do **název** pole, které je pod nově přidaný `MaxNumber` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte  **Datový typ Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.  
  
7.  Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.  
  
8.  Klikněte na tlačítko **proměnné** v levém dolním rohu návrháře postupu provádění zobrazit **proměnné** podokně.  
  
9. Klikněte na tlačítko **vytvořit proměnnou**.  
  
    > [!TIP]
    >  Pokud ne **vytvořit proměnnou** pole se zobrazí, klikněte na tlačítko <xref:System.Activities.Statements.StateMachine> aktivity na plochu návrháře pracovního postupu a vyberte ji.  
  
10. Typ `Guess` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
11. Klikněte na tlačítko **vytvořit proměnnou**.  
  
12. Typ `Target` do **název** vyberte **Int32** z **typ proměnné** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení proměnné.  
  
13. Klikněte na tlačítko **proměnné** v levého dolního rohu návrháře aktivit, zavřete **proměnné** podokně.  
  
### <a name="to-add-the-workflow-activities"></a>Přidání aktivit pracovního postupu  
  
1.  Klikněte na tlačítko **nazvané State1** ji vyberte. V **okno vlastností**, změnit **DisplayName** k `Initialize Target`.  
  
    > [!TIP]
    >  Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.  
  
2.  Dvakrát klikněte na nově pojmenovaném **inicializovat cílové** stavu v Návrháři pracovních postupů a rozbalte ho.  
  
3.  Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a umístěte ho do **položka** oddíl stavu. Typ `Target` do **k** pole a následující výraz, který **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.  
  
4.  Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.  
  
5.  Přetáhněte **stavu** aktivita z **stavového stroje** část **nástrojů** do návrháře postupu provádění a najeďte myší na **inicializovat cíl** stavu. Všimněte si, že čtyři trojúhelníky zobrazí kolem **inicializovat cílové** stav, když je nový stav nad ním. Vyřadit nový stav na trojúhelník, který je hned pod **inicializovat cílové** stavu. To umístí nového stavu do pracovního postupu a vytvoří přechod z **inicializovat cílové** stavu do nového stavu.  
  
6.  Klikněte na tlačítko **nazvané State1** vybraný a změňte **DisplayName** k `Enter Guess`a potom dvakrát klikněte na stav v Návrháři pracovních postupů a rozbalte ho.  
  
7.  Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho do **položka** oddíl stavu.  
  
8.  Zadejte následující výraz do **Text** vlastnosti **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Přetáhněte **přiřadit** aktivita z **primitiv** část **nástrojů** a umístěte na **ukončovací** oddíl stavu.  
  
10. Typ `Turns` do **k** pole a `Turns + 1` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole.  
  
11. Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.  
  
12. Přetáhněte **FinalState** aktivity z **stavového stroje** část **nástrojů**, najeďte myší **zadejte odhad** stavu a umístěte ho na trojúhelník, který se zobrazí napravo od **zadejte uhodnout** stavu tak, aby se vytvoří s přechodem mezi **zadejte uhodnout** a **FinalState**.  
  
13. Výchozí název přechodu je **T2**. Klikněte na tlačítko přechodu v Návrháři postupu provádění jej vyberte a nastavte jeho **DisplayName** k **odhad správný**. Potom klikněte na tlačítko a vyberte **FinalState**a přetáhněte ji na pravé straně tak, aby uvolnil prostor pro úplný přechod název zobrazený aniž zakreslovat buď dva stavy. To usnadní dokončete zbývající kroky v tomto kurzu.  
  
14. Dvakrát klikněte na nově pojmenovaném **odhad správný** přechodu v Návrháři pracovních postupů a rozbalte ho.  
  
15. Přetáhněte **readint –** aktivita z **NumberGuessWorkflowActivities** část **nástrojů** a umístěte jej do **aktivační událost** oddílu přechodu.  
  
16. V **okno vlastností** pro **readint –** aktivity, typ `"EnterGuess"` včetně uvozovek do **BookmarkName** vlastnost hodnoty pole a typ `Guess`do **výsledek** vlastnost hodnota – pole  
  
17. Zadejte následující výraz do **odhad správný** přechod na **podmínku** pole s hodnotou vlastnosti.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.  
  
    > [!NOTE]
    >  Přechod nastane aktivační událost přijetí a <xref:System.Activities.Statements.Transition.Condition%2A>, pokud jsou k dispozici, je vyhodnocen jako `True`. Pro tohoto přechodu je Pokud uživatele `Guess` odpovídá náhodně generované `Target`, pak řízení se předá **FinalState** a dokončení pracovního postupu.  
  
19. V závislosti na tom, zda je odhad správný, by měl pracovní postup buď na přechod **FinalState** nebo zpět **zadejte odhad** stavu pro jinou akci. Obě přechody sdílet stejnou spouštěcí událost trigger čekání na odhad uživatele k přijetí prostřednictvím **readint –** aktivity. Tomu se říká sdílené přechodu. Vytvořit sdílené přechod, klikněte na kruh, který označuje začátek **odhad správný** přechod a přetáhněte ho do požadovaného stavu. V tomto případě je přechod přechod, takže přetáhněte počáteční bod **odhad správný** přechod a umístěte ho zpátky do dolní části **zadejte uhodnout** stavu. Po vytvoření přechodu, vyberte ho v Návrháři pracovních postupů a nastavte jeho **DisplayName** vlastnost **uhodnout nesprávné**.  
  
    > [!NOTE]
    >  Sdílené přechody lze také vytvořit z v rámci přechodu návrháře kliknutím **přidat sdílené triggeru, přechod** v dolní části návrháře přechod a pak vyberete požadovanou cílovou stavu z  **Dostupné stavy připojení** rozevíracího seznamu.  
  
    > [!NOTE]
    >  Všimněte si, že pokud <xref:System.Activities.Statements.Transition.Condition%2A> přechodu vyhodnocen `false` (nebo vyhodnotit všechny podmínky sdílené spouštěcí události přechodu `false`), nedojde k přechodu a budou všechny aktivační události pro všechny přechody ze stavu znovu naplánována. V tomto kurzu, nemůže tato situace nastat z důvodu způsob, jakým jsou podmínky nakonfigurované (máme konkrétní akce pro Určuje, zda je odhad správný nebo není správná).  
  
20. Dvakrát klikněte **uhodnout nesprávné** přechodu v Návrháři pracovních postupů a rozbalte ho. Všimněte si, že **aktivační událost** je již nastaven na stejnou **readint –** aktivitu, která byla použita **odhad správný** přechodu.  
  
21. Zadejte následující výraz do **podmínku** pole s hodnotou vlastnosti.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Přetáhněte **Pokud** aktivita z **tok řízení** část **nástrojů** a umístěte jej do **akce** části přechodu.  
  
23. Zadejte následující výraz do **Pokud** aktivity **podmínku** pole s hodnotou vlastnosti.  
  
    ```
    Guess < Target  
    ```  
  
24. Přetáhněte dva **WriteLine** aktivity z **primitiv** část **nástrojů** a umístit je tak, že jeden je v **pak** část **Pokud** aktivity a jeden je v **Else** oddílu.  
  
25. Klikněte na tlačítko **WriteLine** aktivity v **pak** části jej vyberte a zadejte následující výraz do **Text** pole s hodnotou vlastnosti.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Klikněte na tlačítko **WriteLine** aktivity v **Else** části jej vyberte a zadejte následující výraz do **Text** pole s hodnotou vlastnosti.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. Vraťte se do celkového stavu počítače zobrazení v Návrháři postupu provádění kliknutím **stavový stroj StateMachine** z jeho zobrazení v horní části návrháře postupu provádění.  
  
     Následující příklad ukazuje dokončený pracovní postup.  
  
     ![Dokončení pracovního postupu stavového stroje](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>K vytvoření pracovního postupu  
  
1.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
     Návod, jak spustit workflow, najdete dalším tématu s názvem [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Pokud jste už dokončili [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) krok s jiným stylem pracovního postupu a chcete ji spustit pomocí pracovní postup stavového stroje z tohoto kroku, přeskočte k části [sestavíte a spustíte aplikaci](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) část [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Programování Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Návrh pracovních postupů](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Postupy: Vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Postupy: Spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
