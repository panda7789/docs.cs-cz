---
title: "Pomocí kolekce aktivit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84218f16f846e640baea663efc7153a40a6c764a
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="using-collection-activities"></a><span data-ttu-id="73810-102">Pomocí kolekce aktivit</span><span class="sxs-lookup"><span data-stu-id="73810-102">Using Collection Activities</span></span>
<span data-ttu-id="73810-103">Tento příklad znázorňuje způsob použití aktivity kolekce (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, a <xref:System.Activities.Statements.RemoveFromCollection%601>) s třídou, která implementuje <xref:System.Collections.ICollection> rozhraní a jak vytvořit vlastní aktivity, který iteruje nad kolekcí do Vytiskněte obsah jednotlivých prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="73810-103">This sample demonstrates how to use the collection activities (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, and <xref:System.Activities.Statements.RemoveFromCollection%601>) with a class that implements the <xref:System.Collections.ICollection> interface and how to create a custom activity that iterates over a collection to print out the contents of each element in the collection.</span></span> <span data-ttu-id="73810-104">Vlastní aktivity, která se nazývá `PrintCollection`, pošle tisk do konzoly nástroje členů položky kolekci s názvem `Numbers`.</span><span class="sxs-lookup"><span data-stu-id="73810-104">The custom activity, which is named `PrintCollection`, prints to the console the item members of a collection named `Numbers`.</span></span>  
  
 <span data-ttu-id="73810-105">Následující tabulka popisuje čtyři aktivity, které poskytují manipulaci kolekce pro pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="73810-105">The following table describes the four activities that provide collection manipulation for workflows.</span></span>  
  
|<span data-ttu-id="73810-106">Název aktivity</span><span class="sxs-lookup"><span data-stu-id="73810-106">Activity name</span></span>|<span data-ttu-id="73810-107">Popis</span><span class="sxs-lookup"><span data-stu-id="73810-107">Description</span></span>|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|<span data-ttu-id="73810-108">Přidá položku do kolekce.</span><span class="sxs-lookup"><span data-stu-id="73810-108">Adds an item to a collection.</span></span>|  
|<xref:System.Activities.Statements.ClearCollection%601>|<span data-ttu-id="73810-109">Vymaže všechny položky v kolekci</span><span class="sxs-lookup"><span data-stu-id="73810-109">Clears all items in a collection</span></span>|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|<span data-ttu-id="73810-110">Vrátí `true` Pokud zadaná položka existuje v kolekci.</span><span class="sxs-lookup"><span data-stu-id="73810-110">Returns `true` if specified item exists in collection.</span></span>|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|<span data-ttu-id="73810-111">Odebere položku z kolekce.</span><span class="sxs-lookup"><span data-stu-id="73810-111">Removes an item from a collection.</span></span>|  
  
 <span data-ttu-id="73810-112">Ukázkový soubor obsahuje dvě řešení, jeden v adresáři CodedWorkflow a dalších v adresáři DesignerWorkflow.</span><span class="sxs-lookup"><span data-stu-id="73810-112">The sample consists of two solutions, one under the CodedWorkflow directory and the other under the DesignerWorkflow directory.</span></span> <span data-ttu-id="73810-113">Jejich ukázka dvěma různými způsoby použití aktivity pro stejné účely.</span><span class="sxs-lookup"><span data-stu-id="73810-113">They demonstrate two different ways of using the activities for the same purposes.</span></span>  
  
|<span data-ttu-id="73810-114">Řešení</span><span class="sxs-lookup"><span data-stu-id="73810-114">Solution</span></span>|<span data-ttu-id="73810-115">Popis</span><span class="sxs-lookup"><span data-stu-id="73810-115">Description</span></span>|<span data-ttu-id="73810-116">Hlavní soubory</span><span class="sxs-lookup"><span data-stu-id="73810-116">Main Files</span></span>|  
|-|-|-|  
|<span data-ttu-id="73810-117">CodedWorkflow</span><span class="sxs-lookup"><span data-stu-id="73810-117">CodedWorkflow</span></span>|<span data-ttu-id="73810-118">Vzorku klientskou aplikaci, která ukazuje, jak má být vyvolán aktivity kolekce prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="73810-118">Sample client application that demonstrates how to invoke the collection activities programmatically.</span></span>|<span data-ttu-id="73810-119">**PrintCollection.cs**: Pomocná aktivitu vytiskněte ke konzole každá položka v kolekci.</span><span class="sxs-lookup"><span data-stu-id="73810-119">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="73810-120">**Program.cs**: prostřednictvím kódu programu sestavení pořadí aktivity, která obsahuje řadu aktivit kolekce a provede ji.</span><span class="sxs-lookup"><span data-stu-id="73810-120">**Program.cs**: programmatically builds a sequence activity that contains a series of collection activities, and executes it.</span></span>|  
|<span data-ttu-id="73810-121">DesignerWorkflow</span><span class="sxs-lookup"><span data-stu-id="73810-121">DesignerWorkflow</span></span>|<span data-ttu-id="73810-122">Vzorku klientskou aplikaci, která demonstruje použití aktivity kolekce deklarativně v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="73810-122">Sample client application that demonstrates how to use the collection activities declaratively in the workflow designer.</span></span>|<span data-ttu-id="73810-123">**CollectionWorkflow.xaml**: pracovní postup vytvořený v deklarativně pomocí návrháře, který používá kolekce aktivit.</span><span class="sxs-lookup"><span data-stu-id="73810-123">**CollectionWorkflow.xaml**: a workflow created declaratively with the designer that uses the collection activities.</span></span><br /><br /> <span data-ttu-id="73810-124">**PrintCollection.cs**: Pomocná aktivitu vytiskněte ke konzole každá položka v kolekci.</span><span class="sxs-lookup"><span data-stu-id="73810-124">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="73810-125">**Program.cs**: vyvolá pracovní postup popsaný v CollectionWorkflow.xaml.</span><span class="sxs-lookup"><span data-stu-id="73810-125">**Program.cs**: invokes the workflow described in CollectionWorkflow.xaml.</span></span>|  
  
 <span data-ttu-id="73810-126">V ukázce, položka členy kolekce `Numbers` jsou vytištěné na konzole pomocí definované vlastní aktivity, názvem `PrintCollection`.</span><span class="sxs-lookup"><span data-stu-id="73810-126">In the demonstration, the item members of collection `Numbers` are printed on the console using a custom-defined activity called `PrintCollection`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="73810-127">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="73810-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="73810-128">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Collection.sln.</span><span class="sxs-lookup"><span data-stu-id="73810-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Collection.sln solution file.</span></span>  
  
2.  <span data-ttu-id="73810-129">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="73810-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="73810-130">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="73810-130">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="73810-131">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="73810-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="73810-132">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="73810-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="73810-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="73810-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="73810-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="73810-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`