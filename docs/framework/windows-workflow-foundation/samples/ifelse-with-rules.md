---
title: IfElse s pravidly
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 31906f04149a0ca7659201965ca565c7fa2af305
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483003"
---
# <a name="ifelse-with-rules"></a><span data-ttu-id="9744d-102">IfElse s pravidly</span><span class="sxs-lookup"><span data-stu-id="9744d-102">IfElse With Rules</span></span>
<span data-ttu-id="9744d-103">Tento příklad ukazuje použití podmínku pravidla, která se <xref:System.Workflow.Activities.IfElseActivity> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9744d-103">This sample shows the use of a rule condition with an <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span>  
  
 <span data-ttu-id="9744d-104">Ukázka předá `OrderValue` parametr z hostitele.</span><span class="sxs-lookup"><span data-stu-id="9744d-104">The sample passes in an `OrderValue` parameter from the host.</span></span> <span data-ttu-id="9744d-105">Hodnota parametru je používán podmínku pravidla, která na první větev <xref:System.Workflow.Activities.IfElseActivity> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9744d-105">The value of the parameter is used in a rule condition on the first branch of the <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span> <span data-ttu-id="9744d-106">Pokud je hodnota menší než 10 000, provede první větev a <xref:System.Workflow.Activities.CodeActivity> aktivity v první větev vytiskne **získat schválení správcem** do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9744d-106">If the value is less than 10,000, the first branch executes, and the <xref:System.Workflow.Activities.CodeActivity> activity in the first branch prints **Get Manager Approval** to the console.</span></span> <span data-ttu-id="9744d-107">Pokud je hodnota větší než 10 000 operací, <xref:System.Workflow.Activities.CodeActivity> aktivity v druhé větvi spustí a vytiskne **získat schválení Viceprezidentka**.</span><span class="sxs-lookup"><span data-stu-id="9744d-107">If the value is greater than 10,000, the <xref:System.Workflow.Activities.CodeActivity> activity in the second branch executes and prints **Get VP Approval**.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="9744d-108">K vytvoření vzorku</span><span class="sxs-lookup"><span data-stu-id="9744d-108">To build the sample</span></span>  
  
1.  <span data-ttu-id="9744d-109">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9744d-109">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="9744d-110">Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="9744d-110">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9744d-111">Spuštění řešení bez ladění stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="9744d-111">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="9744d-112">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="9744d-112">To run the sample</span></span>  
  
-   <span data-ttu-id="9744d-113">V okně příkazového řádku sady SDK spusťte soubor .exe ve složce IfElseWithRules\bin\debug (nebo ve složce IfElseWithRules\bin pro verzi ukázky, která se týká jazyka Visual Basic), který se nachází pod hlavní složku pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="9744d-113">In the SDK Command Prompt window, run the .exe file in the IfElseWithRules\bin\debug folder (or the IfElseWithRules\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9744d-114">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9744d-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9744d-115">Před pokračováním zkontrolujte následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="9744d-115">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9744d-116">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9744d-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9744d-117">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="9744d-117">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a><span data-ttu-id="9744d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9744d-118">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
