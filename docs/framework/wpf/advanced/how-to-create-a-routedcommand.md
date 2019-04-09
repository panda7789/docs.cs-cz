---
title: 'Postupy: Vytvoření objektu RoutedCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: d433658a3039c262d2f682eff09df646d978018c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109041"
---
# <a name="how-to-create-a-routedcommand"></a>Postupy: Vytvoření objektu RoutedCommand
Tento příklad ukazuje, jak vytvořit vlastní <xref:System.Windows.Input.RoutedCommand> a jak implementovat vlastní příkaz tak, že vytvoříte <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> a jejich připojením <xref:System.Windows.Input.CommandBinding>.  Další informace o příkazů najdete v tématu [přehled příkazů](commanding-overview.md).  
  
## <a name="example"></a>Příklad  
 Prvním krokem při vytváření <xref:System.Windows.Input.RoutedCommand> je definování příkazu a vytvoření jeho instance.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 Chcete-li použít příkaz v aplikaci, musí být vytvořeny obslužné rutiny událostí, které definují, co dělá příkaz  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 Další, <xref:System.Windows.Input.CommandBinding> se vytvoří, která přidruží tento příkaz obslužné rutiny událostí. <xref:System.Windows.Input.CommandBinding> Je vytvořena na konkrétní objekt.  Tento objekt definuje rozsah <xref:System.Windows.Input.CommandBinding> ve stromu elementů  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 Posledním krokem je použití příkazu.  Jedním ze způsobů spuštění příkazu je přidružte jej k <xref:System.Windows.Input.ICommandSource>, například <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 Po kliknutí na tlačítko <xref:System.Windows.Input.RoutedCommand.Execute%2A> metodu na vlastní <xref:System.Windows.Input.RoutedCommand> je volána.  <xref:System.Windows.Input.RoutedCommand> Vyvolá <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> směrovaných událostí.  Tyto události procházení stromu element hledání <xref:System.Windows.Input.CommandBinding> pro tento konkrétní příkaz.  Pokud <xref:System.Windows.Input.CommandBinding> nenajde, <xref:System.Windows.Input.ExecutedRoutedEventHandler> přidružené <xref:System.Windows.Input.CommandBinding> je volána.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Input.RoutedCommand>
- [Přehled příkazů](commanding-overview.md)
