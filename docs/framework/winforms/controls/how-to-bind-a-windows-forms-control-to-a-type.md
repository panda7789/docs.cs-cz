---
title: 'Postupy: Vázání ovládacího prvku Windows Forms k typu'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a1782d7af7dc7155834926f4b94cf57adf6c4d53
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="0f9a9-102">Postupy: Vázání ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="0f9a9-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="0f9a9-103">Při vytváření ovládacích prvků, které pracují s daty, někdy zjistíte, je potřeba vytvořit vazbu ovládacího prvku do typu, nikoli objekt.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="0f9a9-104">Tato situace nastane zejména v době návrhu, když data nemusí být k dispozici, ale vaše ovládací prvky vázané na data pořád potřebovat k zobrazení informací z veřejné rozhraní typu.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="0f9a9-105">Například může vytvořit vazbu <xref:System.Windows.Forms.DataGridView> řízení k objektu vystavené webové služby a chcete <xref:System.Windows.Forms.DataGridView> ovládací prvek pro názvy vlastního typu označení její sloupce v době návrhu se členem.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="0f9a9-106">Můžete snadno vytvořit vazbu ovládacího prvku s typem s <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f9a9-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f9a9-107">Example</span></span>  
 <span data-ttu-id="0f9a9-108">Následující příklad kódu ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládacího prvku do vlastního typu pomocí <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="0f9a9-109">Když spustíte v příkladu, můžete si všimnout <xref:System.Windows.Forms.DataGridView> má označené sloupce, které odpovídají vlastnosti `Customer` objektu, než je ovládací prvek naplněný daty.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="0f9a9-110">V příkladu má tlačítko Přidat zákazníka k přidání dat <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0f9a9-111">Po kliknutí na tlačítko Nový `Customer` objekt přidán do <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="0f9a9-112">Ve scénáři reálného může volání webové služby nebo jiného zdroje dat získat data.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f9a9-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0f9a9-113">Compiling the Code</span></span>  
 <span data-ttu-id="0f9a9-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="0f9a9-114">This example requires:</span></span>  
  
-   <span data-ttu-id="0f9a9-115">Odkazy na systém a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0f9a9-116">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0f9a9-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0f9a9-117">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="0f9a9-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="0f9a9-118">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0f9a9-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9a9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f9a9-119">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="0f9a9-120">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="0f9a9-120">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
