---
title: 'Postupy: Detekce stisknuté klávesy Enter'
description: Rozpoznat, kdy je na klávesnici v Windows Presentation Foundation vybraný klávesa ENTER Tento příklad se skládá z XAML a souboru kódu na pozadí.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163182"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="c9614-104">Postupy: Detekce stisknuté klávesy Enter</span><span class="sxs-lookup"><span data-stu-id="c9614-104">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="c9614-105">Tento příklad ukazuje, jak zjistit, kdy se <xref:System.Windows.Input.Key.Enter> klávesa stiskne na klávesnici.</span><span class="sxs-lookup"><span data-stu-id="c9614-105">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="c9614-106">Tento příklad se skládá ze [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru a souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="c9614-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9614-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9614-107">Example</span></span>  
 <span data-ttu-id="c9614-108">Když uživatel stiskne klávesu <xref:System.Windows.Input.Key.Enter> v <xref:System.Windows.Controls.TextBox> , zobrazí se vstup v textovém poli v jiné oblasti [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c9614-108">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="c9614-109">Následující kód XAML vytvoří uživatelské rozhraní, které se skládá z typu <xref:System.Windows.Controls.StackPanel> , a <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="c9614-109">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="c9614-110">Následující kód na pozadí vytvoří <xref:System.Windows.UIElement.KeyDown> obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="c9614-110">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="c9614-111">Pokud klávesa, která se stiskne <xref:System.Windows.Input.Key.Enter> , je klíč, zobrazí se zpráva v <xref:System.Windows.Controls.TextBlock> .</span><span class="sxs-lookup"><span data-stu-id="c9614-111">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="c9614-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9614-112">See also</span></span>

- [<span data-ttu-id="c9614-113">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="c9614-113">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="c9614-114">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="c9614-114">Routed Events Overview</span></span>](routed-events-overview.md)
