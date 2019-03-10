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
ms.openlocfilehash: 641a6c1c99169c6836c33b3e84b2ae02aba298d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707713"
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Vývoj ovládacích prvků Windows Forms v době návrhu
Pro autory ovládací prvek rozhraní .NET Framework poskytuje celou řadu technologií pro vytváření ovládacího prvku. Autoři už nejsou omezeny na vytváření složených ovládacích prvků, které slouží jako kolekce dříve existující ovládací prvky. Prostřednictvím dědičnosti můžete vytvořit vlastní ovládací prvky z předchozích složených ovládacích prvků nebo dříve existující ovládací prvky Windows Forms. Také si můžete navrhovat vlastní ovládací prvky, které implementují vlastní vykreslování. Tyto možnosti umožňují značnou flexibilitu při návrhu a funkci vizuální rozhraní. Abyste mohli využívat tyto funkce, měli seznámit s koncepty programování založené na objektu.  
  
> [!NOTE]
>  Není nutné mít důkladné znalosti o dědičnosti, ale pravděpodobně pro vás bude užitečné k odkazování na [základní informace o dědičnosti (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud chcete vytvořit vlastní ovládací prvky pro použití na webové formuláře, naleznete v tématu [vyvíjet vlastní serverové ovládací prvky ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Návod: Vytvoření složeného ovládacího prvku s jazykem Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Ukazuje, jak vytvořit jednoduchý složeného ovládacího prvku v jazyce Visual Basic.  
  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Ukazuje, jak vytvořit jednoduchý složeného ovládacího prvku v jazyce C#.  
  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Ukazuje, jak vytvořit jednoduchý ovládací prvek Windows Forms pomocí dědičnost v jazyce Visual Basic.  
  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Ukazuje, jak vytvořit jednoduchý ovládací prvek Windows Forms pomocí dědičnosti v C#.  
  
 [Návod: Provádění obecných úloh pomocí inteligentních značek na Windows Forms ovládací prvky](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Ukazuje, jak použít funkci inteligentních značek v ovládacích prvcích Windows Forms.  
  
 [Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
 Ukazuje způsob použití <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atribut pro serializaci kolekce.  
  
 [Návod: Ovládací prvky ladění vlastního Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Ukazuje, jak ladit návrhu chování ovládacího prvku Windows Forms.  
  
 [Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio Design-Time](creating-a-wf-control-design-time-features.md)  
 Ukazuje, jak úzce integrovány složeného ovládacího prvku do vývojového prostředí.  
  
 [Postupy: Autor ovládacích prvků Windows Forms](how-to-author-controls-for-windows-forms.md)  
 Poskytuje přehled důležitých informací pro implementaci ovládacího prvku Windows Forms.  
  
 [Postupy: Vytváření složených ovládacích prvků](how-to-author-composite-controls.md)  
 Ukazuje, jak vytvořit ovládací prvek dědění ze složeného ovládacího prvku.  
  
 [Postupy: Dědit ze třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)  
 Poskytuje přehled o postupu pro vytvoření složeného ovládacího prvku.  
  
 [Postupy: Dědění z existujících Windows Forms ovládacích prvků](how-to-inherit-from-existing-windows-forms-controls.md)  
 Ukazuje, jak vytvořit dědění z ovládacího prvku rozšířené <xref:System.Windows.Forms.Button> třídu ovládacího prvku.  
  
 [Postupy: Dědit ze třídy Control](how-to-inherit-from-the-control-class.md)  
 Přehled vytváření ovládacího prvku rozšířené.  
  
 [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Ukazuje způsob použití <xref:System.Windows.Forms.Control.Dock%2A> vlastnost zarovnání ovládacího prvku na hraničních zařízeních zabírá formuláře.  
  
 [Postupy: Zobrazení ovládacího prvku v zvolit položky panelu nástrojů – dialogové okno](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Ukazuje postup při instalaci ovládacího prvku tak, aby se zobrazovalo ve **přizpůsobení panelu nástrojů** dialogové okno.  
  
 [Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Ukazuje způsob použití <xref:System.Drawing.ToolboxBitmapAttribute> ikonou vedle svého vlastního ovládacího prvku v zobrazení **nástrojů**.  
  
 [Postupy: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Ukazuje způsob použití **kontejner testu UserControl** otestovat chování složeného ovládacího prvku.  
  
 [Chyby v rámci doby návrhu v Návrháři formulářů](design-time-errors-in-the-windows-forms-designer.md)  
 Vysvětluje význam a použití seznamu chyb návrhu, který se zobrazí v sadě Microsoft Visual Studio, když se nepodaří načíst Návrháře formulářů Windows.  
  
 [Řešení potíží s vytvářením ovládacích prvků a komponent](troubleshooting-control-and-component-authoring.md)  
 Ukazuje, jak diagnostikovat a opravit běžné chyby, které může dojít, pokud vytváříte vlastní součást nebo ovládací prvek.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)  
 Popisuje, jak vytvořit vlastní ovládací prvky s rozhraním .NET Framework.  
  
 [Jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md)  
 Představuje modul common language runtime, který je navržené pro zjednodušení vytváření a používání komponent. Důležitou součástí toto zjednodušení je rozšířenou interoperabilitu mezi součástmi, které jsou napsané v různých programovacích jazycích. Specifikace CLS (Common Language) umožňuje vytvořit komponenty, které pracují s více programovacích jazyků a nástrojů.  
  
 [Návod: Automatické vyplnění nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Popisuje, jak povolit komponentu nebo ovládací prvek, který se má zobrazit **přizpůsobení panelu nástrojů** dialogové okno.
