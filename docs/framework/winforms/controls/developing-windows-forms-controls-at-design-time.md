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
ms.openlocfilehash: 11c3d9d6e7faa4741365316339d38f9fda69d059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965708"
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="0f387-102">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="0f387-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="0f387-103">Pro autory ovládacích prvků .NET Framework poskytuje širokou část technologie pro tvorbu ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="0f387-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="0f387-104">Autoři již nejsou omezeni na návrh složených ovládacích prvků, které fungují jako kolekce existujících ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="0f387-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="0f387-105">Prostřednictvím dědičnosti můžete vytvořit vlastní ovládací prvky z předexistujících složených ovládacích prvků nebo z existujících ovládacích prvků model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0f387-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="0f387-106">Můžete také navrhnout vlastní ovládací prvky, které implementují vlastní malování.</span><span class="sxs-lookup"><span data-stu-id="0f387-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="0f387-107">Tyto možnosti umožňují značnou flexibilitu pro návrh a funkčnost vizuálního rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0f387-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="0f387-108">Chcete-li využít výhod těchto funkcí, měli byste být obeznámeni s koncepty programování na základě objektů.</span><span class="sxs-lookup"><span data-stu-id="0f387-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f387-109">Není nutné důkladné porozumění dědičnosti, ale může to být užitečné pro odkazování na [základy dědičnosti (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="0f387-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="0f387-110">Chcete-li vytvořit vlastní ovládací prvky pro použití ve webových formulářích, přečtěte si téma [vývoj vlastních ovládacích prvků ASP.NET serveru](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0f387-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f387-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0f387-111">In This Section</span></span>  
 [<span data-ttu-id="0f387-112">Návod: Vytváření složeného ovládacího prvku pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f387-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="0f387-113">Ukazuje, jak vytvořit jednoduchý složený ovládací prvek v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0f387-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="0f387-114">Návod: Vytváření složeného ovládacího prvku pomocí vizuáluC#</span><span class="sxs-lookup"><span data-stu-id="0f387-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="0f387-115">Ukazuje, jak vytvořit jednoduchý složený ovládací prvek v C#.</span><span class="sxs-lookup"><span data-stu-id="0f387-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="0f387-116">Návod: Dědění z ovládacího prvku model Windows Forms s Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f387-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="0f387-117">Ukazuje, jak vytvořit jednoduchý ovládací prvek model Windows Forms pomocí dědičnosti v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0f387-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="0f387-118">Návod: Dědění z ovládacího prvku model Windows Forms pomocí vizuáluC#</span><span class="sxs-lookup"><span data-stu-id="0f387-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="0f387-119">Ukazuje, jak vytvořit jednoduchý ovládací prvek model Windows Forms pomocí dědičnosti C#v.</span><span class="sxs-lookup"><span data-stu-id="0f387-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="0f387-120">Návod: Provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f387-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="0f387-121">Ukazuje, jak používat funkci inteligentních značek na ovládacím prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0f387-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="0f387-122">Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="0f387-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="0f387-123">Ukazuje, jak použít <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atribut k serializaci kolekce.</span><span class="sxs-lookup"><span data-stu-id="0f387-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="0f387-124">Návod: Ladění vlastních ovládacích prvků model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="0f387-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="0f387-125">Ukazuje, jak ladit chování ovládacího prvku model Windows Forms při návrhu.</span><span class="sxs-lookup"><span data-stu-id="0f387-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="0f387-126">Návod: Vytvoření ovládacího prvku model Windows Forms, který využívá výhod funkcí nástroje Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="0f387-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="0f387-127">Ukazuje, jak úzce integrovat složený ovládací prvek do návrhového prostředí.</span><span class="sxs-lookup"><span data-stu-id="0f387-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="0f387-128">Postupy: Vytváření ovládacích prvků pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f387-128">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="0f387-129">Poskytuje přehled důležitých informací pro implementaci ovládacího prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0f387-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="0f387-130">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="0f387-130">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
 <span data-ttu-id="0f387-131">Ukazuje, jak vytvořit ovládací prvek děděním ze složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0f387-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="0f387-132">Postupy: Zdědit z třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="0f387-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="0f387-133">Poskytuje přehled postupu pro vytvoření složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0f387-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="0f387-134">Postupy: Zdědit z existujících ovládacích prvků model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f387-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="0f387-135">Ukazuje, jak vytvořit rozšířený ovládací prvek děděním z <xref:System.Windows.Forms.Button> třídy ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0f387-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="0f387-136">Postupy: Zdědit z třídy ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="0f387-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="0f387-137">Poskytuje přehled o vytvoření rozšířeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0f387-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="0f387-138">Postupy: Zarovnání ovládacího prvku na okraje formulářů v době návrhu</span><span class="sxs-lookup"><span data-stu-id="0f387-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="0f387-139">Ukazuje, jak použít <xref:System.Windows.Forms.Control.Dock%2A> vlastnost k zarovnání ovládacího prvku na okraj formuláře, který zabírá.</span><span class="sxs-lookup"><span data-stu-id="0f387-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="0f387-140">Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="0f387-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="0f387-141">Ukazuje postup instalace ovládacího prvku tak, aby se zobrazil v dialogovém okně **přizpůsobení sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="0f387-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="0f387-142">Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="0f387-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="0f387-143">Ukazuje, jak použít, <xref:System.Drawing.ToolboxBitmapAttribute> Chcete-li zobrazit ikonu vedle vlastního ovládacího prvku v sadě **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="0f387-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="0f387-144">Postupy: Testování chování prvku UserControl v době běhu</span><span class="sxs-lookup"><span data-stu-id="0f387-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="0f387-145">Ukazuje, jak použít **kontejner testu UserControl** k otestování chování složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0f387-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="0f387-146">Chyby v rámci doby návrhu v Návrháři formulářů</span><span class="sxs-lookup"><span data-stu-id="0f387-146">Design-Time Errors in the Windows Forms Designer</span></span>](design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="0f387-147">Vysvětluje význam a použití Seznam chyb v době návrhu, která se zobrazí v Microsoft Visual Studio, když se nepovede model Windows Forms návrháře.</span><span class="sxs-lookup"><span data-stu-id="0f387-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="0f387-148">Řešení potíží s vytvářením ovládacích prvků a komponent</span><span class="sxs-lookup"><span data-stu-id="0f387-148">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="0f387-149">Ukazuje, jak diagnostikovat a opravovat běžné problémy, ke kterým může dojít při vytváření vlastní komponenty nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0f387-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0f387-150">Reference</span><span class="sxs-lookup"><span data-stu-id="0f387-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="0f387-151">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0f387-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="0f387-152">Popisuje tuto třídu a má odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0f387-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0f387-153">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0f387-153">Related Sections</span></span>  
 [<span data-ttu-id="0f387-154">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0f387-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="0f387-155">Popisuje, jak vytvořit vlastní ovládací prvky pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f387-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="0f387-156">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="0f387-156">Language Independence and Language-Independent Components</span></span>](../../../standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="0f387-157">Zavádí modul CLR (Common Language Runtime), který je navržen tak, aby zjednodušil vytváření a používání komponent.</span><span class="sxs-lookup"><span data-stu-id="0f387-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="0f387-158">Důležitým aspektem tohoto zjednodušení je Rozšířená interoperabilita mezi součástmi napsanými pomocí různých programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="0f387-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="0f387-159">Specifikace CLS (Common Language Specification) umožňuje vytvářet nástroje a komponenty, které pracují s více programovacími jazyky.</span><span class="sxs-lookup"><span data-stu-id="0f387-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="0f387-160">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="0f387-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="0f387-161">Popisuje, jak povolit zobrazení vaší komponenty nebo ovládacího prvku v dialogovém okně **přizpůsobit sadu nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="0f387-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
