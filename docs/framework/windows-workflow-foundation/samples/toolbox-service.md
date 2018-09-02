---
title: Služba sady nástrojů
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b21f10c763f3f82591f947eb4cc48cf90f4ac79
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406459"
---
# <a name="toolbox-service"></a><span data-ttu-id="be6a4-102">Služba sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="be6a4-102">Toolbox Service</span></span>
<span data-ttu-id="be6a4-103">Tato ukázka předvádí, jak aktualizovat [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] panelu nástrojů aktivity na základě kontextu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="be6a4-103">This sample demonstrates how to update the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] Toolbox activities based on the context of the workflow.</span></span> <span data-ttu-id="be6a4-104">Ukázka obsahuje pracovní postup, který změní obsah sady nástrojů založené na tom, jestli je vybraná vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="be6a4-104">The sample contains a workflow that changes the toolbox contents based on whether a custom activity is selected.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="be6a4-105">Diskuse</span><span class="sxs-lookup"><span data-stu-id="be6a4-105">Discussion</span></span>  
 <span data-ttu-id="be6a4-106">Při vytváření pracovního postupu, zákazníci chtějí obecně jejich nástrojů být závislá na kontextu.</span><span class="sxs-lookup"><span data-stu-id="be6a4-106">During workflow authoring, customers generally want their Toolbox to be context sensitive.</span></span> <span data-ttu-id="be6a4-107">Uživatel může třeba zajistit, že panelu nástrojů zobrazuje několik dalších aktivit, když je konkrétní aktivita přidána do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="be6a4-107">For example, the user may want to ensure that the Toolbox shows a few additional activities when a specific activity is added to the workflow.</span></span> <span data-ttu-id="be6a4-108">Pokud aktivity jsou odebrány z pracovního postupu, by měl panel nástrojů reagovat odpovídajícím způsobem na základě domény požadavků.</span><span class="sxs-lookup"><span data-stu-id="be6a4-108">If the activities are removed from the workflow, the toolbox should react appropriately based on the domain requirements.</span></span>  
  
 <span data-ttu-id="be6a4-109">V Návrháři znovu hostovaných pracovních postupů ovládací prvek ovládacího prvku panelu nástrojů a zajistit, aby na základě modelu změn v pracovním postupu, hostitel aktivuje odpovídající změny v ovládacím prvku panel nástrojů.</span><span class="sxs-lookup"><span data-stu-id="be6a4-109">In a re-hosted workflow designer, you control the Toolbox control and can ensure that based on the Model changes in the workflow, the host triggers appropriate changes in the Toolbox control.</span></span> <span data-ttu-id="be6a4-110">Nicméně v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], panel nástrojů není řízen uživatele a proto je potřeba rozhraní upravte jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="be6a4-110">However, in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], the toolbox is not controlled by the user and thus an interface is required to modify its contents.</span></span> <span data-ttu-id="be6a4-111">`IActivityToolboxService` je rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be6a4-111">`IActivityToolboxService` is that interface.</span></span>  
  
 <span data-ttu-id="be6a4-112">Rozhraní API poskytuje následující čtyři metody.</span><span class="sxs-lookup"><span data-stu-id="be6a4-112">The API provides the following four methods.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="be6a4-113">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="be6a4-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="be6a4-114">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení WorkflowSimulator.sln.</span><span class="sxs-lookup"><span data-stu-id="be6a4-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WorkflowSimulator.sln solution file.</span></span>  
  
2.  <span data-ttu-id="be6a4-115">Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="be6a4-115">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="be6a4-116">Otevřete soubor Workflow.xaml.</span><span class="sxs-lookup"><span data-stu-id="be6a4-116">Open the Workflow.xaml file.</span></span>  
  
4.  <span data-ttu-id="be6a4-117">Přidat **CustomActivity** přetahováním z panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="be6a4-117">Add a **CustomActivity** by dragging and dropping it from the toolbox.</span></span> <span data-ttu-id="be6a4-118">Všimněte si, že volá další kategorie panelu nástrojů: **novou kategorii WF** pomocí další aktivity **přiřadit**.</span><span class="sxs-lookup"><span data-stu-id="be6a4-118">Notice that an additional Toolbox category called: **New WF Category** with an additional activity **Assign**.</span></span>  
  
5.  <span data-ttu-id="be6a4-119">Nyní zrušit výběr **CustomActivity** přetáhněte další aktivitu do něj.</span><span class="sxs-lookup"><span data-stu-id="be6a4-119">Now unselect the **CustomActivity** by dragging another activity into it.</span></span>  
  
6.  <span data-ttu-id="be6a4-120">Položka **přiřadit** v kategorii **novou kategorii WF** ve skupinovém rámečku panelu nástrojů je odebraná.</span><span class="sxs-lookup"><span data-stu-id="be6a4-120">The item **Assign** in the category **New WF Category** under Toolbox is now removed.</span></span> <span data-ttu-id="be6a4-121">Navíc vzhledem k tomu, že neexistují žádné další položky v kategorii, bude odebrána také.</span><span class="sxs-lookup"><span data-stu-id="be6a4-121">Also, because there are no more items left in the category, the category is removed as well.</span></span>  
  
7.  <span data-ttu-id="be6a4-122">Vyberte **CustomActivity** znovu a kategorie a **přiřadit** aktivita je přidána zpět.</span><span class="sxs-lookup"><span data-stu-id="be6a4-122">Select the **CustomActivity** again and the category and **Assign** activity is added back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="be6a4-123">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="be6a4-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="be6a4-124">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="be6a4-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="be6a4-125">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="be6a4-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="be6a4-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="be6a4-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
