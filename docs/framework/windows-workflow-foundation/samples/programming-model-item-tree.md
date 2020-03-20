---
title: Programování stromu položek modelu
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f14b140fdac95f3763cc5625841a725793876fa4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142690"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="48f61-102">Programování stromu položek modelu</span><span class="sxs-lookup"><span data-stu-id="48f61-102">Programming Model Item Tree</span></span>
<span data-ttu-id="48f61-103">Tato ukázka ukazuje, <xref:System.Activities.Presentation.Model.ModelItem> jak procházet strom pomocí deklarativní datové vazby ze stromového zobrazení Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="48f61-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="48f61-104">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="48f61-104">Sample Details</span></span>
 <span data-ttu-id="48f61-105">Strom <xref:System.Activities.Presentation.Model.ModelItem> je abstrakce, která se používá infrastruktury Windows Workflow Designer vystavit data o základní instance upravované.</span><span class="sxs-lookup"><span data-stu-id="48f61-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="48f61-106">Následující obrázek je znázornění různých vrstev infrastruktury v rámci Návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="48f61-106">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![Diagram, který zobrazuje architekturu Návrháře pracovních postupů.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="48f61-108">A <xref:System.Activities.Presentation.Model.ModelItem> se skládá z ukazatele na základní hodnotu, <xref:System.Activities.Presentation.Model.ModelProperty> stejně jako kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="48f61-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="48f61-109">Objekt <xref:System.Activities.Presentation.Model.ModelProperty> zase skládá z dat, jako je například název a typ vlastnosti a pak ukazatel <xref:System.Activities.Presentation.Model.ModelItem>na hodnotu, která je zase jiný .</span><span class="sxs-lookup"><span data-stu-id="48f61-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="48f61-110">Převaděč hodnot se používá k <xref:System.Activities.Presentation.Model.ModelItem>manipulaci <xref:System.Activities.Presentation.Model.ModelProperty> s některými s vrácené z a, aby se správně zobrazí ve stromovém zobrazení.</span><span class="sxs-lookup"><span data-stu-id="48f61-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="48f61-111">Ukázka pak ukazuje, jak imperativně programovat proti stromu <xref:System.Activities.Presentation.Model.ModelItem> pomocí imperativní syntaxe, jak je vidět v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="48f61-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="48f61-112">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="48f61-112">To use this sample</span></span>

1. <span data-ttu-id="48f61-113">Otevřete řešení ProgrammingModelItemTree.sln v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="48f61-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="48f61-114">Vytvořte řešení výběrem **sestavení řešení** z nabídky **sestavení.**</span><span class="sxs-lookup"><span data-stu-id="48f61-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="48f61-115">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="48f61-115">Press F5 to run the application.</span></span> <span data-ttu-id="48f61-116">Poté se zobrazí formulář WPF.</span><span class="sxs-lookup"><span data-stu-id="48f61-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="48f61-117">Klepnutím na tlačítko **Načíst WF** načtěte tlačítko <xref:System.Activities.Presentation.Model.ModelItem> a spojte jej se stromovou zobrazení.</span><span class="sxs-lookup"><span data-stu-id="48f61-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="48f61-118">Kliknutím na tlačítko **Změnit strom položky modelu** se spustí předchozí kód pro přidání položky do stromu a nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="48f61-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48f61-119">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="48f61-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="48f61-120">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="48f61-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="48f61-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="48f61-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48f61-122">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="48f61-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="48f61-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="48f61-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
