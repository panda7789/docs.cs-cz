---
title: RangeEnumeration aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dc793d57718dbc68f304d3eb5031a9fa96b00cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="110ae-102">RangeEnumeration aktivity</span><span class="sxs-lookup"><span data-stu-id="110ae-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="110ae-103">Tento příklad ukazuje, jak vytvořit vlastní aktivitu, který iteruje nad kolekcí čísel. V následující tabulce jsou hlavní soubory obsažené ve vzorku.</span><span class="sxs-lookup"><span data-stu-id="110ae-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="110ae-104">Název souboru</span><span class="sxs-lookup"><span data-stu-id="110ae-104">File name</span></span>|<span data-ttu-id="110ae-105">Popis</span><span class="sxs-lookup"><span data-stu-id="110ae-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="110ae-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="110ae-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="110ae-107">Definuje vlastní aktivity s názvem `RangeEnumeration` , přepíše <xref:System.Activities.NativeActivity> třídy a smyčky prostřednictvím řady čísel.</span><span class="sxs-lookup"><span data-stu-id="110ae-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="110ae-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="110ae-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="110ae-109">Klientská aplikace, která používá `RangeEnumeration` aktivity Iterujte přes kolekci čísel.</span><span class="sxs-lookup"><span data-stu-id="110ae-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="110ae-110">V následující tabulce jsou vlastnosti `RangeEnumeration` aktivity.</span><span class="sxs-lookup"><span data-stu-id="110ae-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="110ae-111">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="110ae-111">Property</span></span>|<span data-ttu-id="110ae-112">Popis</span><span class="sxs-lookup"><span data-stu-id="110ae-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="110ae-113">Spustit</span><span class="sxs-lookup"><span data-stu-id="110ae-113">Start</span></span>|<span data-ttu-id="110ae-114">Spuštění smyčky z na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="110ae-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="110ae-115">Zastavit</span><span class="sxs-lookup"><span data-stu-id="110ae-115">Stop</span></span>|<span data-ttu-id="110ae-116">Zastavit smyčky v na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="110ae-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="110ae-117">Krok</span><span class="sxs-lookup"><span data-stu-id="110ae-117">Step</span></span>|<span data-ttu-id="110ae-118">Určuje, kolik k iteraci v každém.</span><span class="sxs-lookup"><span data-stu-id="110ae-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="110ae-119">Text</span><span class="sxs-lookup"><span data-stu-id="110ae-119">Body</span></span>|<span data-ttu-id="110ae-120">Určuje kód provést při každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="110ae-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="110ae-121">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="110ae-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="110ae-122">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="110ae-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="110ae-123">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="110ae-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="110ae-124">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="110ae-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="110ae-125">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="110ae-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="110ae-126">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="110ae-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="110ae-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="110ae-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="110ae-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="110ae-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`