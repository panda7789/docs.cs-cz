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
ms.openlocfilehash: 267a56cbfd9025e2e20f1468535e5544146535a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529857"
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Vývoj ovládacích prvků Windows Forms v době návrhu
Pro ovládací prvek autory rozhraní .NET Framework poskytuje širokou řadu vytváření technologie ovládacího prvku. Autoři je už omezený na navrhování složené ovládací prvky, které fungují jako kolekce dříve existující ovládacích prvků. Prostřednictvím dědičnosti můžete vytvořit své vlastní ovládací prvky z dříve existující složené ovládací prvky nebo dříve existující ovládací prvky Windows Forms. Můžete taky navrhnout vlastní ovládací prvky, které implementují vlastní Malování. Tyto možnosti Povolit značnou flexibilitu při návrhu a funkčnost visual rozhraní. Abyste mohli využívat tyto funkce, musí být obeznámeni s koncepty programování na základě objektů.  
  
> [!NOTE]
>  Není nutné mít důkladné znalosti týkající se dědičnosti, ale může být užitečné k odkazování na [základní informace o dědičnosti (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud chcete vytvořit vlastní ovládací prvky pro použití na webové formuláře naleznete v části [vývoj vlastních serverových ovládacích prvků ASP.NET](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Ukazuje, jak vytvořit jednoduché složeného ovládacího prvku v jazyce Visual Basic.  
  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Ukazuje, jak vytvořit jednoduché složeného ovládacího prvku v jazyce C#.  
  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Ukazuje postup vytvoření jednoduchého ovládacího prvku Windows Forms s použitím dědičnosti v jazyce Visual Basic.  
  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Ukazuje postup vytvoření jednoduchého ovládacího prvku Windows Forms s použitím dědičnosti v jazyce C#.  
  
 [Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Ukazuje, jak používat funkci inteligentních značek v ovládacích prvcích Windows Forms.  
  
 [Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 Ukazuje, jak používat <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atribut k serializaci kolekce.  
  
 [Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Ukazuje, jak k ladění návrhu chování ovládacího prvku Windows Forms.  
  
 [Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 Ukazuje, jak úzce integruje složeného ovládacího prvku do prostředí návrhu.  
  
 [Postupy: Vytváření ovládacích prvků pro Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Poskytuje přehled aspektů pro implementaci ovládacího prvku Windows Forms.  
  
 [Postupy: Vytváření složených ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 Ukazuje, jak vytvořit ovládací prvek dědění ze složeného ovládacího prvku.  
  
 [Postupy: Dědění ze třídy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 Obsahuje přehled postupu pro vytvoření složeného ovládacího prvku.  
  
 [Postupy: Dědění ze stávajících ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 Ukazuje, jak vytvořit dědění z ovládacího prvku rozšířené <xref:System.Windows.Forms.Button> třídu ovládacího prvku.  
  
 [Postupy: Dědění ze třídy Control](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 Poskytuje přehled vytvoření ovládacího prvku rozšířené.  
  
 [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Ukazuje, jak používat <xref:System.Windows.Forms.Control.Dock%2A> vlastnost zarovnání ovládacího prvku hrany zabírá formuláře.  
  
 [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Ukazuje postup instalace vlastního ovládacího prvku tak, aby se zobrazuje v **přizpůsobení sady nástrojů** dialogové okno.  
  
 [Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Ukazuje, jak používat <xref:System.Drawing.ToolboxBitmapAttribute> zobrazíte ikonu vedle vašeho vlastního ovládacího prvku v **sada nástrojů**.  
  
 [Postupy: Otestování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Ukazuje, jak používat **UserControl Test kontejneru** k testování chování složeného ovládacího prvku.  
  
 [Chyby v rámci doby návrhu v Návrháři formulářů](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 Vysvětluje význam a použití seznamu chyb návrhu, které se zobrazí v sadě Microsoft Visual Studio po Návrhář formulářů Windows nepodaří načíst.  
  
 [Řešení potíží s vytvářením ovládacích prvků a komponent](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Ukazuje, jak diagnostikovat a opravit běžné problémy, které může dojít, když vytváříte vlastní komponenta nebo ovládací prvek.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 Popisuje, jak vytvořit vlastní ovládací prvky s rozhraním .NET Framework.  
  
 [Jazyková nezávislost a jazykově nezávislé komponenty](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 Představuje modul common language runtime, který je určený k zjednodušení vytváření a používání komponent. Důležitým aspektem toto zjednodušení je rozšířenou interoperabilitu mezi součástmi, které jsou napsané v různých programovacích jazyků. Specifikace CLS (Common Language) umožňuje vytvořit nástroje a součásti, které pracují s více programovacích jazyků.  
  
 [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Popisuje, jak povolit komponenta nebo ovládací prvek, který se má zobrazit v **přizpůsobení sady nástrojů** dialogové okno.
