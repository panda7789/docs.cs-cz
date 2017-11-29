---
title: "Vystavení dat s CacheMetadata"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aea620d740b7b95747395821d622f267943352da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="21788-102">Vystavení dat s CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="21788-102">Exposing data with CacheMetadata</span></span>
<span data-ttu-id="21788-103">Před provedením aktivitu, modulu runtime pracovního postupu získá všechny informace o aktivitě, která je nutné, aby byla zachována jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="21788-103">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="21788-104">Získá tyto informace při provádění modulu runtime pracovního postupu <xref:System.Activities.Activity.CacheMetadata%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="21788-104">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="21788-105">Výchozí implementace této metody poskytuje modul runtime s všechny veřejné argumenty, proměnné a podřízené aktivity vystavené aktivity v době, kdy je se provedla; Pokud aktivita musí poskytnout další informace pro modul runtime než to (například soukromé členy, nebo aktivity plánování pomocí aktivity), k tomu lze přepsat tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="21788-105">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>  
  
## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="21788-106">Výchozí chování CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="21788-106">Default CacheMetadata behavior</span></span>  
 <span data-ttu-id="21788-107">Výchozí implementaci <xref:System.Activities.NativeActivity.CacheMetadata%2A> pro aktivity, které jsou odvozeny od <xref:System.Activities.NativeActivity> zpracovává následující typy metoda následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="21788-107">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>  
  
-   <span data-ttu-id="21788-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, nebo <xref:System.Activities.InOutArgument%601> (obecné argumenty): tyto argumenty jsou zveřejněné modulu runtime jako argumenty s názvem a zadejte rovna zveřejněné vlastnost název a typ, směr odpovídající argument a některá data ověření.</span><span class="sxs-lookup"><span data-stu-id="21788-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>  
  
-   <span data-ttu-id="21788-109"><xref:System.Activities.Variable>nebo jakékoli její podtřídou: tito členové jsou viditelné na modulu runtime jako veřejné proměnné.</span><span class="sxs-lookup"><span data-stu-id="21788-109"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>  
  
-   <span data-ttu-id="21788-110"><xref:System.Activities.Activity>nebo jakékoli její podtřídou: tito členové jsou viditelné na modulu runtime jako veřejné podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="21788-110"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="21788-111">Výchozí chování může být implementováno výslovně voláním <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>a předejte podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="21788-111">The default behavior can be implemented explicity by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>  
  
-   <span data-ttu-id="21788-112"><xref:System.Activities.ActivityDelegate>nebo jakékoli její podtřídou: tito členové jsou viditelné na modulu runtime jako veřejné delegáti.</span><span class="sxs-lookup"><span data-stu-id="21788-112"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>  
  
-   <span data-ttu-id="21788-113"><xref:System.Collections.ICollection>typu <xref:System.Activities.Variable>: všechny elementy v kolekci jsou viditelné na modulu runtime jako veřejné proměnné.</span><span class="sxs-lookup"><span data-stu-id="21788-113"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>  
  
-   <span data-ttu-id="21788-114"><xref:System.Collections.ICollection>typu <xref:System.Activities.Activity>: všechny elementy v kolekci jsou viditelné na modulu runtime jako veřejné podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="21788-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>  
  
-   <span data-ttu-id="21788-115"><xref:System.Collections.ICollection>typu <xref:System.Activities.ActivityDelegate>: všechny elementy v kolekci jsou viditelné na modulu runtime jako veřejné delegáti.</span><span class="sxs-lookup"><span data-stu-id="21788-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>  
  
 <span data-ttu-id="21788-116"><xref:System.Activities.Activity.CacheMetadata%2A> Pro aktivity, které jsou odvozeny od <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, a <xref:System.Activities.AsyncCodeActivity> také fungovat jako výše, vyjma následujících rozdílů:</span><span class="sxs-lookup"><span data-stu-id="21788-116">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>  
  
-   <span data-ttu-id="21788-117">Třídy, které jsou odvozeny od <xref:System.Activities.Activity> nelze naplánovat podřízené aktivity nebo delegáti, takže tito členové jsou zveřejněné jako importované podřízené objekty a delegáti;</span><span class="sxs-lookup"><span data-stu-id="21788-117">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>  
  
-   <span data-ttu-id="21788-118">Třídy, které jsou odvozeny od <xref:System.Activities.CodeActivity> a <xref:System.Activities.AsyncCodeActivity> nepodporují proměnné, děti nebo delegáti, takže se zveřejní pouze argumenty.</span><span class="sxs-lookup"><span data-stu-id="21788-118">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>  
  
## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="21788-119">Přepsání CacheMetadata poskytovat informace o modulu runtime</span><span class="sxs-lookup"><span data-stu-id="21788-119">Overriding CacheMetadata to provide information to the runtime</span></span>  
 <span data-ttu-id="21788-120">Následující fragment kódu ukazuje, jak přidat informace o členech do metadat aktivity během provádění <xref:System.Activities.Activity.CacheMetadata%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="21788-120">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="21788-121">Všimněte si, že základní metoda je volána pro ukládání do mezipaměti všechny veřejná data o aktivitě.</span><span class="sxs-lookup"><span data-stu-id="21788-121">Note that the base of the method is called to cache all public data about the activity.</span></span>  
  
```  
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
  
## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="21788-122">Pomocí CacheMetadata vystavit implementace podřízené objekty</span><span class="sxs-lookup"><span data-stu-id="21788-122">Using CacheMetadata to expose implementation children</span></span>  
 <span data-ttu-id="21788-123">Chcete-li předat data do podřízené aktivity, které chcete naplánovat aktivitou pomocí proměnných, je potřeba přidat proměnné jako proměnné implementace; veřejné proměnné nemůže mít jejich hodnotami nastavenými tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="21788-123">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="21788-124">Důvodem je, že aktivity mají za cíl více provést, protože implementace funkce (která mají parametry), nikoli zapouzdřené třídy (která mají vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="21788-124">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="21788-125">Existují však situace, ve kterých jsou argumenty musí být explicitně nastaveny, například při použití <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, od naplánovanou činností nemá přístup k nadřazené aktivity argumenty způsobem by podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="21788-125">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>  
  
 <span data-ttu-id="21788-126">Následující fragment kódu ukazuje, jak má být předán formuláře argument nativní aktivity naplánované aktivity pomocí <xref:System.Activities.Activity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="21788-126">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>  
  
```  
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
