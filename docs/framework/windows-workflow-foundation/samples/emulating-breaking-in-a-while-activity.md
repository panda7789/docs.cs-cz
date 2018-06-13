---
title: Emulace nejnovější ve chvíli aktivity
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 37c64c2b8dc03d58f9c2802edef644fe4888e87d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514710"
---
# <a name="emulating-breaking-in-a-while-activity"></a><span data-ttu-id="a6450-102">Emulace nejnovější ve chvíli aktivity</span><span class="sxs-lookup"><span data-stu-id="a6450-102">Emulating breaking in a While activity</span></span>
<span data-ttu-id="a6450-103">Tento příklad ukazuje, jak rozdělit opakování mechanismus z následujících aktivit: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, a <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="a6450-103">This sample demonstrates how to break the looping mechanism of the following activities: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span>  
  
 <span data-ttu-id="a6450-104">To je užitečné, protože Windows Workflow Foundation (WF) neobsahuje žádnou aktivitu pro přerušení provádění těchto smyčky.</span><span class="sxs-lookup"><span data-stu-id="a6450-104">This is useful because Windows Workflow Foundation (WF) does not include any activity to break the execution of these loops.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="a6450-105">Scénář</span><span class="sxs-lookup"><span data-stu-id="a6450-105">Scenario</span></span>  
 <span data-ttu-id="a6450-106">Ukázka vyhledá první spolehlivé dodavatele ze seznamu dodavatelů (instance `Vendor` třídy).</span><span class="sxs-lookup"><span data-stu-id="a6450-106">The sample finds the first reliable vendor from a list of vendors (instances of the `Vendor` class).</span></span> <span data-ttu-id="a6450-107">Má jednotlivých dodavatelů `ID`, `Name` a spolehlivost číselnou hodnotu, která určuje, jak spolehlivé dodavatele.</span><span class="sxs-lookup"><span data-stu-id="a6450-107">Each vendor has an `ID`, a `Name` and a numeric reliability value that determines how dependable the vendor is.</span></span> <span data-ttu-id="a6450-108">Ukázka vytvoří vlastní aktivity volá `FindReliableVendor` který přijímá dva vstupní parametry (seznam dodavateli a hodnotu minimální spolehlivost) a vrátí první dodavatele tohoto seznamu, který odpovídá zadaným kritériím.</span><span class="sxs-lookup"><span data-stu-id="a6450-108">The sample creates a custom activity called `FindReliableVendor` that receives two input parameters (a list of vendors and a minimum reliability value) and returns the first vendor of the list that matches the supplied criteria.</span></span>  
  
## <a name="breaking-a-loop"></a><span data-ttu-id="a6450-109">Pozastavení smyčku</span><span class="sxs-lookup"><span data-stu-id="a6450-109">Breaking a Loop</span></span>  
 <span data-ttu-id="a6450-110">Windows Workflow Foundation (WF) nezahrnuje aktivitu pro přerušení smyčku.</span><span class="sxs-lookup"><span data-stu-id="a6450-110">Windows Workflow Foundation (WF) does not include an activity to break a loop.</span></span> <span data-ttu-id="a6450-111">Ukázka kódu provede nejnovější smyčku pomocí <xref:System.Activities.Statements.If> aktivity a několik proměnné.</span><span class="sxs-lookup"><span data-stu-id="a6450-111">The code sample accomplishes breaking a loop by using an <xref:System.Activities.Statements.If> activity and several variables.</span></span> <span data-ttu-id="a6450-112">V ukázce <xref:System.Activities.Statements.While> aktivity je porušený jednou `reliableVendor` proměnné je jiné než přiřazenou hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="a6450-112">In the sample, the <xref:System.Activities.Statements.While> activity is broken once the `reliableVendor` variable is assigned a value other than `null`.</span></span>  
  
 <span data-ttu-id="a6450-113">Následující příklad kódu ukazuje, jak ukázku dělí chvíli smyčky.</span><span class="sxs-lookup"><span data-stu-id="a6450-113">The following code example demonstrates how the sample breaks a while loop.</span></span>  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a6450-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a6450-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="a6450-115">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení EmulatingBreakInWhile.sln.</span><span class="sxs-lookup"><span data-stu-id="a6450-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EmulatingBreakInWhile.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a6450-116">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a6450-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a6450-117">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="a6450-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a6450-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="a6450-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a6450-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a6450-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a6450-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a6450-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a6450-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a6450-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`