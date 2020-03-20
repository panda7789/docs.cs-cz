---
title: Neobecná aktivita ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 08dbac3974915f823a4f6e39f35927453a7c4b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142703"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="dcacb-102">Neobecná aktivita ForEach</span><span class="sxs-lookup"><span data-stu-id="dcacb-102">Non-Generic ForEach</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="dcacb-103">do své sady nástrojů dodává soubor činností <xref:System.Activities.Statements.ForEach%601>kontrolního toku, <xref:System.Collections.Generic.IEnumerable%601> včetně , který umožňuje itací prostřednictvím sbírek.</span><span class="sxs-lookup"><span data-stu-id="dcacb-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="dcacb-104"><xref:System.Activities.Statements.ForEach%601>vyžaduje, <xref:System.Activities.Statements.ForEach%601.Values%2A> aby jeho <xref:System.Collections.Generic.IEnumerable%601>majetek byl typu .</span><span class="sxs-lookup"><span data-stu-id="dcacb-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="dcacb-105">To vylučuje uživatelům iterace přes datové <xref:System.Collections.Generic.IEnumerable%601> struktury, <xref:System.Collections.ArrayList>které implementují rozhraní (například).</span><span class="sxs-lookup"><span data-stu-id="dcacb-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="dcacb-106">Neobecná verze <xref:System.Activities.Statements.ForEach%601> překonává tento požadavek na úkor další složitosti za běhu pro zajištění kompatibility typů hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="dcacb-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="dcacb-107">Tato ukázka ukazuje, jak <xref:System.Activities.Statements.ForEach%601> implementovat neobecné aktivity a jeho návrháře.</span><span class="sxs-lookup"><span data-stu-id="dcacb-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="dcacb-108">Tuto aktivitu lze použít k <xref:System.Collections.ArrayList>iterátu prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="dcacb-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="dcacb-109">Foreach aktivity</span><span class="sxs-lookup"><span data-stu-id="dcacb-109">ForEach Activity</span></span>  
 <span data-ttu-id="dcacb-110">Příkaz jazyka C#/Visual Basic `foreach` obsahuje výčet prvků kolekce a provádí vložený příkaz pro každý prvek kolekce.</span><span class="sxs-lookup"><span data-stu-id="dcacb-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="dcacb-111">Rovnocenné [!INCLUDE[wf1](../../../../includes/wf1-md.md)] činnosti `foreach` jsou <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.ParallelForEach%601>a .</span><span class="sxs-lookup"><span data-stu-id="dcacb-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="dcacb-112">Aktivita <xref:System.Activities.Statements.ForEach%601> obsahuje seznam hodnot a tělo.</span><span class="sxs-lookup"><span data-stu-id="dcacb-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="dcacb-113">Za běhu je seznam iterován a tělo je spuštěno pro každou hodnotu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="dcacb-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="dcacb-114">Pro většinu případů obecná verze aktivity by měla být upřednostňovaným řešením, protože pokrývá většinu scénářů, ve kterých by se použila, a poskytuje kontrolu typů v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="dcacb-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="dcacb-115">Neobecnou verzi lze použít pro iterace prostřednictvím typů, <xref:System.Collections.IEnumerable> které implementují neobecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dcacb-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="dcacb-116">Definice třídy</span><span class="sxs-lookup"><span data-stu-id="dcacb-116">Class Definition</span></span>  
 <span data-ttu-id="dcacb-117">Následující příklad kódu ukazuje definici neobecné `ForEach` aktivity.</span><span class="sxs-lookup"><span data-stu-id="dcacb-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
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
  
 <span data-ttu-id="dcacb-118">Tělo (volitelné)</span><span class="sxs-lookup"><span data-stu-id="dcacb-118">Body (optional)</span></span>  
 <span data-ttu-id="dcacb-119">Typ <xref:System.Activities.ActivityAction> <xref:System.Object>, který je proveden pro každý prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="dcacb-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="dcacb-120">Každý jednotlivý prvek je předán `Argument` do těla prostřednictvím své vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dcacb-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="dcacb-121">Hodnoty (volitelné)</span><span class="sxs-lookup"><span data-stu-id="dcacb-121">Values (optional)</span></span>  
 <span data-ttu-id="dcacb-122">Kolekce prvků, které jsou iterovány nad.</span><span class="sxs-lookup"><span data-stu-id="dcacb-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="dcacb-123">Zajištění, že všechny prvky kolekce jsou kompatibilní typy se provádí za běhu.</span><span class="sxs-lookup"><span data-stu-id="dcacb-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="dcacb-124">Příklad použití ForEach</span><span class="sxs-lookup"><span data-stu-id="dcacb-124">Example of Using ForEach</span></span>  
 <span data-ttu-id="dcacb-125">Následující kód ukazuje, jak používat ForEach aktivity v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dcacb-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
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
  
|<span data-ttu-id="dcacb-126">Podmínka</span><span class="sxs-lookup"><span data-stu-id="dcacb-126">Condition</span></span>|<span data-ttu-id="dcacb-127">Zpráva</span><span class="sxs-lookup"><span data-stu-id="dcacb-127">Message</span></span>|<span data-ttu-id="dcacb-128">Severity</span><span class="sxs-lookup"><span data-stu-id="dcacb-128">Severity</span></span>|<span data-ttu-id="dcacb-129">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="dcacb-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="dcacb-130">Hodnoty jsou`null`</span><span class="sxs-lookup"><span data-stu-id="dcacb-130">Values is `null`</span></span>|<span data-ttu-id="dcacb-131">Hodnota pro argument požadované aktivity "Hodnoty" nebyla zadána.</span><span class="sxs-lookup"><span data-stu-id="dcacb-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="dcacb-132">Chyba</span><span class="sxs-lookup"><span data-stu-id="dcacb-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="dcacb-133">Návrhář Foreach</span><span class="sxs-lookup"><span data-stu-id="dcacb-133">ForEach Designer</span></span>  
 <span data-ttu-id="dcacb-134">Návrhář aktivity pro ukázku má podobný vzhled jako návrhář, <xref:System.Activities.Statements.ForEach%601> který je k dispozici pro předdefinovanou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="dcacb-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="dcacb-135">Návrhář se zobrazí v panelu nástrojů v kategorii **Ukázky**, **Neobecné aktivity.**</span><span class="sxs-lookup"><span data-stu-id="dcacb-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="dcacb-136">Návrhář se nazývá **ForEachWithBodyFactory** v panelu nástrojů, <xref:System.Activities.Presentation.IActivityTemplateFactory> protože aktivita zpřístupňuje v panelu <xref:System.Activities.ActivityAction>nástrojů, který vytvoří aktivitu s správně nakonfigurované .</span><span class="sxs-lookup"><span data-stu-id="dcacb-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="dcacb-137">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="dcacb-137">To run this sample</span></span>  
  
1. <span data-ttu-id="dcacb-138">Nastavte projekt podle svého výběru jako počáteční projekt řešení:</span><span class="sxs-lookup"><span data-stu-id="dcacb-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="dcacb-139">**CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="dcacb-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="dcacb-140">**DesignerTestClient** ukazuje, jak používat aktivitu v rámci návrháře.</span><span class="sxs-lookup"><span data-stu-id="dcacb-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="dcacb-141">Sestavení a spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="dcacb-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dcacb-142">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="dcacb-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dcacb-143">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="dcacb-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dcacb-144">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="dcacb-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dcacb-145">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="dcacb-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
