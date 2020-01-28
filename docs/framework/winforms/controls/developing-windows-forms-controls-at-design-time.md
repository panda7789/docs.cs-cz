---
title: Vývoj ovládacích prvků v době návrhu
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
ms.openlocfilehash: dac049ea6a51037daa0e23dc93476e4410b2df06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745994"
---
# <a name="develop-windows-forms-controls-at-design-time"></a>Vývoj ovládacích prvků model Windows Forms v době návrhu

Pro autory ovládacích prvků .NET Framework poskytuje širokou část technologie pro tvorbu ovládacích prvků. Autoři již nejsou omezeni na návrh složených ovládacích prvků, které fungují jako kolekce existujících ovládacích prvků. Prostřednictvím dědičnosti můžete vytvořit vlastní ovládací prvky z předexistujících složených ovládacích prvků nebo z existujících ovládacích prvků model Windows Forms. Můžete také navrhnout vlastní ovládací prvky, které implementují vlastní malování. Tyto možnosti umožňují značnou flexibilitu pro návrh a funkčnost vizuálního rozhraní. Chcete-li využít výhod těchto funkcí, měli byste být obeznámeni s koncepty programování na základě objektů.

> [!NOTE]
> Není nutné důkladné porozumění dědičnosti, ale může to být užitečné pro odkazování na [základy dědičnosti (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

Chcete-li vytvořit vlastní ovládací prvky pro použití ve webových formulářích, přečtěte si téma [vývoj vlastních ovládacích prvků ASP.NET serveru](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).

## <a name="in-this-section"></a>V tomto oddílu

[Návod: vytváření složeného ovládacího prvku](walkthrough-authoring-a-composite-control-with-visual-csharp.md)\
Ukazuje, jak vytvořit jednoduchý složený ovládací prvek v C#.

[Návod: dědění z ovládacího prvku model Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)\
Ukazuje, jak vytvořit jednoduchý ovládací prvek model Windows Forms pomocí dědičnosti C#v.

[Návod: provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)\
Ukazuje, jak používat funkci inteligentních značek na ovládacím prvku model Windows Forms.

[Návod: serializace kolekcí standardních typů pomocí\ DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)
Ukazuje, jak použít atribut <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> k serializaci kolekce.

[Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)\
Ukazuje, jak ladit chování ovládacího prvku model Windows Forms při návrhu.

[Návod: vytvoření ovládacího prvku model Windows Forms, který využívá výhod funkcí Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md)\
Ukazuje, jak úzce integrovat složený ovládací prvek do návrhového prostředí.

[Postupy: vytváření ovládacích prvků pro model Windows Forms](how-to-author-controls-for-windows-forms.md)\
Poskytuje přehled důležitých informací pro implementaci ovládacího prvku model Windows Forms.

[Postupy: vytváření složených ovládacích prvků](how-to-author-composite-controls.md)\
Ukazuje, jak vytvořit ovládací prvek děděním ze složeného ovládacího prvku.

[Postupy: dědění ze třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)\
Poskytuje přehled postupu pro vytvoření složeného ovládacího prvku.

[Postupy: dědění z existujících ovládacích prvků model Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)\
Ukazuje, jak vytvořit rozšířený ovládací prvek děděním z třídy ovládacího prvku <xref:System.Windows.Forms.Button>.

[Postupy: dědění z třídy ovládacího prvku](how-to-inherit-from-the-control-class.md)\
Poskytuje přehled o vytvoření rozšířeného ovládacího prvku.

[Postupy: zarovnání ovládacího prvku na okraje formulářů v době návrhu](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)\
Ukazuje, jak použít vlastnost <xref:System.Windows.Forms.Control.Dock%2A> k zarovnání ovládacího prvku na okraj formuláře, který zabírá.

[Postupy: zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)\
Ukazuje postup instalace ovládacího prvku tak, aby se zobrazil v dialogovém okně **přizpůsobení sady nástrojů** .

[Postupy: poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](how-to-provide-a-toolbox-bitmap-for-a-control.md)\
Ukazuje, jak použít <xref:System.Drawing.ToolboxBitmapAttribute> k zobrazení ikony vedle vlastního ovládacího prvku v sadě **nástrojů**.

[Postupy: testování chování prvku UserControl v době běhu](how-to-test-the-run-time-behavior-of-a-usercontrol.md)\
Ukazuje, jak použít **kontejner testu UserControl** k otestování chování složeného ovládacího prvku.

[Chyby v době návrhu v Návrhář formulářů](design-time-errors-in-the-windows-forms-designer.md)\
Vysvětluje význam a použití Seznam chyb v době návrhu, která se zobrazí v Microsoft Visual Studio, když se nepovede model Windows Forms návrháře.

[Řešení potíží s řízením a vytvářením komponent](troubleshooting-control-and-component-authoring.md)\
Ukazuje, jak diagnostikovat a opravovat běžné problémy, ke kterým může dojít při vytváření vlastní komponenty nebo ovládacího prvku.

## <a name="reference"></a>Odkaz

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a>Související oddíly

[Vývoj vlastních model Windows Formsových ovládacích prvků pomocí .NET Framework](developing-custom-windows-forms-controls.md)\
Popisuje, jak vytvořit vlastní ovládací prvky pomocí .NET Framework.

[Jazyková nezávislost a součásti nezávislé na jazyce](../../../standard/language-independence-and-language-independent-components.md)\
Zavádí modul CLR (Common Language Runtime), který je navržen tak, aby zjednodušil vytváření a používání komponent. Důležitým aspektem tohoto zjednodušení je Rozšířená interoperabilita mezi součástmi napsanými pomocí různých programovacích jazyků. Specifikace CLS (Common Language Specification) umožňuje vytvářet nástroje a komponenty, které pracují s více programovacími jazyky.

[Návod: automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)\
Popisuje, jak povolit zobrazení vaší komponenty nebo ovládacího prvku v dialogovém okně **přizpůsobit sadu nástrojů** .
