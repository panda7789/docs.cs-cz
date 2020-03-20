---
title: 'Postupy: Implementace rozhraní ICommandSource'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6c18e0b77ec53d9bd3e7ce610f2940effe603c88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174690"
---
# <a name="how-to-implement-icommandsource"></a>Postupy: Implementace rozhraní ICommandSource

Tento příklad ukazuje, jak vytvořit zdroj <xref:System.Windows.Input.ICommandSource>příkazu implementací . Zdroj příkazu je objekt, který ví, jak vyvolat příkaz. Rozhraní <xref:System.Windows.Input.ICommandSource> zveřejňuje tři členy:

- <xref:System.Windows.Input.ICommandSource.Command%2A>: příkaz, který bude vyvolán.
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: uživatelem definovaný datový typ, který je předán ze zdroje příkazu metodě, která zpracovává příkaz.
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: objekt, na který je příkaz prováděn.

V tomto příkladu je vytvořena třída, <xref:System.Windows.Controls.Slider> která dědí <xref:System.Windows.Input.ICommandSource> z ovládacího prvku a implementuje rozhraní.
  
## <a name="example"></a>Příklad

WPF poskytuje řadu tříd, <xref:System.Windows.Input.ICommandSource>které <xref:System.Windows.Controls.Button>implementují , například , <xref:System.Windows.Controls.MenuItem>a <xref:System.Windows.Documents.Hyperlink>. Zdroj příkazu definuje, jak vyvolá příkaz. Tyto třídy vyvolat příkaz, když jsou kliknuty a <xref:System.Windows.Input.ICommandSource.Command%2A> stanou se zdrojem příkazu pouze při jejich vlastnost je nastavena.

V tomto příkladu vyvoláte příkaz při přesunutí jezdce nebo přesněji při <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> změně vlastnosti.

Následuje definice třídy:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

Dalším krokem je implementace <xref:System.Windows.Input.ICommandSource> členů. V tomto příkladu jsou <xref:System.Windows.DependencyProperty> vlastnosti implementovány jako objekty. To umožňuje vlastnosti používat datové vazby. Další informace o <xref:System.Windows.DependencyProperty> třídě naleznete v tématu [Přehled vlastností závislostí](dependency-properties-overview.md). Další informace o datové vazbě naleznete v přehledu [datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).

Zde <xref:System.Windows.Input.ICommandSource.Command%2A> je zobrazena pouze nemovitost.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
Následuje <xref:System.Windows.DependencyProperty> zpětné volání změny:

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

Dalším krokem je přidání a odebrání příkazu, který je přidružen ke zdroji příkazu. Vlastnost <xref:System.Windows.Input.ICommandSource.Command%2A> nelze jednoduše přepsat při přidání nového příkazu, protože obslužné rutiny událostí přidružené k předchozímu příkazu, pokud byl jeden, musí být nejprve odebrány.

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

Dalším krokem je vytvoření logiky pro obslužnou rutinu. <xref:System.Windows.Input.ICommand.CanExecuteChanged>

Událost <xref:System.Windows.Input.ICommand.CanExecuteChanged> upozorní zdroj příkazu, že schopnost příkazu provést na aktuální cíl příkazu se může změnit. Když zdroj příkazu obdrží tuto událost, <xref:System.Windows.Input.ICommand.CanExecute%2A> obvykle volá metodu v příkazu. Pokud příkaz nelze spustit na aktuální cíl příkazu, zdroj příkazu obvykle zakázat sám. Pokud příkaz lze spustit na aktuální cíl příkazu, zdroj příkazu obvykle povolí sám.

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

Posledním krokem je <xref:System.Windows.Input.ICommand.Execute%2A> metoda. Pokud je příkaz <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> je volána metoda; <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> jinak je volána metoda.

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [Přehled příkazů](commanding-overview.md)
