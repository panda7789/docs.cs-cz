---
title: 'Postupy: Implementace rozhraní ICommandSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 9308bfbbb7fff86ca5e93c1155cc29e4ee0d05f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-icommandsource"></a>Postupy: Implementace rozhraní ICommandSource
Tento příklad ukazuje, jak vytvořit zdroj příkaz implementací <xref:System.Windows.Input.ICommandSource>.  Příkaz zdroj je objekt, který umí vyvolání příkazu.  <xref:System.Windows.Input.ICommandSource> Rozhraní zveřejňuje tři členy: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, a <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> je příkaz, který bude vyvolán. <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> Je uživatelský datový typ, který je předán ze zdroje příkaz metodu, která zpracovává příkaz. <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Je objekt, který se spouští na příkaz.  
  
 V tomto příkladu se vytvoří třídu které podtřídy <xref:System.Windows.Controls.Slider> řízení a implementuje <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje několik tříd, které implementují třídu <xref:System.Windows.Input.ICommandSource>, jako například <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, a <xref:System.Windows.Controls.ListBoxItem>.  Příkaz zdroj definuje, jak se volá příkaz.   <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.MenuItem> vyvolání příkazu při jsou kliknutí.  A <xref:System.Windows.Controls.ListBoxItem> Vyvolá příkaz po double klepnutí. Tyto třídy stane pouze příkaz zdroje při jejich <xref:System.Windows.Input.ICommandSource.Command%2A> je nastavena.  
  
 V tomto příkladu jsme se vyvolat příkaz když přesunete posuvník nebo přesněji, když <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> vlastnost je změnit.  
  
 Toto je definici třídy.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 Dalším krokem je implementace <xref:System.Windows.Input.ICommandSource> členy.  V tomto příkladu jsou implementované vlastnosti jako <xref:System.Windows.DependencyProperty> objekty.  To umožňuje vlastnosti, které chcete použít datovou vazbu.  Další informace o <xref:System.Windows.DependencyProperty> naleznete [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Další informace o vazbě dat najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Pouze <xref:System.Windows.Input.ICommandSource.Command%2A> vlastnosti se zobrazí tady.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Tady je <xref:System.Windows.DependencyProperty> změnit zpětného volání.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 Dalším krokem je přidání a odebrání příkaz, který je přidružen ke zdroji příkaz.  <xref:System.Windows.Input.ICommandSource.Command%2A> Vlastnost nejde jednoduše přepsat, když se přidá nový příkaz, protože obslužné rutiny událostí přidružený k předchozí příkaz, pokud byl jeden, musí být nejprve odebrány.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 Posledním krokem je vytvoření logiku pro <xref:System.Windows.Input.ICommand.CanExecuteChanged> obslužné rutiny a <xref:System.Windows.Input.ICommand.Execute%2A> metoda.  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged> Událost upozorní zdroji příkaz, který možná změnil možnost provedení příkazu na cíli aktuální příkaz.  Tato událost přijetí příkazu zdroj obvykle volá <xref:System.Windows.Input.ICommand.CanExecute%2A> metoda na příkaz.  Pokud aktuální cíl příkaz nelze provést příkaz, příkaz zdroj se obvykle sama deaktivuje.  Pokud příkaz můžete spustit na aktuální příkaz cíl, zdroj příkazu bude obvykle povolit sám sebe.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 Posledním krokem je <xref:System.Windows.Input.ICommand.Execute%2A> metoda.  Pokud je příkaz <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> je metoda, jinak <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> metoda je volána.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Input.ICommandSource>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.Input.RoutedCommand>  
 [Přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md)
