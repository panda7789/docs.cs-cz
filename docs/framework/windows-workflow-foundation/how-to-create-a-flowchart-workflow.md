---
title: 'Postupy: Vytvoření pracovního postupu vývojového diagramu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 0faf4d77b1ea2881ba8e029d544f2e42cf552349
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989690"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Postupy: Vytvoření pracovního postupu vývojového diagramu
Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit. V tomto tématu se seznámíte s vytvořením pracovního postupu, který používá předdefinované aktivity, jako je například aktivita <xref:System.Activities.Statements.Flowchart>, a vlastní aktivity z předchozích [postupy: Vytvoření aktivity](how-to-create-an-activity.md) tématu. Pracovní postup modeluje číslo odhadující hru.  
  
> [!NOTE]
> Každé téma v kurzu Začínáme závisí na předchozích tématech. Chcete-li dokončit toto téma, je nutné nejprve dokončit [postupy: Vytvořte](how-to-create-an-activity.md)aktivity.  
  
> [!NOTE]
> Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu  
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** a vyberte **Přidat**, **Nová položka**.  
  
2. V uzlu **nainstalované**, **běžné položky** vyberte **pracovní postup**. V seznamu **pracovních postupů** vyberte **aktivita** .  
  
3. Do pole **název** zadejte `FlowchartNumberGuessWorkflow` a klikněte na **Přidat**.  
  
4. Přetáhněte aktivitu **vývojového diagramu** z oddílu **vývojového diagramu** na **panel nástrojů** a přetáhněte ji na popisek **aktivity** na návrhovou plochu pracovního postupu.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Postup vytvoření proměnných a argumentů pracovního postupu  
  
1. Dvojím kliknutím na **FlowchartNumberGuessWorkflow. XAML** v **Průzkumník řešení** zobrazíte pracovní postup v návrháři, pokud ještě není zobrazený.  
  
2. Kliknutím na **argumenty** v levé dolní části návrháře pracovních postupů zobrazíte podokno **argumenty** .  
  
3. Klikněte na **vytvořit argument**.  
  
4. Do pole **název** zadejte `MaxNumber`, v rozevíracím seznamu **směr** vyberte možnost **v, v** rozevíracím seznamu **typ argumentu** vyberte **Int32** a pak stisknutím klávesy ENTER uložte argument.  
  
5. Klikněte na **vytvořit argument**.  
  
6. Do pole **název** , které je pod nově přidaným `MaxNumber` argumentem, zadejte `Turns`, v rozevíracím seznamu **směr** vyberte **typ** **Int32** a potom stiskněte klávesu ENTER.  
  
7. Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .  
  
8. Kliknutím na **proměnné** v levém dolním rohu návrháře pracovních postupů zobrazíte podokno **proměnné** .  
  
9. Klikněte na **vytvořit proměnnou**.  
  
    > [!TIP]
    > Pokud se nezobrazí žádné pole **vytvořit proměnnou** , vyberte ji kliknutím na aktivitu <xref:System.Activities.Statements.Flowchart> na ploše návrháře pracovního postupu.  
  
10. Do pole **název** zadejte `Guess`, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.  
  
11. Klikněte na **vytvořit proměnnou**.  
  
12. Do pole **název** zadejte `Target`, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.  
  
13. Kliknutím na **proměnné** v levém dolním rohu návrháře aktivit zavřete podokno **proměnné** .  
  
### <a name="to-add-the-workflow-activities"></a>Přidání aktivit pracovního postupu  
  
1. Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a umístěte ji na **spouštěcí** uzel, který je v horní části vývojového diagramu. Pokud je aktivita **přiřazení** nad **počátečním** uzlem, zobrazí se kolem **počátečního** uzlu tři trojúhelníky. Přetáhněte aktivitu **přiřazení** na trojúhelník, který je přímo pod **počátečním** uzlem. Tato akce spojí dvě položky dohromady a určí aktivitu **přiřazení** jako první aktivitu ve vývojovém diagramu.  
  
    > [!NOTE]
    > Aktivity můžete v pracovním postupu uvést také jako počáteční aktivitu, a to tak, že je ručně propojíte aktivitu s počátečním uzlem. Provedete to tak, že najedete myší na **spouštěcí** uzel, kliknete na jeden z obdélníků, který se zobrazí, když je ukazatel myši nad **spouštěcím** uzlem, a přetáhnete spojovací čáru dolů na požadovanou aktivitu a umístíte ji na jeden z obdélníků, které se zobrazí. Aktivitu můžete také označit jako počáteční aktivitu tak, že na ni kliknete pravým tlačítkem myši a zvolíte **nastavit jako spouštěcí uzel**.  
  
2. Do pole **do** zadejte `Target` a do následujícího výrazu vložte  **C# výraz** nebo **Zadejte pole výrazu VB** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .  
  
3. Přetáhněte aktivitu **prompt** z části **NumberGuessWorkflowActivities** na **panelu nástrojů**, přetáhněte ji pod aktivitu **přiřazení** z předchozího kroku a připojte aktivitu **výzvy** k aktivitě **přiřazení** . Existují tři způsoby, jak propojit dvě aktivity. Prvním způsobem je připojení při vyřazení aktivity s **výzvou** v pracovním postupu. Při přetahování aktivity **výzvy** k pracovnímu postupu umístěte ukazatel myši na aktivitu **přiřadit** a přetáhněte ji na jeden ze čtyř trojúhelníků, který se zobrazí, když je aktivita **výzvy** nad aktivitou **přiřazení** . Druhým způsobem je vyřadit aktivitu **výzvy** do pracovního postupu v požadovaném umístění. Pak najeďte myší na aktivitu **přiřazení** a přetáhněte jeden z obdélníků, který se zobrazí v poli pro činnost **výzvy** . Přetáhněte myš, aby se propojovací čára z aktivity **přiřazení** připojovala k jednomu z obdélníků aktivity **výzvy** , a pak uvolněte tlačítko myši. Třetí způsob se velmi podobá prvnímu, s tím rozdílem, že místo přetažení aktivity **výzvy** ze **sady nástrojů**ho přetáhnete z jeho umístění na návrhové ploše pracovního postupu, najeďte myší nad aktivitu **přiřadit** a umístěte ho na jeden ze zobrazených trojúhelníků.  
  
4. V **okně Vlastnosti** aktivity **výzvy** zadejte do pole hodnota vlastnosti **Bookmark** text `"EnterGuess"` včetně uvozovek. Do pole hodnota vlastnosti **výsledek** zadejte `Guess` a do pole vlastnost **text** zadejte následující výraz.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .  
  
5. Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a připojte ji pomocí jedné z metod popsaných v předchozím kroku, aby se **zobrazila** pod aktivitou výzvy.  
  
6. Do pole **do** zadejte `Turns` a `Turns + 1` do pole **Zadejte C# výraz** nebo **Zadejte výraz VB** .  
  
7. Přetáhněte **použitím objektu FlowDecision** z části **vývojového diagramu** v **sadě nástrojů** a připojte ji pod aktivitu **přiřazení** . V **okně Vlastnosti**zadejte následující výraz do pole hodnota vlastnosti **podmínky** .  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. Přetáhněte další aktivitu **použitím objektu FlowDecision** ze **sady nástrojů** a přetáhněte ji pod první. Připojte dvě aktivity přetažením z obdélníku, který je označen jako **false** u horní aktivity **použitím objektu FlowDecision** na obdélník v horní části druhé aktivity **použitím objektu FlowDecision** .  
  
    > [!TIP]
    > Pokud nevidíte v **použitím objektu FlowDecision**popisky **true** a **false** , najeďte myší na **použitím objektu FlowDecision**.  
  
9. Klikněte na druhou aktivitu **použitím objektu FlowDecision** a vyberte ji. V **okně Vlastnosti**zadejte následující výraz do pole hodnota vlastnosti **podmínky** .  
  
    ```text
    Guess < Target
    ```  
  
10. Přetáhněte dvě aktivity **WriteLine** z části **primitiva** v **sadě nástrojů** a přetáhněte je tak, aby byly vedle sebe pod dvěma **použitím objektu FlowDecision** aktivitami. Připojte **skutečnou** akci nejnižší aktivity **použitím objektu FlowDecision** k aktivitě **WriteLine** a nejvíce vlevo a akci **false** u aktivity napravo napravo.  
  
11. Klikněte na aktivitu **vywriteline** úplně vlevo a vyberte ji a do pole hodnota vlastnosti **text** v **okně Vlastnosti**zadejte následující výraz.  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. Připojte řádek **WriteLine** k levé straně aktivity **výzvy** , která je nad ním.  
  
13. Klikněte **na aktivitu** napravo od jejího výběru a vyberte ji a do pole hodnota vlastnosti **text** v **okně Vlastnosti**zadejte následující výraz.  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. Připojte aktivitu **WriteLine** k pravé straně aktivity s **výzvou** nad ní.  
  
     Následující příklad znázorňuje dokončený pracovní postup.  
  
     ![Diagram znázorňující dokončený vývojový diagram programovací model Windows Workflow Foundation.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a>Postup sestavení pracovního postupu  
  
1. Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.  
  
     Pokyny ke spuštění pracovního postupu najdete v dalším tématu [: Spusťte](how-to-run-a-workflow.md)pracovního postupu. Pokud jste již dokončili [: Spusťte pracovní postup](how-to-run-a-workflow.md) kroku s jiným stylem pracovního postupu a přejete si ho spustit pomocí pracovního postupu vývojového diagramu z tohoto kroku, přeskočte dopředu na [sestavení a spusťte aplikaci](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) v části [postupy: Spusťte](how-to-run-a-workflow.md)pracovního postupu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programování Windows Workflow Foundation](programming.md)
- [Návrh pracovních postupů](designing-workflows.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvoření](how-to-create-an-activity.md) aktivity
- [Postupy: Spuštění pracovního postupu](how-to-run-a-workflow.md)
