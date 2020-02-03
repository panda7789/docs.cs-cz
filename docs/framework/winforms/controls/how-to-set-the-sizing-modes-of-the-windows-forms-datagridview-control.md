---
title: Nastavení režimů změny velikosti ovládacího prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738402"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="b2982-102">Postupy: Nastavení režimů změny velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b2982-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b2982-103">Následující postupy ukazují některé běžné scénáře, které přizpůsobují nebo kombinují možnosti změny velikosti dostupné pro ovládací prvek <xref:System.Windows.Forms.DataGridView> a pro konkrétní sloupce v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="b2982-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="b2982-104">Vytvoření sloupce s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="b2982-104">To create a fixed-width column</span></span>  
  
- <span data-ttu-id="b2982-105">Vlastnost <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> nastavte na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, vlastnost <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> na <xref:System.Windows.Forms.DataGridViewTriState.False>, vlastnost <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> na `true`a vlastnost <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2982-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="b2982-106">Vytvoření sloupce, který upraví jeho velikost tak, aby odpovídal jeho obsahu</span><span class="sxs-lookup"><span data-stu-id="b2982-106">To create a column that adjusts its size to fit its content</span></span>  
  
- <span data-ttu-id="b2982-107">Vlastnost <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> nastavte na režim změny velikosti podle obsahu.</span><span class="sxs-lookup"><span data-stu-id="b2982-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="b2982-108">Vytvoření sloupců v režimu výplně pro hodnoty různé velikosti a důležitosti</span><span class="sxs-lookup"><span data-stu-id="b2982-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
- <span data-ttu-id="b2982-109">Nastavte vlastnost <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> pro nastavení režimu změny velikosti pro všechny sloupce, které nepřepisují tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2982-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="b2982-110">Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> sloupců na hodnoty, které jsou úměrné jejich průměrné šířce obsahu.</span><span class="sxs-lookup"><span data-stu-id="b2982-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="b2982-111">Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> důležitých sloupců, aby se zajistilo částečné zobrazení obsahu.</span><span class="sxs-lookup"><span data-stu-id="b2982-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="b2982-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2982-112">Example</span></span>  
 <span data-ttu-id="b2982-113">Následující příklad kompletního kódu poskytuje ukázkovou aplikaci, která vám pomůže pochopit možnosti změny velikosti popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="b2982-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="b2982-114">Chcete-li použít tuto ukázkovou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="b2982-114">To use this demonstration application:</span></span>  
  
- <span data-ttu-id="b2982-115">Změňte velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="b2982-115">Change the size of the form.</span></span> <span data-ttu-id="b2982-116">Sledujte, jak se sloupce v režimu výplně mění na šířku a přitom zachovávají poměry označené hodnotami <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="b2982-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="b2982-117">V případě, že je formulář příliš malý, sledujte, jak se <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> sloupce zabrání v změně.</span><span class="sxs-lookup"><span data-stu-id="b2982-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
- <span data-ttu-id="b2982-118">Změňte velikost sloupců přetažením oddělovačů sloupců pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="b2982-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="b2982-119">Sledujte, jak se u některých sloupců nedá změnit velikost, a jak se sloupce s možností změny velikosti nedají zúžit, než jaká je jejich minimální šířka.</span><span class="sxs-lookup"><span data-stu-id="b2982-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2982-120">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b2982-120">Compiling the Code</span></span>  
 <span data-ttu-id="b2982-121">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b2982-121">This example requires:</span></span>  
  
- <span data-ttu-id="b2982-122">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="b2982-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2982-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2982-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
