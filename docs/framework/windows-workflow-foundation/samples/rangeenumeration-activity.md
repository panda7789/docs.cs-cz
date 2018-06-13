---
title: RangeEnumeration aktivity
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: 9aa04c80f20e2d410fb49e2d07d836c8c5ab1b4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516575"
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="312cf-102">RangeEnumeration aktivity</span><span class="sxs-lookup"><span data-stu-id="312cf-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="312cf-103">Tento příklad ukazuje, jak vytvořit vlastní aktivitu, který iteruje nad kolekcí čísel. V následující tabulce jsou hlavní soubory obsažené ve vzorku.</span><span class="sxs-lookup"><span data-stu-id="312cf-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="312cf-104">Název souboru</span><span class="sxs-lookup"><span data-stu-id="312cf-104">File name</span></span>|<span data-ttu-id="312cf-105">Popis</span><span class="sxs-lookup"><span data-stu-id="312cf-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="312cf-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="312cf-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="312cf-107">Definuje vlastní aktivity s názvem `RangeEnumeration` , přepíše <xref:System.Activities.NativeActivity> třídy a smyčky prostřednictvím řady čísel.</span><span class="sxs-lookup"><span data-stu-id="312cf-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="312cf-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="312cf-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="312cf-109">Klientská aplikace, která používá `RangeEnumeration` aktivity Iterujte přes kolekci čísel.</span><span class="sxs-lookup"><span data-stu-id="312cf-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="312cf-110">V následující tabulce jsou vlastnosti `RangeEnumeration` aktivity.</span><span class="sxs-lookup"><span data-stu-id="312cf-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="312cf-111">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="312cf-111">Property</span></span>|<span data-ttu-id="312cf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="312cf-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="312cf-113">Spustit</span><span class="sxs-lookup"><span data-stu-id="312cf-113">Start</span></span>|<span data-ttu-id="312cf-114">Spuštění smyčky z na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="312cf-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="312cf-115">Zastavit</span><span class="sxs-lookup"><span data-stu-id="312cf-115">Stop</span></span>|<span data-ttu-id="312cf-116">Zastavit smyčky v na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="312cf-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="312cf-117">Krok</span><span class="sxs-lookup"><span data-stu-id="312cf-117">Step</span></span>|<span data-ttu-id="312cf-118">Určuje, kolik k iteraci v každém.</span><span class="sxs-lookup"><span data-stu-id="312cf-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="312cf-119">Text</span><span class="sxs-lookup"><span data-stu-id="312cf-119">Body</span></span>|<span data-ttu-id="312cf-120">Určuje kód provést při každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="312cf-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="312cf-121">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="312cf-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="312cf-122">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="312cf-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="312cf-123">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="312cf-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="312cf-124">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="312cf-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="312cf-125">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="312cf-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="312cf-126">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="312cf-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="312cf-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="312cf-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="312cf-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="312cf-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`