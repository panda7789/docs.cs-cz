---
title: "Postupy: Povolení příkazu"
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
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e90f7f69aebf48bbc27321d3808468a2df49f793
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enable-a-command"></a><span data-ttu-id="49b5a-102">Postupy: Povolení příkazu</span><span class="sxs-lookup"><span data-stu-id="49b5a-102">How to: Enable a Command</span></span>
<span data-ttu-id="49b5a-103">Následující příklad ukazuje, jak používat tvorba příkazů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49b5a-103">The following example demonstrates how to use commanding in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  <span data-ttu-id="49b5a-104">Tento příklad ukazuje, jak přidružit <xref:System.Windows.Input.RoutedCommand> k <xref:System.Windows.Controls.Button>, vytvoření <xref:System.Windows.Input.CommandBinding>a vytváření obslužných rutin událostí, které implementují třídu <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="49b5a-104">The example shows how to associate a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Button>, create a <xref:System.Windows.Input.CommandBinding>, and create the event handlers which implement the <xref:System.Windows.Input.RoutedCommand>.</span></span>  <span data-ttu-id="49b5a-105">Další informace o tvorba příkazů najdete v tématu [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="49b5a-105">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49b5a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="49b5a-106">Example</span></span>  
 <span data-ttu-id="49b5a-107">První část kód vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], který se skládá z <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.StackPanel>a vytvoří <xref:System.Windows.Input.CommandBinding> který přidruží obslužné rutiny příkazů s <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="49b5a-107">The first section of code creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], which consists of a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.StackPanel>, and creates a <xref:System.Windows.Input.CommandBinding> that associates the command handlers with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="49b5a-108"><xref:System.Windows.Input.ICommandSource.Command%2A> Vlastnost <xref:System.Windows.Controls.Button> přidružen <xref:System.Windows.Input.ApplicationCommands.Close%2A> příkaz.</span><span class="sxs-lookup"><span data-stu-id="49b5a-108">The <xref:System.Windows.Input.ICommandSource.Command%2A> property of the <xref:System.Windows.Controls.Button> is associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="49b5a-109"><xref:System.Windows.Input.CommandBinding> Je přidán do <xref:System.Windows.Input.CommandBindingCollection> kořenové <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="49b5a-109">The <xref:System.Windows.Input.CommandBinding> is added to the <xref:System.Windows.Input.CommandBindingCollection> of the root <xref:System.Windows.Window>.</span></span> <span data-ttu-id="49b5a-110"><xref:System.Windows.Input.CommandBinding.Executed> a <xref:System.Windows.Input.CommandBinding.CanExecute> jsou připojené k této vazbě a přidružené obslužné rutiny událostí <xref:System.Windows.Input.ApplicationCommands.Close%2A> příkaz.</span><span class="sxs-lookup"><span data-stu-id="49b5a-110">The <xref:System.Windows.Input.CommandBinding.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers are attached to this binding and associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="49b5a-111">Bez <xref:System.Windows.Input.CommandBinding> neexistuje žádný příkaz logiku, pouze mechanismus pro vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="49b5a-111">Without the <xref:System.Windows.Input.CommandBinding> there is no command logic, only a mechanism to invoke the command.</span></span>  <span data-ttu-id="49b5a-112">Když <xref:System.Windows.Controls.Button> po kliknutí na <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> se vyvolá při cíl příkazu následuje <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span><span class="sxs-lookup"><span data-stu-id="49b5a-112">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> is raised on the command target followed by the <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span></span>  <span data-ttu-id="49b5a-113">Tyto události procházení stromu element hledání <xref:System.Windows.Input.CommandBinding> pro tuto konkrétní příkaz.</span><span class="sxs-lookup"><span data-stu-id="49b5a-113">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for that particular command.</span></span>  <span data-ttu-id="49b5a-114">Stojí za zmínku, že <xref:System.Windows.RoutedEvent> tunelové propojení a bublin prostřednictvím stromu element musí dát pozor tam, kde <xref:System.Windows.Input.CommandBinding> je.</span><span class="sxs-lookup"><span data-stu-id="49b5a-114">It is worth noting that because <xref:System.Windows.RoutedEvent> tunnel and bubble through the element tree, care must be taken in where the <xref:System.Windows.Input.CommandBinding> is put.</span></span>   <span data-ttu-id="49b5a-115">Pokud <xref:System.Windows.Input.CommandBinding> je na stejné úrovni jako cíl příkazu nebo jiného uzlu, který se nenachází na trasa <xref:System.Windows.RoutedEvent>, <xref:System.Windows.Input.CommandBinding> nebude přístupná.</span><span class="sxs-lookup"><span data-stu-id="49b5a-115">If the <xref:System.Windows.Input.CommandBinding> is on a sibling of the command target or another node that is not on the route of the <xref:System.Windows.RoutedEvent>, the <xref:System.Windows.Input.CommandBinding> will not be accessed.</span></span>  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 <span data-ttu-id="49b5a-116">V další části kódu implementuje <xref:System.Windows.Input.CommandManager.Executed> a <xref:System.Windows.Input.CommandBinding.CanExecute> obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="49b5a-116">The next section of code implements the <xref:System.Windows.Input.CommandManager.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers.</span></span>  
  
 <span data-ttu-id="49b5a-117"><xref:System.Windows.Input.CommandManager.Executed> Události volá metodu zavřete otevření souboru.</span><span class="sxs-lookup"><span data-stu-id="49b5a-117">The <xref:System.Windows.Input.CommandManager.Executed> handler calls a method to close the open file.</span></span>  <span data-ttu-id="49b5a-118"><xref:System.Windows.Input.CommandBinding.CanExecute> Události volá metodu k určení, zda je soubor otevřený.</span><span class="sxs-lookup"><span data-stu-id="49b5a-118">The <xref:System.Windows.Input.CommandBinding.CanExecute> handler calls a method to determine whether a file is open.</span></span>  <span data-ttu-id="49b5a-119">Pokud je soubor otevřený <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> je nastaven na `true`, jinak je nastaven na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="49b5a-119">If a file is open, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> is set to `true`; otherwise, it is set to `false`.</span></span>  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a><span data-ttu-id="49b5a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="49b5a-120">See Also</span></span>  
 [<span data-ttu-id="49b5a-121">Tvorba příkazů – přehled</span><span class="sxs-lookup"><span data-stu-id="49b5a-121">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
