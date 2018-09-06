---
title: 'Postupy: vytvoření aktivity'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: deb1b6ca5c6fc996a015e32dd5e0c7b9bd6530fa
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867878"
---
# <a name="how-to-create-an-activity"></a>Postupy: vytvoření aktivity
Aktivity jsou základní jednotka chování v [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Je možné implementovat logiku spouštění aktivity ve spravovaném kódu nebo se dá implementovat pomocí další aktivity. Toto téma ukazuje, jak vytvořit dvě aktivity. První aktivita je jednoduchá aktivita, která používá kód implementovat logiku jeho spuštění. Implementace druhou aktivitu se definuje pomocí další aktivity. Tyto aktivity se používají v následujících krocích v tomto kurzu.  
  
> [!NOTE]
>  Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-activity-library-project"></a>Vytvoření projektu knihovny aktivit  
  
1.  Otevřít [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a zvolte **nový**, **projektu** z **souboru** nabídky.  
  
2.  Rozbalte **ostatní typy projektů** uzlu **nainstalováno**, **šablony** seznam a vyberte **řešení sady Visual Studio**.  
  
3.  Vyberte **prázdné řešení** z **řešení sady Visual Studio** seznamu. Ujistěte se, že **rozhraní .NET Framework 4.5** je vybrali v rozevíracím seznamu verzi rozhraní .NET Framework. Typ `WF45GettingStartedTutorial` v **název** pole a potom klikněte na tlačítko **OK**.  
  
4.  Klikněte pravým tlačítkem na **WF45GettingStartedTutorial** v **Průzkumníka řešení** a zvolte **přidat**, **nový projekt**.  
  
    > [!TIP]
    >  Pokud **Průzkumníka řešení** okno nezobrazí, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
5.  V **nainstalováno** uzlu, vyberte **Visual C#**, **pracovního postupu** (nebo **jazyka Visual Basic**, **pracovního postupu**). Ujistěte se, že **rozhraní .NET Framework 4.5** výběru v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze rozevíracího seznamu. Vyberte **knihovny aktivit** z **pracovního postupu** seznamu. Typ `NumberGuessWorkflowActivities` v **název** pole a potom klikněte na tlačítko **OK**.  
  
    > [!NOTE]
    >  V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalováno** uzlu.  
  
6.  Klikněte pravým tlačítkem na **Activity1.xaml** v **Průzkumníka řešení** a zvolte **odstranit**. Klikněte na tlačítko **OK** potvrďte.  
  
### <a name="to-create-the-readint-activity"></a>Vytvořit aktivitu readint –  
  
1.  Zvolte **přidat novou položku** z **projektu** nabídky.  
  
2.  V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivita s kódem** z **pracovního postupu** seznamu.  
  
3.  Typ `ReadInt` do **název** pole a potom klikněte na tlačítko **přidat**.  
  
4.  Nahraďte existující `ReadInt` definice s následující definicí.  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` Aktivity je odvozena z <xref:System.Activities.NativeActivity%601> místo <xref:System.Activities.CodeActivity>, což je výchozí hodnota pro kód šablony aktivit. <xref:System.Activities.CodeActivity%601> lze použít, pokud aktivita poskytuje jeden výsledek, který je zveřejněný prostřednictvím <xref:System.Activities.Activity%601.Result%2A> argument, ale <xref:System.Activities.CodeActivity%601> nepodporuje používání záložek, takže <xref:System.Activities.NativeActivity%601> se používá.  
  
### <a name="to-create-the-prompt-activity"></a>Vytvořit aktivitu příkazový řádek  
  
1.  Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B. Vytváření projektu umožňuje `ReadInt` aktivity v tomto projektu, který se má použít k vytvoření vlastní aktivity v tomto kroku.  
  
2.  Zvolte **přidat novou položku** z **projektu** nabídky.  
  
3.  V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivity** z **pracovního postupu** seznamu.  
  
4.  Typ `Prompt` do **název** pole a potom klikněte na tlačítko **přidat**.  
  
5.  Dvakrát klikněte na panel **Prompt.xaml** v **Průzkumníka řešení** se zobrazí v návrháři, pokud je už se nezobrazí.  
  
6.  Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit zobrazíte **argumenty** podokně.  
  
7.  Klikněte na tlačítko **vytvořit Argument**.  
  
8.  Typ `BookmarkName` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.  
  
9. Klikněte na tlačítko **vytvořit Argument**.  
  
10. Typ `Result` do **název** pole, které se nachází pod nově přidaný `BookmarkName` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte možnost **Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.  
  
11. Klikněte na tlačítko **vytvořit Argument**.  
  
12. Typ `Text` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.  
  
     Tyto tři argumenty, které jsou vázány na odpovídající argument <xref:System.Activities.Statements.WriteLine> a `ReadInt` aktivity, které jsou přidány do `Prompt` aktivity v následujících krocích.  
  
13. Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.  
  
14. Přetáhněte **pořadí** aktivita z **tok řízení** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek **Výzvy** návrháře aktivit.  
  
    > [!TIP]
    >  Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.  
  
15. Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek **Pořadí** aktivity.  
  
16. Vytvoření vazby **Text** argument **WriteLine** aktivitu **Text** argument **výzvy** aktivitu tak, že zadáte `Text` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole **vlastnosti** okno a poté stiskněte klávesu KARTĚ klíč dvakrát. Tím zavře okno technologie IntelliSense seznam členů a uloží hodnotu vlastnosti přesunutím výběr vypnout vlastnost. Tuto vlastnost můžete nastavit také tak, že zadáte `Text` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole přímo na aktivitu.  
  
    > [!TIP]
    >  Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.  
  
17. Přetáhněte **readint –** aktivita z **NumberGuessWorkflowActivities** část **nástrojů** a umístěte jej do **pořadí** aktivitu tak, že následuje **WriteLine** aktivity.  
  
18. Vytvoření vazby **BookmarkName** argument **readint –** aktivitu **BookmarkName** argument **výzvy** aktivitu tak, že zadáte `BookmarkName` do **zadejte výraz jazyka VB.** políčka napravo od **BookmarkName** argumentu **okno Vlastnosti**a stiskněte klávesu TAB dvě časový limit zavřete okno technologie IntelliSense seznam členů a uložte vlastnosti.  
  
19. Vytvoření vazby **výsledek** argument **readint –** aktivitu **výsledek** argument **výzvy** aktivitu tak, že zadáte `Result` do **zadejte výraz jazyka VB.** políčka napravo od **výsledek** argumentu **okno vlastností**a potom stiskněte klávesu Tabulátor dvakrát.  
  
20. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
     Pokyny k vytvoření pracovního postupu pomocí těchto aktivit naleznete v části Další krok v tomto kurzu [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [Návrh a implementace vlastních aktivit](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [Kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Postupy: Vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Použití ExpressionTextBox v návrháři vlastní aktivity](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
