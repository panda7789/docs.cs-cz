---
title: "Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a25b0dc81a6511698394eb86343f09051befc87f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="10fc2-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="10fc2-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>
<span data-ttu-id="10fc2-103">Při vytváření ovládacích prvků, které pracují s daty, někdy potřebujete k vytvoření vazby ovládacího prvku typu, nikoli objekt.</span><span class="sxs-lookup"><span data-stu-id="10fc2-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="10fc2-104">Obvykle je nutné vytvořit vazbu ovládacího prvku typu v době návrhu, když data nemusí být k dispozici, ale stále chcete vaše ovládací prvky vázané na data k zobrazení dat z veřejné rozhraní typu.</span><span class="sxs-lookup"><span data-stu-id="10fc2-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="10fc2-105">Následující postupy ukazují, jak vytvořit nový <xref:System.Windows.Forms.BindingSource> který je vázaný na typ a poté jak pro některé vlastnosti typu na vazbu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="10fc2-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="10fc2-106">Pro vazbu na typ BindingSource</span><span class="sxs-lookup"><span data-stu-id="10fc2-106">To bind the BindingSource to a type</span></span>  
  
1.  <span data-ttu-id="10fc2-107">Vytvořte projekt Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="10fc2-107">Create a Windows Forms project.</span></span>  
  
     <span data-ttu-id="10fc2-108">Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="10fc2-108">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="10fc2-109">V **návrhu** zobrazení, přetáhněte ji <xref:System.Windows.Forms.BindingSource> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="10fc2-109">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>  
  
3.  <span data-ttu-id="10fc2-110">V **vlastnosti** okně klikněte na šipku u položky <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="10fc2-110">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>  
  
4.  <span data-ttu-id="10fc2-111">V **Editor typů uživatelského rozhraní pro zdroj dat**, klikněte na tlačítko **přidat zdroj dat projektu**.</span><span class="sxs-lookup"><span data-stu-id="10fc2-111">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>  
  
5.  <span data-ttu-id="10fc2-112">Na **zvolte typ zdroje dat** vyberte **objekt** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="10fc2-112">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>  
  
6.  <span data-ttu-id="10fc2-113">Vyberte typ k vytvoření vazby:</span><span class="sxs-lookup"><span data-stu-id="10fc2-113">Select the type to bind to:</span></span>  
  
    -   <span data-ttu-id="10fc2-114">Pokud v aktuálním projektu, které chcete vytvořit vazbu na typ nebo sestavení, které obsahuje typ je již přidána jako odkaz, rozbalte uzly se najít typ, který má být a pak ho vyberte.</span><span class="sxs-lookup"><span data-stu-id="10fc2-114">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>  
  
         <span data-ttu-id="10fc2-115">-nebo-</span><span class="sxs-lookup"><span data-stu-id="10fc2-115">-or-</span></span>  
  
    -   <span data-ttu-id="10fc2-116">Pokud chcete vytvořit vazbu na typ je v jiném sestavení není aktuálně v seznamu odkazů na, klikněte na tlačítko **přidat odkaz na**a klikněte **projekty** kartě. Vyberte projekt, který obsahuje objekt obchodní a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="10fc2-116">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="10fc2-117">Tento projekt se objeví v seznamu sestavení, tak můžete rozbalit uzly se najít typ můžete má a pak ho vyberte.</span><span class="sxs-lookup"><span data-stu-id="10fc2-117">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="10fc2-118">Pokud chcete vytvořit vazbu na typ v framework nebo Microsoft sestavení, zrušte **skrýt sestavení, které začínají s Microsoftem nebo systému** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="10fc2-118">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>  
  
7.  <span data-ttu-id="10fc2-119">Klikněte na tlačítko **Další**a potom klikněte na **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="10fc2-119">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="10fc2-120">K vytvoření vazby ovládacího prvku BindingSource</span><span class="sxs-lookup"><span data-stu-id="10fc2-120">To bind the control to the BindingSource</span></span>  
  
1.  <span data-ttu-id="10fc2-121">Přidat <xref:System.Windows.Forms.TextBox> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="10fc2-121">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>  
  
2.  <span data-ttu-id="10fc2-122">V **vlastnosti** okno, rozbalte **(datové vazby)** uzlu.</span><span class="sxs-lookup"><span data-stu-id="10fc2-122">In the **Properties** window, expand the **(DataBindings)** node.</span></span>  
  
3.  <span data-ttu-id="10fc2-123">Klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="10fc2-123">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
4.  <span data-ttu-id="10fc2-124">V **Editor typů uživatelského rozhraní pro zdroj dat**, rozbalte uzel <xref:System.Windows.Forms.BindingSource> přidali dříve a vyberte vlastnost typu vázané chcete vytvořit vazbu <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="10fc2-124">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10fc2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="10fc2-125">See Also</span></span>  
 [<span data-ttu-id="10fc2-126">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="10fc2-126">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="10fc2-127">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="10fc2-127">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [<span data-ttu-id="10fc2-128">Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10fc2-128">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
