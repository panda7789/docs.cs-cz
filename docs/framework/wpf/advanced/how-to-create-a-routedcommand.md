---
title: 'Postupy: Vytvoření objektu RoutedCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: 75e6c435516fe2a174cf991bd41f24e1b30a212a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544105"
---
# <a name="how-to-create-a-routedcommand"></a><span data-ttu-id="63630-102">Postupy: Vytvoření objektu RoutedCommand</span><span class="sxs-lookup"><span data-stu-id="63630-102">How to: Create a RoutedCommand</span></span>
<span data-ttu-id="63630-103">Tento příklad ukazuje, jak vytvořit vlastní <xref:System.Windows.Input.RoutedCommand> a implementaci vlastního příkazu tak, že vytvoříte <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> a jejich připojení <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="63630-103">This example shows how to create a custom <xref:System.Windows.Input.RoutedCommand> and how to implement the custom command by creating a <xref:System.Windows.Input.ExecutedRoutedEventHandler> and a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and attaching them to a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="63630-104">Další informace o tvorba příkazů najdete v tématu [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="63630-104">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63630-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="63630-105">Example</span></span>  
 <span data-ttu-id="63630-106">Prvním krokem při vytváření <xref:System.Windows.Input.RoutedCommand> je definování příkazu a vytváření instancí ho.</span><span class="sxs-lookup"><span data-stu-id="63630-106">The first step in creating a <xref:System.Windows.Input.RoutedCommand> is defining the command and instantiating it.</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 <span data-ttu-id="63630-107">Chcete-li použít příkaz v aplikaci, musí být vytvořen obslužné rutiny událostí, které definují, jaké příkaz</span><span class="sxs-lookup"><span data-stu-id="63630-107">In order to use the command in an application, event handlers which define what the command does must be created</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 <span data-ttu-id="63630-108">Další, <xref:System.Windows.Input.CommandBinding> se vytvoří, který přidruží příkaz obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="63630-108">Next, a  <xref:System.Windows.Input.CommandBinding> is created which associates the command with the event handlers.</span></span> <span data-ttu-id="63630-109"><xref:System.Windows.Input.CommandBinding> Je vytvořena na konkrétní objekt.</span><span class="sxs-lookup"><span data-stu-id="63630-109">The <xref:System.Windows.Input.CommandBinding> is created on a specific object.</span></span>  <span data-ttu-id="63630-110">Tento objekt definuje rozsah <xref:System.Windows.Input.CommandBinding> ve stromové struktuře – element</span><span class="sxs-lookup"><span data-stu-id="63630-110">This object defines the scope of the <xref:System.Windows.Input.CommandBinding> in the element tree</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 <span data-ttu-id="63630-111">Posledním krokem je vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="63630-111">The final step is invoking the command.</span></span>  <span data-ttu-id="63630-112">Jedním ze způsobů k vyvolání příkazu je její přidružení <xref:System.Windows.Input.ICommandSource>, například <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="63630-112">One way to invoke a command is to associate it with a <xref:System.Windows.Input.ICommandSource>, such as a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 <span data-ttu-id="63630-113">Při kliknutí na tlačítko <xref:System.Windows.Input.RoutedCommand.Execute%2A> metodu vlastní <xref:System.Windows.Input.RoutedCommand> je volána.</span><span class="sxs-lookup"><span data-stu-id="63630-113">When the Button is clicked, the <xref:System.Windows.Input.RoutedCommand.Execute%2A> method on the custom <xref:System.Windows.Input.RoutedCommand> is called.</span></span>  <span data-ttu-id="63630-114"><xref:System.Windows.Input.RoutedCommand> Vyvolá <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> směrované události.</span><span class="sxs-lookup"><span data-stu-id="63630-114">The <xref:System.Windows.Input.RoutedCommand> raises the <xref:System.Windows.Input.CommandManager.PreviewExecuted> and <xref:System.Windows.Input.CommandManager.Executed> routed events.</span></span>  <span data-ttu-id="63630-115">Tyto události procházení stromu element hledání <xref:System.Windows.Input.CommandBinding> pro tento konkrétní příkaz.</span><span class="sxs-lookup"><span data-stu-id="63630-115">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for this particular command.</span></span>  <span data-ttu-id="63630-116">Pokud <xref:System.Windows.Input.CommandBinding> nenajde, <xref:System.Windows.Input.ExecutedRoutedEventHandler> přidružené <xref:System.Windows.Input.CommandBinding> je volána.</span><span class="sxs-lookup"><span data-stu-id="63630-116">If a <xref:System.Windows.Input.CommandBinding> is found, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> associated with <xref:System.Windows.Input.CommandBinding> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63630-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="63630-117">See Also</span></span>  
 <xref:System.Windows.Input.RoutedCommand>  
 [<span data-ttu-id="63630-118">Přehled příkazů</span><span class="sxs-lookup"><span data-stu-id="63630-118">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
