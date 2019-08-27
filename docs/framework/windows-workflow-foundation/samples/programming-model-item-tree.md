---
title: Programování stromu položek modelu
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f2d89cb2a3b0f6167f043148ea793ec1c264a556
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038177"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="db71e-102">Programování stromu položek modelu</span><span class="sxs-lookup"><span data-stu-id="db71e-102">Programming Model Item Tree</span></span>
<span data-ttu-id="db71e-103">Tato ukázka předvádí, <xref:System.Activities.Presentation.Model.ModelItem> jak navigovat strom pomocí deklarativní datové vazby ze zobrazení stromu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="db71e-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="db71e-104">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="db71e-104">Sample Details</span></span>
 <span data-ttu-id="db71e-105">Strom je abstrakce, kterou používá [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastruktura k vystavování dat o upravované podkladové instanci. <xref:System.Activities.Presentation.Model.ModelItem></span><span class="sxs-lookup"><span data-stu-id="db71e-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="db71e-106">Následující ilustrace znázorňuje různé vrstvy infrastruktury v rámci [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db71e-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>

 ![Diagram znázorňující architekturu Návrhář postupu provádění.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="db71e-108">Se skládá z ukazatele na podkladovou hodnotu, jakož i <xref:System.Activities.Presentation.Model.ModelProperty> kolekce objektů. <xref:System.Activities.Presentation.Model.ModelItem></span><span class="sxs-lookup"><span data-stu-id="db71e-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="db71e-109">Objekt je zase tvořen daty, jako jsou název a typ vlastnosti, a potom ukazatel na hodnotu, která je zase další <xref:System.Activities.Presentation.Model.ModelItem>. <xref:System.Activities.Presentation.Model.ModelProperty></span><span class="sxs-lookup"><span data-stu-id="db71e-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="db71e-110">Konvertor hodnot se používá k manipulaci <xref:System.Activities.Presentation.Model.ModelItem>s některými z a vrácenými z a <xref:System.Activities.Presentation.Model.ModelProperty> tak, aby se ve stromovém zobrazení zobrazovaly správně.</span><span class="sxs-lookup"><span data-stu-id="db71e-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="db71e-111">Ukázka pak demonstruje, jak imperativně programovat <xref:System.Activities.Presentation.Model.ModelItem> proti stromu pomocí imperativní syntaxe, jak je vidět v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="db71e-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="db71e-112">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="db71e-112">To use this sample</span></span>

1. <span data-ttu-id="db71e-113">Otevřete řešení ProgrammingModelItemTree. sln v aplikaci Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="db71e-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="db71e-114">Sestavte řešení výběrem možnosti **Sestavit řešení** v nabídce **sestavení** .</span><span class="sxs-lookup"><span data-stu-id="db71e-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="db71e-115">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="db71e-115">Press F5 to run the application.</span></span> <span data-ttu-id="db71e-116">Pak se zobrazí formulář WPF.</span><span class="sxs-lookup"><span data-stu-id="db71e-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="db71e-117">Kliknutím na tlačítko **načíst WF** načtěte <xref:System.Activities.Presentation.Model.ModelItem> a navažte ho do stromového zobrazení.</span><span class="sxs-lookup"><span data-stu-id="db71e-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="db71e-118">Kliknutím na tlačítko **změnit strom položky modelu** se spustí předchozí kód pro přidání položky do stromu a nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="db71e-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db71e-119">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="db71e-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="db71e-120">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="db71e-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="db71e-121">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="db71e-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="db71e-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="db71e-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="db71e-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db71e-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
