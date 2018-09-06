---
title: Použití procedurálních aktivit
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: bd83f1a0fa9f3af7c22cee73fbc4f984a9ebf53c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804748"
---
# <a name="using-procedural-activities"></a><span data-ttu-id="2dc9e-102">Použití procedurálních aktivit</span><span class="sxs-lookup"><span data-stu-id="2dc9e-102">Using Procedural Activities</span></span>
<span data-ttu-id="2dc9e-103">Ukázka používá <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, a <xref:System.Activities.Statements.WriteLine> aktivity k implementaci opakovaně uhodnout her.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-103">The sample uses the <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, and <xref:System.Activities.Statements.WriteLine> activities to implement a guessing game.</span></span> <span data-ttu-id="2dc9e-104">Náhodné číslo vybere rozluštění hry a hráč musí odhadnout toto číslo.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-104">The guessing game selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="2dc9e-105">Když hráč odešle nesprávné odhad, pracovní postup poskytuje nápovědu, jestli se má uhodnout vyšší nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-105">When the player submits an incorrect guess, the workflow provides a hint whether to guess higher or lower.</span></span> <span data-ttu-id="2dc9e-106">Pokud hráč uhádne číslo menší než 7 pokusů o přihlášení, zobrazí se uživateli speciální Blahopřejeme.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-106">If the player guesses the number in less than 7 attempts, a special congratulations is displayed to the user.</span></span>  
  
## <a name="custom-activities-in-this-sample"></a><span data-ttu-id="2dc9e-107">Vlastní aktivity v této ukázce</span><span class="sxs-lookup"><span data-stu-id="2dc9e-107">Custom Activities in this Sample</span></span>  
  
### <a name="readline"></a><span data-ttu-id="2dc9e-108">ReadLine</span><span class="sxs-lookup"><span data-stu-id="2dc9e-108">ReadLine</span></span>  
 <span data-ttu-id="2dc9e-109">Přečte řádek textu z konzoly.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-109">Reads a line of text from the console.</span></span> <span data-ttu-id="2dc9e-110">Tato aktivita je odvozen od <xref:System.Activities.NativeActivity> třídy a vytvoří záložku, která je obnovit pomocí konzolové aplikace při čtení řádku.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-110">This activity derives from the <xref:System.Activities.NativeActivity> class and creates a bookmark that is resumed by the console application when a line is read.</span></span>  
  
### <a name="promptint"></a><span data-ttu-id="2dc9e-111">PromptInt</span><span class="sxs-lookup"><span data-stu-id="2dc9e-111">PromptInt</span></span>  
 <span data-ttu-id="2dc9e-112">Zobrazí výzvu k zadání čísla a pak přečte z okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-112">Prompts the user to type in a number and then reads it from a console window.</span></span> <span data-ttu-id="2dc9e-113">Aktivita je odvozena z <xref:System.Activities.Activity%601> a používá <xref:System.Activities.Statements.WriteLine> a `ReadLine` aktivity.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-113">The activity derives from <xref:System.Activities.Activity%601> and uses the <xref:System.Activities.Statements.WriteLine> and `ReadLine` activities.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="2dc9e-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="2dc9e-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="2dc9e-115">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení GuessingGame.sln.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the GuessingGame.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2dc9e-116">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2dc9e-117">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2dc9e-118">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2dc9e-119">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2dc9e-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2dc9e-120">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2dc9e-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2dc9e-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`