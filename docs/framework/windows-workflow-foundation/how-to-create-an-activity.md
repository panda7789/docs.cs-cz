---
title: 'Postupy: Vytvoření aktivity'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 48df9b90a92468858bd3ac5498bd83fd0d57fe75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009796"
---
# <a name="how-to-create-an-activity"></a>Postupy: Vytvoření aktivity

Aktivity jsou základní jednotka chování v [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Je možné implementovat logiku spouštění aktivity ve spravovaném kódu nebo se dá implementovat pomocí další aktivity. Toto téma ukazuje, jak vytvořit dvě aktivity. První aktivita je jednoduchá aktivita, která používá kód implementovat logiku jeho spuštění. Implementace druhou aktivitu se definuje pomocí další aktivity. Tyto aktivity se používají v následujících krocích v tomto kurzu.

> [!NOTE]
> Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="create-the-activity-library-project"></a>Vytvořte projekt knihovny aktivit

1. Otevřít Visual Studio a zvolte **nový** > **projektu** z **souboru** nabídky.

2. V **nový projekt** dialogového okna, v části **nainstalováno** vyberte **Visual C#** > **pracovního postupu** (nebo **Jazyka Visual Basic** > **pracovního postupu**).

    > [!NOTE]
    > Pokud se nezobrazí **pracovního postupu** kategorii šablon, budete muset nainstalovat **Windows Workflow Foundation** komponentu sady Visual Studio. Zvolte **otevřít instalační program Visual Studio** odkazu na levé straně **nový projekt** dialogového okna. V instalačním programu Visual Studio, vyberte **jednotlivé komponenty** kartu. Potom v části **vývojových aktivit** kategorii, vyberte **Windows Workflow Foundation** komponenty. Zvolte **změnit** pro instalaci součásti.

3. Vyberte **knihovny aktivit** šablony projektu. Typ `NumberGuessWorkflowActivities` v **název** pole a potom klikněte na tlačítko **OK**.

4. Klikněte pravým tlačítkem na **Activity1.xaml** v **Průzkumníka řešení** a zvolte **odstranit**. Klikněte na tlačítko **OK** potvrďte.

## <a name="create-the-readint-activity"></a>Vytvořit aktivitu readint –

1. Zvolte **přidat novou položku** z **projektu** nabídky.

2. V **nainstalováno** > **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivita s kódem** z **pracovního postupu** seznamu.

3. Typ `ReadInt` do **název** pole a potom klikněte na tlačítko **přidat**.

4. Nahraďte existující `ReadInt` definice s následující definicí.

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > `ReadInt` Aktivity je odvozena z <xref:System.Activities.NativeActivity%601> místo <xref:System.Activities.CodeActivity>, což je výchozí hodnota pro kód šablony aktivit. <xref:System.Activities.CodeActivity%601> lze použít, pokud aktivita poskytuje jeden výsledek, který je zveřejněný prostřednictvím <xref:System.Activities.Activity%601.Result%2A> argument, ale <xref:System.Activities.CodeActivity%601> nepodporuje používání záložek, takže <xref:System.Activities.NativeActivity%601> se používá.

## <a name="create-the-prompt-activity"></a>Vytvořit aktivitu příkazový řádek

1. Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení projektu. Vytváření projektu umožňuje `ReadInt` aktivity v tomto projektu, který se má použít k vytvoření vlastní aktivity v tomto kroku.

2. Zvolte **přidat novou položku** z **projektu** nabídky.

3. V **nainstalováno** > **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivity** z **pracovního postupu** seznamu.

4. Typ `Prompt` do **název** pole a potom klikněte na tlačítko **přidat**.

5. Dvakrát klikněte na panel **Prompt.xaml** v **Průzkumníka řešení** se zobrazí v návrháři, pokud je už se nezobrazí.

6. Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit zobrazíte **argumenty** podokně.

7. Klikněte na tlačítko **vytvořit Argument**.

8. Typ `BookmarkName` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a poté stiskněte klávesu **Enter** uložit argument.

9. Klikněte na tlačítko **vytvořit Argument**.

10. Typ `Result` do **název** pole, které se nachází pod nově přidaný `BookmarkName` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte možnost **Int32** z **typ argumentu** rozevíracího seznamu a poté stiskněte klávesu **Enter**.

11. Klikněte na tlačítko **vytvořit Argument**.

12. Typ `Text` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a poté stiskněte klávesu **Enter** uložit argument.

     Tyto tři argumenty, které jsou vázány na odpovídající argument <xref:System.Activities.Statements.WriteLine> a `ReadInt` aktivity, které jsou přidány do `Prompt` aktivity v následujících krocích.

13. Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.

14. Přetáhněte **pořadí** aktivita z **tok řízení** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek **Výzvy** návrháře aktivit.

    > [!TIP]
    > Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.

15. Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek **Pořadí** aktivity.

16. Vytvoření vazby **Text** argument **WriteLine** aktivitu **Text** argument **výzvy** aktivitu tak, že zadáte `Text` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole **vlastnosti** okno a poté stiskněte klávesu **kartu** klíč dvakrát. Tím zavře okno technologie IntelliSense seznam členů a uloží hodnotu vlastnosti přesunutím výběr vypnout vlastnost. Tuto vlastnost můžete nastavit také tak, že zadáte `Text` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole přímo na aktivitu.

    > [!TIP]
    > Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.

17. Přetáhněte **readint –** aktivita z **NumberGuessWorkflowActivities** část **nástrojů** a umístěte jej do **pořadí** aktivitu tak, že následuje **WriteLine** aktivity.

18. Vytvoření vazby **BookmarkName** argument **readint –** aktivitu **BookmarkName** argument **výzvy** aktivitu tak, že zadáte `BookmarkName` do **zadejte výraz jazyka VB.** políčka napravo od **BookmarkName** argumentu **okno vlastností**a potom stiskněte klávesu **Kartu** klíč dvakrát zavřete okno technologie IntelliSense seznam členů a uložte vlastnosti.

19. Vytvoření vazby **výsledek** argument **readint –** aktivitu **výsledek** argument **výzvy** aktivitu tak, že zadáte `Result` do **zadejte výraz jazyka VB.** políčka napravo od **výsledek** argumentu **okno vlastností**a potom stiskněte klávesu **kartu** klíč dvakrát.

20. Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení řešení.

## <a name="next-steps"></a>Další kroky

Pokyny k vytvoření pracovního postupu pomocí těchto aktivit naleznete v části Další krok v tomto kurzu [jak: Vytvoření pracovního postupu](how-to-create-a-workflow.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [Návrh a implementace vlastních aktivit](designing-and-implementing-custom-activities.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Postupy: Vytvoření pracovního postupu](how-to-create-a-workflow.md)
- [Použití ExpressionTextBox v návrháři vlastní aktivity](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)