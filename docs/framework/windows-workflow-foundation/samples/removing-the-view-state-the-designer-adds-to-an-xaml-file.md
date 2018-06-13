---
title: Odebrání stav zobrazení návrháře přidá do souboru XAML
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f63723c29c76854602308ba3e8d7e6dd65d9fb94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517833"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="eb32a-102">Odebrání stav zobrazení návrháře přidá do souboru XAML</span><span class="sxs-lookup"><span data-stu-id="eb32a-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="eb32a-103">Tento příklad ukazuje, jak vytvořte třídu, která je odvozena z <xref:System.Windows.Markup.XamlWriter> a odebere zobrazení stavu ze souboru XAML.</span><span class="sxs-lookup"><span data-stu-id="eb32a-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]<span data-ttu-id="eb32a-104"> zapisuje informace do dokumentu XAML, která se označuje jako stav zobrazení.</span><span class="sxs-lookup"><span data-stu-id="eb32a-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="eb32a-105">Stav zobrazení odkazuje na informace, který je požadován v době návrhu, jako je například umístění rozložení, který není nutný za běhu.</span><span class="sxs-lookup"><span data-stu-id="eb32a-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="eb32a-106"> Vloží do dokumentu XAML tyto informace, jako je upravit.</span><span class="sxs-lookup"><span data-stu-id="eb32a-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]<span data-ttu-id="eb32a-107"> zapisuje do souboru XAML s stav zobrazení `mc:Ignorable` atributů, takže tyto informace není načíst, pokud modul runtime načte souboru XAML.</span><span class="sxs-lookup"><span data-stu-id="eb32a-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="eb32a-108">Tento příklad ukazuje, jak vytvořte třídu, která odebere této informace o stavu zobrazení při zpracování uzlů XAML.</span><span class="sxs-lookup"><span data-stu-id="eb32a-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="eb32a-109">Diskusní</span><span class="sxs-lookup"><span data-stu-id="eb32a-109">Discussion</span></span>  
 <span data-ttu-id="eb32a-110">Tento příklad znázorňuje, jak vytvořit vlastní zapisovač.</span><span class="sxs-lookup"><span data-stu-id="eb32a-110">This sample demonstrates how to create a custom writer.</span></span>  
  
 <span data-ttu-id="eb32a-111">Pokud chcete vytvořit vlastní zapisovač XAML, vytvořte třídu, která dědí z <xref:System.Windows.Markup.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="eb32a-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="eb32a-112">Jak často jsou vnořené zapisovače XAML, je typické ke sledování "vnitřní" XAML zapisovače.</span><span class="sxs-lookup"><span data-stu-id="eb32a-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="eb32a-113">Tyto "vnitřní ' zapisovače si lze představit jako odkaz na zbývající zásobníku zapisovačů XAML, umožní vám tak, aby měl více vstupních bodů k práci a potom delegovat zpracování ke zbytku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="eb32a-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>  
  
 <span data-ttu-id="eb32a-114">V této ukázce jsou několik položek, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="eb32a-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="eb32a-115">Jeden je zkontrolujte, zda je položka zapisovaný z Návrháře oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="eb32a-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="eb32a-116">Všimněte si, že to taky odstraní na použití jiných typů z Návrháře oboru názvů v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="eb32a-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="eb32a-117">Tím se vytvoří také zásobník XAML členů, které se používají při procházení datový proud uzlu.</span><span class="sxs-lookup"><span data-stu-id="eb32a-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="eb32a-118">Zbývající práce Tato ukázka je součástí z velké části <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` metoda.</span><span class="sxs-lookup"><span data-stu-id="eb32a-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>  
  
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
  
 <span data-ttu-id="eb32a-119">Následující metody pak zkontrolujte, zda jsou stále obsažené v kontejneru zobrazení stavu a pokud ano, vrátí a nepředávejte uzel dolů v zásobníku zapisovače.</span><span class="sxs-lookup"><span data-stu-id="eb32a-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>  
  
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
  
 <span data-ttu-id="eb32a-120">Pokud chcete používat vlastní zapisovač XAML, můžete, musí být propojeny ho společně v zásobníku zapisovačů XAML.</span><span class="sxs-lookup"><span data-stu-id="eb32a-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="eb32a-121">Následující kód ukazuje, jak je možné používat.</span><span class="sxs-lookup"><span data-stu-id="eb32a-121">The following code shows how this can be used.</span></span>  
  
```csharp 
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="eb32a-122">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="eb32a-122">To use this sample</span></span>  
  
1. <span data-ttu-id="eb32a-123">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ViewStateCleaningWriter.sln.</span><span class="sxs-lookup"><span data-stu-id="eb32a-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ViewStateCleaningWriter.sln solution file.</span></span>  
  
2. <span data-ttu-id="eb32a-124">Otevřete příkazový řádek a přejděte do adresáře, kde je založená ViewStageCleaningWriter.exe.</span><span class="sxs-lookup"><span data-stu-id="eb32a-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>  
  
3. <span data-ttu-id="eb32a-125">Spusťte ViewStateCleaningWriter.exe na soubor Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="eb32a-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>  

   <span data-ttu-id="eb32a-126">Syntaxe pro spustitelný soubor je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eb32a-126">The syntax for the executable is shown in the following example.</span></span>  
  
   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```
   
   <span data-ttu-id="eb32a-127">Tento soubor XAML pro výstupy \[Výstupní_soubor], která obsahuje všechny zobrazení informací o stavu odebrat.</span><span class="sxs-lookup"><span data-stu-id="eb32a-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb32a-128">Pro <xref:System.Activities.Statements.Sequence> pracovního postupu, počet virtualizace jsou pomocné parametry odebrána.</span><span class="sxs-lookup"><span data-stu-id="eb32a-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="eb32a-129">To způsobí, že návrháře přepočítat rozložení další čas, který je načten.</span><span class="sxs-lookup"><span data-stu-id="eb32a-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="eb32a-130">Při použití této ukázky pro <xref:System.Activities.Statements.Flowchart>, budou odebrány všechny umístění a směrování informace řádku a na dalších načítání do návrháře přibývají všechny aktivity na levé straně obrazovky.</span><span class="sxs-lookup"><span data-stu-id="eb32a-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>  
  
#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="eb32a-131">Chcete-li vytvořit a ukázkový soubor XAML pro použití s této ukázky</span><span class="sxs-lookup"><span data-stu-id="eb32a-131">To create a sample XAML file for use with this sample</span></span>  
  
1. <span data-ttu-id="eb32a-132">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb32a-132">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2. <span data-ttu-id="eb32a-133">Vytvořte novou konzolovou aplikaci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="eb32a-133">Create a new Workflow Console Application.</span></span>  
  
3. <span data-ttu-id="eb32a-134">Přetáhnout myší na plátno několik aktivit</span><span class="sxs-lookup"><span data-stu-id="eb32a-134">Drag and drop a few activities onto the canvas</span></span>  
  
4. <span data-ttu-id="eb32a-135">Uložte soubor XAML workflowu.</span><span class="sxs-lookup"><span data-stu-id="eb32a-135">Save the workflow XAML file.</span></span>  
  
5. <span data-ttu-id="eb32a-136">Zkontrolujte soubor XAML zobrazíte zobrazení stavu přidružené vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eb32a-136">Inspect the XAML file to see the view state attached properties.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eb32a-137">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="eb32a-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eb32a-138">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="eb32a-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="eb32a-139">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="eb32a-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eb32a-140">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="eb32a-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
