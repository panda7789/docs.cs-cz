---
title: Vývoj ovládacích prvků Windows Forms v době návrhu
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
ms.openlocfilehash: b58318a3e0e9881725d3c260251288c720fa4132
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745108"
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="2a834-102">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="2a834-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="2a834-103">Pro autory ovládací prvek rozhraní .NET Framework poskytuje celou řadu technologií pro vytváření ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2a834-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="2a834-104">Autoři už nejsou omezeny na vytváření složených ovládacích prvků, které slouží jako kolekce dříve existující ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="2a834-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="2a834-105">Prostřednictvím dědičnosti můžete vytvořit vlastní ovládací prvky z předchozích složených ovládacích prvků nebo dříve existující ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2a834-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="2a834-106">Také si můžete navrhovat vlastní ovládací prvky, které implementují vlastní vykreslování.</span><span class="sxs-lookup"><span data-stu-id="2a834-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="2a834-107">Tyto možnosti umožňují značnou flexibilitu při návrhu a funkci vizuální rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a834-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="2a834-108">Abyste mohli využívat tyto funkce, měli seznámit s koncepty programování založené na objektu.</span><span class="sxs-lookup"><span data-stu-id="2a834-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a834-109">Není nutné mít důkladné znalosti o dědičnosti, ale pravděpodobně pro vás bude užitečné k odkazování na [základní informace o dědičnosti (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="2a834-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="2a834-110">Pokud chcete vytvořit vlastní ovládací prvky pro použití na webové formuláře, naleznete v tématu [vyvíjet vlastní serverové ovládací prvky ASP.NET](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="2a834-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a834-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2a834-111">In This Section</span></span>  
 [<span data-ttu-id="2a834-112">Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="2a834-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="2a834-113">Ukazuje, jak vytvořit jednoduchý složeného ovládacího prvku v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2a834-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="2a834-114">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="2a834-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="2a834-115">Ukazuje, jak vytvořit jednoduchý složeného ovládacího prvku v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="2a834-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="2a834-116">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="2a834-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="2a834-117">Ukazuje, jak vytvořit jednoduchý ovládací prvek Windows Forms pomocí dědičnost v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2a834-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="2a834-118">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="2a834-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="2a834-119">Ukazuje, jak vytvořit jednoduchý ovládací prvek Windows Forms pomocí dědičnosti v C#.</span><span class="sxs-lookup"><span data-stu-id="2a834-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="2a834-120">Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a834-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="2a834-121">Ukazuje, jak použít funkci inteligentních značek v ovládacích prvcích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2a834-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="2a834-122">Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="2a834-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="2a834-123">Ukazuje způsob použití <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atribut pro serializaci kolekce.</span><span class="sxs-lookup"><span data-stu-id="2a834-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="2a834-124">Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="2a834-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="2a834-125">Ukazuje, jak ladit návrhu chování ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2a834-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="2a834-126">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="2a834-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="2a834-127">Ukazuje, jak úzce integrovány složeného ovládacího prvku do vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="2a834-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="2a834-128">Postupy: Vytváření ovládacích prvků pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a834-128">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="2a834-129">Poskytuje přehled důležitých informací pro implementaci ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2a834-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="2a834-130">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="2a834-130">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 <span data-ttu-id="2a834-131">Ukazuje, jak vytvořit ovládací prvek dědění ze složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2a834-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="2a834-132">Postupy: Dědění ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="2a834-132">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="2a834-133">Poskytuje přehled o postupu pro vytvoření složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2a834-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="2a834-134">Postupy: Dědění ze stávajících ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a834-134">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="2a834-135">Ukazuje, jak vytvořit dědění z ovládacího prvku rozšířené <xref:System.Windows.Forms.Button> třídu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2a834-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="2a834-136">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="2a834-136">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="2a834-137">Přehled vytváření ovládacího prvku rozšířené.</span><span class="sxs-lookup"><span data-stu-id="2a834-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="2a834-138">Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu</span><span class="sxs-lookup"><span data-stu-id="2a834-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="2a834-139">Ukazuje způsob použití <xref:System.Windows.Forms.Control.Dock%2A> vlastnost zarovnání ovládacího prvku na hraničních zařízeních zabírá formuláře.</span><span class="sxs-lookup"><span data-stu-id="2a834-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="2a834-140">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="2a834-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="2a834-141">Ukazuje postup při instalaci ovládacího prvku tak, aby se zobrazovalo ve **přizpůsobení panelu nástrojů** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2a834-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="2a834-142">Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2a834-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="2a834-143">Ukazuje způsob použití <xref:System.Drawing.ToolboxBitmapAttribute> ikonou vedle svého vlastního ovládacího prvku v zobrazení **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="2a834-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="2a834-144">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="2a834-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="2a834-145">Ukazuje způsob použití **kontejner testu UserControl** otestovat chování složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2a834-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="2a834-146">Chyby v rámci doby návrhu v Návrháři formulářů</span><span class="sxs-lookup"><span data-stu-id="2a834-146">Design-Time Errors in the Windows Forms Designer</span></span>](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="2a834-147">Vysvětluje význam a použití seznamu chyb návrhu, který se zobrazí v sadě Microsoft Visual Studio, když se nepodaří načíst Návrháře formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="2a834-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="2a834-148">Řešení potíží s vytvářením ovládacích prvků a komponent</span><span class="sxs-lookup"><span data-stu-id="2a834-148">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="2a834-149">Ukazuje, jak diagnostikovat a opravit běžné chyby, které může dojít, pokud vytváříte vlastní součást nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="2a834-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2a834-150">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2a834-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="2a834-151">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="2a834-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="2a834-152">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="2a834-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2a834-153">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2a834-153">Related Sections</span></span>  
 [<span data-ttu-id="2a834-154">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2a834-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="2a834-155">Popisuje, jak vytvořit vlastní ovládací prvky s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a834-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="2a834-156">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="2a834-156">Language Independence and Language-Independent Components</span></span>](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="2a834-157">Představuje modul common language runtime, který je navržené pro zjednodušení vytváření a používání komponent.</span><span class="sxs-lookup"><span data-stu-id="2a834-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="2a834-158">Důležitou součástí toto zjednodušení je rozšířenou interoperabilitu mezi součástmi, které jsou napsané v různých programovacích jazycích.</span><span class="sxs-lookup"><span data-stu-id="2a834-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="2a834-159">Specifikace CLS (Common Language) umožňuje vytvořit komponenty, které pracují s více programovacích jazyků a nástrojů.</span><span class="sxs-lookup"><span data-stu-id="2a834-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="2a834-160">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="2a834-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="2a834-161">Popisuje, jak povolit komponentu nebo ovládací prvek, který se má zobrazit **přizpůsobení panelu nástrojů** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2a834-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
