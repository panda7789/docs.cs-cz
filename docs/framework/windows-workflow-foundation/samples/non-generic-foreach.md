---
title: Neobecná aktivita ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 0274cd5b87e6039ff40afa3108986ffd113fc4fb
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478315"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="37deb-102">Neobecná aktivita ForEach</span><span class="sxs-lookup"><span data-stu-id="37deb-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="37deb-103"> ve svých nástrojů se dodává sadu tok řízení aktivit, včetně <xref:System.Activities.Statements.ForEach%601>, který umožňuje procházení <xref:System.Collections.Generic.IEnumerable%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="37deb-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="37deb-104"><xref:System.Activities.Statements.ForEach%601> vyžaduje jeho <xref:System.Activities.Statements.ForEach%601.Values%2A> vlastnost typu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="37deb-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="37deb-105">To vylučuje uživatele od iterování celého datové struktury, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní (třeba <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="37deb-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="37deb-106">Obecné verzi <xref:System.Activities.Statements.ForEach%601> překonává tento požadavek za cenu za běhu složitější pro zajištění kompatibility typy hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="37deb-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="37deb-107">Tento příklad ukazuje, jak implementovat neobecných <xref:System.Activities.Statements.ForEach%601> aktivita a její návrháře.</span><span class="sxs-lookup"><span data-stu-id="37deb-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="37deb-108">Tuto aktivitu lze použít k iteraci v rámci <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="37deb-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="37deb-109">Aktivita ForEach</span><span class="sxs-lookup"><span data-stu-id="37deb-109">ForEach Activity</span></span>  
 <span data-ttu-id="37deb-110">C# /VB `foreach` příkaz vytvoří výčet prvků kolekce, provádění vloženým příkazem pro každý prvek kolekce.</span><span class="sxs-lookup"><span data-stu-id="37deb-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="37deb-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Ekvivalentní činnosti `foreach` jsou <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="37deb-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="37deb-112"><xref:System.Activities.Statements.ForEach%601> Aktivita obsahuje seznam hodnot a tělo.</span><span class="sxs-lookup"><span data-stu-id="37deb-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="37deb-113">Za běhu je provést iteraci seznamu a text je provedena pro každou hodnotu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="37deb-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="37deb-114">Pro většinu případů obecné verze aktivity musí být preferovaným řešením, protože zabírá většinu scénářů, ve kterých by se použily a poskytuje kontrolu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="37deb-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="37deb-115">Neobecnou verze může být použita pro iterace typy, které implementují neobecné <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="37deb-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="37deb-116">Definice třídy</span><span class="sxs-lookup"><span data-stu-id="37deb-116">Class Definition</span></span>  
 <span data-ttu-id="37deb-117">Následující příklad kódu ukazuje definice není obecný `ForEach` aktivity.</span><span class="sxs-lookup"><span data-stu-id="37deb-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```  
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
  
 <span data-ttu-id="37deb-118">Text (volitelné)</span><span class="sxs-lookup"><span data-stu-id="37deb-118">Body (optional)</span></span>  
 <span data-ttu-id="37deb-119"><xref:System.Activities.ActivityAction> Typu <xref:System.Object>, který je proveden pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="37deb-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="37deb-120">Každý jednotlivý prvek je předán do datové části prostřednictvím jeho `Argument` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="37deb-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="37deb-121">Hodnoty (volitelné)</span><span class="sxs-lookup"><span data-stu-id="37deb-121">Values (optional)</span></span>  
 <span data-ttu-id="37deb-122">Kolekce prvků, které jsou provést iteraci.</span><span class="sxs-lookup"><span data-stu-id="37deb-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="37deb-123">Zajištění, že jsou všechny prvky kolekce typů kompatibilní se provádí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="37deb-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="37deb-124">Příklad použití příkazu ForEach</span><span class="sxs-lookup"><span data-stu-id="37deb-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="37deb-125">Následující kód ukazuje, jak pomocí aktivity ForEach v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37deb-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```  
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
  
|<span data-ttu-id="37deb-126">Podmínka</span><span class="sxs-lookup"><span data-stu-id="37deb-126">Condition</span></span>|<span data-ttu-id="37deb-127">Zpráva</span><span class="sxs-lookup"><span data-stu-id="37deb-127">Message</span></span>|<span data-ttu-id="37deb-128">Závažnost</span><span class="sxs-lookup"><span data-stu-id="37deb-128">Severity</span></span>|<span data-ttu-id="37deb-129">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="37deb-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="37deb-130">Hodnoty `null`</span><span class="sxs-lookup"><span data-stu-id="37deb-130">Values is `null`</span></span>|<span data-ttu-id="37deb-131">Nebyla zadána hodnota pro povinný argument aktivity "Hodnoty".</span><span class="sxs-lookup"><span data-stu-id="37deb-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="37deb-132">Chyba</span><span class="sxs-lookup"><span data-stu-id="37deb-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="37deb-133">Návrhář ForEach</span><span class="sxs-lookup"><span data-stu-id="37deb-133">ForEach Designer</span></span>  
 <span data-ttu-id="37deb-134">Návrhář aktivity pro ukázku je podobné jako u vzhled do návrháře k dispozici pro předdefinované <xref:System.Activities.Statements.ForEach%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="37deb-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="37deb-135">Návrhář se zobrazí na panelu nástrojů v **ukázky**, **neobecné aktivity** kategorie.</span><span class="sxs-lookup"><span data-stu-id="37deb-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="37deb-136">Návrháře jmenuje **ForEachWithBodyFactory** v sadě nástrojů, protože zveřejňuje aktivity <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivita s správně nakonfigurovaný <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="37deb-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="37deb-137">Tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="37deb-137">To run this sample</span></span>  
  
1.  <span data-ttu-id="37deb-138">Nastavte projekt podle vašeho výběru jako spouštěcí projekt řešení:</span><span class="sxs-lookup"><span data-stu-id="37deb-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1.  <span data-ttu-id="37deb-139">**CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="37deb-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="37deb-140">**DesignerTestClient** ukazuje, jak pomocí aktivity v návrháři.</span><span class="sxs-lookup"><span data-stu-id="37deb-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="37deb-141">Sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="37deb-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37deb-142">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="37deb-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="37deb-143">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="37deb-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="37deb-144">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="37deb-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37deb-145">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="37deb-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
