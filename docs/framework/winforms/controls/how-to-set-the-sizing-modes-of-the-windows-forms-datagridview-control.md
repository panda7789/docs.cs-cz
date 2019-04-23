---
title: 'Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: d92322da6644c110f5e3177acebea62799a0ed89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977870"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="b566e-102">Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b566e-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b566e-103">Následující postupy ukazují některé běžné scénáře, které přizpůsobit nebo můžete zkombinovat k dispozici pro nastavení velikosti možností <xref:System.Windows.Forms.DataGridView> ovládacího prvku a pro konkrétní sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="b566e-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="b566e-104">Chcete-li vytvořit sloupec pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="b566e-104">To create a fixed-width column</span></span>  
  
-   <span data-ttu-id="b566e-105">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> vlastnost <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost `true`a <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b566e-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="b566e-106">Chcete-li vytvořit sloupec, který upraví jeho velikost podle jeho obsahu</span><span class="sxs-lookup"><span data-stu-id="b566e-106">To create a column that adjusts its size to fit its content</span></span>  
  
-   <span data-ttu-id="b566e-107">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> vlastnosti k určení velikosti na základě obsahu režimu.</span><span class="sxs-lookup"><span data-stu-id="b566e-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="b566e-108">Chcete-li vytvořit režim vyplnění sloupce pro hodnoty různých velikostí a význam</span><span class="sxs-lookup"><span data-stu-id="b566e-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
-   <span data-ttu-id="b566e-109">Nastavte <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> nastavit režim změny velikosti pro všechny sloupce, které nepřepisují tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b566e-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="b566e-110">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> šířku obsahu vlastnosti sloupce se mají hodnoty, které jsou přímo úměrná jejich průměr.</span><span class="sxs-lookup"><span data-stu-id="b566e-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="b566e-111">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> vlastnosti sloupců důležité k zajištění částečné zobrazení obsahu.</span><span class="sxs-lookup"><span data-stu-id="b566e-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="b566e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b566e-112">Example</span></span>  
 <span data-ttu-id="b566e-113">Následující příklad kompletní kód poskytuje ukázkové aplikace, která vám pomůžou pochopit nastavení velikosti možností popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="b566e-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="b566e-114">Použití této ukázkové aplikaci:</span><span class="sxs-lookup"><span data-stu-id="b566e-114">To use this demonstration application:</span></span>  
  
-   <span data-ttu-id="b566e-115">Změňte velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="b566e-115">Change the size of the form.</span></span> <span data-ttu-id="b566e-116">Sledujte, jak změnit režim vyplnění sloupce jejich šířky při zachování rozměry indikován <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="b566e-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="b566e-117">Podívejte se jak sloupce <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> brání jeho změnu, když je formulář příliš malá.</span><span class="sxs-lookup"><span data-stu-id="b566e-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
-   <span data-ttu-id="b566e-118">Změníte velikost sloupce přetažením oddělovače sloupců pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="b566e-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="b566e-119">Sledujte, jak nemůže být některé sloupce, jehož velikost byla změněna a jak umožňující změnu velikosti sloupců nelze nastavit užší než jeho minimální šířku.</span><span class="sxs-lookup"><span data-stu-id="b566e-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b566e-120">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b566e-120">Compiling the Code</span></span>  
 <span data-ttu-id="b566e-121">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b566e-121">This example requires:</span></span>  
  
-   <span data-ttu-id="b566e-122">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b566e-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b566e-123">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b566e-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b566e-124">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="b566e-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b566e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b566e-125">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
