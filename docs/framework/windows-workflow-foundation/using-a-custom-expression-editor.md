---
title: Použití editoru vlastních výrazů
ms.date: 03/30/2017
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
ms.openlocfilehash: a1cd92766c8897868920c1465ddb3eeabae1aa97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182719"
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="cd90f-102">Použití editoru vlastních výrazů</span><span class="sxs-lookup"><span data-stu-id="cd90f-102">Using a Custom Expression Editor</span></span>
<span data-ttu-id="cd90f-103">Editor vlastních výrazů lze implementovat tak, aby poskytoval bohatší nebo jednodušší prostředí pro úpravy výrazů.</span><span class="sxs-lookup"><span data-stu-id="cd90f-103">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="cd90f-104">Existuje několik scénářů, ve kterých můžete chtít použít editor vlastních výrazů:</span><span class="sxs-lookup"><span data-stu-id="cd90f-104">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
- <span data-ttu-id="cd90f-105">Poskytování podpory pro technologie IntelliSense a další funkce pro bohaté úpravy v návrháři pracovních postupů s rehosted.</span><span class="sxs-lookup"><span data-stu-id="cd90f-105">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="cd90f-106">Tato funkce musí být k dispozici, protože výchozí editor výrazů sady Visual Studio nelze použít v rehosted aplikacích.</span><span class="sxs-lookup"><span data-stu-id="cd90f-106">This functionality must be provided because the default Visual Studio expression editor cannot be used in rehosted applications.</span></span>  
  
- <span data-ttu-id="cd90f-107">Chcete-li zjednodušit prostředí pro úpravy výrazů pro uživatele obchodníanalytik, tak, aby například nutné se učit visual basic nebo zabývat se výrazy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cd90f-107">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn Visual Basic or deal with Visual Basic expressions.</span></span>  
  
 <span data-ttu-id="cd90f-108">K implementaci editoru vlastních výrazů jsou zapotřebí tři základní kroky:</span><span class="sxs-lookup"><span data-stu-id="cd90f-108">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1. <span data-ttu-id="cd90f-109">Implementujte rozhraní <xref:System.Activities.Presentation.View.IExpressionEditorService>.</span><span class="sxs-lookup"><span data-stu-id="cd90f-109">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="cd90f-110">Toto rozhraní spravuje vytváření a ničení editorů výrazů.</span><span class="sxs-lookup"><span data-stu-id="cd90f-110">This interface manages the creation and destruction of expression editors.</span></span>  
  
2. <span data-ttu-id="cd90f-111">Implementujte rozhraní <xref:System.Activities.Presentation.View.IExpressionEditorInstance>.</span><span class="sxs-lookup"><span data-stu-id="cd90f-111">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="cd90f-112">Toto rozhraní implementuje uživatelské rozhraní pro úpravu výrazu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd90f-112">This interface implements the UI for expression editing UI.</span></span>  
  
3. <span data-ttu-id="cd90f-113">Publikujte <xref:System.Activities.Presentation.View.IExpressionEditorService> v aplikaci rehosted workflow.</span><span class="sxs-lookup"><span data-stu-id="cd90f-113">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="cd90f-114">Implementace editoru vlastních výrazů v knihovně tříd</span><span class="sxs-lookup"><span data-stu-id="cd90f-114">Implementing a Custom Expression Editor in a Class Library</span></span>  
 <span data-ttu-id="cd90f-115">Zde je ukázka kódu pro třídu `MyEditorService` (proof of <xref:System.Activities.Presentation.View.IExpressionEditorService> concept), která implementuje rozhraní je obsažena v projektu knihovny MyExpressionEditorService.</span><span class="sxs-lookup"><span data-stu-id="cd90f-115">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Activities.Presentation.View;  
using System.Activities.Presentation.Hosting;  
using System.Activities.Presentation.Model;  
  
namespace MyExpressionEditorService  
{  
    public class MyEditorService : IExpressionEditorService  
    {  
        public void CloseExpressionEditors()  
        {  
  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, System.Windows.Size initialSize)  
                {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType)  
            {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType, System.Windows.Size initialSize)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public void UpdateContext(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces)  
        {  
  
        }  
  
    }  
}  
```  
  
 <span data-ttu-id="cd90f-116">Zde je kód `MyExpressionEditorInstance` pro třídu, <xref:System.Activities.Presentation.View.IExpressionEditorInstance> která implementuje rozhraní v projektu knihovny MyExpressionEditorService.</span><span class="sxs-lookup"><span data-stu-id="cd90f-116">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
```csharp  
using System;  
using System.Activities.Presentation.View;  
using System.Windows;  
using System.Reflection;  
using System.Windows.Controls;  
  
namespace MyExpressionEditorService  
{  
    public class MyExpressionEditorInstance : IExpressionEditorInstance  
    {  
        private TextBox textBox = new TextBox();  
  
        public bool AcceptsReturn { get; set; }  
        public bool AcceptsTab { get; set; }  
        public bool HasAggregateFocus {  
            get  
            {  
                return true;  
            }  
        }  
  
        public System.Windows.Controls.ScrollBarVisibility HorizontalScrollBarVisibility { get; set; }  
        public System.Windows.Controls.Control HostControl {  
            get  
            {  
                return textBox;  
            }  
        }  
        public int MaxLines { get; set; }  
        public int MinLines { get; set; }  
        public string Text { get; set; }  
        public System.Windows.Controls.ScrollBarVisibility VerticalScrollBarVisibility { get; set; }  
  
        public event EventHandler Closing;  
        public event EventHandler GotAggregateFocus;  
        public event EventHandler LostAggregateFocus;  
        public event EventHandler TextChanged;  
  
        public bool CanCompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCopy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanDecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanGlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanIncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanPaste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanQuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanRedo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanUndo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
  
        public void ClearSelection()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public void Close()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public bool CompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Copy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Cut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool DecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public void Focus()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public string GetCommittedText()  
        {  
            return "CommittedText";  
        }  
        public bool GlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool IncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool ParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Paste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool QuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Redo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Undo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
    }  
}  
```  
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="cd90f-117">Publikování editoru vlastních výrazů v projektu WPF</span><span class="sxs-lookup"><span data-stu-id="cd90f-117">Publishing a Custom Expression Editor in a WPF Project</span></span>  
 <span data-ttu-id="cd90f-118">Zde je kód, který ukazuje, jak rehost návrháře v aplikaci `MyEditorService` WPF a jak vytvořit a publikovat službu.</span><span class="sxs-lookup"><span data-stu-id="cd90f-118">Here is the code that shows how to rehost the designer in a WPF application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="cd90f-119">Před použitím tohoto kódu přidejte odkaz na projekt knihovny MyExpressionEditorService z projektu, který obsahuje aplikaci avalon2.</span><span class="sxs-lookup"><span data-stu-id="cd90f-119">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
```csharp  
using System.Windows;  
using System.Windows.Controls;  
using System.Activities.Presentation;  
using System.Activities.Statements;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation.View;  
using MyExpressionEditorService;  
  
namespace WpfApplication1  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
  
        private MyEditorService expressionEditorService;  
        public MainWindow()  
        {  
            InitializeComponent();  
            new DesignerMetadata().Register();  
            createDesigner();  
        }  
  
        public void createDesigner()  
        {  
            WorkflowDesigner designer = new WorkflowDesigner();  
            Sequence root = new Sequence()  
            {  
                Activities = {  
                new Assign(),  
                new WriteLine()}  
            };  
  
            designer.Load(root);  
  
            Grid.SetColumn(designer.View, 0);  
  
            // Create ExpressionEditorService
            this.expressionEditorService = new MyEditorService();  
  
            // Publish the instance of MyEditorService.  
            designer.Context.Services.Publish<IExpressionEditorService>(this.expressionEditorService);  
  
            MyGrid.Children.Add(designer.View);  
        }  
    }  
}  
```  
  
### <a name="notes"></a><span data-ttu-id="cd90f-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd90f-120">Notes</span></span>  
 <span data-ttu-id="cd90f-121">Pokud používáte **expressiontextbox** ovládací prvek ve vlastní návrháře aktivit, není nutné vytvářet <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> a <xref:System.Activities.Presentation.View.IExpressionEditorService> ničit editory výrazů pomocí <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> a metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd90f-121">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="cd90f-122">Třída <xref:System.Activities.Presentation.View.ExpressionTextBox> to zvládá za vás.</span><span class="sxs-lookup"><span data-stu-id="cd90f-122">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd90f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd90f-123">See also</span></span>

- <xref:System.Activities.Presentation.View.IExpressionEditorService>
- <xref:System.Activities.Presentation.View.IExpressionEditorInstance>
- [<span data-ttu-id="cd90f-124">Použití ExpressionTextBox v návrháři vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="cd90f-124">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
