---
title: Neobecná aktivita ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 70d5de587dda3cb61205a8d77f2173df9b93498b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210582"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="82b6e-102">Neobecná aktivita ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="82b6e-102">Non-Generic ParallelForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="82b6e-103"> ve svých nástrojů se dodává sadu tok řízení aktivit, včetně <xref:System.Activities.Statements.ParallelForEach%601>, který umožňuje procházení <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` kolekce.</span><span class="sxs-lookup"><span data-stu-id="82b6e-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.</span></span>  
  
 <span data-ttu-id="82b6e-104"><xref:System.Activities.Statements.ParallelForEach%601> vyžaduje jeho <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> vlastnost typu <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="82b6e-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span></span> <span data-ttu-id="82b6e-105">To vylučuje uživatele od iterování celého datové struktury, které implementují <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` rozhraní (třeba <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="82b6e-105">This precludes users from iterating over data structures that implement <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="82b6e-106">Obecné verzi <xref:System.Activities.Statements.ParallelForEach%601> překonává tento požadavek za cenu za běhu složitější pro zajištění kompatibility typy hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="82b6e-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="82b6e-107">Tento příklad ukazuje, jak implementovat neobecných <xref:System.Activities.Statements.ParallelForEach%601> aktivita a její návrháře.</span><span class="sxs-lookup"><span data-stu-id="82b6e-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="82b6e-108">Tuto aktivitu lze použít k iteraci v rámci <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="82b6e-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="parallelforeach-activity"></a><span data-ttu-id="82b6e-109">Použití aktivity ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="82b6e-109">ParallelForEach Activity</span></span>  
 <span data-ttu-id="82b6e-110">C# /VB `foreach` příkaz vytvoří výčet prvků kolekce, provádění vloženým příkazem pro každý prvek kolekce.</span><span class="sxs-lookup"><span data-stu-id="82b6e-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="82b6e-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Jsou ekvivalentní aktivity <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="82b6e-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="82b6e-112"><xref:System.Activities.Statements.ForEach%601> Aktivita obsahuje seznam hodnot a tělo.</span><span class="sxs-lookup"><span data-stu-id="82b6e-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="82b6e-113">Za běhu je provést iteraci seznamu a text je provedena pro každou hodnotu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="82b6e-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="82b6e-114"><xref:System.Activities.Statements.ParallelForEach%601> má <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>tak, aby <xref:System.Activities.Statements.ParallelForEach%601> aktivity může-li dokončeny včas vyhodnocení <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="82b6e-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="82b6e-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Je vyhodnocen po každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="82b6e-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>  
  
 <span data-ttu-id="82b6e-116">Pro většinu případů obecné verze aktivity musí být preferovaným řešením, protože zabírá většinu scénářů, ve kterých se používá a nabízí kontrolu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="82b6e-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="82b6e-117">Neobecnou verze může být použita pro iterace typy, které implementují neobecné <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="82b6e-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="82b6e-118">Definice třídy</span><span class="sxs-lookup"><span data-stu-id="82b6e-118">Class Definition</span></span>  
 <span data-ttu-id="82b6e-119">Následující příklad kódu ukazuje definice není obecný `ParallelForEach` aktivita.</span><span class="sxs-lookup"><span data-stu-id="82b6e-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>  
  
```  
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
  
 <span data-ttu-id="82b6e-120">Text (volitelné)</span><span class="sxs-lookup"><span data-stu-id="82b6e-120">Body (optional)</span></span>  
 <span data-ttu-id="82b6e-121"><xref:System.Activities.ActivityAction> Typu <xref:System.Object>, který je proveden pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="82b6e-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="82b6e-122">Každý jednotlivý prvek, jeho vlastnost Argument předána do datové části.</span><span class="sxs-lookup"><span data-stu-id="82b6e-122">Each individual element is passed into the Body through its Argument property.</span></span>  
  
 <span data-ttu-id="82b6e-123">Hodnoty (volitelné)</span><span class="sxs-lookup"><span data-stu-id="82b6e-123">Values (optional)</span></span>  
 <span data-ttu-id="82b6e-124">Kolekce prvků, které jsou provést iteraci.</span><span class="sxs-lookup"><span data-stu-id="82b6e-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="82b6e-125">Zajištění, že jsou všechny prvky kolekce typů kompatibilní se provádí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="82b6e-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
 <span data-ttu-id="82b6e-126">CompletionCondition (volitelné)</span><span class="sxs-lookup"><span data-stu-id="82b6e-126">CompletionCondition (optional)</span></span>  
 <span data-ttu-id="82b6e-127"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Vlastnost je vyhodnocen po dokončení všech iterací.</span><span class="sxs-lookup"><span data-stu-id="82b6e-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="82b6e-128">Pokud je vyhodnocen jako `true`, pak naplánované zrušení čekající iterací.</span><span class="sxs-lookup"><span data-stu-id="82b6e-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="82b6e-129">Pokud není tato vlastnost nastavena, všechny aktivity v kolekci větví spuštěno až do dokončení.</span><span class="sxs-lookup"><span data-stu-id="82b6e-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>  
  
## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="82b6e-130">Příklad použití ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="82b6e-130">Example of Using ParallelForEach</span></span>  
 <span data-ttu-id="82b6e-131">Následující kód ukazuje, jak pomocí aktivity ParallelForEach v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="82b6e-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>  
  
```  
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
  
## <a name="parallelforeach-designer"></a><span data-ttu-id="82b6e-132">Návrhář ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="82b6e-132">ParallelForEach Designer</span></span>  
 <span data-ttu-id="82b6e-133">Návrhář aktivity pro ukázku je podobné jako u vzhled do návrháře k dispozici pro předdefinované <xref:System.Activities.Statements.ParallelForEach%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="82b6e-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="82b6e-134">Návrhář se zobrazí na panelu nástrojů v **ukázky**, **neobecné aktivity** kategorie.</span><span class="sxs-lookup"><span data-stu-id="82b6e-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="82b6e-135">Návrháře jmenuje **ParallelForEachWithBodyFactory** v sadě nástrojů, protože zveřejňuje aktivity <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivita pomocí správně nakonfigurovaných <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="82b6e-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```  
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
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="82b6e-136">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="82b6e-136">To run the sample</span></span>  
  
1.  <span data-ttu-id="82b6e-137">Nastavte jako projekt po spuštění řešení projekt podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="82b6e-137">Set the project of your choice as the startup project of the solution.</span></span>  
  
    1.  <span data-ttu-id="82b6e-138">**CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="82b6e-138">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="82b6e-139">**DesignerTestClient** ukazuje, jak pomocí aktivity v návrháři.</span><span class="sxs-lookup"><span data-stu-id="82b6e-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="82b6e-140">Sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="82b6e-140">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82b6e-141">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="82b6e-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="82b6e-142">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="82b6e-142">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="82b6e-143">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="82b6e-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82b6e-144">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="82b6e-144">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
