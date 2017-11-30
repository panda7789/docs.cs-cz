---
title: "Postupy: vytvoření aktivity"
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
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: "39"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b52daa513bad9d0cb05fcabb27ff5755f8dba2a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-activity"></a>Postupy: vytvoření aktivity
Aktivity jsou core jednotky chování v [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Logika spuštění aktivity můžete implementují ve spravovaném kódu nebo se dá implementovat pomocí jiné aktivity. Toto téma ukazuje, jak vytvořit dvě aktivity. První aktivita je jednoduchý aktivity, která používá kód k implementaci jeho logiku spouštění. Implementace druhá aktivita je definována pomocí jiné aktivity. Tyto aktivity se používají v následující kroky v tomto kurzu.  
  
> [!NOTE]
>  Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-activity-library-project"></a>Vytvoření projektu knihovny aktivit  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a zvolte **nový**, **projektu** z **souboru** nabídky.  
  
2.  Rozbalte položku **jiné typy projektů** uzlu **nainstalovaná**, **šablony** seznam a vyberte **řešení sady Visual Studio**.  
  
3.  Vyberte **prázdného řešení** z **řešení sady Visual Studio** seznamu. Ujistěte se, že **rozhraní .NET Framework 4.5** je vybraný v rozevíracím seznamu verze rozhraní .NET Framework. Typ `WF45GettingStartedTutorial` v **název** pole a pak klikněte na **OK**.  
  
4.  Klikněte pravým tlačítkem na **WF45GettingStartedTutorial** v **Průzkumníku řešení** a zvolte **přidat**, **nový projekt**.  
  
    > [!TIP]
    >  Pokud **Průzkumníku řešení** se nezobrazí okno, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
5.  V **nainstalovaná** uzlu, vyberte **Visual C#**, **pracovního postupu** (nebo **jazyka Visual Basic**, **pracovního postupu**). Ujistěte se, že **rozhraní .NET Framework 4.5** vybrán [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze rozevíracího seznamu. Vyberte **knihovna aktivit** z **pracovního postupu** seznamu. Typ `NumberGuessWorkflowActivities` v **název** pole a pak klikněte na **OK**.  
  
    > [!NOTE]
    >  V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky**uzlu **nainstalovaná** uzlu.  
  
6.  Klikněte pravým tlačítkem na **Activity1.xaml** v **Průzkumníku řešení** a zvolte **odstranit**. Klikněte na tlačítko **OK** k potvrzení.  
  
### <a name="to-create-the-readint-activity"></a>Chcete-li vytvořit readint – aktivity  
  
1.  Zvolte **přidat novou položku** z **projektu** nabídky.  
  
2.  V **nainstalovaná**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **kód aktivity** z **pracovního postupu** seznamu.  
  
3.  Typ `ReadInt` do **název** pole a pak klikněte na **přidat**.  
  
4.  Nahradit existující `ReadInt` definice s následující definice.  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` Aktivity je odvozena z <xref:System.Activities.NativeActivity%601> místo <xref:System.Activities.CodeActivity>, což je výchozí nastavení pro šablony aktivit kódu. <xref:System.Activities.CodeActivity%601>lze použít, pokud aktivita poskytuje jeden výsledek, který je k dispozici prostřednictvím <xref:System.Activities.Activity%601.Result%2A> argument, ale <xref:System.Activities.CodeActivity%601> nepodporuje použití záložek, takže <xref:System.Activities.NativeActivity%601> se používá.  
  
### <a name="to-create-the-prompt-activity"></a>Chcete-li vytvořit výzva aktivity  
  
1.  Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B. Sestavení projektu umožňuje `ReadInt` aktivity v tomto projektu, který se má použít k vytvoření vlastní aktivity z tohoto kroku.  
  
2.  Zvolte **přidat novou položku** z **projektu** nabídky.  
  
3.  V **nainstalovaná**, **společné položky** uzlu, vyberte **pracovního postupu**. Vyberte **aktivity** z **pracovního postupu** seznamu.  
  
4.  Typ `Prompt` do **název** pole a pak klikněte na **přidat**.  
  
5.  Klikněte dvakrát na **Prompt.xaml** v **Průzkumníku řešení** k zobrazení v návrháři, pokud již není zobrazen.  
  
6.  Klikněte na tlačítko **argumenty** v levém dolním straně Návrhář aktivity zobrazíte **argumenty** podokně.  
  
7.  Klikněte na tlačítko **vytvořit Argument**.  
  
8.  Typ `BookmarkName` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení argument.  
  
9. Klikněte na tlačítko **vytvořit Argument**.  
  
10. Typ `Result` do **název** pole, které je pod nově přidaný `BookmarkName` argument, vyberte **Out** z **směr** rozevíracího seznamu, vyberte možnost **Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.  
  
11. Klikněte na tlačítko **vytvořit Argument**.  
  
12. Typ `Text` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER pro uložení argument.  
  
     Tyto tři argumenty je vázána na odpovídající argumenty <xref:System.Activities.Statements.WriteLine> a `ReadInt` aktivity, které jsou přidány do `Prompt` aktivity v následujících krocích.  
  
13. Klikněte na tlačítko **argumenty** v levém dolním straně Návrhář aktivity zavřete **argumenty** podokně.  
  
14. Přetáhněte **pořadí** aktivity z **tok řízení** části **sada nástrojů** a umístěte jej do **aktivity sem umístěte** popisek **Výzva** Návrhář aktivity.  
  
    > [!TIP]
    >  Pokud **sada nástrojů** se nezobrazí okno, vyberte **sada nástrojů** z **zobrazení** nabídky.  
  
15. Přetáhněte **WriteLine** aktivity z **primitiv** části **sada nástrojů** a umístěte jej do **aktivity sem umístěte** popisek **Pořadí** aktivity.  
  
16. Vytvoření vazby **Text** argument **WriteLine** aktivitu **Text** argument **výzva** aktivity zadáním `Text` do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole **vlastnosti** okna a potom stiskněte klávesu na KARTĚ klíče dvakrát. To se zavře okno technologie IntelliSense seznam členů a uloží hodnotu vlastnosti přesunutím výběr vypnout vlastnost. Tuto vlastnost lze také nastavit tak, že zadáte `Text` do **zadejte výraz jazyka C#** nebo **zadejte výraz VB** pole na aktivity sám sebe.  
  
    > [!TIP]
    >  Pokud **vlastnosti – okno** není zobrazený, vyberte **vlastnosti – okno** z **zobrazení** nabídky.  
  
17. Přetažení **readint –** aktivity z **NumberGuessWorkflowActivities** části **sada nástrojů** a umístěte jej do **pořadí** aktivity, které se řídí **WriteLine** aktivity.  
  
18. Vytvoření vazby **NázevZáložky** argument **readint –** aktivitu **NázevZáložky** argument **výzva** aktivity zadáním `BookmarkName` do **zadejte výraz VB** pole napravo od **NázevZáložky** argument ve **vlastnosti – okno**a potom stiskněte klávesu Tabulátor dva časový limit uložení vlastnosti a zavřete okno IntelliSense seznam členů.  
  
19. Vytvoření vazby **výsledek** argument **readint –** aktivitu **výsledek** argument **výzva** aktivity zadáním `Result` do **zadejte výraz jazyka Visual Basic** pole napravo od **výsledek** argument **vlastnosti – okno**a potom stiskněte klávesu Tabulátor dvakrát.  
  
20. Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
     Pokyny k vytvoření pracovního postupu pomocí těchto aktivit na další krok v tomto kurzu, najdete v tématu [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [Navrhování a implementace vlastních aktivit](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [Kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Pomocí ExpressionTextBox v Návrháři vlastní aktivity](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
