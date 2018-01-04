---
title: "Postupy: Vytváření rozšíření pomocí prvku ScrollViewer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2066ccce28138cfecf4e0b4574d45783a9ba4ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="d9416-102">Postupy: Vytváření rozšíření pomocí prvku ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="d9416-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="d9416-103">Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander> ovládací prvek, který obsahuje komplexní obsah, například bitové kopie a text.</span><span class="sxs-lookup"><span data-stu-id="d9416-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="d9416-104">Tento příklad také zvýrazněna obsah <xref:System.Windows.Controls.Expander> v <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9416-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9416-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9416-105">Example</span></span>  
 <span data-ttu-id="d9416-106">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="d9416-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="d9416-107">V příkladu se používá <xref:System.Windows.Controls.Primitives.BulletDecorator> ovládací prvek, který obsahuje bitovou kopii a text, aby bylo možné definovat <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9416-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="d9416-108">A <xref:System.Windows.Controls.ScrollViewer> řízení poskytuje metodu pro posouvání rozšířené obsah.</span><span class="sxs-lookup"><span data-stu-id="d9416-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="d9416-109">Všimněte si, že v příkladu je nastaven <xref:System.Windows.FrameworkElement.Height%2A> vlastnost <xref:System.Windows.Controls.ScrollViewer> místo na obsah.</span><span class="sxs-lookup"><span data-stu-id="d9416-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="d9416-110">Pokud <xref:System.Windows.FrameworkElement.Height%2A> je nastavený na obsah, <xref:System.Windows.Controls.ScrollViewer> neumožňuje uživateli posuňte se k obsahu.</span><span class="sxs-lookup"><span data-stu-id="d9416-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="d9416-111"><xref:System.Windows.FrameworkElement.Width%2A> Je nastavena na <xref:System.Windows.Controls.Expander> řízení a toto nastavení se vztahuje na <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a rozšířená obsah.</span><span class="sxs-lookup"><span data-stu-id="d9416-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="d9416-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9416-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="d9416-113">Přehled rozšíření</span><span class="sxs-lookup"><span data-stu-id="d9416-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="d9416-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="d9416-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
