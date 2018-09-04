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
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563519"
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Vývoj ovládacích prvků Windows Forms v době návrhu
Pro autory ovládací prvek rozhraní .NET Framework poskytuje celou řadu technologií pro vytváření ovládacího prvku. Autoři už nejsou omezeny na vytváření složených ovládacích prvků, které slouží jako kolekce dříve existující ovládací prvky. Prostřednictvím dědičnosti můžete vytvořit vlastní ovládací prvky z předchozích složených ovládacích prvků nebo dříve existující ovládací prvky Windows Forms. Také si můžete navrhovat vlastní ovládací prvky, které implementují vlastní vykreslování. Tyto možnosti umožňují značnou flexibilitu při návrhu a funkci vizuální rozhraní. Abyste mohli využívat tyto funkce, měli seznámit s koncepty programování založené na objektu.  
  
> [!NOTE]
>  Není nutné mít důkladné znalosti o dědičnosti, ale pravděpodobně pro vás bude užitečné k odkazování na [základní informace o dědičnosti (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud chcete vytvořit vlastní ovládací prvky pro použití na webové formuláře, naleznete v tématu [vyvíjet vlastní serverové ovládací prvky ASP.NET](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Ukazuje, jak vytvořit jednoduchý složeného ovládacího prvku v jazyce Visual Basic.  
  
 [Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Ukazuje, jak vytvořit jednoduchý složeného ovládacího prvku v jazyce C#.  
  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Ukazuje, jak vytvořit jednoduchý ovládací prvek Windows Forms pomocí dědičnost v jazyce Visual Basic.  
  
 [Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Ukazuje, jak vytvořit jednoduchý ovládací prvek Windows Forms pomocí dědičnosti v C#.  
  
 [Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Ukazuje, jak použít funkci inteligentních značek v ovládacích prvcích Windows Forms.  
  
 [Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 Ukazuje způsob použití <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atribut pro serializaci kolekce.  
  
 [Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Ukazuje, jak ladit návrhu chování ovládacího prvku Windows Forms.  
  
 [Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 Ukazuje, jak úzce integrovány složeného ovládacího prvku do vývojového prostředí.  
  
 [Postupy: Vytváření ovládacích prvků pro Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Poskytuje přehled důležitých informací pro implementaci ovládacího prvku Windows Forms.  
  
 [Postupy: Vytváření složených ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 Ukazuje, jak vytvořit ovládací prvek dědění ze složeného ovládacího prvku.  
  
 [Postupy: Dědění ze třídy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 Poskytuje přehled o postupu pro vytvoření složeného ovládacího prvku.  
  
 [Postupy: Dědění ze stávajících ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 Ukazuje, jak vytvořit dědění z ovládacího prvku rozšířené <xref:System.Windows.Forms.Button> třídu ovládacího prvku.  
  
 [Postupy: Dědění ze třídy Control](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 Přehled vytváření ovládacího prvku rozšířené.  
  
 [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Ukazuje způsob použití <xref:System.Windows.Forms.Control.Dock%2A> vlastnost zarovnání ovládacího prvku na hraničních zařízeních zabírá formuláře.  
  
 [Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Ukazuje postup při instalaci ovládacího prvku tak, aby se zobrazovalo ve **přizpůsobení panelu nástrojů** dialogové okno.  
  
 [Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Ukazuje způsob použití <xref:System.Drawing.ToolboxBitmapAttribute> ikonou vedle svého vlastního ovládacího prvku v zobrazení **nástrojů**.  
  
 [Postupy: Otestování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Ukazuje způsob použití **kontejner testu UserControl** otestovat chování složeného ovládacího prvku.  
  
 [Chyby v rámci doby návrhu v Návrháři formulářů](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 Vysvětluje význam a použití seznamu chyb návrhu, který se zobrazí v sadě Microsoft Visual Studio, když se nepodaří načíst Návrháře formulářů Windows.  
  
 [Řešení potíží s vytvářením ovládacích prvků a komponent](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Ukazuje, jak diagnostikovat a opravit běžné chyby, které může dojít, pokud vytváříte vlastní součást nebo ovládací prvek.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Tato třída popisuje a obsahuje odkazy na všechny její členy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 Popisuje, jak vytvořit vlastní ovládací prvky s rozhraním .NET Framework.  
  
 [Jazyková nezávislost a jazykově nezávislé komponenty](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 Představuje modul common language runtime, který je navržené pro zjednodušení vytváření a používání komponent. Důležitou součástí toto zjednodušení je rozšířenou interoperabilitu mezi součástmi, které jsou napsané v různých programovacích jazycích. Specifikace CLS (Common Language) umožňuje vytvořit komponenty, které pracují s více programovacích jazyků a nástrojů.  
  
 [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Popisuje, jak povolit komponentu nebo ovládací prvek, který se má zobrazit **přizpůsobení panelu nástrojů** dialogové okno.
