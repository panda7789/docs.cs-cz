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
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="c59a7-102">Postupy: Implementace rozhraní ICommandSource</span><span class="sxs-lookup"><span data-stu-id="c59a7-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="c59a7-103">Tento příklad ukazuje, jak vytvořit zdroj <xref:System.Windows.Input.ICommandSource>příkazu implementací .</span><span class="sxs-lookup"><span data-stu-id="c59a7-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="c59a7-104">Zdroj příkazu je objekt, který ví, jak vyvolat příkaz.</span><span class="sxs-lookup"><span data-stu-id="c59a7-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="c59a7-105">Rozhraní <xref:System.Windows.Input.ICommandSource> zveřejňuje tři členy:</span><span class="sxs-lookup"><span data-stu-id="c59a7-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="c59a7-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: příkaz, který bude vyvolán.</span><span class="sxs-lookup"><span data-stu-id="c59a7-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="c59a7-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: uživatelem definovaný datový typ, který je předán ze zdroje příkazu metodě, která zpracovává příkaz.</span><span class="sxs-lookup"><span data-stu-id="c59a7-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="c59a7-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: objekt, na který je příkaz prováděn.</span><span class="sxs-lookup"><span data-stu-id="c59a7-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="c59a7-109">V tomto příkladu je vytvořena třída, <xref:System.Windows.Controls.Slider> která dědí <xref:System.Windows.Input.ICommandSource> z ovládacího prvku a implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c59a7-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="c59a7-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c59a7-110">Example</span></span>

<span data-ttu-id="c59a7-111">WPF poskytuje řadu tříd, <xref:System.Windows.Input.ICommandSource>které <xref:System.Windows.Controls.Button>implementují , například , <xref:System.Windows.Controls.MenuItem>a <xref:System.Windows.Documents.Hyperlink>.</span><span class="sxs-lookup"><span data-stu-id="c59a7-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="c59a7-112">Zdroj příkazu definuje, jak vyvolá příkaz.</span><span class="sxs-lookup"><span data-stu-id="c59a7-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="c59a7-113">Tyto třídy vyvolat příkaz, když jsou kliknuty a <xref:System.Windows.Input.ICommandSource.Command%2A> stanou se zdrojem příkazu pouze při jejich vlastnost je nastavena.</span><span class="sxs-lookup"><span data-stu-id="c59a7-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="c59a7-114">V tomto příkladu vyvoláte příkaz při přesunutí jezdce nebo přesněji při <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> změně vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c59a7-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="c59a7-115">Následuje definice třídy:</span><span class="sxs-lookup"><span data-stu-id="c59a7-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="c59a7-116">Dalším krokem je implementace <xref:System.Windows.Input.ICommandSource> členů.</span><span class="sxs-lookup"><span data-stu-id="c59a7-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="c59a7-117">V tomto příkladu jsou <xref:System.Windows.DependencyProperty> vlastnosti implementovány jako objekty.</span><span class="sxs-lookup"><span data-stu-id="c59a7-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="c59a7-118">To umožňuje vlastnosti používat datové vazby.</span><span class="sxs-lookup"><span data-stu-id="c59a7-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="c59a7-119">Další informace o <xref:System.Windows.DependencyProperty> třídě naleznete v tématu [Přehled vlastností závislostí](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c59a7-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="c59a7-120">Další informace o datové vazbě naleznete v přehledu [datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c59a7-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="c59a7-121">Zde <xref:System.Windows.Input.ICommandSource.Command%2A> je zobrazena pouze nemovitost.</span><span class="sxs-lookup"><span data-stu-id="c59a7-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="c59a7-122">Následuje <xref:System.Windows.DependencyProperty> zpětné volání změny:</span><span class="sxs-lookup"><span data-stu-id="c59a7-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="c59a7-123">Dalším krokem je přidání a odebrání příkazu, který je přidružen ke zdroji příkazu.</span><span class="sxs-lookup"><span data-stu-id="c59a7-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="c59a7-124">Vlastnost <xref:System.Windows.Input.ICommandSource.Command%2A> nelze jednoduše přepsat při přidání nového příkazu, protože obslužné rutiny událostí přidružené k předchozímu příkazu, pokud byl jeden, musí být nejprve odebrány.</span><span class="sxs-lookup"><span data-stu-id="c59a7-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="c59a7-125">Dalším krokem je vytvoření logiky pro obslužnou rutinu. <xref:System.Windows.Input.ICommand.CanExecuteChanged></span><span class="sxs-lookup"><span data-stu-id="c59a7-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="c59a7-126">Událost <xref:System.Windows.Input.ICommand.CanExecuteChanged> upozorní zdroj příkazu, že schopnost příkazu provést na aktuální cíl příkazu se může změnit.</span><span class="sxs-lookup"><span data-stu-id="c59a7-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="c59a7-127">Když zdroj příkazu obdrží tuto událost, <xref:System.Windows.Input.ICommand.CanExecute%2A> obvykle volá metodu v příkazu.</span><span class="sxs-lookup"><span data-stu-id="c59a7-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="c59a7-128">Pokud příkaz nelze spustit na aktuální cíl příkazu, zdroj příkazu obvykle zakázat sám.</span><span class="sxs-lookup"><span data-stu-id="c59a7-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="c59a7-129">Pokud příkaz lze spustit na aktuální cíl příkazu, zdroj příkazu obvykle povolí sám.</span><span class="sxs-lookup"><span data-stu-id="c59a7-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="c59a7-130">Posledním krokem je <xref:System.Windows.Input.ICommand.Execute%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c59a7-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="c59a7-131">Pokud je příkaz <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> je volána metoda; <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> jinak je volána metoda.</span><span class="sxs-lookup"><span data-stu-id="c59a7-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="c59a7-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="c59a7-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="c59a7-133">Přehled příkazů</span><span class="sxs-lookup"><span data-stu-id="c59a7-133">Commanding Overview</span></span>](commanding-overview.md)
