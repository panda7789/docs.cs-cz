---
title: 'Postupy: Implementace rozhraní ICommandSource'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 755377d25a2deb48aa9da86d4182075e30763530
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345087"
---
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="2d248-102">Postupy: Implementace rozhraní ICommandSource</span><span class="sxs-lookup"><span data-stu-id="2d248-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="2d248-103">Tento příklad ukazuje, jak vytvořit zdroj příkazu implementací <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="2d248-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="2d248-104">Zdroj příkazu je objekt, který ví, jak vyvolat příkaz.</span><span class="sxs-lookup"><span data-stu-id="2d248-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="2d248-105">Rozhraní <xref:System.Windows.Input.ICommandSource> zpřístupňuje tři členy:</span><span class="sxs-lookup"><span data-stu-id="2d248-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="2d248-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: příkaz, který bude vyvolán.</span><span class="sxs-lookup"><span data-stu-id="2d248-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="2d248-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: uživatelsky definovaný datový typ, který se předává ze zdroje příkazu metodě, která zpracovává příkaz.</span><span class="sxs-lookup"><span data-stu-id="2d248-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="2d248-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: objekt, na kterém je příkaz spuštěn.</span><span class="sxs-lookup"><span data-stu-id="2d248-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="2d248-109">V tomto příkladu je vytvořena třída, která dědí z ovládacího prvku <xref:System.Windows.Controls.Slider> a implementuje rozhraní <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="2d248-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="2d248-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d248-110">Example</span></span>

<span data-ttu-id="2d248-111">WPF poskytuje řadu tříd, které implementují <xref:System.Windows.Input.ICommandSource>, například <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>a <xref:System.Windows.Documents.Hyperlink>.</span><span class="sxs-lookup"><span data-stu-id="2d248-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="2d248-112">Zdroj příkazu definuje způsob, jakým Vyvolá příkaz.</span><span class="sxs-lookup"><span data-stu-id="2d248-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="2d248-113">Tyto třídy vyvolávají příkaz při kliknutí a stanou se pouze zdrojem příkazu, je-li nastavena jeho vlastnost <xref:System.Windows.Input.ICommandSource.Command%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d248-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="2d248-114">V tomto příkladu vyvoláte příkaz při přesunutí posuvníku nebo přesněji, když se změní vlastnost <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d248-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="2d248-115">Následuje definice třídy:</span><span class="sxs-lookup"><span data-stu-id="2d248-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="2d248-116">Dalším krokem je implementace <xref:System.Windows.Input.ICommandSource> členů.</span><span class="sxs-lookup"><span data-stu-id="2d248-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="2d248-117">V tomto příkladu jsou vlastnosti implementovány jako objekty <xref:System.Windows.DependencyProperty>.</span><span class="sxs-lookup"><span data-stu-id="2d248-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="2d248-118">To umožňuje, aby vlastnosti používaly datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="2d248-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="2d248-119">Další informace o třídě <xref:System.Windows.DependencyProperty> naleznete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d248-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="2d248-120">Další informace o datové vazbě najdete v tématu [Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d248-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="2d248-121">Tady je zobrazená jenom vlastnost <xref:System.Windows.Input.ICommandSource.Command%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d248-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>
 
[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="2d248-122">Následuje <xref:System.Windows.DependencyProperty> zpětného volání změny:</span><span class="sxs-lookup"><span data-stu-id="2d248-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="2d248-123">Dalším krokem je přidání a odebrání příkazu, který je přidružen ke zdroji příkazů.</span><span class="sxs-lookup"><span data-stu-id="2d248-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="2d248-124">Vlastnost <xref:System.Windows.Input.ICommandSource.Command%2A> nelze jednoduše přepsat při přidání nového příkazu, protože obslužné rutiny událostí přidružené k předchozímu příkazu (pokud existovaly), musí být nejprve odebrány.</span><span class="sxs-lookup"><span data-stu-id="2d248-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="2d248-125">Dalším krokem je vytvoření logiky pro obslužnou rutinu <xref:System.Windows.Input.ICommand.CanExecuteChanged>.</span><span class="sxs-lookup"><span data-stu-id="2d248-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="2d248-126">Událost <xref:System.Windows.Input.ICommand.CanExecuteChanged> upozorní zdroj příkazu, že se mohla změnit schopnost příkazu spustit na aktuálním cíli příkazu.</span><span class="sxs-lookup"><span data-stu-id="2d248-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="2d248-127">Když zdroj příkazu obdrží tuto událost, obvykle volá metodu <xref:System.Windows.Input.ICommand.CanExecute%2A> příkazu.</span><span class="sxs-lookup"><span data-stu-id="2d248-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="2d248-128">Pokud příkaz nelze provést na aktuálním cíli příkazu, bude zdroj příkazu obvykle zapínat sám sebe.</span><span class="sxs-lookup"><span data-stu-id="2d248-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="2d248-129">Pokud se příkaz může spustit na aktuálním cíli příkazu, bude zdroj příkazu obvykle umožňovat sám sebe.</span><span class="sxs-lookup"><span data-stu-id="2d248-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="2d248-130">Posledním krokem je metoda <xref:System.Windows.Input.ICommand.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d248-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="2d248-131">Pokud je příkaz <xref:System.Windows.Input.RoutedCommand>, je volána metoda <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A>; v opačném případě je volána metoda <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d248-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="2d248-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d248-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="2d248-133">Přehled příkazů</span><span class="sxs-lookup"><span data-stu-id="2d248-133">Commanding Overview</span></span>](commanding-overview.md)
