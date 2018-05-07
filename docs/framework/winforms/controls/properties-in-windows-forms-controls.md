---
title: Vlastnosti v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: aa7d8be158f4e0a7b2b95bf02cb0d1e173041f59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="properties-in-windows-forms-controls"></a>Vlastnosti v ovládacích prvcích Windows Forms
Ovládacího prvku Windows Forms základní třídy dědí mnoho vlastností formuláře <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Patří mezi ně vlastnosti, jako <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>a mnohé další. Podrobnosti o zděděné vlastnosti najdete v tématu <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Vám může potlačení zděděné vlastnosti v vlastního ovládacího prvku, stejně jako definovat nové vlastnosti.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Definování vlastnosti](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 Ukazuje, jak implementovat vlastnost pro vlastní ovládací prvek nebo součást a ukazuje, jak integrovat vlastnost do prostředí návrhu.  
  
 [Definování výchozích hodnot pomocí metod ShouldSerialize a Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Ukazuje, jak definovat výchozí hodnoty vlastností pro vlastní ovládací prvek nebo součást.  
  
 [Události změny vlastnosti](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 Popisuje, jak povolit změnu vlastnosti oznámení při změně hodnoty vlastnosti.  
  
 [Postupy: Vystavení vlastností základních ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 Ukazuje, jak vystavení vlastností základních ovládacích prvků v vlastní složeného ovládacího prvku.  
  
 [Implementace metody ve vlastních ovládacích prvcích](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 Popisuje, jak implementovat metody ve vlastních ovládacích prvků a komponent.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.UserControl>  
 Dokumenty základní třídu pro implementaci složených ovládacích prvků.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Dokumenty atribut, který určuje <xref:System.ComponentModel.TypeConverter> pro typ vlastní vlastnosti.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Atribut, který určuje dokumentů <xref:System.Drawing.Design.UITypeEditor> pro vlastní vlastnost.  
  
## <a name="related-sections"></a>Související oddíly  
 [Atributy v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 Popisuje atributy, které můžete provést u vlastnosti nebo jinými členy vlastní ovládací prvky a součásti.  
  
 [Atributy doby návrhu pro součásti](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 Seznam atributů metadata pro použití komponent a ovládacích prvků tak, aby se zobrazí správně v době návrhu v Návrháři visual.  
  
 [Rozšíření podpory návrhu](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 Popisuje, jak k implementaci třídy, jako je editory a návrhářů, které podporují návrhu.
