---
title: "Vlastní aktivity k přepínači na rozsahu hodnot"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2f422c4001c2e6ec46fc796e8dbf1b85e6a2b77
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-activity-to-switch-on-a-range-of-values"></a><span data-ttu-id="725fd-102">Vlastní aktivity k přepínači na rozsahu hodnot</span><span class="sxs-lookup"><span data-stu-id="725fd-102">Custom Activity to Switch on a Range of Values</span></span>
<span data-ttu-id="725fd-103">Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která rozšiřuje použití <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="725fd-103">This sample demonstrates how to create a custom activity that extends the use of a <xref:System.Activities.Statements.Switch%601>.</span></span> <span data-ttu-id="725fd-104">Konvenční <xref:System.Activities.Statements.Switch%601> příkaz umožňuje přepnutí na základě jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="725fd-104">A conventional <xref:System.Activities.Statements.Switch%601> statement allows switching based upon a single value.</span></span> <span data-ttu-id="725fd-105">Ale existují obchodní scénáře, kde musí přejít aktivitu na základě rozsahu hodnot.</span><span class="sxs-lookup"><span data-stu-id="725fd-105">But, there are business scenarios where an activity must switch based upon a range of values.</span></span> <span data-ttu-id="725fd-106">Například aktivita může provést jednu akci, pokud je hodnota přepnut na 1 až 5, další akci, pokud je hodnota 6 až 10 a výchozí akce pro všechny ostatní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="725fd-106">For example, an activity might execute one action when the value being switched upon is between 1 and 5, another action when the value is between 6 and 10, and a default action for all other values.</span></span> <span data-ttu-id="725fd-107">Tato vlastní aktivita umožňuje přesně tento scénář.</span><span class="sxs-lookup"><span data-stu-id="725fd-107">This custom activity enables exactly that scenario.</span></span>  
  
## <a name="the-switchrange-activity"></a><span data-ttu-id="725fd-108">SwitchRange aktivity</span><span class="sxs-lookup"><span data-stu-id="725fd-108">The SwitchRange Activity</span></span>  
 <span data-ttu-id="725fd-109">`SwitchRange` Aktivity plány podřízené aktivity, pokud je hodnota výsledek jejího výrazu zahrnuté v rozsahu mezi jeho `Cases`.</span><span class="sxs-lookup"><span data-stu-id="725fd-109">The `SwitchRange` activity schedules a child activity when the result value of its expression is included within the range of one of its `Cases`.</span></span>  
  
 <span data-ttu-id="725fd-110">Následující příklad kódu je vlastní aktivity, které přepínače na základě rozsahu hodnot.</span><span class="sxs-lookup"><span data-stu-id="725fd-110">The following code example is a custom activity that switches based upon a range of values.</span></span>  
  
```csharp  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|<span data-ttu-id="725fd-111">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="725fd-111">Property</span></span>|<span data-ttu-id="725fd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="725fd-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="725fd-113">Výraz</span><span class="sxs-lookup"><span data-stu-id="725fd-113">Expression</span></span>|<span data-ttu-id="725fd-114">Toto je výraz, který se vyhodnotí a porovná s rozsahy v seznamu případů.</span><span class="sxs-lookup"><span data-stu-id="725fd-114">This is the expression to be evaluated and compared against the ranges in the Cases list.</span></span> <span data-ttu-id="725fd-115">Výsledkem výrazu je typu T.</span><span class="sxs-lookup"><span data-stu-id="725fd-115">The result of the expression is of type T.</span></span>|  
|<span data-ttu-id="725fd-116">Případy</span><span class="sxs-lookup"><span data-stu-id="725fd-116">Cases</span></span>|<span data-ttu-id="725fd-117">Každý případ se skládá z rozsah (od a do) a aktivitu (text).</span><span class="sxs-lookup"><span data-stu-id="725fd-117">Each case consists of a range (From and To) and an activity (Body).</span></span> <span data-ttu-id="725fd-118">Výraz je vyhodnocena a porovná s rozsahy.</span><span class="sxs-lookup"><span data-stu-id="725fd-118">The expression is evaluated and compared against the ranges.</span></span> <span data-ttu-id="725fd-119">Pokud je výsledek výrazu v rozsahu mezi v případech, bude odpovídající aktivita se spustí.</span><span class="sxs-lookup"><span data-stu-id="725fd-119">If the result of the expression is within the range of one of the cases, the corresponding activity is executed.</span></span>|  
|<span data-ttu-id="725fd-120">Výchozí</span><span class="sxs-lookup"><span data-stu-id="725fd-120">Default</span></span>|<span data-ttu-id="725fd-121">Aktivita, která se spustí, pokud je nalezena shoda s žádné případu.</span><span class="sxs-lookup"><span data-stu-id="725fd-121">The activity that is executed when no case is matched.</span></span> <span data-ttu-id="725fd-122">Pokud nastavíte hodnotu `null`, nebyla provedena žádná akce.</span><span class="sxs-lookup"><span data-stu-id="725fd-122">When set to `null`, no action is taken.</span></span>|  
  
## <a name="caserange-class"></a><span data-ttu-id="725fd-123">CaseRange – třída</span><span class="sxs-lookup"><span data-stu-id="725fd-123">CaseRange Class</span></span>  
 <span data-ttu-id="725fd-124">`CaseRange` Třída reprezentuje rozsahem v rámci `SwitchRange` aktivity.</span><span class="sxs-lookup"><span data-stu-id="725fd-124">The `CaseRange` class represents a range within a `SwitchRange` activity.</span></span> <span data-ttu-id="725fd-125">Všechny instance řetězce `CaseRange` obsahuje rozsah (tvořený `From` a `To`) a `Body` aktivity, která je naplánováno, pokud výraz ve `SwitchRange` vyhodnotí v rámci rozsahu.</span><span class="sxs-lookup"><span data-stu-id="725fd-125">Every instance of `CaseRange` contains a range (composed of a `From` and a `To`) and a `Body` activity that is scheduled if the expression in the `SwitchRange` is evaluated within the range.</span></span>  
  
 <span data-ttu-id="725fd-126">Následující příklad kódu je definice pro `CaseRange` třídy.</span><span class="sxs-lookup"><span data-stu-id="725fd-126">The following code example is the definition for the `CaseRange` class.</span></span>  
  
```  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="725fd-127">Jak `SwitchRange` a `CaseRange` třídy, které jsou definovány v ukázce jsou obecné třídy, které můžete pracovat s žádným typem, který implementuje `IComparable`, například <xref:System.Activities.Statements.Switch%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="725fd-127">Both the `SwitchRange` and `CaseRange` classes, which are defined in the sample are generic classes that can work with any type that implements `IComparable`, like the <xref:System.Activities.Statements.Switch%601> class.</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="725fd-128">Využití vzorků</span><span class="sxs-lookup"><span data-stu-id="725fd-128">Sample Usage</span></span>  
 <span data-ttu-id="725fd-129">Následující příklad kódu ukazuje, jak používat `SwitchRange` aktivity.</span><span class="sxs-lookup"><span data-stu-id="725fd-129">The following code example demonstrates how to use the `SwitchRange` activity.</span></span>  
  
```csharp  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="725fd-130">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="725fd-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="725fd-131">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení SwitchRange.sln.</span><span class="sxs-lookup"><span data-stu-id="725fd-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SwitchRange.sln solution file.</span></span>  
  
2.  <span data-ttu-id="725fd-132">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="725fd-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="725fd-133">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="725fd-133">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="725fd-134">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="725fd-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="725fd-135">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="725fd-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="725fd-136">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="725fd-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="725fd-137">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="725fd-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`  
  
## <a name="see-also"></a><span data-ttu-id="725fd-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="725fd-138">See Also</span></span>
