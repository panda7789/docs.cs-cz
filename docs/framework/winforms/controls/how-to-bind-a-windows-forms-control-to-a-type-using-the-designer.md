---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 33df9e050dd8c2b3ace8ff89cbd5939b538fcd95
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780218"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="2adb2-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="2adb2-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>
<span data-ttu-id="2adb2-103">Při vytváření ovládacích prvků, které pracují s daty, někdy potřebujete k vytvoření vazby ovládacího prvku typu, nikoli objekt.</span><span class="sxs-lookup"><span data-stu-id="2adb2-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="2adb2-104">Obvykle budete muset vytvoření vazby ovládacího prvku na typ v době návrhu, když dat nemusí být k dispozici, ale stále chcete své ovládací prvky vázané na data pro zobrazení dat z veřejného rozhraní typu.</span><span class="sxs-lookup"><span data-stu-id="2adb2-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="2adb2-105">Následující postupy ukazují, jak vytvořit nový <xref:System.Windows.Forms.BindingSource> , který je s vazbou na typ a pak jednu z vlastností typu vazba <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="2adb2-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="2adb2-106">Pro vazbu na typ objektu BindingSource</span><span class="sxs-lookup"><span data-stu-id="2adb2-106">To bind the BindingSource to a type</span></span>  
  
1.  <span data-ttu-id="2adb2-107">Vytvoření projektu Windows Forms (**souboru** > **nový** > **projektu** > **Visual C#** nebo **Jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).</span><span class="sxs-lookup"><span data-stu-id="2adb2-107">Create a Windows Forms project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="2adb2-108">V **návrhu** zobrazení, přetáhněte <xref:System.Windows.Forms.BindingSource> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="2adb2-108">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>  
  
3.  <span data-ttu-id="2adb2-109">V **vlastnosti** okna, klikněte na šipku u <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2adb2-109">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>  
  
4.  <span data-ttu-id="2adb2-110">V **editoru typů uživatelského rozhraní DataSource**, klikněte na tlačítko **přidat zdroj dat projektu**.</span><span class="sxs-lookup"><span data-stu-id="2adb2-110">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>  
  
5.  <span data-ttu-id="2adb2-111">Na **zvolte typ zdroje dat** stránce **objekt** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="2adb2-111">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>  
  
6.  <span data-ttu-id="2adb2-112">Vyberte typ, který chcete vytvořit vazbu na:</span><span class="sxs-lookup"><span data-stu-id="2adb2-112">Select the type to bind to:</span></span>  
  
    -   <span data-ttu-id="2adb2-113">Pokud je typ, který chcete vytvořit vazbu k v aktuálním projektu nebo sestavení obsahující typ je již přidána jako odkaz, rozbalte uzly najít požadovaný typ a pak ho vyberte.</span><span class="sxs-lookup"><span data-stu-id="2adb2-113">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>  
  
         <span data-ttu-id="2adb2-114">-nebo-</span><span class="sxs-lookup"><span data-stu-id="2adb2-114">-or-</span></span>  
  
    -   <span data-ttu-id="2adb2-115">Pokud chcete vytvořit vazbu na typ je v jiném sestavení, není aktuálně v seznamu odkazů, klikněte na tlačítko **přidat odkaz**a potom klikněte na tlačítko **projekty** kartu. Vyberte projekt, který obsahuje obchodní objekt a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="2adb2-115">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="2adb2-116">Tento projekt se objeví v seznamu sestavení, tak lze rozbalit uzly se najít typ můžete a pak vyberte ho.</span><span class="sxs-lookup"><span data-stu-id="2adb2-116">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2adb2-117">Pokud chcete vytvořit vazbu na typ v rámci nebo sestavení Microsoft, zrušte zaškrtnutí políčka **skrýt sestavení, které začínají s Microsoftem nebo systém** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="2adb2-117">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>  
  
7.  <span data-ttu-id="2adb2-118">Klikněte na tlačítko **Další**a potom klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="2adb2-118">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="2adb2-119">K vytvoření vazby ovládacího prvku BindingSource</span><span class="sxs-lookup"><span data-stu-id="2adb2-119">To bind the control to the BindingSource</span></span>  
  
1.  <span data-ttu-id="2adb2-120">Přidat <xref:System.Windows.Forms.TextBox> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="2adb2-120">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>  
  
2.  <span data-ttu-id="2adb2-121">V **vlastnosti** okna, rozbalte **(DataBindings)** uzlu.</span><span class="sxs-lookup"><span data-stu-id="2adb2-121">In the **Properties** window, expand the **(DataBindings)** node.</span></span>  
  
3.  <span data-ttu-id="2adb2-122">Klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2adb2-122">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
4.  <span data-ttu-id="2adb2-123">V **editoru typů uživatelského rozhraní DataSource**, rozbalte uzel pro <xref:System.Windows.Forms.BindingSource> přidali dříve a vyberte vlastnost vázaný typ, který chcete vytvořit vazbu k <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="2adb2-123">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2adb2-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2adb2-124">See Also</span></span>  
 [<span data-ttu-id="2adb2-125">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="2adb2-125">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="2adb2-126">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="2adb2-126">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [<span data-ttu-id="2adb2-127">Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2adb2-127">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
