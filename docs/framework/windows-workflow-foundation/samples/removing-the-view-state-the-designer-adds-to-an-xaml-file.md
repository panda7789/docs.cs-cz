---
title: Odebrání stavu zobrazení, který Návrhář přidá do souboru XAML – WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f431275140e821aa5ec4d2235322f06be87d5ee2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715610"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="9de80-102">Odebrání stavu zobrazení, který Návrhář přidá do souboru XAML</span><span class="sxs-lookup"><span data-stu-id="9de80-102">Removing the view state the designer adds to an XAML file</span></span>

<span data-ttu-id="9de80-103">Tento příklad ukazuje, jak vytvořit třídu, která je odvozena z <xref:System.Xaml.XamlWriter> a odebírá stav zobrazení ze souboru XAML.</span><span class="sxs-lookup"><span data-stu-id="9de80-103">This sample demonstrates how to create a class that derives from <xref:System.Xaml.XamlWriter> and removes view state from a XAML file.</span></span> <span data-ttu-id="9de80-104">Windows Návrhář postupu provádění zapisuje informace do dokumentu XAML, který se označuje jako stav zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9de80-104">Windows Workflow Designer writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="9de80-105">Stav zobrazení odkazuje na informace, které jsou požadovány v době návrhu, jako je například umístění rozložení, které není nutné za běhu.</span><span class="sxs-lookup"><span data-stu-id="9de80-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> <span data-ttu-id="9de80-106">Návrhář postupu provádění vloží tyto informace do dokumentu XAML, jak je upravováno.</span><span class="sxs-lookup"><span data-stu-id="9de80-106">Workflow Designer inserts this information into the XAML document as it is edited.</span></span> <span data-ttu-id="9de80-107">Návrhář postupu provádění zapíše stav zobrazení do souboru XAML pomocí atributu `mc:Ignorable`, takže tyto informace nejsou načteny, pokud modul runtime načte soubor XAML.</span><span class="sxs-lookup"><span data-stu-id="9de80-107">Workflow Designer writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="9de80-108">Tento příklad ukazuje, jak vytvořit třídu, která odebere informace o stavu zobrazení při zpracovávání uzlů XAML.</span><span class="sxs-lookup"><span data-stu-id="9de80-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>

## <a name="discussion"></a><span data-ttu-id="9de80-109">Účely</span><span class="sxs-lookup"><span data-stu-id="9de80-109">Discussion</span></span>

<span data-ttu-id="9de80-110">Tato ukázka předvádí, jak vytvořit vlastní zapisovač.</span><span class="sxs-lookup"><span data-stu-id="9de80-110">This sample demonstrates how to create a custom writer.</span></span>

<span data-ttu-id="9de80-111">Chcete-li vytvořit vlastní zapisovač XAML, vytvořte třídu, která dědí z <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9de80-111">To build a custom XAML writer, create a class that inherits from <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="9de80-112">Protože moduly pro zápis XAML jsou často vnořené, je typický sledovat "vnitřní" zapisovač XAML.</span><span class="sxs-lookup"><span data-stu-id="9de80-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="9de80-113">Tyto "interní" zapisovače lze představit jako odkaz na zbývající zásobník modulů pro zápis XAML, což vám umožní mít více vstupních bodů pro práci a potom delegovat zpracování na zbytek zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9de80-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>

<span data-ttu-id="9de80-114">V této ukázce je k dispozici několik položek zájmu.</span><span class="sxs-lookup"><span data-stu-id="9de80-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="9de80-115">Jedna z nich kontroluje, jestli je položka napsaná z oboru názvů návrháře.</span><span class="sxs-lookup"><span data-stu-id="9de80-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="9de80-116">Všimněte si, že tento postup také odříznout použití jiných typů z oboru názvů návrháře v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="9de80-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>

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

<span data-ttu-id="9de80-117">Tím se také vytvoří zásobník členů XAML, které se používají při procházení datového proudu uzlu.</span><span class="sxs-lookup"><span data-stu-id="9de80-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="9de80-118">Zbývající práce této ukázky je převážně obsažena v `WriteStartMember` metodě.</span><span class="sxs-lookup"><span data-stu-id="9de80-118">The remaining work of this sample is largely contained in the `WriteStartMember` method.</span></span>

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

<span data-ttu-id="9de80-119">Následná metoda pak zkontroluje, zda jsou stále obsažena v kontejneru stavu zobrazení, a pokud ano, vrátí a neprojde uzel dolů v zásobníku zapisovače.</span><span class="sxs-lookup"><span data-stu-id="9de80-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>

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

<span data-ttu-id="9de80-120">Chcete-li použít vlastní zapisovač XAML, musíte ho zřetězit dohromady v zásobníku zapisovačů XAML.</span><span class="sxs-lookup"><span data-stu-id="9de80-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="9de80-121">Následující kód ukazuje, jak to lze použít.</span><span class="sxs-lookup"><span data-stu-id="9de80-121">The following code shows how this can be used.</span></span>

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a><span data-ttu-id="9de80-122">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="9de80-122">To use this sample</span></span>

1. <span data-ttu-id="9de80-123">Pomocí sady Visual Studio 2010 otevřete soubor řešení ViewStateCleaningWriter. sln.</span><span class="sxs-lookup"><span data-stu-id="9de80-123">Using Visual Studio 2010, open the ViewStateCleaningWriter.sln solution file.</span></span>

2. <span data-ttu-id="9de80-124">Otevřete příkazový řádek a přejděte do adresáře, kde je ViewStageCleaningWriter. exe sestaven.</span><span class="sxs-lookup"><span data-stu-id="9de80-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>

3. <span data-ttu-id="9de80-125">Spusťte ViewStateCleaningWriter. exe v souboru Workflow1. XAML.</span><span class="sxs-lookup"><span data-stu-id="9de80-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>

   <span data-ttu-id="9de80-126">Syntaxe pro spustitelný soubor je uvedena v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9de80-126">The syntax for the executable is shown in the following example.</span></span>

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   <span data-ttu-id="9de80-127">Výstupem je soubor XAML pro \[souboru], který obsahuje všechny informace o stavu zobrazení, které byly odebrány.</span><span class="sxs-lookup"><span data-stu-id="9de80-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>

> [!NOTE]
> <span data-ttu-id="9de80-128">U <xref:System.Activities.Statements.Sequence>ho pracovního postupu se odeberou několik pomocných parametrů virtualizace.</span><span class="sxs-lookup"><span data-stu-id="9de80-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="9de80-129">To způsobí, že návrhář přepočítá rozložení při příštím načtení.</span><span class="sxs-lookup"><span data-stu-id="9de80-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="9de80-130">Když použijete tuto ukázku pro <xref:System.Activities.Statements.Flowchart>, všechny informace o umístění a směrování na řádku se odeberou a při následném načítání do návrháře se všechny aktivity načítají na levou stranu obrazovky.</span><span class="sxs-lookup"><span data-stu-id="9de80-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="9de80-131">Vytvoření ukázkového souboru XAML pro použití s touto ukázkou</span><span class="sxs-lookup"><span data-stu-id="9de80-131">To create a sample XAML file for use with this sample</span></span>

1. <span data-ttu-id="9de80-132">Otevřete Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="9de80-132">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="9de80-133">Vytvoří novou konzolovou aplikaci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9de80-133">Create a new Workflow Console Application.</span></span>

3. <span data-ttu-id="9de80-134">Přetažení několika aktivit na plátno</span><span class="sxs-lookup"><span data-stu-id="9de80-134">Drag and drop a few activities onto the canvas</span></span>

4. <span data-ttu-id="9de80-135">Uložte soubor XAML pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9de80-135">Save the workflow XAML file.</span></span>

5. <span data-ttu-id="9de80-136">Zkontrolujte soubor XAML, abyste viděli vlastnosti stavu zobrazení připojené.</span><span class="sxs-lookup"><span data-stu-id="9de80-136">Inspect the XAML file to see the view state attached properties.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9de80-137">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="9de80-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9de80-138">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="9de80-138">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9de80-139">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="9de80-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9de80-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9de80-140">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
