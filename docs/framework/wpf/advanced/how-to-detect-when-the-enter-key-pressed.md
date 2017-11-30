---
title: "Postupy: Detekce stisknuté klávesy Enter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8311083b4b82d4ab4827e8d0a2cf958c67347014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="7e4e0-102">Postupy: Detekce stisknuté klávesy Enter</span><span class="sxs-lookup"><span data-stu-id="7e4e0-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="7e4e0-103">Tento příklad ukazuje, jak zjistit, kdy <xref:System.Windows.Input.Key.Enter> není stisknuta klávesa na klávesnici.</span><span class="sxs-lookup"><span data-stu-id="7e4e0-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="7e4e0-104">V tomto příkladu se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a soubor kódu.</span><span class="sxs-lookup"><span data-stu-id="7e4e0-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e4e0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e4e0-105">Example</span></span>  
 <span data-ttu-id="7e4e0-106">Když uživatel stiskne <xref:System.Windows.Input.Key.Enter> klíče v <xref:System.Windows.Controls.TextBox>, vstup v textovém poli se zobrazí v jiné oblasti [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e4e0-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="7e4e0-107">Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá z <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock>a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7e4e0-107">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="7e4e0-108">Následující kód vytvoří <xref:System.Windows.UIElement.KeyDown> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7e4e0-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="7e4e0-109">Pokud je klíč, který je stisknutí <xref:System.Windows.Input.Key.Enter> klíče, zobrazí se zpráva v <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="7e4e0-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="7e4e0-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e4e0-110">See Also</span></span>  
 [<span data-ttu-id="7e4e0-111">Vstupní – přehled</span><span class="sxs-lookup"><span data-stu-id="7e4e0-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="7e4e0-112">Přehled směrované události</span><span class="sxs-lookup"><span data-stu-id="7e4e0-112">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
