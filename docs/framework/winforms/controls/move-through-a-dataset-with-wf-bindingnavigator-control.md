---
title: "Postupy: Pohyb v prvku DataSet pomocí ovládacího prvku Windows Forms BindingNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17710411811fbba94f81814876903b167f97e2fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="9bbfd-102">Postupy: Pohyb v prvku DataSet pomocí ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="9bbfd-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="9bbfd-103">Při sestavování datové aplikace, musíte se často zobrazíte kolekce dat pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="9bbfd-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="9bbfd-104"><xref:System.Windows.Forms.BindingNavigator> Ovládacího prvku ve spojení s <xref:System.Windows.Forms.BindingSource> součást, nabízí pohodlný a rozšiřitelné řešení pro procházení kolekce a zobrazování položek postupně.</span><span class="sxs-lookup"><span data-stu-id="9bbfd-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bbfd-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9bbfd-105">Example</span></span>  
 <span data-ttu-id="9bbfd-106">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.BindingNavigator> ovládací prvek, chcete-li procházet data.</span><span class="sxs-lookup"><span data-stu-id="9bbfd-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="9bbfd-107">Je součástí sady <xref:System.Data.DataView>, která je vázána <xref:System.Windows.Forms.TextBox> řízení s <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="9bbfd-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bbfd-108">Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="9bbfd-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="9bbfd-109">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="9bbfd-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="9bbfd-110">Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="9bbfd-110">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9bbfd-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9bbfd-111">Compiling the Code</span></span>  
 <span data-ttu-id="9bbfd-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9bbfd-112">This example requires:</span></span>  
  
-   <span data-ttu-id="9bbfd-113">Odkazy na systém, System.Data, System.Drawing, System.Windows.Forms a System.Xml sestavení.</span><span class="sxs-lookup"><span data-stu-id="9bbfd-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="9bbfd-114">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9bbfd-114">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9bbfd-115">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="9bbfd-115">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="9bbfd-116">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9bbfd-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbfd-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bbfd-117">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="9bbfd-118">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="9bbfd-118">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="9bbfd-119">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="9bbfd-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="9bbfd-120">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="9bbfd-120">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
