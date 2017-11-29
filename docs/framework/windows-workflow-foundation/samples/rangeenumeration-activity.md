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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 024cdc9ae082171fb33a63493ac0fbfdd45d3c72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="01134-102">RangeEnumeration aktivity</span><span class="sxs-lookup"><span data-stu-id="01134-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="01134-103">Tento příklad ukazuje, jak vytvořit vlastní aktivitu, který iteruje nad kolekcí čísel. V následující tabulce jsou hlavní soubory obsažené ve vzorku.</span><span class="sxs-lookup"><span data-stu-id="01134-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="01134-104">Název souboru</span><span class="sxs-lookup"><span data-stu-id="01134-104">File name</span></span>|<span data-ttu-id="01134-105">Popis</span><span class="sxs-lookup"><span data-stu-id="01134-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01134-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="01134-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="01134-107">Definuje vlastní aktivity s názvem `RangeEnumeration` , přepíše <xref:System.Activities.NativeActivity> třídy a smyčky prostřednictvím řady čísel.</span><span class="sxs-lookup"><span data-stu-id="01134-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="01134-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="01134-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="01134-109">Klientská aplikace, která používá `RangeEnumeration` aktivity Iterujte přes kolekci čísel.</span><span class="sxs-lookup"><span data-stu-id="01134-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="01134-110">V následující tabulce jsou vlastnosti `RangeEnumeration` aktivity.</span><span class="sxs-lookup"><span data-stu-id="01134-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="01134-111">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="01134-111">Property</span></span>|<span data-ttu-id="01134-112">Popis</span><span class="sxs-lookup"><span data-stu-id="01134-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="01134-113">Spustit</span><span class="sxs-lookup"><span data-stu-id="01134-113">Start</span></span>|<span data-ttu-id="01134-114">Spuštění smyčky z na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="01134-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="01134-115">Zastavit</span><span class="sxs-lookup"><span data-stu-id="01134-115">Stop</span></span>|<span data-ttu-id="01134-116">Zastavit smyčky v na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="01134-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="01134-117">Krok</span><span class="sxs-lookup"><span data-stu-id="01134-117">Step</span></span>|<span data-ttu-id="01134-118">Určuje, kolik k iteraci v každém.</span><span class="sxs-lookup"><span data-stu-id="01134-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="01134-119">Text</span><span class="sxs-lookup"><span data-stu-id="01134-119">Body</span></span>|<span data-ttu-id="01134-120">Určuje kód provést při každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="01134-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="01134-121">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="01134-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="01134-122">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="01134-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="01134-123">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="01134-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="01134-124">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="01134-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="01134-125">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="01134-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01134-126">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="01134-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="01134-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="01134-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01134-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="01134-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`  
  
## <a name="see-also"></a><span data-ttu-id="01134-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="01134-129">See Also</span></span>
