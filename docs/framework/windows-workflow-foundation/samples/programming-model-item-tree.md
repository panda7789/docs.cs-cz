---
title: Programování stromu položek modelu
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: efda69ac568b0ad9c5fdcf4d42722c5b7dadd3f3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715668"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="9fdbd-102">Programování stromu položek modelu</span><span class="sxs-lookup"><span data-stu-id="9fdbd-102">Programming Model Item Tree</span></span>
<span data-ttu-id="9fdbd-103">Tato ukázka předvádí, jak navigovat <xref:System.Activities.Presentation.Model.ModelItem> stromu pomocí deklarativní datové vazby ze zobrazení stromu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="9fdbd-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="9fdbd-104">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="9fdbd-104">Sample Details</span></span>
 <span data-ttu-id="9fdbd-105"><xref:System.Activities.Presentation.Model.ModelItem> strom je abstrakcí, kterou používá infrastruktura Windows Návrhář postupu provádění k vystavování dat o upravované podkladové instanci.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="9fdbd-106">Následující ilustrace znázorňuje různé vrstvy infrastruktury v rámci Návrhář postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-106">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![Diagram znázorňující architekturu Návrhář postupu provádění.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="9fdbd-108"><xref:System.Activities.Presentation.Model.ModelItem> se skládá z ukazatele na podkladovou hodnotu a kolekce objektů <xref:System.Activities.Presentation.Model.ModelProperty>.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="9fdbd-109">Objekt <xref:System.Activities.Presentation.Model.ModelProperty> se zase skládá z dat, jako jsou název a typ vlastnosti a potom ukazatel na hodnotu, která je zase další <xref:System.Activities.Presentation.Model.ModelItem>.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="9fdbd-110">Konvertor hodnot se používá k manipulaci s některými <xref:System.Activities.Presentation.Model.ModelItem>y vrácenými z <xref:System.Activities.Presentation.Model.ModelProperty>, aby byly správně zobrazeny ve stromovém zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="9fdbd-111">Ukázka pak demonstruje, jak imperativně programovat do stromu <xref:System.Activities.Presentation.Model.ModelItem> pomocí imperativní syntaxe, jak je vidět v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="9fdbd-112">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="9fdbd-112">To use this sample</span></span>

1. <span data-ttu-id="9fdbd-113">Otevřete řešení ProgrammingModelItemTree. sln v aplikaci Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="9fdbd-114">Sestavte řešení výběrem možnosti **Sestavit řešení** v nabídce **sestavení** .</span><span class="sxs-lookup"><span data-stu-id="9fdbd-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="9fdbd-115">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-115">Press F5 to run the application.</span></span> <span data-ttu-id="9fdbd-116">Pak se zobrazí formulář WPF.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="9fdbd-117">Kliknutím na tlačítko **Load WF** načtěte <xref:System.Activities.Presentation.Model.ModelItem> a vytvořte jeho svázání se stromovým zobrazením.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="9fdbd-118">Kliknutím na tlačítko **změnit strom položky modelu** se spustí předchozí kód pro přidání položky do stromu a nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9fdbd-119">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9fdbd-120">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="9fdbd-121">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9fdbd-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9fdbd-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="9fdbd-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fdbd-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
