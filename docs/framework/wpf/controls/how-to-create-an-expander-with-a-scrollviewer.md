---
title: 'Postupy: Vytvoření rozšíření pomocí prvku ScrollViewer'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: ef0bc5d344f7d465de9209708430d3e61d40d4f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59114647"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="233c4-102">Postupy: Vytvoření rozšíření pomocí prvku ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="233c4-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="233c4-103">Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander> ovládací prvek, který obsahuje komplexní obsah, jako je například image a text.</span><span class="sxs-lookup"><span data-stu-id="233c4-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="233c4-104">V příkladu také vloží obsah <xref:System.Windows.Controls.Expander> v <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="233c4-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="233c4-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="233c4-105">Example</span></span>  
 <span data-ttu-id="233c4-106">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="233c4-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="233c4-107">V příkladu se používá <xref:System.Windows.Controls.Primitives.BulletDecorator> ovládací prvek, který obsahuje obrázek a text, aby bylo možné definovat <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="233c4-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="233c4-108">A <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku poskytuje metodu pro posouvání rozšířené obsahu.</span><span class="sxs-lookup"><span data-stu-id="233c4-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="233c4-109">Všimněte si, že v příkladu je nastavena <xref:System.Windows.FrameworkElement.Height%2A> vlastnost <xref:System.Windows.Controls.ScrollViewer> místo na obsah.</span><span class="sxs-lookup"><span data-stu-id="233c4-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="233c4-110">Pokud <xref:System.Windows.FrameworkElement.Height%2A> nastavená na obsah, <xref:System.Windows.Controls.ScrollViewer> neumožňuje uživateli, aby posouval obsah.</span><span class="sxs-lookup"><span data-stu-id="233c4-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="233c4-111"><xref:System.Windows.FrameworkElement.Width%2A> Je nastavena na <xref:System.Windows.Controls.Expander> ovládacího prvku a toto nastavení platí pro <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a rozšířené obsah.</span><span class="sxs-lookup"><span data-stu-id="233c4-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="233c4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="233c4-112">See also</span></span>

- <xref:System.Windows.Controls.Expander>
- [<span data-ttu-id="233c4-113">Přehled rozšíření</span><span class="sxs-lookup"><span data-stu-id="233c4-113">Expander Overview</span></span>](expander-overview.md)
- [<span data-ttu-id="233c4-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="233c4-114">How-to Topics</span></span>](expander-how-to-topics.md)
