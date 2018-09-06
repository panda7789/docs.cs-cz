---
title: Vlastní aktivita Hello World
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: fde745fae7470ec763b6b5030a60436a6525e3c0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856849"
---
# <a name="hello-world-custom-activity"></a><span data-ttu-id="f1321-102">Vlastní aktivita Hello World</span><span class="sxs-lookup"><span data-stu-id="f1321-102">Hello World Custom Activity</span></span>
<span data-ttu-id="f1321-103">Tento příklad ukazuje několik klíčových funkcí z Windows Workflow Foundation (WF), jak vytvořit jednoduchý vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="f1321-103">This sample demonstrates several key features of Windows Workflow Foundation (WF), including how to create a simple custom activity.</span></span> <span data-ttu-id="f1321-104">Některé funkce v této ukázce jsme vám ukázali vytváříte vlastní aktivity v jazyce C# a pomocí `in` a `out` argumenty (<xref:System.Activities.InArgument> a <xref:System.Activities.OutArgument>).</span><span class="sxs-lookup"><span data-stu-id="f1321-104">Some of the features demonstrated in this sample are creating a custom activity in C# and using `in` and `out` arguments (<xref:System.Activities.InArgument> and <xref:System.Activities.OutArgument>).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1321-105">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="f1321-105">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f1321-106">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f1321-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f1321-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f1321-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1321-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f1321-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a><span data-ttu-id="f1321-109">Vytvoření pracovního postupu v kódu</span><span class="sxs-lookup"><span data-stu-id="f1321-109">Creating a Workflow in Code</span></span>  
 <span data-ttu-id="f1321-110">V této ukázce jsou dvě vlastní aktivity vytvořené využitím kódu C#.</span><span class="sxs-lookup"><span data-stu-id="f1321-110">In this sample, two custom activities are created using C# code.</span></span> <span data-ttu-id="f1321-111">Jak vlastní aktivity dědí přímo nebo nepřímo <xref:System.Activities.Activity%601> vrátit jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f1321-111">Both custom activities inherit directly or indirectly from <xref:System.Activities.Activity%601> to return a single value.</span></span> <span data-ttu-id="f1321-112">Výhodou použití obecných návratovou hodnotu, namísto dědění z neobecné <xref:System.Activities.Activity> třídy, je, že některé aktivity (například <xref:System.Activities.Statements.Assign>) budou mít přístup k návratovou hodnotu, když se použije jako součást složené aktivity.</span><span class="sxs-lookup"><span data-stu-id="f1321-112">The advantage of using the generic return value, instead of inheriting from the non-generic <xref:System.Activities.Activity> class, is that some activities (such as <xref:System.Activities.Statements.Assign>) are able to access the return value when used as part of a composed activity.</span></span>  
  
 <span data-ttu-id="f1321-113">AppendString</span><span class="sxs-lookup"><span data-stu-id="f1321-113">AppendString</span></span>  
 <span data-ttu-id="f1321-114">Tato aktivita se dědí z <xref:System.Activities.Activity%601>a použije <xref:System.Activities.Statements.Assign> aktivitu, která spojuje dva řetězce současně.</span><span class="sxs-lookup"><span data-stu-id="f1321-114">This activity inherits from <xref:System.Activities.Activity%601>, and uses an <xref:System.Activities.Statements.Assign> activity that concatenates two strings together.</span></span>  
  
 <span data-ttu-id="f1321-115">Předřaďte řetězec</span><span class="sxs-lookup"><span data-stu-id="f1321-115">Prepend String</span></span>  
 <span data-ttu-id="f1321-116">Tato aktivita dědí přímo z <xref:System.Activities.CodeActivity%601>a vytvoří podobné funkce jako `AppendString` aktivitu, která používá logiku implementovat v kódu namísto se skládá z již existujících aktivit.</span><span class="sxs-lookup"><span data-stu-id="f1321-116">This activity inherits directly from <xref:System.Activities.CodeActivity%601>, and creates similar functionality to the `AppendString` activity, which uses logic implemented in code rather than being composed of a pre-existing activity.</span></span>  
  
 <span data-ttu-id="f1321-117">Následující soubory jsou zahrnuty v tomto projektu.</span><span class="sxs-lookup"><span data-stu-id="f1321-117">The following files are included in this project.</span></span>  
  
 <span data-ttu-id="f1321-118">AppendString.cs</span><span class="sxs-lookup"><span data-stu-id="f1321-118">AppendString.cs</span></span>  
 <span data-ttu-id="f1321-119">Vlastní aktivita, která připojí řetězce dohromady.</span><span class="sxs-lookup"><span data-stu-id="f1321-119">The custom activity that appends strings together.</span></span> <span data-ttu-id="f1321-120">Přijímá řetězec a zkombinuje je literál textovým řetězcem "říká hello world" do formuláře zprávu o dokončení jako výstup.</span><span class="sxs-lookup"><span data-stu-id="f1321-120">It takes in a string and combines it with a literal text string " says hello world" to form a complete message as output.</span></span>  
  
 <span data-ttu-id="f1321-121">PrependString.cs</span><span class="sxs-lookup"><span data-stu-id="f1321-121">PrependString.cs</span></span>  
 <span data-ttu-id="f1321-122">Tato aktivita předpon předdefinované řetězcové vstupní řetězec.</span><span class="sxs-lookup"><span data-stu-id="f1321-122">This activity prefixes a predefined string to an input string.</span></span>  
  
 <span data-ttu-id="f1321-123">Sequence1.XAML</span><span class="sxs-lookup"><span data-stu-id="f1321-123">Sequence1.xaml</span></span>  
 <span data-ttu-id="f1321-124">Pracovní postup, který se používá `AppendString` a `PrependString` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="f1321-124">A workflow that uses the `AppendString` and `PrependString` custom activities.</span></span>  
  
 <span data-ttu-id="f1321-125">Program.cs</span><span class="sxs-lookup"><span data-stu-id="f1321-125">Program.cs</span></span>  
 <span data-ttu-id="f1321-126">Program, který spouští pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="f1321-126">A program that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f1321-127">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="f1321-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="f1321-128">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení HelloWorld.sln.</span><span class="sxs-lookup"><span data-stu-id="f1321-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f1321-129">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f1321-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f1321-130">Abyste mohli spustit řešení, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="f1321-130">To run the solution, press F5.</span></span>