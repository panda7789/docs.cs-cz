---
title: 'Postupy: Vytvoření elementu StackPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: bcf6decff2fbc012b5f8b62794f0d7b2cd9f29fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050997"
---
# <a name="how-to-create-a-stackpanel"></a><span data-ttu-id="8fc40-102">Postupy: Vytvoření elementu StackPanel</span><span class="sxs-lookup"><span data-stu-id="8fc40-102">How to: Create a StackPanel</span></span>
<span data-ttu-id="8fc40-103">Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="8fc40-103">This example shows how to create a <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fc40-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fc40-104">Example</span></span>  
 <span data-ttu-id="8fc40-105">A <xref:System.Windows.Controls.StackPanel> umožňuje zásobníku prvky v zadaném směru.</span><span class="sxs-lookup"><span data-stu-id="8fc40-105">A <xref:System.Windows.Controls.StackPanel> allows you to stack elements in a specified direction.</span></span> <span data-ttu-id="8fc40-106">Pomocí vlastností, které jsou definovány na <xref:System.Windows.Controls.StackPanel>, obsah byl zajištěn tok obě svisle, což je výchozí nastavení, nebo vodorovně.</span><span class="sxs-lookup"><span data-stu-id="8fc40-106">By using properties that are defined on <xref:System.Windows.Controls.StackPanel>, content can flow both vertically, which is the default setting, or horizontally.</span></span>  
  
 <span data-ttu-id="8fc40-107">Následující příklad svisle zásobníků pět <xref:System.Windows.Controls.TextBlock> ovládací prvky, každý s jiným <xref:System.Windows.Controls.Border> a <xref:System.Windows.Controls.Border.Background%2A>, s použitím <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="8fc40-107">The following example vertically stacks five <xref:System.Windows.Controls.TextBlock> controls, each with a different <xref:System.Windows.Controls.Border> and <xref:System.Windows.Controls.Border.Background%2A>, by using <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="8fc40-108">Podřízené prvky, které nemají zadán <xref:System.Windows.FrameworkElement.Width%2A> roztáhnout tak, aby vyplnil nadřazené okno; nicméně jsou podřízené prvky, které mají zadanou <xref:System.Windows.FrameworkElement.Width%2A>, je umístěn okna na střed.</span><span class="sxs-lookup"><span data-stu-id="8fc40-108">The child elements that have no specified <xref:System.Windows.FrameworkElement.Width%2A> stretch to fill the parent window; however, the child elements that have a specified <xref:System.Windows.FrameworkElement.Width%2A>, are centered within the window.</span></span>  
  
 <span data-ttu-id="8fc40-109">Výchozí směr zásobníku <xref:System.Windows.Controls.StackPanel> je svislý.</span><span class="sxs-lookup"><span data-stu-id="8fc40-109">The default stack direction in a <xref:System.Windows.Controls.StackPanel> is vertical.</span></span> <span data-ttu-id="8fc40-110">K řízení toku obsahu v <xref:System.Windows.Controls.StackPanel>, použijte <xref:System.Windows.Controls.StackPanel.Orientation%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8fc40-110">To control content flow in a <xref:System.Windows.Controls.StackPanel>, use the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property.</span></span> <span data-ttu-id="8fc40-111">Vodorovné zarovnání můžete řídit pomocí <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8fc40-111">You can control horizontal alignment by using the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property.</span></span>  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fc40-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fc40-112">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- [<span data-ttu-id="8fc40-113">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="8fc40-113">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="8fc40-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="8fc40-114">How-to Topics</span></span>](stackpanel-how-to-topics.md)
