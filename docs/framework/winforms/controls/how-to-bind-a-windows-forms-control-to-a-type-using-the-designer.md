---
title: Svázání ovládacího prvku s typem pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 2257489e123ceeea819ad3538952db51b726c7e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742029"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="87998-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="87998-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>

<span data-ttu-id="87998-103">Při vytváření ovládacích prvků, které komunikují s daty, někdy je nutné vytvořit navázání ovládacího prvku na typ místo objektu.</span><span class="sxs-lookup"><span data-stu-id="87998-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="87998-104">Obvykle je nutné svázat ovládací prvek s typem v době návrhu, pokud data nemusí být k dispozici, ale přesto chcete, aby ovládací prvky vázané na data zobrazovaly data z veřejného rozhraní typu.</span><span class="sxs-lookup"><span data-stu-id="87998-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="87998-105">Následující postupy ukazují, jak vytvořit nový <xref:System.Windows.Forms.BindingSource> vázaný na typ a následně jak svázat jednu z vlastností typu s vlastností <xref:System.Windows.Forms.TextBox.Text%2A> <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="87998-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>

### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="87998-106">Navázání objektu BindingSource na typ</span><span class="sxs-lookup"><span data-stu-id="87998-106">To bind the BindingSource to a type</span></span>

1. <span data-ttu-id="87998-107">Vytvořte projekt model Windows Forms (**soubor** > **Nový** > **projektu** > **vizuálu C#**  nebo **Visual Basic** > **klasické plochy** > **model Windows Forms aplikaci**).</span><span class="sxs-lookup"><span data-stu-id="87998-107">Create a Windows Forms project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="87998-108">V **návrhovém** zobrazení přetáhněte komponentu <xref:System.Windows.Forms.BindingSource> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="87998-108">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>

3. <span data-ttu-id="87998-109">V okně **vlastnosti** klikněte na šipku u vlastnosti <xref:System.Windows.Forms.BindingSource.DataSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="87998-109">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>

4. <span data-ttu-id="87998-110">V **editoru typu uživatelského rozhraní DataSource**klikněte na **Přidat zdroj dat projektu**.</span><span class="sxs-lookup"><span data-stu-id="87998-110">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>

5. <span data-ttu-id="87998-111">Na stránce **Zvolte typ zdroje dat** vyberte **objekt** a klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="87998-111">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>

6. <span data-ttu-id="87998-112">Vyberte typ, na který se má vytvořit vazba:</span><span class="sxs-lookup"><span data-stu-id="87998-112">Select the type to bind to:</span></span>

    - <span data-ttu-id="87998-113">Pokud je typ, ke kterému chcete vytvořit vazby, v aktuálním projektu nebo sestavení, které obsahuje typ, je již přidáno jako odkaz, rozbalte uzly a Najděte požadovaný typ a pak ho vyberte.</span><span class="sxs-lookup"><span data-stu-id="87998-113">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>

      <span data-ttu-id="87998-114">\-nebo-</span><span class="sxs-lookup"><span data-stu-id="87998-114">\-or-</span></span>

    - <span data-ttu-id="87998-115">Pokud je typ, ke kterému chcete vytvořit vazby, v jiném sestavení, které není aktuálně v seznamu odkazů, klikněte na tlačítko **Přidat odkaz**a poté klikněte na kartu **projekty** . Vyberte projekt obsahující požadovaný obchodní objekt a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="87998-115">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="87998-116">Tento projekt se zobrazí v seznamu sestavení, takže můžete rozbalit uzly a najít požadovaný typ a pak ho vybrat.</span><span class="sxs-lookup"><span data-stu-id="87998-116">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>

      > [!NOTE]
      > <span data-ttu-id="87998-117">Pokud chcete vytvořit vazby na typ v rozhraní nebo sestavení společnosti Microsoft, zrušte zaškrtnutí políčka **Skrýt sestavení, která začínají na Microsoft nebo System** .</span><span class="sxs-lookup"><span data-stu-id="87998-117">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>

7. <span data-ttu-id="87998-118">Klikněte na **Další**a potom na **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="87998-118">Click **Next**, and then click **Finish**.</span></span>

### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="87998-119">Navázání ovládacího prvku na objekt BindingSource</span><span class="sxs-lookup"><span data-stu-id="87998-119">To bind the control to the BindingSource</span></span>

1. <span data-ttu-id="87998-120">Přidejte <xref:System.Windows.Forms.TextBox> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="87998-120">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>

2. <span data-ttu-id="87998-121">V okně **vlastnosti** rozbalte uzel **(datové vazby)** .</span><span class="sxs-lookup"><span data-stu-id="87998-121">In the **Properties** window, expand the **(DataBindings)** node.</span></span>

3. <span data-ttu-id="87998-122">Klikněte na šipku vedle vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="87998-122">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

4. <span data-ttu-id="87998-123">V **editoru typu uživatelského rozhraní DataSource**rozbalte uzel pro <xref:System.Windows.Forms.BindingSource> přidané dříve a vyberte vlastnost vázaného typu, který chcete svázat s vlastností <xref:System.Windows.Forms.TextBox.Text%2A> <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="87998-123">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="see-also"></a><span data-ttu-id="87998-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="87998-124">See also</span></span>

- [<span data-ttu-id="87998-125">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="87998-125">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="87998-126">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="87998-126">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
- [<span data-ttu-id="87998-127">Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87998-127">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
