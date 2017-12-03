---
title: "Sada nástrojů služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 294c530072b2d694f9aeb54d04b36d72bb6da637
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="toolbox-service"></a><span data-ttu-id="5d9cd-102">Sada nástrojů služby</span><span class="sxs-lookup"><span data-stu-id="5d9cd-102">Toolbox Service</span></span>
<span data-ttu-id="5d9cd-103">Tento příklad ukazuje, jak aktualizovat [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sada nástrojů aktivit na základě kontextu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-103">This sample demonstrates how to update the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] Toolbox activities based on the context of the workflow.</span></span> <span data-ttu-id="5d9cd-104">Ukázka obsahuje pracovní postup, který změní obsah sady nástrojů založené na tom, jestli je vybrané vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-104">The sample contains a workflow that changes the toolbox contents based on whether a custom activity is selected.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5d9cd-105">Diskusní</span><span class="sxs-lookup"><span data-stu-id="5d9cd-105">Discussion</span></span>  
 <span data-ttu-id="5d9cd-106">Při vytváření obsahu pracovního postupu, chcete zákazníkům obecně jejich nástrojů jako závislé na kontextu.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-106">During workflow authoring, customers generally want their Toolbox to be context sensitive.</span></span> <span data-ttu-id="5d9cd-107">Uživatel například může chtít zajistit, že sady nástrojů ukazuje několik další aktivity, při přidání konkrétní aktivitu do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-107">For example, the user may want to ensure that the Toolbox shows a few additional activities when a specific activity is added to the workflow.</span></span> <span data-ttu-id="5d9cd-108">Pokud aktivity budou odebrány z pracovního postupu, by měl sady nástrojů reagují odpovídajícím způsobem v závislosti na požadavcích domény.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-108">If the activities are removed from the workflow, the toolbox should react appropriately based on the domain requirements.</span></span>  
  
 <span data-ttu-id="5d9cd-109">V Návrháři znovu hostovaných pracovních postupů řídit ovládacího prvku sady nástrojů a zajistit, aby na základě změn modelu v pracovním postupu, hostitele spustí potřebné změny v ovládacím prvku panel nástrojů.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-109">In a re-hosted workflow designer, you control the Toolbox control and can ensure that based on the Model changes in the workflow, the host triggers appropriate changes in the Toolbox control.</span></span> <span data-ttu-id="5d9cd-110">Ale v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], sady nástrojů není řízené uživateli, a proto je potřeba rozhraní upravit její obsah.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-110">However, in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], the toolbox is not controlled by the user and thus an interface is required to modify its contents.</span></span> <span data-ttu-id="5d9cd-111">`IActivityToolboxService`je tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-111">`IActivityToolboxService` is that interface.</span></span>  
  
 <span data-ttu-id="5d9cd-112">Rozhraní API poskytuje následující čtyři metody.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-112">The API provides the following four methods.</span></span>  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5d9cd-113">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="5d9cd-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5d9cd-114">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WorkflowSimulator.sln.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WorkflowSimulator.sln solution file.</span></span>  
  
2.  <span data-ttu-id="5d9cd-115">Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-115">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="5d9cd-116">Otevřete soubor Workflow.xaml.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-116">Open the Workflow.xaml file.</span></span>  
  
4.  <span data-ttu-id="5d9cd-117">Přidat **CustomActivity** přetahováním myší z panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-117">Add a **CustomActivity** by dragging and dropping it from the toolbox.</span></span> <span data-ttu-id="5d9cd-118">Všimněte si, že volat další sady nástrojů kategorii: **novou kategorii WF** s další aktivitu **přiřadit**.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-118">Notice that an additional Toolbox category called: **New WF Category** with an additional activity **Assign**.</span></span>  
  
5.  <span data-ttu-id="5d9cd-119">Nyní zrušte výběr **CustomActivity** tak, že přetáhnete jinou aktivitu do ní.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-119">Now unselect the **CustomActivity** by dragging another activity into it.</span></span>  
  
6.  <span data-ttu-id="5d9cd-120">Položka **přiřadit** v kategorii **novou kategorii WF** v rámci sady nástrojů je teď odebrané.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-120">The item **Assign** in the category **New WF Category** under Toolbox is now removed.</span></span> <span data-ttu-id="5d9cd-121">Navíc vzhledem k tomu, že neexistují žádné další položky left v kategorii, bude odebrána také.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-121">Also, because there are no more items left in the category, the category is removed as well.</span></span>  
  
7.  <span data-ttu-id="5d9cd-122">Vyberte **CustomActivity** znovu a kategorie a **přiřadit** aktivity je přidány zpět.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-122">Select the **CustomActivity** again and the category and **Assign** activity is added back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5d9cd-123">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5d9cd-124">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5d9cd-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5d9cd-125">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5d9cd-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5d9cd-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
