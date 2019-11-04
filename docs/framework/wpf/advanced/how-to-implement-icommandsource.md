---
title: 'Postupy: Implementace rozhraní ICommandSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 974b145a125a158bcafff93f8e9bc11001e00bf1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453581"
---
# <a name="how-to-implement-icommandsource"></a>Postupy: Implementace rozhraní ICommandSource
Tento příklad ukazuje, jak vytvořit zdroj příkazu implementací <xref:System.Windows.Input.ICommandSource>.  Zdroj příkazu je objekt, který ví, jak vyvolat příkaz.  Rozhraní <xref:System.Windows.Input.ICommandSource> zpřístupňuje tři členy: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>a <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.  <xref:System.Windows.Input.ICommandSource.Command%2A> je příkaz, který bude vyvolán. <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> je uživatelsky definovaný datový typ, který se předává ze zdroje příkazu metodě, která zpracovává příkaz. <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je objekt, na kterém je příkaz spuštěn.  
  
 V tomto příkladu je vytvořena třída, která podtřídí ovládací prvek <xref:System.Windows.Controls.Slider> a implementuje <xref:System.Windows.Input.ICommandSource>.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje řadu tříd, které implementují <xref:System.Windows.Input.ICommandSource>, například <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>a <xref:System.Windows.Controls.ListBoxItem>.  Zdroj příkazu definuje způsob, jakým Vyvolá příkaz.   <xref:System.Windows.Controls.Button> a při kliknutí <xref:System.Windows.Controls.MenuItem> Vyvolá příkaz.  <xref:System.Windows.Controls.ListBoxItem> Vyvolá příkaz při dvojitém kliknutí. Tyto třídy se stanou zdrojem příkazu pouze v případě, že je nastavena jejich vlastnost <xref:System.Windows.Input.ICommandSource.Command%2A>.  
  
 V tomto příkladu vyvoláme příkaz při přesunutí posuvníku nebo přesnější, když se změní vlastnost <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.  
  
 Následuje definice třídy.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 Dalším krokem je implementace <xref:System.Windows.Input.ICommandSource> členů.  V tomto příkladu jsou vlastnosti implementovány jako objekty <xref:System.Windows.DependencyProperty>.  To umožňuje, aby vlastnosti používaly datovou vazbu.  Další informace o třídě <xref:System.Windows.DependencyProperty> naleznete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).  Další informace o datové vazbě najdete v tématu [Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md).  
  
 Tady je zobrazená jenom vlastnost <xref:System.Windows.Input.ICommandSource.Command%2A>.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 Následuje <xref:System.Windows.DependencyProperty> zpětného volání změny.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 Dalším krokem je přidání a odebrání příkazu, který je přidružen ke zdroji příkazů.  Vlastnost <xref:System.Windows.Input.ICommandSource.Command%2A> nelze jednoduše přepsat při přidání nového příkazu, protože obslužné rutiny událostí přidružené k předchozímu příkazu (pokud existovaly), musí být nejprve odebrány.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 Posledním krokem je vytvoření logiky pro obslužnou rutinu <xref:System.Windows.Input.ICommand.CanExecuteChanged> a metodu <xref:System.Windows.Input.ICommand.Execute%2A>.  
  
 Událost <xref:System.Windows.Input.ICommand.CanExecuteChanged> upozorní zdroj příkazu, že se mohla změnit schopnost příkazu spustit na aktuálním cíli příkazu.  Když zdroj příkazu obdrží tuto událost, obvykle volá metodu <xref:System.Windows.Input.ICommand.CanExecute%2A> příkazu.  Pokud příkaz nelze provést na aktuálním cíli příkazu, bude zdroj příkazu obvykle zapínat sám sebe.  Pokud se příkaz může spustit na aktuálním cíli příkazu, bude zdroj příkazu obvykle umožňovat sám sebe.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 Posledním krokem je metoda <xref:System.Windows.Input.ICommand.Execute%2A>.  Pokud je příkaz <xref:System.Windows.Input.RoutedCommand>, je volána metoda <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A>; v opačném případě je volána metoda <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A>.  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Přehled příkazů](commanding-overview.md)
