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
# <a name="developing-windows-forms-controls-at-design-time"></a>Vývoj ovládacích prvků Windows Forms v době návrhu
Pro autory ovládacích prvků .NET Framework poskytuje širokou část technologie pro tvorbu ovládacích prvků. Autoři již nejsou omezeni na návrh složených ovládacích prvků, které fungují jako kolekce existujících ovládacích prvků. Prostřednictvím dědičnosti můžete vytvořit vlastní ovládací prvky z předexistujících složených ovládacích prvků nebo z existujících ovládacích prvků model Windows Forms. Můžete také navrhnout vlastní ovládací prvky, které implementují vlastní malování. Tyto možnosti umožňují značnou flexibilitu pro návrh a funkčnost vizuálního rozhraní. Chcete-li využít výhod těchto funkcí, měli byste být obeznámeni s koncepty programování na základě objektů.  
  
> [!NOTE]
> Není nutné důkladné porozumění dědičnosti, ale může to být užitečné pro odkazování na [základy dědičnosti (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Chcete-li vytvořit vlastní ovládací prvky pro použití ve webových formulářích, přečtěte si téma [vývoj vlastních ovládacích prvků ASP.NET serveru](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Návod: Vytváření složeného ovládacího prvku pomocí Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Ukazuje, jak vytvořit jednoduchý složený ovládací prvek v Visual Basic.  
  
 [Návod: Vytváření složeného ovládacího prvku pomocí vizuáluC#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Ukazuje, jak vytvořit jednoduchý složený ovládací prvek v C#.  
  
 [Návod: Dědění z ovládacího prvku model Windows Forms s Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Ukazuje, jak vytvořit jednoduchý ovládací prvek model Windows Forms pomocí dědičnosti v Visual Basic.  
  
 [Návod: Dědění z ovládacího prvku model Windows Forms pomocí vizuáluC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Ukazuje, jak vytvořit jednoduchý ovládací prvek model Windows Forms pomocí dědičnosti C#v.  
  
 [Návod: Provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Ukazuje, jak používat funkci inteligentních značek na ovládacím prvku model Windows Forms.  
  
 [Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
 Ukazuje, jak použít <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atribut k serializaci kolekce.  
  
 [Návod: Ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Ukazuje, jak ladit chování ovládacího prvku model Windows Forms při návrhu.  
  
 [Návod: Vytvoření ovládacího prvku model Windows Forms, který využívá výhod funkcí nástroje Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md)  
 Ukazuje, jak úzce integrovat složený ovládací prvek do návrhového prostředí.  
  
 [Postupy: Vytváření ovládacích prvků pro model Windows Forms](how-to-author-controls-for-windows-forms.md)  
 Poskytuje přehled důležitých informací pro implementaci ovládacího prvku model Windows Forms.  
  
 [Postupy: Vytváření složených ovládacích prvků](how-to-author-composite-controls.md)  
 Ukazuje, jak vytvořit ovládací prvek děděním ze složeného ovládacího prvku.  
  
 [Postupy: Zdědit z třídy UserControl](how-to-inherit-from-the-usercontrol-class.md)  
 Poskytuje přehled postupu pro vytvoření složeného ovládacího prvku.  
  
 [Postupy: Zdědit z existujících ovládacích prvků model Windows Forms](how-to-inherit-from-existing-windows-forms-controls.md)  
 Ukazuje, jak vytvořit rozšířený ovládací prvek děděním z <xref:System.Windows.Forms.Button> třídy ovládacího prvku.  
  
 [Postupy: Zdědit z třídy ovládacího prvku](how-to-inherit-from-the-control-class.md)  
 Poskytuje přehled o vytvoření rozšířeného ovládacího prvku.  
  
 [Postupy: Zarovnání ovládacího prvku na okraje formulářů v době návrhu](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Ukazuje, jak použít <xref:System.Windows.Forms.Control.Dock%2A> vlastnost k zarovnání ovládacího prvku na okraj formuláře, který zabírá.  
  
 [Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Ukazuje postup instalace ovládacího prvku tak, aby se zobrazil v dialogovém okně **přizpůsobení sady nástrojů** .  
  
 [Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Ukazuje, jak použít, <xref:System.Drawing.ToolboxBitmapAttribute> Chcete-li zobrazit ikonu vedle vlastního ovládacího prvku v sadě **nástrojů**.  
  
 [Postupy: Testování chování prvku UserControl v době běhu](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Ukazuje, jak použít **kontejner testu UserControl** k otestování chování složeného ovládacího prvku.  
  
 [Chyby v rámci doby návrhu v Návrháři formulářů](design-time-errors-in-the-windows-forms-designer.md)  
 Vysvětluje význam a použití Seznam chyb v době návrhu, která se zobrazí v Microsoft Visual Studio, když se nepovede model Windows Forms návrháře.  
  
 [Řešení potíží s vytvářením ovládacích prvků a komponent](troubleshooting-control-and-component-authoring.md)  
 Ukazuje, jak diagnostikovat a opravovat běžné problémy, ke kterým může dojít při vytváření vlastní komponenty nebo ovládacího prvku.  
  
## <a name="reference"></a>Reference  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Popisuje tuto třídu a má odkazy na všechny její členy.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Popisuje tuto třídu a má odkazy na všechny její členy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)  
 Popisuje, jak vytvořit vlastní ovládací prvky pomocí .NET Framework.  
  
 [Jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md)  
 Zavádí modul CLR (Common Language Runtime), který je navržen tak, aby zjednodušil vytváření a používání komponent. Důležitým aspektem tohoto zjednodušení je Rozšířená interoperabilita mezi součástmi napsanými pomocí různých programovacích jazyků. Specifikace CLS (Common Language Specification) umožňuje vytvářet nástroje a komponenty, které pracují s více programovacími jazyky.  
  
 [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Popisuje, jak povolit zobrazení vaší komponenty nebo ovládacího prvku v dialogovém okně **přizpůsobit sadu nástrojů** .
