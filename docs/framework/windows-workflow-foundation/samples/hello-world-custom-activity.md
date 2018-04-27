---
title: Hello World vlastní aktivity
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa441a3019b0ef6df31dc0a46be7ea7e8e00a4b8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="hello-world-custom-activity"></a><span data-ttu-id="99bf8-102">Hello World vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="99bf8-102">Hello World Custom Activity</span></span>
<span data-ttu-id="99bf8-103">Tento příklad znázorňuje několik klíčových funkcí systému Windows Workflow Foundation (WF), včetně toho, jak vytvořit jednoduché vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="99bf8-103">This sample demonstrates several key features of Windows Workflow Foundation (WF), including how to create a simple custom activity.</span></span> <span data-ttu-id="99bf8-104">Některé funkce předvedená v této ukázce vytváření vlastních aktivit v C# a pomocí `in` a `out` argumenty (<xref:System.Activities.InArgument> a <xref:System.Activities.OutArgument>).</span><span class="sxs-lookup"><span data-stu-id="99bf8-104">Some of the features demonstrated in this sample are creating a custom activity in C# and using `in` and `out` arguments (<xref:System.Activities.InArgument> and <xref:System.Activities.OutArgument>).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99bf8-105">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="99bf8-105">The samples may already be installed on your computer.</span></span> <span data-ttu-id="99bf8-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="99bf8-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="99bf8-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="99bf8-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="99bf8-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="99bf8-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a><span data-ttu-id="99bf8-109">Vytvoření pracovního postupu v kódu</span><span class="sxs-lookup"><span data-stu-id="99bf8-109">Creating a Workflow in Code</span></span>  
 <span data-ttu-id="99bf8-110">V této ukázce jsou vytvořeny dva vlastní aktivity pomocí kódu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="99bf8-110">In this sample, two custom activities are created using C# code.</span></span> <span data-ttu-id="99bf8-111">I vlastní aktivity dědí přímo nebo nepřímo <xref:System.Activities.Activity%601> vrátit jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="99bf8-111">Both custom activities inherit directly or indirectly from <xref:System.Activities.Activity%601> to return a single value.</span></span> <span data-ttu-id="99bf8-112">Výhodou použití obecné návratovou hodnotu, místo, která dědí z neobecnou <xref:System.Activities.Activity> třídy, je, že některé aktivity (například <xref:System.Activities.Statements.Assign>) mají přístup návratovou hodnotu, pokud se používá jako součást složený aktivity.</span><span class="sxs-lookup"><span data-stu-id="99bf8-112">The advantage of using the generic return value, instead of inheriting from the non-generic <xref:System.Activities.Activity> class, is that some activities (such as <xref:System.Activities.Statements.Assign>) are able to access the return value when used as part of a composed activity.</span></span>  
  
 <span data-ttu-id="99bf8-113">AppendString</span><span class="sxs-lookup"><span data-stu-id="99bf8-113">AppendString</span></span>  
 <span data-ttu-id="99bf8-114">Tato aktivita se dědí z <xref:System.Activities.Activity%601>a používá <xref:System.Activities.Statements.Assign> aktivity, která zřetězí dva řetězce společně.</span><span class="sxs-lookup"><span data-stu-id="99bf8-114">This activity inherits from <xref:System.Activities.Activity%601>, and uses an <xref:System.Activities.Statements.Assign> activity that concatenates two strings together.</span></span>  
  
 <span data-ttu-id="99bf8-115">Předřadit řetězec</span><span class="sxs-lookup"><span data-stu-id="99bf8-115">Prepend String</span></span>  
 <span data-ttu-id="99bf8-116">Tato aktivita dědí přímo z <xref:System.Activities.CodeActivity%601>a vytvoří podobné funkce jako `AppendString` aktivity, která používá logiku implementované v kódu místo se skládá z předchozích aktivit.</span><span class="sxs-lookup"><span data-stu-id="99bf8-116">This activity inherits directly from <xref:System.Activities.CodeActivity%601>, and creates similar functionality to the `AppendString` activity, which uses logic implemented in code rather than being composed of a pre-existing activity.</span></span>  
  
 <span data-ttu-id="99bf8-117">Následující soubory jsou zahrnuté v tomto projektu.</span><span class="sxs-lookup"><span data-stu-id="99bf8-117">The following files are included in this project.</span></span>  
  
 <span data-ttu-id="99bf8-118">AppendString.cs</span><span class="sxs-lookup"><span data-stu-id="99bf8-118">AppendString.cs</span></span>  
 <span data-ttu-id="99bf8-119">Vlastní aktivity, která připojí řetězce společně.</span><span class="sxs-lookup"><span data-stu-id="99bf8-119">The custom activity that appends strings together.</span></span> <span data-ttu-id="99bf8-120">Přebírá v řetězci a jeho kombinuje literálu textovým řetězcem "uvádí hello, world" formuláře dokončení zprávu jako výstup.</span><span class="sxs-lookup"><span data-stu-id="99bf8-120">It takes in a string and combines it with a literal text string " says hello world" to form a complete message as output.</span></span>  
  
 <span data-ttu-id="99bf8-121">PrependString.cs</span><span class="sxs-lookup"><span data-stu-id="99bf8-121">PrependString.cs</span></span>  
 <span data-ttu-id="99bf8-122">Tato aktivita předpony řetězec předdefinované tak, aby vstupní řetězec.</span><span class="sxs-lookup"><span data-stu-id="99bf8-122">This activity prefixes a predefined string to an input string.</span></span>  
  
 <span data-ttu-id="99bf8-123">Sequence1.XAML</span><span class="sxs-lookup"><span data-stu-id="99bf8-123">Sequence1.xaml</span></span>  
 <span data-ttu-id="99bf8-124">Pracovní postup, který používá `AppendString` a `PrependString` vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="99bf8-124">A workflow that uses the `AppendString` and `PrependString` custom activities.</span></span>  
  
 <span data-ttu-id="99bf8-125">Program.cs</span><span class="sxs-lookup"><span data-stu-id="99bf8-125">Program.cs</span></span>  
 <span data-ttu-id="99bf8-126">Program, který spouští pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="99bf8-126">A program that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="99bf8-127">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="99bf8-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="99bf8-128">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení HelloWorld.sln.</span><span class="sxs-lookup"><span data-stu-id="99bf8-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="99bf8-129">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="99bf8-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="99bf8-130">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="99bf8-130">To run the solution, press F5.</span></span>