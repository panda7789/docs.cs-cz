---
title: "Neobecné ParallelForEach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eb019aed7fce267506ddb495609df5a80a8f8d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="0c8f6-102">Neobecné ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="0c8f6-102">Non-Generic ParallelForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="0c8f6-103">se dodává v jeho nástrojů sadu aktivity toku řízení, včetně <xref:System.Activities.Statements.ParallelForEach%601>, což umožňuje iterace v rámci <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` kolekce.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-103"> ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` collections.</span></span>  
  
 <span data-ttu-id="0c8f6-104"><xref:System.Activities.Statements.ParallelForEach%601>vyžaduje jeho <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> vlastnost, která má být typu <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`.</span></span> <span data-ttu-id="0c8f6-105">To vylučuje uživatelé z iterování přes datové struktury, které implementují <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` rozhraní (například <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="0c8f6-105">This precludes users from iterating over data structures that implement <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="0c8f6-106">Verze neobecnou <xref:System.Activities.Statements.ParallelForEach%601> překonává tento požadavek za cenu složitější běhu k zajištění kompatibility typů hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="0c8f6-107">Tento příklad ukazuje, jak implementovat není obecný <xref:System.Activities.Statements.ParallelForEach%601> aktivita a její designer.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="0c8f6-108">Tato aktivita lze použít k iteraci v rámci <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="parallelforeach-activity"></a><span data-ttu-id="0c8f6-109">ParallelForEach aktivity</span><span class="sxs-lookup"><span data-stu-id="0c8f6-109">ParallelForEach Activity</span></span>  
 <span data-ttu-id="0c8f6-110">C# / VB. `foreach` příkaz zobrazí prvky kolekce, provádění příkazu embedded pro každý prvek kolekce.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-110">The C#/VB `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="0c8f6-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Ekvivalentní aktivity jsou <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="0c8f6-112"><xref:System.Activities.Statements.ForEach%601> Aktivity obsahuje seznam hodnoty a text.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="0c8f6-113">V době běhu je vstupní seznamu a text je provést pro každou hodnotu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="0c8f6-114"><xref:System.Activities.Statements.ParallelForEach%601>má <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>tak, aby <xref:System.Activities.Statements.ParallelForEach%601> aktivity mohli dokončit již v rané fázi, pokud vyhodnocení <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="0c8f6-115"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Vyhodnotí po dokončení každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>  
  
 <span data-ttu-id="0c8f6-116">Pro většině případů obecné verze aktivity musí být upřednostňované řešení, protože pokrývá většinu scénářů, ve kterých se používá a poskytuje typ kontroly v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="0c8f6-117">Verze neobecnou lze použít pro iterace v rámci typy, které implementují neobecnou <xref:System.Collections.IEnumerable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="0c8f6-118">Definice třídy</span><span class="sxs-lookup"><span data-stu-id="0c8f6-118">Class Definition</span></span>  
 <span data-ttu-id="0c8f6-119">Následující příklad kódu ukazuje definici není obecný `ParallelForEach` aktivita.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>  
  
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
  
 <span data-ttu-id="0c8f6-120">Text (volitelné)</span><span class="sxs-lookup"><span data-stu-id="0c8f6-120">Body (optional)</span></span>  
 <span data-ttu-id="0c8f6-121"><xref:System.Activities.ActivityAction> Typu <xref:System.Object>, který je spouštěna každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="0c8f6-122">Každý jednotlivý prvek předána do těla jeho vlastnosti argumentu.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-122">Each individual element is passed into the Body through its Argument property.</span></span>  
  
 <span data-ttu-id="0c8f6-123">Hodnoty (volitelné)</span><span class="sxs-lookup"><span data-stu-id="0c8f6-123">Values (optional)</span></span>  
 <span data-ttu-id="0c8f6-124">Kolekce elementů, které jsou vstupní přes.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="0c8f6-125">Zajistíte, že všechny elementy kolekce typů kompatibilní se provádí za běhu.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
 <span data-ttu-id="0c8f6-126">CompletionCondition (volitelné)</span><span class="sxs-lookup"><span data-stu-id="0c8f6-126">CompletionCondition (optional)</span></span>  
 <span data-ttu-id="0c8f6-127"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Vlastnost vyhodnotí po dokončení všech iterací.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="0c8f6-128">Pokud je vyhodnocen jako `true`, pak naplánované čeká na opakování došlo ke zrušení.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="0c8f6-129">Pokud není tato vlastnost nastavena, všechny aktivity v kolekci větví spustit až do dokončení.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>  
  
## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="0c8f6-130">Příklad použití ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="0c8f6-130">Example of Using ParallelForEach</span></span>  
 <span data-ttu-id="0c8f6-131">Následující kód ukazuje, jak pomocí aktivity ParallelForEach v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>  
  
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
  
## <a name="parallelforeach-designer"></a><span data-ttu-id="0c8f6-132">Návrhář ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="0c8f6-132">ParallelForEach Designer</span></span>  
 <span data-ttu-id="0c8f6-133">Návrhář aktivity pro vzorovou se podobá vzhledu s návrháře zadaná pro integrované <xref:System.Activities.Statements.ParallelForEach%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="0c8f6-134">Návrhář se zobrazí v panelu nástrojů v **ukázky**, **aktivity obecného bez** kategorie.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="0c8f6-135">Návrhář jmenuje **ParallelForEachWithBodyFactory** v sadě nástrojů, protože zpřístupní aktivity <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivita s správně nakonfigurované <xref:System.Activities.ActivityAction>.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
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
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="0c8f6-136">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="0c8f6-136">To run the sample</span></span>  
  
1.  <span data-ttu-id="0c8f6-137">Nastavte projekt zvoleného jako spouštěný projekt řešení.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-137">Set the project of your choice as the startup project of the solution.</span></span>  
  
    1.  <span data-ttu-id="0c8f6-138">**CodeTestClient** ukazuje, jak pomocí aktivity pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-138">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2.  <span data-ttu-id="0c8f6-139">**DesignerTestClient** ukazuje, jak pomocí aktivity v návrháři.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2.  <span data-ttu-id="0c8f6-140">Sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-140">Build and run the project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0c8f6-141">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0c8f6-142">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0c8f6-142">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0c8f6-143">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0c8f6-144">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0c8f6-144">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
