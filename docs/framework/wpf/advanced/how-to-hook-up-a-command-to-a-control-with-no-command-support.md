---
title: "Postupy: Propojení příkazu s ovládacím prvkem bez podpory příkazů"
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
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f38a6f900ee2b253708da4b63bdc2f474fa3ab1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a><span data-ttu-id="16b5a-102">Postupy: Propojení příkazu s ovládacím prvkem bez podpory příkazů</span><span class="sxs-lookup"><span data-stu-id="16b5a-102">How to: Hook Up a Command to a Control with No Command Support</span></span>
<span data-ttu-id="16b5a-103">Následující příklad ukazuje, jak spojit <xref:System.Windows.Input.RoutedCommand> k <xref:System.Windows.Controls.Control> které není mít vestavěnou podporou pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="16b5a-103">The following example shows how to hook up a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Control> which does not have built in support for the command.</span></span>  <span data-ttu-id="16b5a-104">Kompletní příklad, který zachytí až příkazů pro více zdrojů, najdete v článku [vytvořit vlastní vzorek RoutedCommand](http://go.microsoft.com/fwlink/?LinkID=159980) ukázka.</span><span class="sxs-lookup"><span data-stu-id="16b5a-104">For a complete sample which hooks up commands to multiple sources, see the [Create a Custom RoutedCommand Sample](http://go.microsoft.com/fwlink/?LinkID=159980) sample.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16b5a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="16b5a-105">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="16b5a-106">poskytuje knihovnu běžných příkazů, které pravidelně dojde programátorům aplikací.</span><span class="sxs-lookup"><span data-stu-id="16b5a-106"> provides a library of common commands which application programmers encounter regularly.</span></span>  <span data-ttu-id="16b5a-107">Jsou třídy, které tvoří příkaz knihovny: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, a <xref:System.Windows.Documents.EditingCommands>.</span><span class="sxs-lookup"><span data-stu-id="16b5a-107">The classes which comprise the command library are: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, and <xref:System.Windows.Documents.EditingCommands>.</span></span>  
  
 <span data-ttu-id="16b5a-108">Statické <xref:System.Windows.Input.RoutedCommand> objekty, které tvoří tyto třídy nezadávejte příkaz logiku.</span><span class="sxs-lookup"><span data-stu-id="16b5a-108">The static <xref:System.Windows.Input.RoutedCommand> objects which make up these classes do not supply command logic.</span></span>  <span data-ttu-id="16b5a-109">Příkaz s přidružen logiku pro příkaz <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="16b5a-109">The logic for the command is associated with the command with a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="16b5a-110">Mnoho ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mít vestavěnou podporou pro některé příkazy v knihovně příkaz.</span><span class="sxs-lookup"><span data-stu-id="16b5a-110">Many controls in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] have built in support for some of the commands in the command library.</span></span>  <span data-ttu-id="16b5a-111"><xref:System.Windows.Controls.TextBox>, například podporuje mnoho příkazů úpravy aplikací, jako <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, a <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.</span><span class="sxs-lookup"><span data-stu-id="16b5a-111"><xref:System.Windows.Controls.TextBox>, for example, supports many of the application edit commands such as <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, and <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.</span></span>  <span data-ttu-id="16b5a-112">Vývojář aplikace nemá žádnou zvláštní získat tyto příkazy pro práci s tyto ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="16b5a-112">The application developer does not have to do anything special to get these commands to work with these controls.</span></span>  <span data-ttu-id="16b5a-113">Pokud <xref:System.Windows.Controls.TextBox> je cílem příkazu po provedení příkazu je bude zpracovávat pomocí příkazu <xref:System.Windows.Input.CommandBinding> , je integrovaná do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="16b5a-113">If the <xref:System.Windows.Controls.TextBox> is the command target when the command is executed, it will handle the command using the <xref:System.Windows.Input.CommandBinding> that is built into the control.</span></span>  
  
 <span data-ttu-id="16b5a-114">Následující ukazuje způsob použití <xref:System.Windows.Controls.Button> jako zdroj pro příkaz <xref:System.Windows.Input.ApplicationCommands.Open%2A> příkaz.</span><span class="sxs-lookup"><span data-stu-id="16b5a-114">The following shows how to use a <xref:System.Windows.Controls.Button> as the command source for the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  <span data-ttu-id="16b5a-115">A <xref:System.Windows.Input.CommandBinding> se vytvoří tento partnerů zadaný <xref:System.Windows.Input.CanExecuteRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> s <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="16b5a-115">A <xref:System.Windows.Input.CommandBinding> is created that associates the specified <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="16b5a-116">Nejprve je vytvořen zdroj příkazu.</span><span class="sxs-lookup"><span data-stu-id="16b5a-116">First, the command source is created.</span></span>  <span data-ttu-id="16b5a-117">A <xref:System.Windows.Controls.Button> slouží jako zdroj příkazu.</span><span class="sxs-lookup"><span data-stu-id="16b5a-117">A <xref:System.Windows.Controls.Button> is used as the command source.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 <span data-ttu-id="16b5a-118">Dále <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> se vytvářejí.</span><span class="sxs-lookup"><span data-stu-id="16b5a-118">Next, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> are created.</span></span>  <span data-ttu-id="16b5a-119"><xref:System.Windows.Input.ExecutedRoutedEventHandler> Jednoduše otevře <xref:System.Windows.MessageBox> označuje, že příkaz provést.</span><span class="sxs-lookup"><span data-stu-id="16b5a-119">The <xref:System.Windows.Input.ExecutedRoutedEventHandler> simply opens a <xref:System.Windows.MessageBox> to signify that the command executed.</span></span>  <span data-ttu-id="16b5a-120"><xref:System.Windows.Input.CanExecuteRoutedEventHandler> Nastaví <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="16b5a-120">The <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sets the <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> property to `true`.</span></span>  <span data-ttu-id="16b5a-121">Za normálních okolností může spustit obslužnou rutinu by provedl robustnější kontroluje, pokud příkaz může spustit na aktuální příkaz cíl.</span><span class="sxs-lookup"><span data-stu-id="16b5a-121">Normally, the can execute handler would perform more robust checks to see if the command could execute on the current command target.</span></span>  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 <span data-ttu-id="16b5a-122">Nakonec <xref:System.Windows.Input.CommandBinding> se vytvoří v kořenovém <xref:System.Windows.Window> aplikace, která přidruží obslužné rutiny události směrované na <xref:System.Windows.Input.ApplicationCommands.Open%2A> příkaz.</span><span class="sxs-lookup"><span data-stu-id="16b5a-122">Finally, a <xref:System.Windows.Input.CommandBinding> is created on the root <xref:System.Windows.Window> of the application that associates the routed events handlers to the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a><span data-ttu-id="16b5a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="16b5a-123">See Also</span></span>  
 [<span data-ttu-id="16b5a-124">Tvorba příkazů – přehled</span><span class="sxs-lookup"><span data-stu-id="16b5a-124">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [<span data-ttu-id="16b5a-125">Propojte příkaz do ovládacího prvku s podporou příkaz</span><span class="sxs-lookup"><span data-stu-id="16b5a-125">Hook Up a Command to a Control with Command Support</span></span>](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
