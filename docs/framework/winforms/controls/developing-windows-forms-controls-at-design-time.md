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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f6afb13a01075d3aa2d101100a0c3bfe31c6ee29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460079"
---
# <a name="develop-windows-forms-controls-at-design-time"></a><span data-ttu-id="aa106-102">Vývoj ovládacích prvků model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="aa106-102">Develop Windows Forms controls at design time</span></span>

<span data-ttu-id="aa106-103">Pro autory ovládacích prvků .NET Framework poskytuje širokou část technologie pro tvorbu ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="aa106-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="aa106-104">Autoři již nejsou omezeni na návrh složených ovládacích prvků, které fungují jako kolekce existujících ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="aa106-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="aa106-105">Prostřednictvím dědičnosti můžete vytvořit vlastní ovládací prvky z předexistujících složených ovládacích prvků nebo z existujících ovládacích prvků model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aa106-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="aa106-106">Můžete také navrhnout vlastní ovládací prvky, které implementují vlastní malování.</span><span class="sxs-lookup"><span data-stu-id="aa106-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="aa106-107">Tyto možnosti umožňují značnou flexibilitu pro návrh a funkčnost vizuálního rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa106-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="aa106-108">Chcete-li využít výhod těchto funkcí, měli byste být obeznámeni s koncepty programování na základě objektů.</span><span class="sxs-lookup"><span data-stu-id="aa106-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="aa106-109">Není nutné důkladné porozumění dědičnosti, ale může to být užitečné pro odkazování na [základy dědičnosti (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="aa106-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

<span data-ttu-id="aa106-110">Chcete-li vytvořit vlastní ovládací prvky pro použití ve webových formulářích, přečtěte si téma [vývoj vlastních ovládacích prvků ASP.NET serveru](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="aa106-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="aa106-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="aa106-111">In this section</span></span>

<span data-ttu-id="aa106-112">[Návod: vytváření složeného ovládacího prvku](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-112">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="aa106-113">Ukazuje, jak vytvořit jednoduchý složený ovládací prvek v C#.</span><span class="sxs-lookup"><span data-stu-id="aa106-113">Shows how to create a simple composite control in C#.</span></span>

<span data-ttu-id="aa106-114">[Návod: dědění z ovládacího prvku model Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-114">[Walkthrough: Inheriting from a Windows Forms Control](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="aa106-115">Ukazuje, jak vytvořit jednoduchý ovládací prvek model Windows Forms pomocí dědičnosti C#v.</span><span class="sxs-lookup"><span data-stu-id="aa106-115">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>

<span data-ttu-id="aa106-116">[Návod: provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-116">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span></span>\
<span data-ttu-id="aa106-117">Ukazuje, jak používat funkci inteligentních značek na ovládacím prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aa106-117">Shows how to use the smart tag feature on Windows Forms controls.</span></span>

<span data-ttu-id="aa106-118">[Návod: serializace kolekcí standardních typů pomocí\ DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-118">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)\</span></span>
<span data-ttu-id="aa106-119">Ukazuje, jak použít atribut <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> k serializaci kolekce.</span><span class="sxs-lookup"><span data-stu-id="aa106-119">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>

<span data-ttu-id="aa106-120">[Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-120">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="aa106-121">Ukazuje, jak ladit chování ovládacího prvku model Windows Forms při návrhu.</span><span class="sxs-lookup"><span data-stu-id="aa106-121">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>

<span data-ttu-id="aa106-122">[Návod: vytvoření ovládacího prvku model Windows Forms, který využívá výhod funkcí Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-122">[Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md)</span></span>\
<span data-ttu-id="aa106-123">Ukazuje, jak úzce integrovat složený ovládací prvek do návrhového prostředí.</span><span class="sxs-lookup"><span data-stu-id="aa106-123">Shows how to tightly integrate a composite control into the design environment.</span></span>

<span data-ttu-id="aa106-124">[Postupy: vytváření ovládacích prvků pro model Windows Forms](how-to-author-controls-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-124">[How to: Author Controls for Windows Forms](how-to-author-controls-for-windows-forms.md)</span></span>\
<span data-ttu-id="aa106-125">Poskytuje přehled důležitých informací pro implementaci ovládacího prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aa106-125">Provides an overview of considerations for implementing a Windows Forms control.</span></span>

<span data-ttu-id="aa106-126">[Postupy: vytváření složených ovládacích prvků](how-to-author-composite-controls.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-126">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>\
<span data-ttu-id="aa106-127">Ukazuje, jak vytvořit ovládací prvek děděním ze složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aa106-127">Shows how to create a control by inheriting from a composite control.</span></span>

<span data-ttu-id="aa106-128">[Postupy: dědění ze třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-128">[How to: Inherit from the UserControl Class](how-to-inherit-from-the-usercontrol-class.md)</span></span>\
<span data-ttu-id="aa106-129">Poskytuje přehled postupu pro vytvoření složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aa106-129">Provides an overview of the procedure for creating a composite control.</span></span>

<span data-ttu-id="aa106-130">[Postupy: dědění z existujících ovládacích prvků model Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-130">[How to: Inherit from Existing Windows Forms Controls](how-to-inherit-from-existing-windows-forms-controls.md)</span></span>\
<span data-ttu-id="aa106-131">Ukazuje, jak vytvořit rozšířený ovládací prvek děděním z třídy ovládacího prvku <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="aa106-131">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>

<span data-ttu-id="aa106-132">[Postupy: dědění z třídy ovládacího prvku](how-to-inherit-from-the-control-class.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-132">[How to: Inherit from the Control Class](how-to-inherit-from-the-control-class.md)</span></span>\
<span data-ttu-id="aa106-133">Poskytuje přehled o vytvoření rozšířeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aa106-133">Provides an overview of creating an extended control.</span></span>

<span data-ttu-id="aa106-134">[Postupy: zarovnání ovládacího prvku na okraje formulářů v době návrhu](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-134">[How to: Align a Control to the Edges of Forms at Design Time](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span></span>\
<span data-ttu-id="aa106-135">Ukazuje, jak použít vlastnost <xref:System.Windows.Forms.Control.Dock%2A> k zarovnání ovládacího prvku na okraj formuláře, který zabírá.</span><span class="sxs-lookup"><span data-stu-id="aa106-135">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="aa106-136">[Postupy: zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-136">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>\
<span data-ttu-id="aa106-137">Ukazuje postup instalace ovládacího prvku tak, aby se zobrazil v dialogovém okně **přizpůsobení sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="aa106-137">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>

<span data-ttu-id="aa106-138">[Postupy: poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-138">[How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span></span>\
<span data-ttu-id="aa106-139">Ukazuje, jak použít <xref:System.Drawing.ToolboxBitmapAttribute> k zobrazení ikony vedle vlastního ovládacího prvku v sadě **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="aa106-139">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="aa106-140">[Postupy: testování chování prvku UserControl v době běhu](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-140">[How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span></span>\
<span data-ttu-id="aa106-141">Ukazuje, jak použít **kontejner testu UserControl** k otestování chování složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aa106-141">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>

<span data-ttu-id="aa106-142">[Chyby v době návrhu v Návrhář formulářů](design-time-errors-in-the-windows-forms-designer.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-142">[Design-Time Errors in the Windows Forms Designer](design-time-errors-in-the-windows-forms-designer.md)</span></span>\
<span data-ttu-id="aa106-143">Vysvětluje význam a použití Seznam chyb v době návrhu, která se zobrazí v Microsoft Visual Studio, když se nepovede model Windows Forms návrháře.</span><span class="sxs-lookup"><span data-stu-id="aa106-143">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>

<span data-ttu-id="aa106-144">[Řešení potíží s řízením a vytvářením komponent](troubleshooting-control-and-component-authoring.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-144">[Troubleshooting Control and Component Authoring](troubleshooting-control-and-component-authoring.md)</span></span>\
<span data-ttu-id="aa106-145">Ukazuje, jak diagnostikovat a opravovat běžné problémy, ke kterým může dojít při vytváření vlastní komponenty nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aa106-145">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>

## <a name="reference"></a><span data-ttu-id="aa106-146">Odkaz</span><span class="sxs-lookup"><span data-stu-id="aa106-146">Reference</span></span>

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a><span data-ttu-id="aa106-147">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="aa106-147">Related sections</span></span>

<span data-ttu-id="aa106-148">[Vývoj vlastních model Windows Formsových ovládacích prvků pomocí .NET Framework](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-148">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="aa106-149">Popisuje, jak vytvořit vlastní ovládací prvky pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa106-149">Discusses how to create your own custom controls with the .NET Framework.</span></span>

<span data-ttu-id="aa106-150">[Jazyková nezávislost a součásti nezávislé na jazyce](../../../standard/language-independence-and-language-independent-components.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-150">[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)</span></span>\
<span data-ttu-id="aa106-151">Zavádí modul CLR (Common Language Runtime), který je navržen tak, aby zjednodušil vytváření a používání komponent.</span><span class="sxs-lookup"><span data-stu-id="aa106-151">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="aa106-152">Důležitým aspektem tohoto zjednodušení je Rozšířená interoperabilita mezi součástmi napsanými pomocí různých programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="aa106-152">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="aa106-153">Specifikace CLS (Common Language Specification) umožňuje vytvářet nástroje a komponenty, které pracují s více programovacími jazyky.</span><span class="sxs-lookup"><span data-stu-id="aa106-153">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>

<span data-ttu-id="aa106-154">[Návod: automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span><span class="sxs-lookup"><span data-stu-id="aa106-154">[Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span></span>\
<span data-ttu-id="aa106-155">Popisuje, jak povolit zobrazení vaší komponenty nebo ovládacího prvku v dialogovém okně **přizpůsobit sadu nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="aa106-155">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
