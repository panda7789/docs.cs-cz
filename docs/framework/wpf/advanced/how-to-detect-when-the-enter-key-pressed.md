---
title: 'Postupy: Detekce stisknuté klávesy Enter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004821"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="19fa7-102">Postupy: Detekce stisknuté klávesy Enter</span><span class="sxs-lookup"><span data-stu-id="19fa7-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="19fa7-103">Tento příklad ukazuje, jak zjistit, kdy se na klávesnici stiskne klávesa <xref:System.Windows.Input.Key.Enter>.</span><span class="sxs-lookup"><span data-stu-id="19fa7-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="19fa7-104">Tento příklad se skládá ze souboru [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="19fa7-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19fa7-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="19fa7-105">Example</span></span>  
 <span data-ttu-id="19fa7-106">Když uživatel stiskne v <xref:System.Windows.Controls.TextBox> klíč <xref:System.Windows.Input.Key.Enter>, vstup v textovém poli se zobrazí v jiné oblasti [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19fa7-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="19fa7-107">Následující kód XAML vytvoří uživatelské rozhraní, které se skládá z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="19fa7-107">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="19fa7-108">Následující kód za vytvoří obslužnou rutinu události <xref:System.Windows.UIElement.KeyDown>.</span><span class="sxs-lookup"><span data-stu-id="19fa7-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="19fa7-109">Pokud je Stisknutá klávesa <xref:System.Windows.Input.Key.Enter>, zobrazí se v <xref:System.Windows.Controls.TextBlock> zpráva.</span><span class="sxs-lookup"><span data-stu-id="19fa7-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="19fa7-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19fa7-110">See also</span></span>

- [<span data-ttu-id="19fa7-111">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="19fa7-111">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="19fa7-112">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="19fa7-112">Routed Events Overview</span></span>](routed-events-overview.md)
