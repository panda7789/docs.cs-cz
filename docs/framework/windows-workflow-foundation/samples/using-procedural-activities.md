---
title: "Pomocí procedurální aktivit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c391316959829c77d16dd87af51d9fe1915dc88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-procedural-activities"></a><span data-ttu-id="9d6a4-102">Pomocí procedurální aktivit</span><span class="sxs-lookup"><span data-stu-id="9d6a4-102">Using Procedural Activities</span></span>
<span data-ttu-id="9d6a4-103">Ukázce se používá <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, a <xref:System.Activities.Statements.WriteLine> aktivity k implementaci uhodnutí her.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-103">The sample uses the <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, and <xref:System.Activities.Statements.WriteLine> activities to implement a guessing game.</span></span> <span data-ttu-id="9d6a4-104">Hádání herní vybere náhodné číslo a má přehrávač tak snadno uhodnout toto číslo.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-104">The guessing game selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="9d6a4-105">Když přehrávač odešle nesprávné odhad, pracovní postup poskytuje nápovědu ohledně uhodnout vyšší nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-105">When the player submits an incorrect guess, the workflow provides a hint whether to guess higher or lower.</span></span> <span data-ttu-id="9d6a4-106">Pokud přehrávač odhadne číslo menší než 7 pokusů o přihlášení, zobrazí se uživateli speciální Blahopřejeme.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-106">If the player guesses the number in less than 7 attempts, a special congratulations is displayed to the user.</span></span>  
  
## <a name="custom-activities-in-this-sample"></a><span data-ttu-id="9d6a4-107">Vlastní aktivity v této ukázce</span><span class="sxs-lookup"><span data-stu-id="9d6a4-107">Custom Activities in this Sample</span></span>  
  
### <a name="readline"></a><span data-ttu-id="9d6a4-108">ReadLine</span><span class="sxs-lookup"><span data-stu-id="9d6a4-108">ReadLine</span></span>  
 <span data-ttu-id="9d6a4-109">Přečte řádek textu z konzoly.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-109">Reads a line of text from the console.</span></span> <span data-ttu-id="9d6a4-110">Tato aktivita je odvozena z <xref:System.Activities.NativeActivity> třídy a vytvoří záložku, na kterou je obnoveno pomocí konzolové aplikace, pokud je pro čtení na řádku.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-110">This activity derives from the <xref:System.Activities.NativeActivity> class and creates a bookmark that is resumed by the console application when a line is read.</span></span>  
  
### <a name="promptint"></a><span data-ttu-id="9d6a4-111">PromptInt</span><span class="sxs-lookup"><span data-stu-id="9d6a4-111">PromptInt</span></span>  
 <span data-ttu-id="9d6a4-112">Zobrazí výzvu k zadání čísla a potom načte z okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-112">Prompts the user to type in a number and then reads it from a console window.</span></span> <span data-ttu-id="9d6a4-113">Aktivita je odvozena z <xref:System.Activities.Activity%601> a používá <xref:System.Activities.Statements.WriteLine> a `ReadLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-113">The activity derives from <xref:System.Activities.Activity%601> and uses the <xref:System.Activities.Statements.WriteLine> and `ReadLine` activities.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="9d6a4-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="9d6a4-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="9d6a4-115">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení GuessingGame.sln.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the GuessingGame.sln solution file.</span></span>  
  
2.  <span data-ttu-id="9d6a4-116">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9d6a4-117">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9d6a4-118">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9d6a4-119">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9d6a4-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9d6a4-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d6a4-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9d6a4-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`  
  
## <a name="see-also"></a><span data-ttu-id="9d6a4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d6a4-122">See Also</span></span>
