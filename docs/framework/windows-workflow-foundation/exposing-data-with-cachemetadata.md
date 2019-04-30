---
title: Zveřejnění dat pomocí CacheMetadata
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: a044c896e56541ee954fc33853376eb8293c6ede
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945701"
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="21e74-102">Zveřejnění dat pomocí CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="21e74-102">Exposing data with CacheMetadata</span></span>

<span data-ttu-id="21e74-103">Před provedením aktivity, modulu runtime pracovního postupu získá všechny informace o aktivitě, která potřebuje, aby byla zachována jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="21e74-103">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="21e74-104">Získá tyto informace při provádění modulu runtime pracovního postupu <xref:System.Activities.Activity.CacheMetadata%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="21e74-104">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="21e74-105">Výchozí implementace této metody poskytuje modul runtime se všemi veřejné argumenty, proměnných a podřízené aktivity, které jsou vystavené aktivity v době, kdy je spuštěn; Pokud aktivita musí poskytovat další informace k modulu runtime než to (například soukromé členy nebo aktivity k naplánování aktivita), tato metoda může být potlačena za účelem ho zadat.</span><span class="sxs-lookup"><span data-stu-id="21e74-105">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>

## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="21e74-106">Výchozí chování CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="21e74-106">Default CacheMetadata behavior</span></span>

<span data-ttu-id="21e74-107">Výchozí implementace <xref:System.Activities.NativeActivity.CacheMetadata%2A> pro aktivity, které jsou odvozeny z <xref:System.Activities.NativeActivity> zpracovává následující typy metoda následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="21e74-107">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>

- <span data-ttu-id="21e74-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, nebo <xref:System.Activities.InOutArgument%601> (obecné argumenty): Tyto argumenty jsou vystaveny jako argumenty s názvem modulu runtime a zadejte rovna vystavené název a typ, směr příslušnou argumentem a některá data ověření.</span><span class="sxs-lookup"><span data-stu-id="21e74-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>

- <span data-ttu-id="21e74-109"><xref:System.Activities.Variable> nebo jakékoliv podtřídy jejich: Tyto členy jsou vystaveny pro modul runtime jako veřejné proměnné.</span><span class="sxs-lookup"><span data-stu-id="21e74-109"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="21e74-110"><xref:System.Activities.Activity> nebo jakékoliv podtřídy jejich: Tyto členy jsou vystaveny pro modul runtime jako veřejné podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="21e74-110"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="21e74-111">Výchozí chování můžete implementovat explicitně voláním <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>a předejte podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="21e74-111">The default behavior can be implemented explicitly by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>

- <span data-ttu-id="21e74-112"><xref:System.Activities.ActivityDelegate> nebo jakékoliv podtřídy jejich: Tyto členy jsou vystaveny modul runtime jako veřejné delegátů.</span><span class="sxs-lookup"><span data-stu-id="21e74-112"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>

- <span data-ttu-id="21e74-113"><xref:System.Collections.ICollection> typu <xref:System.Activities.Variable>: Všechny elementy v kolekci jsou vystaveny pro modul runtime jako veřejné proměnné.</span><span class="sxs-lookup"><span data-stu-id="21e74-113"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="21e74-114"><xref:System.Collections.ICollection> typu <xref:System.Activities.Activity>: Všechny elementy v kolekci jsou vystaveny pro modul runtime jako veřejné podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="21e74-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>

- <span data-ttu-id="21e74-115"><xref:System.Collections.ICollection> typu <xref:System.Activities.ActivityDelegate>: Všechny elementy v kolekci jsou vystaveny modul runtime jako veřejné delegátů.</span><span class="sxs-lookup"><span data-stu-id="21e74-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>

<span data-ttu-id="21e74-116"><xref:System.Activities.Activity.CacheMetadata%2A> Pro aktivity, které jsou odvozeny z <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, a <xref:System.Activities.AsyncCodeActivity> také funkci jak je uvedeno výše, vyjma následujících rozdílů:</span><span class="sxs-lookup"><span data-stu-id="21e74-116">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>

- <span data-ttu-id="21e74-117">Třídy, které jsou odvozeny z <xref:System.Activities.Activity> nelze naplánovat podřízených aktivit nebo delegátů, tak, aby takové členy jsou vystaveny jako importované podřízené položky a delegáti;</span><span class="sxs-lookup"><span data-stu-id="21e74-117">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>

- <span data-ttu-id="21e74-118">Třídy, které jsou odvozeny z <xref:System.Activities.CodeActivity> a <xref:System.Activities.AsyncCodeActivity> nepodporují proměnné, podřízené položky nebo delegátů, takže budou přístupné pouze argumenty.</span><span class="sxs-lookup"><span data-stu-id="21e74-118">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="21e74-119">Přepsání CacheMetadata poskytnout informace o modulu runtime</span><span class="sxs-lookup"><span data-stu-id="21e74-119">Overriding CacheMetadata to provide information to the runtime</span></span>

<span data-ttu-id="21e74-120">Následující fragment kódu ukazuje, jak přidat informace o členech metadat aktivity během provádění <xref:System.Activities.Activity.CacheMetadata%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="21e74-120">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="21e74-121">Všimněte si, že základní metoda je volána pro ukládání do mezipaměti všechny veřejné dat o aktivitě.</span><span class="sxs-lookup"><span data-stu-id="21e74-121">Note that the base of the method is called to cache all public data about the activity.</span></span>

```csharp
protected override void CacheMetadata(NativeActivityMetadata metadata)
{
    base.CacheMetadata(metadata);
    metadata.AddImplementationChild(this._writeLine);
    metadata.AddVariable(this._myVariable);
    metadata.AddImplementationVariable(this._myImplementationVariable);

    RuntimeArgument argument = new RuntimeArgument("MyArgument", ArgumentDirection.In, typeof(SomeType));
    metadata.Bind(argument, this.SomeName);
    metadata.AddArgument(argument);
}
```

## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="21e74-122">Pomocí CacheMetadata vystavit podřízené položky implementace</span><span class="sxs-lookup"><span data-stu-id="21e74-122">Using CacheMetadata to expose implementation children</span></span>

<span data-ttu-id="21e74-123">Chcete-li předat data do podřízené aktivity, které jsou k naplánování aktivitou pomocí proměnných, je potřeba přidat proměnné jako proměnné implementace; veřejné proměnné nemůžou mít jejich hodnoty nastavit tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="21e74-123">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="21e74-124">Důvodem je, že aktivity mají více provést, protože implementace funkce (které mají parametry), a ne zapouzdřený objekt třídy (které mají vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="21e74-124">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="21e74-125">Existují však situace, ve kterých jsou argumenty musí být explicitně nastaveny, například při použití <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, protože naplánované aktivity nemá přístup k Nadřazená aktivita argumentů tak, jak by podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="21e74-125">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>

<span data-ttu-id="21e74-126">Následující fragment kódu ukazuje, jak má být předán formulář argument nativní aktivity naplánované aktivity pomocí <xref:System.Activities.Activity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="21e74-126">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>

```csharp
public sealed class ChildActivity : NativeActivity
{
    public WriteLine _writeLine;
    public InArgument<string> Message { get; set; }
    private Variable<string> MessageVariable { get; set; }
    public ChildActivity()
    {
        MessageVariable = new Variable<string>();
        _writeLine = new WriteLine
        {
            Text = new InArgument<string>(MessageVariable),
        };
    }
    protected override void CacheMetadata(NativeActivityMetadata metadata)
    {
        base.CacheMetadata(metadata);
        metadata.AddImplementationVariable(this.MessageVariable);
        metadata.AddImplementationChild(this._writeLine);
    }
    protected override void Execute(NativeActivityContext context)
    {
        string configuredMessage = context.GetValue(Message);
        context.SetValue(MessageVariable, configuredMessage);
        context.ScheduleActivity(this._writeLine);
    }
}
```
