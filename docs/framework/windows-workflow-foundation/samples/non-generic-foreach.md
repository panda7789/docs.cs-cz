---
title: Neobecná aktivita ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: a4bbc594ec0bf2d387e700508c7d92685216accc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715658"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="ee8ea-102">Neobecná aktivita ForEach</span><span class="sxs-lookup"><span data-stu-id="ee8ea-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="ee8ea-103">lodí ve své sadě nástrojů sadu aktivit toku řízení, včetně <xref:System.Activities.Statements.ForEach%601>, což umožňuje iteraci v kolekcích <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="ee8ea-104"><xref:System.Activities.Statements.ForEach%601> vyžaduje, aby vlastnost <xref:System.Activities.Statements.ForEach%601.Values%2A> byla typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="ee8ea-105">To uživatelům brání v iteracích v datových strukturách, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní (například <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="ee8ea-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="ee8ea-106">Neobecná verze <xref:System.Activities.Statements.ForEach%601> přebírá tento požadavek, na úkor více složitosti za běhu za účelem zajištění kompatibility typů hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="ee8ea-107">Tento příklad ukazuje, jak implementovat neobecnou <xref:System.Activities.Statements.ForEach%601> aktivitu a její Návrhář.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="ee8ea-108">Tuto aktivitu lze použít k iterování prostřednictvím <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="ee8ea-109">Aktivita ForEach</span><span class="sxs-lookup"><span data-stu-id="ee8ea-109">ForEach Activity</span></span>  
 <span data-ttu-id="ee8ea-110">Příkaz C#/VB `foreach` vytvoří výčet prvků kolekce a spustí vložený příkaz pro každý prvek kolekce.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="ee8ea-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] ekvivalentní aktivity `foreach` jsou <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="ee8ea-112">Aktivita <xref:System.Activities.Statements.ForEach%601> obsahuje seznam hodnot a textů.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="ee8ea-113">V době běhu se seznam opakuje a text se spustí pro každou hodnotu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="ee8ea-114">Ve většině případů by měla být obecná verze aktivity upřednostňovaným řešením, protože pokrývá většinu scénářů, ve kterých by se použily, a poskytuje kontrolu typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="ee8ea-115">Neobecnou verzi lze použít pro iteraci v rámci typů, které implementují neobecné <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="ee8ea-116">Definice třídy</span><span class="sxs-lookup"><span data-stu-id="ee8ea-116">Class Definition</span></span>  
 <span data-ttu-id="ee8ea-117">Následující příklad kódu ukazuje definici neobecného `ForEach` aktivity.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 <span data-ttu-id="ee8ea-118">Tělo (volitelné)</span><span class="sxs-lookup"><span data-stu-id="ee8ea-118">Body (optional)</span></span>  
 <span data-ttu-id="ee8ea-119"><xref:System.Activities.ActivityAction> typu <xref:System.Object>, který se spustí pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="ee8ea-120">Každý jednotlivý prvek je předán do těla prostřednictvím jeho vlastnosti `Argument`.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="ee8ea-121">Hodnoty (volitelné)</span><span class="sxs-lookup"><span data-stu-id="ee8ea-121">Values (optional)</span></span>  
 <span data-ttu-id="ee8ea-122">Kolekce prvků, které jsou iterované přes.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="ee8ea-123">Zajistěte, aby všechny prvky kolekce byly kompatibilní typy v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="ee8ea-124">Příklad použití příkazu ForEach</span><span class="sxs-lookup"><span data-stu-id="ee8ea-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="ee8ea-125">Následující kód ukazuje, jak použít aktivitu ForEach v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
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
  
|<span data-ttu-id="ee8ea-126">Podmínka</span><span class="sxs-lookup"><span data-stu-id="ee8ea-126">Condition</span></span>|<span data-ttu-id="ee8ea-127">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ee8ea-127">Message</span></span>|<span data-ttu-id="ee8ea-128">Závažnost</span><span class="sxs-lookup"><span data-stu-id="ee8ea-128">Severity</span></span>|<span data-ttu-id="ee8ea-129">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="ee8ea-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="ee8ea-130">Hodnoty jsou `null`</span><span class="sxs-lookup"><span data-stu-id="ee8ea-130">Values is `null`</span></span>|<span data-ttu-id="ee8ea-131">Hodnota argumentu ' Values ' pro požadovanou aktivitu nebyla zadána.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="ee8ea-132">Chyba</span><span class="sxs-lookup"><span data-stu-id="ee8ea-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="ee8ea-133">Návrhář ForEach</span><span class="sxs-lookup"><span data-stu-id="ee8ea-133">ForEach Designer</span></span>  
 <span data-ttu-id="ee8ea-134">Návrhář aktivity pro ukázku je podobný vzhledu pro návrháře poskytnutého pro integrovanou <xref:System.Activities.Statements.ForEach%601> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="ee8ea-135">Návrhář se zobrazí v sadě nástrojů v kategorii **ukázky**, **neobecné aktivity** .</span><span class="sxs-lookup"><span data-stu-id="ee8ea-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="ee8ea-136">Návrhář má název **ForEachWithBodyFactory** v sadě nástrojů, protože aktivita zpřístupňuje <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivitu s správně nakonfigurovanou <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="ee8ea-137">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="ee8ea-137">To run this sample</span></span>  
  
1. <span data-ttu-id="ee8ea-138">Nastavte projekt podle svého výběru jako spouštěcí projekt řešení:</span><span class="sxs-lookup"><span data-stu-id="ee8ea-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="ee8ea-139">**CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="ee8ea-140">**DesignerTestClient** ukazuje, jak používat aktivitu v návrháři.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="ee8ea-141">Sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ee8ea-142">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee8ea-143">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-143">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="ee8ea-144">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee8ea-145">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ee8ea-145">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
