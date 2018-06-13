---
title: Obslužná rutina zrušení Compensable aktivita
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: ce4d67b26a2b4c6a9b507715b48e75e328c5b100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514998"
---
# <a name="cancellation-handler-on-compensable-activity"></a><span data-ttu-id="9f6e8-102">Obslužná rutina zrušení Compensable aktivita</span><span class="sxs-lookup"><span data-stu-id="9f6e8-102">Cancellation Handler on Compensable Activity</span></span>
<span data-ttu-id="9f6e8-103">Tento příklad znázorňuje použití obslužné rutiny zrušení na <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-103">This sample demonstrates the use of a cancellation handler on a <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 <span data-ttu-id="9f6e8-104">Tato ukázka obsahuje dva scénáře, které ukazují použití <xref:System.Activities.Statements.CompensableActivity> zrušení. První scénář obsahuje kořenové compensable aktivity, která obsahuje tři podřízené compensable aktivit.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-104">This sample contains two scenarios that demonstrate the use of <xref:System.Activities.Statements.CompensableActivity> cancellation.The first scenario contains a root compensable activity that contains three child compensable activities.</span></span> <span data-ttu-id="9f6e8-105">Dva podřízené aktivity dokončit své aktivity subjekty, spouští úspěšně.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-105">Two child activities finish running their activity bodies successfully.</span></span> <span data-ttu-id="9f6e8-106">Při spuštění třetí text podřízené aktivity, zaznamená výjimka, která se zpracovává souborem zrušení třetí aktivity zpracování, po jejímž uplynutí se aktivuje zrušení kořenové aktivity.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-106">When the third child activity body runs, it encounters an exception that is handled by canceling the third activity processing, after which the cancellation of the root activity is triggered.</span></span> <span data-ttu-id="9f6e8-107">Logika kořenové aktivity v tomto příkladu je odpovídajícím způsobem další dva podřízené aktivity, které dříve dokončit.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-107">The logic in the root activity in this example is to compensate the other two child activities that completed earlier.</span></span>  
  
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
  
 <span data-ttu-id="9f6e8-108">Druhý scénář znázorňuje, spuštění <xref:System.Activities.Statements.TryCatch> paralelně s <xref:System.Activities.Statements.Delay>, který končí před <xref:System.Activities.Statements.TryCatch> firemní pobočky.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-108">The second scenario demonstrates executing a <xref:System.Activities.Statements.TryCatch> in parallel with a <xref:System.Activities.Statements.Delay>, which finishes before the <xref:System.Activities.Statements.TryCatch> branch.</span></span> <span data-ttu-id="9f6e8-109">Je nastavena podmínka dokončení `true` po dokončení první větev způsobuje jiných větev, která má být zrušena.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-109">The completion condition is set to `true` once the first branch finishes, causing the other branch to be canceled.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9f6e8-110">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="9f6e8-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9f6e8-111">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete CompensationCancellation.sln.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open CompensationCancellation.sln.</span></span>  
  
2.  <span data-ttu-id="9f6e8-112">Sestavit ukázku stisknutím kombinace kláves CTRL + SHIFT + B nebo vyberte možnost "Sestavit řešení" v nabídce sestavení...</span><span class="sxs-lookup"><span data-stu-id="9f6e8-112">Build the sample by pressing CTRL+SHIFT+B or select "Build Solution" from the Build menu..</span></span>  
  
3.  <span data-ttu-id="9f6e8-113">Spustit ukázku stisknutím klávesy F5 nebo vyberte možnost "Spustit ladění" v nabídce ladění.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-113">Run the sample by pressing F5 or select "Start Debugging" from the Debug menu.</span></span> <span data-ttu-id="9f6e8-114">Případně můžete stisknutím kláves Ctrl + F5 nebo vyberte možnost "Spustit bez ladění" v nabídce ladění.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-114">Alternately you may press Ctrl+F5 or select "Start without Debugging" from the Debug menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f6e8-115">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9f6e8-116">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9f6e8-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9f6e8-117">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9f6e8-118">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9f6e8-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`