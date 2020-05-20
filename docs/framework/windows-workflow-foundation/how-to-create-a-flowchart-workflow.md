---
title: 'Postupy: Vytvoření pracovního postupu vývojového diagramu'
description: Tento článek popisuje vytvoření pracovního postupu, který používá předdefinované aktivity a vlastní aktivity z předchozího článku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 6b3fa423200f5c5cfece60f07372ce9678fc0072
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419704"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Postupy: Vytvoření pracovního postupu vývojového diagramu
Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit. V tomto tématu se seznámíte s vytvořením pracovního postupu, který používá předdefinované aktivity, jako je <xref:System.Activities.Statements.Flowchart> aktivita, a vlastní aktivity z předchozího tématu [Postupy: vytvoření aktivity](how-to-create-an-activity.md) . Pracovní postup modeluje číslo odhadující hru.  
  
> [!NOTE]
> Každé téma v kurzu Začínáme závisí na předchozích tématech. Chcete-li dokončit toto téma, je nutné nejprve dokončit [Postupy: vytvoření aktivity](how-to-create-an-activity.md).  
  
> [!NOTE]
> Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>Vytvoření pracovního postupu  
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowActivities** a vyberte **Přidat**, **Nová položka**.  
  
2. V uzlu **nainstalované**, **běžné položky** vyberte **pracovní postup**. V seznamu **pracovních postupů** vyberte **aktivita** .  
  
3. `FlowchartNumberGuessWorkflow`Do pole **název** zadejte a klikněte na **Přidat**.  
  
4. Přetáhněte aktivitu **vývojového diagramu** z oddílu **vývojového diagramu** na **panel nástrojů** a přetáhněte ji na popisek **aktivity** na návrhovou plochu pracovního postupu.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Postup vytvoření proměnných a argumentů pracovního postupu  
  
1. Dvojím kliknutím na **FlowchartNumberGuessWorkflow. XAML** v **Průzkumník řešení** zobrazíte pracovní postup v návrháři, pokud ještě není zobrazený.  
  
2. Kliknutím na **argumenty** v levé dolní části návrháře pracovních postupů zobrazíte podokno **argumenty** .  
  
3. Klikněte na **vytvořit argument**.  
  
4. `MaxNumber`Do pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v vyberte v** rozevíracím seznamu **typ argumentu** možnost **Int32** a potom stiskněte klávesu ENTER a argument uložte.  
  
5. Klikněte na **vytvořit argument**.  
  
6. `Turns`Do pole **název** , které se nachází pod nově přidaným `MaxNumber` argumentem, vyberte **out** v rozevíracím seznamu **směr** , v rozevíracím seznamu **typ argumentu** vyberte **Int32** a potom stiskněte klávesu ENTER.  
  
7. Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .  
  
8. Kliknutím na **proměnné** v levém dolním rohu návrháře pracovních postupů zobrazíte podokno **proměnné** .  
  
9. Klikněte na **vytvořit proměnnou**.  
  
    > [!TIP]
    > Pokud se nezobrazí žádné pole **vytvořit proměnnou** , klikněte na <xref:System.Activities.Statements.Flowchart> aktivitu na ploše návrháře pracovního postupu a vyberte ji.  
  
10. `Guess`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.  
  
11. Klikněte na **vytvořit proměnnou**.  
  
12. `Target`Do pole **název** zadejte, v rozevíracím seznamu **typ proměnné** vyberte **Int32** a pak stisknutím klávesy ENTER uložte proměnnou.  
  
13. Kliknutím na **proměnné** v levém dolním rohu návrháře aktivit zavřete podokno **proměnné** .  
  
### <a name="to-add-the-workflow-activities"></a>Přidání aktivit pracovního postupu  
  
1. Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a umístěte ji na **spouštěcí** uzel, který je v horní části vývojového diagramu. Pokud je aktivita **přiřazení** nad **počátečním** uzlem, zobrazí se kolem **počátečního** uzlu tři trojúhelníky. Přetáhněte aktivitu **přiřazení** na trojúhelník, který je přímo pod **počátečním** uzlem. Tato akce spojí dvě položky dohromady a určí aktivitu **přiřazení** jako první aktivitu ve vývojovém diagramu.  
  
    > [!NOTE]
    > Aktivity můžete v pracovním postupu uvést také jako počáteční aktivitu, a to tak, že je ručně propojíte aktivitu s počátečním uzlem. Provedete to tak, že najedete myší na **spouštěcí** uzel, kliknete na jeden z obdélníků, který se zobrazí, když je ukazatel myši nad **spouštěcím** uzlem, a přetáhnete spojovací čáru dolů na požadovanou aktivitu a umístíte ji na jeden z obdélníků, které se zobrazí. Aktivitu můžete také označit jako počáteční aktivitu tak, že na ni kliknete pravým tlačítkem myši a zvolíte **nastavit jako spouštěcí uzel**.  
  
2. Do `Target` pole **do** vložte a následující výraz zadejte do **výrazu zadejte výraz jazyka C#** nebo **Zadejte pole výrazu VB** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .  
  
3. Přetáhněte aktivitu **prompt** z části **NumberGuessWorkflowActivities** na **panelu nástrojů**, přetáhněte ji pod aktivitu **přiřazení** z předchozího kroku a připojte aktivitu **výzvy** k aktivitě **přiřazení** . Existují tři způsoby, jak propojit dvě aktivity. Prvním způsobem je připojení při vyřazení aktivity s **výzvou** v pracovním postupu. Při přetahování aktivity **výzvy** k pracovnímu postupu umístěte ukazatel myši na aktivitu **přiřadit** a přetáhněte ji na jeden ze čtyř trojúhelníků, který se zobrazí, když je aktivita **výzvy** nad aktivitou **přiřazení** . Druhým způsobem je vyřadit aktivitu **výzvy** do pracovního postupu v požadovaném umístění. Pak najeďte myší na aktivitu **přiřazení** a přetáhněte jeden z obdélníků, který se zobrazí v poli pro činnost **výzvy** . Přetáhněte myš, aby se propojovací čára z aktivity **přiřazení** připojovala k jednomu z obdélníků aktivity **výzvy** , a pak uvolněte tlačítko myši. Třetí způsob se velmi podobá prvnímu, s tím rozdílem, že místo přetažení aktivity **výzvy** ze **sady nástrojů**ho přetáhnete z jeho umístění na návrhové ploše pracovního postupu, najeďte myší nad aktivitu **přiřadit** a umístěte ho na jeden ze zobrazených trojúhelníků.  
  
4. V **okně Vlastnosti** aktivity **výzvy** zadejte `"EnterGuess"` do pole hodnota vlastnosti **Bookmark** text včetně uvozovek. `Guess`Do pole hodnota vlastnosti **výsledek** zadejte a do pole vlastnost **text** zadejte následující výraz.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .  
  
5. Přetáhněte aktivitu **přiřazení** z oddílu **Primitivs** v **sadě nástrojů** a připojte ji pomocí jedné z metod popsaných v předchozím kroku, aby se **zobrazila** pod aktivitou výzvy.  
  
6. Do `Turns` pole **do** zadejte do a vložte `Turns + 1` **výraz jazyka C#** nebo zadejte pole **výrazu VB** .  
  
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
  
10. Přetáhněte dvě aktivity **WriteLine** z části **primitiva** v **sadě nástrojů** a přetáhněte je tak, aby byly vedle sebe pod dvěma **použitím objektu FlowDecision** aktivitami. Připojte **skutečnou** akci nejnižší aktivity **použitím objektu FlowDecision** k aktivitě **WriteLine** a nejvíce vlevo a akci **false** u aktivity napravo napravo. **WriteLine**  
  
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
  
1. Stisknutím kláves CTRL+SHIFT+B řešení sestavíte.  
  
     Pokyny ke spuštění pracovního postupu najdete v dalším tématu [Postup: spuštění pracovního postupu](how-to-run-a-workflow.md). Pokud jste již dokončili [Postup: spuštění kroku pracovního postupu](how-to-run-a-workflow.md) s jiným stylem pracovního postupu a chcete jej spustit pomocí pracovního postupu vývojového diagramu z tohoto kroku, přeskočte dopředu na [sestavení a spusťte aplikaci v](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) tématu [Postupy: spuštění pracovního postupu](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programování Windows Workflow Foundation](programming.md)
- [Návrh pracovních postupů](designing-workflows.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvoření aktivity](how-to-create-an-activity.md)
- [Postupy: Spuštění pracovního postupu](how-to-run-a-workflow.md)
