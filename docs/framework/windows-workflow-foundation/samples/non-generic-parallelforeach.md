---
title: Neobecná ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 33e0c8ef8c04b7d58815760ae1152f63891fdfd5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715646"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="da0d7-102">Neobecná ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="da0d7-102">Non-generic ParallelForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="da0d7-103">lodí ve své sadě nástrojů sadu aktivit toku řízení, včetně <xref:System.Activities.Statements.ParallelForEach%601>, což umožňuje iteraci v kolekcích <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="da0d7-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>

<span data-ttu-id="da0d7-104"><xref:System.Activities.Statements.ParallelForEach%601> vyžaduje, aby vlastnost <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> byla typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="da0d7-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type  <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="da0d7-105">To uživatelům brání v iteracích v datových strukturách, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní (například <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="da0d7-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="da0d7-106">Neobecná verze <xref:System.Activities.Statements.ParallelForEach%601> přebírá tento požadavek, na úkor více složitosti za běhu za účelem zajištění kompatibility typů hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="da0d7-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>

<span data-ttu-id="da0d7-107">Tento příklad ukazuje, jak implementovat neobecnou <xref:System.Activities.Statements.ParallelForEach%601> aktivitu a její Návrhář.</span><span class="sxs-lookup"><span data-stu-id="da0d7-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="da0d7-108">Tuto aktivitu lze použít k iterování prostřednictvím <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="da0d7-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>

## <a name="parallelforeach-activity"></a><span data-ttu-id="da0d7-109">Aktivita ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="da0d7-109">ParallelForEach activity</span></span>

<span data-ttu-id="da0d7-110">Příkaz C#/VB `foreach` vytvoří výčet prvků kolekce a spustí vložený příkaz pro každý prvek kolekce.</span><span class="sxs-lookup"><span data-stu-id="da0d7-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="da0d7-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] ekvivalentní aktivity jsou <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="da0d7-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="da0d7-112">Aktivita <xref:System.Activities.Statements.ForEach%601> obsahuje seznam hodnot a textů.</span><span class="sxs-lookup"><span data-stu-id="da0d7-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="da0d7-113">V době běhu se seznam opakuje a text se spustí pro každou hodnotu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="da0d7-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>

<span data-ttu-id="da0d7-114"><xref:System.Activities.Statements.ParallelForEach%601> má <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, aby byla <xref:System.Activities.Statements.ParallelForEach%601> aktivita dokončena včas, pokud vyhodnocení <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="da0d7-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="da0d7-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> se vyhodnocuje po dokončení každé iterace.</span><span class="sxs-lookup"><span data-stu-id="da0d7-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>

<span data-ttu-id="da0d7-116">Ve většině případů by měla být obecná verze aktivity upřednostňovaným řešením, protože pokrývá většinu scénářů, ve kterých se používá, a poskytuje kontrolu typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="da0d7-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="da0d7-117">Neobecnou verzi lze použít pro iteraci v rámci typů, které implementují neobecné <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="da0d7-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>

## <a name="class-definition"></a><span data-ttu-id="da0d7-118">Definice třídy</span><span class="sxs-lookup"><span data-stu-id="da0d7-118">Class definition</span></span>

<span data-ttu-id="da0d7-119">Následující příklad kódu ukazuje definici neobecného `ParallelForEach` aktivity je.</span><span class="sxs-lookup"><span data-stu-id="da0d7-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

<span data-ttu-id="da0d7-120">Tělo (volitelné) </span><span class="sxs-lookup"><span data-stu-id="da0d7-120">Body (optional)</span></span>\
<span data-ttu-id="da0d7-121"><xref:System.Activities.ActivityAction> typu <xref:System.Object>, který se spustí pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="da0d7-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="da0d7-122">Každý jednotlivý prvek je předán do těla prostřednictvím jeho vlastnosti argumentu.</span><span class="sxs-lookup"><span data-stu-id="da0d7-122">Each individual element is passed into the Body through its Argument property.</span></span>

<span data-ttu-id="da0d7-123">Hodnoty (volitelné) </span><span class="sxs-lookup"><span data-stu-id="da0d7-123">Values (optional)</span></span>\
<span data-ttu-id="da0d7-124">Kolekce prvků, které jsou iterované přes.</span><span class="sxs-lookup"><span data-stu-id="da0d7-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="da0d7-125">Zajistěte, aby všechny prvky kolekce byly kompatibilní typy v době běhu.</span><span class="sxs-lookup"><span data-stu-id="da0d7-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>

<span data-ttu-id="da0d7-126">CompletionCondition (volitelné) </span><span class="sxs-lookup"><span data-stu-id="da0d7-126">CompletionCondition (optional)</span></span>\
<span data-ttu-id="da0d7-127">Vlastnost <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> je vyhodnocena po dokončení jakékoli iterace.</span><span class="sxs-lookup"><span data-stu-id="da0d7-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="da0d7-128">Pokud se vyhodnotí jako `true`, naplánovaných nevyřízených iterací se zruší.</span><span class="sxs-lookup"><span data-stu-id="da0d7-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="da0d7-129">Pokud tato vlastnost není nastavená, všechny aktivity v kolekci větví se spustí až do dokončení.</span><span class="sxs-lookup"><span data-stu-id="da0d7-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>

## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="da0d7-130">Příklad použití ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="da0d7-130">Example of using ParallelForEach</span></span>

<span data-ttu-id="da0d7-131">Následující kód ukazuje, jak používat aktivitu ParallelForEach v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="da0d7-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a><span data-ttu-id="da0d7-132">Návrhář ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="da0d7-132">ParallelForEach designer</span></span>

<span data-ttu-id="da0d7-133">Návrhář aktivity pro ukázku je podobný vzhledu pro návrháře poskytnutého pro integrovanou <xref:System.Activities.Statements.ParallelForEach%601> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="da0d7-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="da0d7-134">Návrhář se zobrazí v sadě nástrojů v kategorii **ukázky**, **neobecné aktivity** .</span><span class="sxs-lookup"><span data-stu-id="da0d7-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="da0d7-135">Návrhář má název **ParallelForEachWithBodyFactory** v sadě nástrojů, protože aktivita zpřístupňuje <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivitu s správně nakonfigurovanou <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="da0d7-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a><span data-ttu-id="da0d7-136">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="da0d7-136">To run the sample</span></span>

1. <span data-ttu-id="da0d7-137">Nastavte zvolený projekt jako projekt po spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="da0d7-137">Set the project of your choice as the startup project of the solution.</span></span>

    1. <span data-ttu-id="da0d7-138">**CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="da0d7-138">**CodeTestClient** shows how to use the activity using code.</span></span>

    2. <span data-ttu-id="da0d7-139">**DesignerTestClient** ukazuje, jak používat aktivitu v návrháři.</span><span class="sxs-lookup"><span data-stu-id="da0d7-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>

2. <span data-ttu-id="da0d7-140">Sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="da0d7-140">Build and run the project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="da0d7-141">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="da0d7-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="da0d7-142">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="da0d7-142">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="da0d7-143">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="da0d7-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="da0d7-144">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="da0d7-144">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
