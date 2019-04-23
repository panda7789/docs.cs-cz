---
title: 'Postupy: Implementace rozhraní ICommandSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 218a17f221598ac29213bd28a0f04adb16bc933b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107364"
---
# <a name="how-to-implement-icommandsource"></a>Postupy: Implementace rozhraní ICommandSource
Tento příklad ukazuje, jak vytvořit příkaz zdroj implementací <xref:System.Windows.Input.ICommandSource>.  Příkaz zdroj je objekt, který umí spuštění příkazu.  <xref:System.Windows.Input.ICommandSource> Rozhraní poskytuje tři členy: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, a <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> je příkaz, který bude vyvolán. <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> Je uživatelsky definovaný datový typ, který je předán ze zdroje příkaz metodu, která zpracovává příkaz. <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Je objekt, který se na spuštění příkazu.  
  
 V tomto příkladu je vytvořená třída které podtřídy <xref:System.Windows.Controls.Slider> ovládacího prvku a implementuje <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje několik tříd, které implementují <xref:System.Windows.Input.ICommandSource>, jako například <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, a <xref:System.Windows.Controls.ListBoxItem>.  Příkaz zdroj definuje, jak Vyvolá příkaz.   <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.MenuItem> vyvolat příkaz při kliknutí.  A <xref:System.Windows.Controls.ListBoxItem> Vyvolá příkaz při dvojitém kliknutí. Tyto třídy jenom tehdy, příkaz zdroj, když jejich <xref:System.Windows.Input.ICommandSource.Command%2A> je nastavena.  
  
 V tomto příkladu jsme se při přesunutí posuvníku vyvolat příkaz nebo přesněji, když <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> je změněna vlastnost.  
  
 Následuje definici třídy.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 Dalším krokem je implementace <xref:System.Windows.Input.ICommandSource> členy.  V tomto příkladu jsou implementované vlastnosti jako <xref:System.Windows.DependencyProperty> objekty.  To umožňuje vlastnosti, které chcete použít datovou vazbu.  Další informace o <xref:System.Windows.DependencyProperty> najdete v tématu [přehled vlastností závislosti](dependency-properties-overview.md).  Další informace o vytváření datových vazeb, najdete v článku [Data Binding Overview](../data/data-binding-overview.md).  
  
 Pouze <xref:System.Windows.Input.ICommandSource.Command%2A> vlastnost je znázorněna zde.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Tady je <xref:System.Windows.DependencyProperty> změnit zpětného volání.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 Dalším krokem je přidání a odebrání příkazu, který je přidružený zdroj příkazu.  <xref:System.Windows.Input.ICommandSource.Command%2A> Vlastnost nelze jednoduše přepsat, když se přidá nový příkaz, protože obslužné rutiny událostí související s předchozí příkaz, pokud existuje, musíte ji nejprve odebrat.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 Posledním krokem je vytvoření logiky pro <xref:System.Windows.Input.ICommand.CanExecuteChanged> obslužné rutiny a <xref:System.Windows.Input.ICommand.Execute%2A> metoda.  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged> Událost upozorní zdroj příkazu, který se mohl změnit možnost příkazu ke spuštění na aktuálním cíli příkazu.  Když zdroj příkaz obdrží tato událost, obvykle volá <xref:System.Windows.Input.ICommand.CanExecute%2A> metoda u příkazu.  Pokud příkaz nelze provést na aktuálním cíli příkazu, zdroj příkazu se obvykle sama deaktivuje.  Pokud příkaz můžete spustit na aktuálním cíli příkazu, zdroj příkazu samotné obvykle povolí.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 Posledním krokem je <xref:System.Windows.Input.ICommand.Execute%2A> metody.  Pokud je příkaz <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> je metoda volaná; v opačném případě <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> metoda je volána.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Přehled příkazů](commanding-overview.md)
