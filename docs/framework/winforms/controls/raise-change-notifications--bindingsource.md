---
title: 'Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 039875473fe3bd1702ad43465edae2c73ffcadca
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397955"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="ccacd-102">Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="ccacd-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="ccacd-103"><xref:System.Windows.Forms.BindingSource> Komponenty automaticky zjistí změny ve zdroji dat. Pokud je typ obsažený v implementuje zdroj dat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a vyvolá <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události při změně hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ccacd-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="ccacd-104">To je užitečné, protože ovládací prvky vázané <xref:System.Windows.Forms.BindingSource> pak automaticky aktualizuje jako změn dat zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ccacd-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ccacd-105">Pokud zdroj dat implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a provádění asynchronní operace, by neměla provést změny pro zdroj dat na vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ccacd-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="ccacd-106">By měl místo toho načtěte data ve vlákně na pozadí a slučování dat do seznamu na vlákně UI.</span><span class="sxs-lookup"><span data-stu-id="ccacd-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccacd-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccacd-107">Example</span></span>  
 <span data-ttu-id="ccacd-108">Následující příklad kódu ukazuje jednoduchý provádění <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ccacd-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="ccacd-109">Také ukazuje, jak <xref:System.Windows.Forms.BindingSource> automaticky předá Změna zdroje dat pro vazbu ovládacího prvku, když <xref:System.Windows.Forms.BindingSource> je vázán na seznam <xref:System.ComponentModel.INotifyPropertyChanged> typu.</span><span class="sxs-lookup"><span data-stu-id="ccacd-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="ccacd-110">Pokud používáte `CallerMemberName` atribut, volání `NotifyPropertyChanged` metoda není nutné zadat název vlastnosti jako argument řetězec.</span><span class="sxs-lookup"><span data-stu-id="ccacd-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="ccacd-111">Další informace najdete v tématu [informace o subjektu volajícím](https://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span><span class="sxs-lookup"><span data-stu-id="ccacd-111">For more information, see [Caller Information](https://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ccacd-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ccacd-112">Compiling the Code</span></span>  
 <span data-ttu-id="ccacd-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ccacd-113">This example requires:</span></span>  
  
-   <span data-ttu-id="ccacd-114">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="ccacd-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ccacd-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ccacd-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ccacd-116">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="ccacd-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="ccacd-117">Viz také [hypertextový odkaz "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ccacd-117">Also see [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccacd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccacd-118">See Also</span></span>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [<span data-ttu-id="ccacd-119">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="ccacd-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="ccacd-120">Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="ccacd-120">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
