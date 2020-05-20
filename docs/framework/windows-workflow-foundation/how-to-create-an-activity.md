---
title: 'Postupy: Vytvoření aktivity'
description: 'V tomto článku se dozvíte, jak vytvořit dvě aktivity v modelu Workflow Foundation: jeden, který používá kód k implementaci své logiky a jedno, které je definováno pomocí jiných aktivit.'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: dae099d102b0c85d09a1ef8bcce56e8a9096bd20
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419587"
---
# <a name="how-to-create-an-activity"></a>Postupy: Vytvoření aktivity

Aktivity jsou základní jednotkou chování v [!INCLUDE[wf1](../../../includes/wf1-md.md)] . Logika provádění aktivity může být implementována ve spravovaném kódu nebo může být implementována pomocí jiných aktivit. Toto téma ukazuje, jak vytvořit dvě aktivity. První aktivita je jednoduchá aktivita, která používá kód k implementaci logiky provádění. Implementace druhé aktivity je definována pomocí jiných aktivit. Tyto aktivity se používají v následujících krocích v tomto kurzu.

> [!NOTE]
> Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="create-the-activity-library-project"></a>Vytvoření projektu knihovny aktivit

1. Otevřete Visual Studio a v **New**  >  nabídce **soubor** vyberte nový**projekt** .

2. V dialogovém okně **Nový projekt** v části **nainstalovaná** kategorie vyberte pracovní **postup Visual C#**  >  **Workflow** (nebo **Visual Basic**  >  **pracovní postup**).

    > [!NOTE]
    > Pokud nevidíte kategorii šablony **pracovního postupu** , bude pravděpodobně nutné nainstalovat **programovací model Windows Workflow Foundation** součást sady Visual Studio. Na levé straně dialogového okna **Nový projekt** klikněte na odkaz **otevřít instalační program pro Visual Studio** . V Instalační program pro Visual Studio vyberte kartu **jednotlivé součásti** . Pak v kategorii **vývojové aktivity** vyberte součást **programovací model Windows Workflow Foundation** . Pro instalaci součásti klikněte na tlačítko **Upravit** .

3. Vyberte šablonu projektu **knihovny aktivit** . `NumberGuessWorkflowActivities`Do pole **název** zadejte a klikněte na **OK**.

4. V **Průzkumník řešení** klikněte pravým tlačítkem na **Activity1. XAML** a vyberte **Odstranit**. Potvrďte kliknutím na tlačítko **OK** .

## <a name="create-the-readint-activity"></a>Vytvoření aktivity ReadInt

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku** .

2. V uzlu **nainstalované**  >  **společné položky** vyberte možnost **pracovní postup**. V seznamu **pracovních postupů** vyberte **aktivita kódu** .

3. `ReadInt`Do pole **název** zadejte a klikněte na **Přidat**.

4. Nahraďte stávající `ReadInt` definici následující definicí.

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > `ReadInt`Aktivita je odvozena z <xref:System.Activities.NativeActivity%601> místo <xref:System.Activities.CodeActivity> , což je výchozí hodnota pro šablonu aktivity kódu. <xref:System.Activities.CodeActivity%601>dá se použít, pokud aktivita poskytuje jeden výsledek, který je vystavený přes <xref:System.Activities.Activity%601.Result%2A> argument, ale nepodporuje <xref:System.Activities.CodeActivity%601> použití záložek, takže <xref:System.Activities.NativeActivity%601> se používá.

## <a name="create-the-prompt-activity"></a>Vytvoření aktivity výzvy

1. Stisknutím **kombinace kláves CTRL** + **+ SHIFT** + **B** Sestavte projekt. Sestavování projektu umožňuje, aby se `ReadInt` aktivita v tomto projektu použila k vytvoření vlastní aktivity z tohoto kroku.

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku** .

3. V uzlu **nainstalované**  >  **společné položky** vyberte možnost **pracovní postup**. V seznamu **pracovních postupů** vyberte **aktivita** .

4. `Prompt`Do pole **název** zadejte a klikněte na **Přidat**.

5. Dvojitým kliknutím na položku **prompt. XAML** v **Průzkumník řešení** ji zobrazte v návrháři, pokud ještě není zobrazená.

6. Kliknutím na **argumenty** v levé dolní části návrháře aktivit zobrazíte podokno **argumenty** .

7. Klikněte na **vytvořit argument**.

8. `BookmarkName`Do pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v, v** rozevíracím seznamu **typ argumentu** vyberte **řetězec** a potom stiskněte klávesu **ENTER** a argument uložte.

9. Klikněte na **vytvořit argument**.

10. `Result`Do pole **název** , které se nachází pod nově přidaným `BookmarkName` argumentem, vyberte **out** v rozevíracím seznamu **směr** , v rozevíracím seznamu **typ argumentu** vyberte **Int32** a potom stiskněte klávesu **ENTER**.

11. Klikněte na **vytvořit argument**.

12. `Text`Do pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v, v** rozevíracím seznamu **typ argumentu** vyberte **řetězec** a potom stiskněte klávesu **ENTER** a argument uložte.

     Tyto tři argumenty jsou vázány na odpovídající argumenty <xref:System.Activities.Statements.WriteLine> `ReadInt` aktivity a, které jsou přidány k `Prompt` aktivitě v následujících krocích.

13. Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .

14. Přetáhněte aktivitu **sekvence** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do pole Sem přetáhněte **aktivitu** Návrhář aktivity **výzvy** .

    > [!TIP]
    > Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .

15. Přetáhněte aktivitu **WriteLine** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji do pole **drop Activity (odkládací aktivita** ) na popisek aktivity **sekvence** .

16. Navažte argument **textu** aktivity **WriteLine** na **textový** argument aktivity **výzvy** zadáním `Text` do **výrazu zadejte výraz jazyka C#** nebo **Zadejte pole výrazu VB** v okně **vlastnosti** a potom stiskněte klávesu **TAB** dvakrát. Tím se nevynechává okno členové seznamu IntelliSense a uloží hodnotu vlastnosti přesunutím výběru mimo vlastnost. Tuto vlastnost lze také nastavit tak, že zadáte `Text` do **výrazu zadejte výraz jazyka C#** nebo do samotné aktivity **Zadejte pole výrazu VB** .

    > [!TIP]
    > Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .

17. Přetáhněte aktivitu **ReadInt** z oddílu **NumberGuessWorkflowActivities** **panelu nástrojů** a přetáhněte ji do aktivity **sekvence** tak, aby se doprovází aktivity **WriteLine** .

18. Zapojte argument **Bookmark** aktivity **ReadInt** k argumentu **Bookmark** aktivity **výzvy** zadáním `BookmarkName` do pole **Zadejte výraz jazyka VB** vpravo od argumentu **Bookmark** v **okně Vlastnosti**a potom stiskněte klávesu **TAB** dvakrát pro zavření okna členů seznamu a vlastnost uložte.

19. Navažte argument **výsledku** aktivity **ReadInt** na **výsledek** aktivity **výzvy** zadáním `Result` do pole **Zadejte výraz VB** napravo od argumentu **výsledek** v **okně Vlastnosti**a potom stiskněte klávesu **TAB** dvakrát.

20. Stisknutím **kombinace kláves CTRL** + **+ SHIFT** + **B** sestavíte řešení.

## <a name="next-steps"></a>Další kroky

Pokyny k vytvoření pracovního postupu pomocí těchto aktivit najdete v dalším kroku v tomto kurzu [: vytvoření pracovního postupu](how-to-create-a-workflow.md).

## <a name="see-also"></a>Viz také

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [Návrh a implementace vlastních aktivit](designing-and-implementing-custom-activities.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvoření pracovního postupu](how-to-create-a-workflow.md)
- [Použití ExpressionTextBox v návrháři vlastní aktivity](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
