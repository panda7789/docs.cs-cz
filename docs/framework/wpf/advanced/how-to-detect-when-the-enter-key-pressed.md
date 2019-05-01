---
title: 'Postupy: Rozpoznat, kdy stisknuté klávesy Enter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a99da5804bbc31897198b9b6d9e21da9f17dfe26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051413"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="f4feb-102">Postupy: Rozpoznat, kdy stisknuté klávesy Enter</span><span class="sxs-lookup"><span data-stu-id="f4feb-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="f4feb-103">Tento příklad ukazuje, jak zjistit, kdy <xref:System.Windows.Input.Key.Enter> stisknutí klávesy na klávesnici.</span><span class="sxs-lookup"><span data-stu-id="f4feb-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="f4feb-104">Tento příklad se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor a soubor kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="f4feb-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4feb-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4feb-105">Example</span></span>  
 <span data-ttu-id="f4feb-106">Když uživatel stiskne klávesu <xref:System.Windows.Input.Key.Enter> klíče v <xref:System.Windows.Controls.TextBox>, vstup v textovém poli se zobrazí v jiné oblasti [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4feb-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="f4feb-107">Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock>a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f4feb-107">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="f4feb-108">Následující kód vytvoří <xref:System.Windows.UIElement.KeyDown> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="f4feb-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="f4feb-109">Pokud je klíč, která byla stisknuta <xref:System.Windows.Input.Key.Enter> klíče, zobrazí se zpráva v <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="f4feb-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="f4feb-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4feb-110">See also</span></span>

- [<span data-ttu-id="f4feb-111">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="f4feb-111">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="f4feb-112">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="f4feb-112">Routed Events Overview</span></span>](routed-events-overview.md)
