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
# <a name="how-to-create-a-routedcommand"></a>Postupy: Vytvoření objektu RoutedCommand
Tento příklad ukazuje, jak vytvořit vlastní <xref:System.Windows.Input.RoutedCommand> a implementaci vlastního příkazu tak, že vytvoříte <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> a jejich připojení <xref:System.Windows.Input.CommandBinding>.  Další informace o tvorba příkazů najdete v tématu [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Příklad  
 Prvním krokem při vytváření <xref:System.Windows.Input.RoutedCommand> je definování příkazu a vytváření instancí ho.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 Chcete-li použít příkaz v aplikaci, musí být vytvořen obslužné rutiny událostí, které definují, jaké příkaz  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 Další, <xref:System.Windows.Input.CommandBinding> se vytvoří, který přidruží příkaz obslužné rutiny událostí. <xref:System.Windows.Input.CommandBinding> Je vytvořena na konkrétní objekt.  Tento objekt definuje rozsah <xref:System.Windows.Input.CommandBinding> ve stromové struktuře – element  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 Posledním krokem je vyvolání příkazu.  Jedním ze způsobů k vyvolání příkazu je její přidružení <xref:System.Windows.Input.ICommandSource>, například <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 Při kliknutí na tlačítko <xref:System.Windows.Input.RoutedCommand.Execute%2A> metodu vlastní <xref:System.Windows.Input.RoutedCommand> je volána.  <xref:System.Windows.Input.RoutedCommand> Vyvolá <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> směrované události.  Tyto události procházení stromu element hledání <xref:System.Windows.Input.CommandBinding> pro tento konkrétní příkaz.  Pokud <xref:System.Windows.Input.CommandBinding> nenajde, <xref:System.Windows.Input.ExecutedRoutedEventHandler> přidružené <xref:System.Windows.Input.CommandBinding> je volána.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Input.RoutedCommand>  
 [Přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md)
