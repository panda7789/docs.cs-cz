---
title: Aktivita RangeEnumeration
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: c9cf522227620422b414adc26cbc0bf338bf57d4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868715"
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="e6c72-102">Aktivita RangeEnumeration</span><span class="sxs-lookup"><span data-stu-id="e6c72-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="e6c72-103">Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která iteruje přes kolekci čísel. Následující tabulka obsahuje podrobnosti o hlavních soubory zahrnuté v ukázce.</span><span class="sxs-lookup"><span data-stu-id="e6c72-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="e6c72-104">Název souboru</span><span class="sxs-lookup"><span data-stu-id="e6c72-104">File name</span></span>|<span data-ttu-id="e6c72-105">Popis</span><span class="sxs-lookup"><span data-stu-id="e6c72-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6c72-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="e6c72-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="e6c72-107">Definuje vlastní aktivita s názvem `RangeEnumeration` , přepíše <xref:System.Activities.NativeActivity> třídy a smyčky prostřednictvím řady čísla.</span><span class="sxs-lookup"><span data-stu-id="e6c72-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="e6c72-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="e6c72-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="e6c72-109">Klientské aplikace používající `RangeEnumeration` aktivity k iteraci přes kolekci čísel.</span><span class="sxs-lookup"><span data-stu-id="e6c72-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="e6c72-110">Následující tabulka obsahuje podrobnosti o vlastnostech `RangeEnumeration` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c72-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="e6c72-111">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e6c72-111">Property</span></span>|<span data-ttu-id="e6c72-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e6c72-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e6c72-113">Spustit</span><span class="sxs-lookup"><span data-stu-id="e6c72-113">Start</span></span>|<span data-ttu-id="e6c72-114">Celé číslo spustit ze smyčky.</span><span class="sxs-lookup"><span data-stu-id="e6c72-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="e6c72-115">Zastavit</span><span class="sxs-lookup"><span data-stu-id="e6c72-115">Stop</span></span>|<span data-ttu-id="e6c72-116">Celé číslo k ukončení smyčky v.</span><span class="sxs-lookup"><span data-stu-id="e6c72-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="e6c72-117">Krok</span><span class="sxs-lookup"><span data-stu-id="e6c72-117">Step</span></span>|<span data-ttu-id="e6c72-118">Určuje, kolik k iteraci v každém.</span><span class="sxs-lookup"><span data-stu-id="e6c72-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="e6c72-119">Text</span><span class="sxs-lookup"><span data-stu-id="e6c72-119">Body</span></span>|<span data-ttu-id="e6c72-120">Určuje kód pro spuštění při každé iteraci.</span><span class="sxs-lookup"><span data-stu-id="e6c72-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e6c72-121">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="e6c72-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="e6c72-122">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="e6c72-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e6c72-123">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="e6c72-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e6c72-124">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="e6c72-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e6c72-125">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e6c72-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e6c72-126">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e6c72-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e6c72-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e6c72-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6c72-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e6c72-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`