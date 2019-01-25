---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 42290fa7d9d38a57e17984ae5f1a9505b099ce1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698281"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="cdb7f-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="cdb7f-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="cdb7f-103">Při vytváření ovládacích prvků, které pracují s daty, někdy najdete je nezbytné pro vytvoření vazby ovládacího prvku do typu, nikoli objekt.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="cdb7f-104">K této situaci dochází především v době návrhu, když dat nemusí být k dispozici, ale své ovládací prvky vázané na data potřebují k zobrazení informací z veřejného rozhraní typu.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="cdb7f-105">Například může vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládací prvek na objekt zveřejněné jako webová služba a chcete <xref:System.Windows.Forms.DataGridView> ovládací prvek popisek její sloupce v době návrhu s členem názvů vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="cdb7f-106">Můžete snadno vytvoření vazby ovládacího prvku na typ s <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdb7f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdb7f-107">Example</span></span>  
 <span data-ttu-id="cdb7f-108">Následující příklad kódu ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládacího prvku pomocí vlastního typu <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="cdb7f-109">Při spuštění v příkladu, můžete si všimnout <xref:System.Windows.Forms.DataGridView> je označené jako sloupce, které odpovídají vlastnosti `Customer` objektu před ovládací prvek naplněný daty.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="cdb7f-110">V příkladu má tlačítko Přidat zákazníka k přidání dat <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="cdb7f-111">Když kliknete na tlačítko Nový `Customer` přidán <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="cdb7f-112">Ve skutečném scénáři může být volání webové služby nebo jiného zdroje dat získat data.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cdb7f-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cdb7f-113">Compiling the Code</span></span>  
 <span data-ttu-id="cdb7f-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cdb7f-114">This example requires:</span></span>  
  
-   <span data-ttu-id="cdb7f-115">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="cdb7f-116">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cdb7f-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cdb7f-117">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="cdb7f-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="cdb7f-118">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="cdb7f-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb7f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdb7f-119">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="cdb7f-120">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="cdb7f-120">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
