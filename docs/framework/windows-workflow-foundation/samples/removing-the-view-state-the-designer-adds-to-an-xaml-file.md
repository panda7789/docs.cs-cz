---
title: Odebrání stavu zobrazení, Návrhář přidá do souboru XAML
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: 0d4dccb16796893df58f709e011657457cc71670
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781684"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="50cff-102">Odebrání stavu zobrazení, Návrhář přidá do souboru XAML</span><span class="sxs-lookup"><span data-stu-id="50cff-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="50cff-103">Tento příklad ukazuje, jak vytvořit třídu, která je odvozena z <xref:System.Windows.Markup.XamlWriter> a odebere zobrazit stav ze souboru XAML.</span><span class="sxs-lookup"><span data-stu-id="50cff-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] <span data-ttu-id="50cff-104">zapisuje informace do dokumentu XAML, který je označován jako stav zobrazení.</span><span class="sxs-lookup"><span data-stu-id="50cff-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="50cff-105">Stav zobrazení odkazuje na informace, které je nutné v době návrhu, jako je například umístění rozložení, které nejsou potřebné v době běhu.</span><span class="sxs-lookup"><span data-stu-id="50cff-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] <span data-ttu-id="50cff-106">Vloží tyto informace do dokumentu XAML, jako je upravovat.</span><span class="sxs-lookup"><span data-stu-id="50cff-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] <span data-ttu-id="50cff-107">zapíše do souboru XAML s stav zobrazení `mc:Ignorable` atribut, takže tyto informace není načten při načtení modulu runtime XAML souboru.</span><span class="sxs-lookup"><span data-stu-id="50cff-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="50cff-108">Tento příklad ukazuje, jak vytvořit třídu, která odebere tuto informace o stavu zobrazení při zpracování uzlů XAML.</span><span class="sxs-lookup"><span data-stu-id="50cff-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>

## <a name="discussion"></a><span data-ttu-id="50cff-109">Diskuse</span><span class="sxs-lookup"><span data-stu-id="50cff-109">Discussion</span></span>
 <span data-ttu-id="50cff-110">Tento příklad ukazuje, jak vytvořit vlastní zapisovače.</span><span class="sxs-lookup"><span data-stu-id="50cff-110">This sample demonstrates how to create a custom writer.</span></span>

 <span data-ttu-id="50cff-111">Pokud chcete vytvořit vlastní zapisovače XAML, vytvořte třídu, která dědí z <xref:System.Windows.Markup.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="50cff-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="50cff-112">Jak často jsou vnořené uživatelé vytvářející obsah XAML, je typické ke sledování "vnitřních" zapisovač XAML.</span><span class="sxs-lookup"><span data-stu-id="50cff-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="50cff-113">Tyto "vnitřní" zapisovače si lze představit jako odkaz na zbývající zásobníku XAML zapisovačů, díky kterým práci a následně delegovat zpracování na zbývající část zásobníku více vstupních bodů.</span><span class="sxs-lookup"><span data-stu-id="50cff-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>

 <span data-ttu-id="50cff-114">V této ukázce se několik položek, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="50cff-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="50cff-115">Jeden je kontrola ověří, zda je položka zapisovaná z Návrháře oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="50cff-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="50cff-116">Všimněte si, že to také odstraní použití jiných typů z Návrháře oboru názvů v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="50cff-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

 <span data-ttu-id="50cff-117">Tím se vytvoří také zásobníku XAML členů, které se používají při rekurzivním průchodu datovém proudu uzlu.</span><span class="sxs-lookup"><span data-stu-id="50cff-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="50cff-118">Zbývající práce Tato ukázka je součástí do značné míry <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` metody.</span><span class="sxs-lookup"><span data-stu-id="50cff-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

 <span data-ttu-id="50cff-119">Následující metody a zkontrolujte, zda jsou stále obsažené v zobrazení stavu kontejneru a pokud ano, vraťte se a nepředávejte uzel dolů zásobníku zapisovače.</span><span class="sxs-lookup"><span data-stu-id="50cff-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

 <span data-ttu-id="50cff-120">Pokud chcete použít vlastní zapisovače XAML, musíte provést řetězení společně v zásobníku zapisovačů XAML.</span><span class="sxs-lookup"><span data-stu-id="50cff-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="50cff-121">Následující kód ukazuje, jak to lze použít.</span><span class="sxs-lookup"><span data-stu-id="50cff-121">The following code shows how this can be used.</span></span>

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="50cff-122">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="50cff-122">To use this sample</span></span>

1. <span data-ttu-id="50cff-123">Pomocí sady Visual Studio 2010, otevřete soubor řešení ViewStateCleaningWriter.sln.</span><span class="sxs-lookup"><span data-stu-id="50cff-123">Using Visual Studio 2010, open the ViewStateCleaningWriter.sln solution file.</span></span>

2. <span data-ttu-id="50cff-124">Otevřete příkazový řádek a přejděte do adresáře, kde je postavená ViewStageCleaningWriter.exe.</span><span class="sxs-lookup"><span data-stu-id="50cff-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>

3. <span data-ttu-id="50cff-125">Spusťte ViewStateCleaningWriter.exe Workflow1.xaml soubor.</span><span class="sxs-lookup"><span data-stu-id="50cff-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>

   <span data-ttu-id="50cff-126">Syntaxe pro spustitelný soubor je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="50cff-126">The syntax for the executable is shown in the following example.</span></span>

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   <span data-ttu-id="50cff-127">Výstupem soubor XAML, který chcete \[outfile], který má všechna zobrazení informací o stavu odebrána.</span><span class="sxs-lookup"><span data-stu-id="50cff-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>

> [!NOTE]
> <span data-ttu-id="50cff-128">Pro <xref:System.Activities.Statements.Sequence> pracovního postupu, počet virtualizace pomocné parametry se odeberou.</span><span class="sxs-lookup"><span data-stu-id="50cff-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="50cff-129">To způsobí, že návrhář přepočítat rozložení při příštím načtení.</span><span class="sxs-lookup"><span data-stu-id="50cff-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="50cff-130">Při použití pro tuto ukázku <xref:System.Activities.Statements.Flowchart>, umístění a směrování informace řádku se odeberou a na následné načítání do návrháře, jsou navršeny všechny aktivity na levé straně obrazovky.</span><span class="sxs-lookup"><span data-stu-id="50cff-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>

#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="50cff-131">K vytvoření ukázkového souboru XAML pro použití s touto ukázkou</span><span class="sxs-lookup"><span data-stu-id="50cff-131">To create a sample XAML file for use with this sample</span></span>

1. <span data-ttu-id="50cff-132">Otevřít Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="50cff-132">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="50cff-133">Vytvořte novou konzolovou aplikaci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="50cff-133">Create a new Workflow Console Application.</span></span>

3. <span data-ttu-id="50cff-134">Přetažení několika aktivity na plátno</span><span class="sxs-lookup"><span data-stu-id="50cff-134">Drag and drop a few activities onto the canvas</span></span>

4. <span data-ttu-id="50cff-135">Uložte soubor XAML pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="50cff-135">Save the workflow XAML file.</span></span>

5. <span data-ttu-id="50cff-136">Zkontrolujte soubor XAML k zobrazení stavu připojené vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="50cff-136">Inspect the XAML file to see the view state attached properties.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50cff-137">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="50cff-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="50cff-138">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="50cff-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="50cff-139">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="50cff-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="50cff-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="50cff-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
