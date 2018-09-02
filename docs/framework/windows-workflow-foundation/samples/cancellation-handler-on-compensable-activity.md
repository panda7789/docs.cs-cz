---
title: Obslužná rutina zrušení u Kompenzovatelné aktivity
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: 2f32d10e22be7fdd1e84229a214409df06efa918
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442704"
---
# <a name="cancellation-handler-on-compensable-activity"></a><span data-ttu-id="06c84-102">Obslužná rutina zrušení u Kompenzovatelné aktivity</span><span class="sxs-lookup"><span data-stu-id="06c84-102">Cancellation Handler on Compensable Activity</span></span>
<span data-ttu-id="06c84-103">Tato ukázka demonstruje použití obslužná rutina zrušení na <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="06c84-103">This sample demonstrates the use of a cancellation handler on a <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 <span data-ttu-id="06c84-104">Tato ukázka obsahuje dva scénáře, které ukazují použití <xref:System.Activities.Statements.CompensableActivity> zrušení. První scénář obsahuje kořenový kompenzovatelná aktivita, která obsahuje tři podřízené kompenzovatelné aktivity.</span><span class="sxs-lookup"><span data-stu-id="06c84-104">This sample contains two scenarios that demonstrate the use of <xref:System.Activities.Statements.CompensableActivity> cancellation.The first scenario contains a root compensable activity that contains three child compensable activities.</span></span> <span data-ttu-id="06c84-105">Dvě podřízené aktivity dokončení úřadů, které jejich činnost úspěšně.</span><span class="sxs-lookup"><span data-stu-id="06c84-105">Two child activities finish running their activity bodies successfully.</span></span> <span data-ttu-id="06c84-106">Třetí text podřízené aktivity spustí, zjistí výjimku, která zpracovává zrušení třetí aktivity zpracování, po jejímž uplynutí se aktivuje zrušení kořenovou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="06c84-106">When the third child activity body runs, it encounters an exception that is handled by canceling the third activity processing, after which the cancellation of the root activity is triggered.</span></span> <span data-ttu-id="06c84-107">Logika v kořenové aktivity v tomto příkladu je odpovídajícím způsobem upravit další dva podřízené aktivity, která dokončila dříve.</span><span class="sxs-lookup"><span data-stu-id="06c84-107">The logic in the root activity in this example is to compensate the other two child activities that completed earlier.</span></span>  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 <span data-ttu-id="06c84-108">Druhý scénář předvádí, provádění <xref:System.Activities.Statements.TryCatch> souběžně s <xref:System.Activities.Statements.Delay>, který končí před <xref:System.Activities.Statements.TryCatch> větve.</span><span class="sxs-lookup"><span data-stu-id="06c84-108">The second scenario demonstrates executing a <xref:System.Activities.Statements.TryCatch> in parallel with a <xref:System.Activities.Statements.Delay>, which finishes before the <xref:System.Activities.Statements.TryCatch> branch.</span></span> <span data-ttu-id="06c84-109">Je nastavena podmínka ukončení `true` po dokončení první větev, příčinou této větve zrušit.</span><span class="sxs-lookup"><span data-stu-id="06c84-109">The completion condition is set to `true` once the first branch finishes, causing the other branch to be canceled.</span></span>  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06c84-110">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="06c84-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="06c84-111">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete CompensationCancellation.sln.</span><span class="sxs-lookup"><span data-stu-id="06c84-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open CompensationCancellation.sln.</span></span>  
  
2.  <span data-ttu-id="06c84-112">Sestavit ukázku stisknutím kombinace kláves CTRL + SHIFT + B nebo vyberte "Sestavit řešení" v nabídce sestavení...</span><span class="sxs-lookup"><span data-stu-id="06c84-112">Build the sample by pressing CTRL+SHIFT+B or select "Build Solution" from the Build menu..</span></span>  
  
3.  <span data-ttu-id="06c84-113">Spusťte ukázku stisknutím klávesy F5 nebo vyberte "Spustit ladění" z menu ladit.</span><span class="sxs-lookup"><span data-stu-id="06c84-113">Run the sample by pressing F5 or select "Start Debugging" from the Debug menu.</span></span> <span data-ttu-id="06c84-114">Případně můžete stisknutím kláves Ctrl + F5 nebo vyberte možnost "Spustit bez ladění" z menu ladit.</span><span class="sxs-lookup"><span data-stu-id="06c84-114">Alternately you may press Ctrl+F5 or select "Start without Debugging" from the Debug menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06c84-115">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="06c84-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06c84-116">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="06c84-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06c84-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="06c84-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06c84-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="06c84-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`