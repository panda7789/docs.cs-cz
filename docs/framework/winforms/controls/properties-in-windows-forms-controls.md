---
title: Vlastnosti v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: b1f7e0f5c1c9a01e47d0d972c56db8da922d2d0b
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664572"
---
# <a name="properties-in-windows-forms-controls"></a>Vlastnosti v ovládacích prvcích Windows Forms
Ovládací prvek Windows Forms dědí mnoho vlastností formuláře základní třídy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Tyto vlastnosti patří například <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>a mnoha dalších. Podrobnosti o zděděné vlastnosti najdete v tématu <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Můžete lze přepsat zděděné vlastnosti v ovládacím prvku také definovat nové vlastnosti.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Definování vlastnosti](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 Ukazuje, jak implementovat vlastnost vlastního ovládacího prvku nebo komponenty a ukazuje, jak integrovat vlastnost do vývojového prostředí.  
  
 [Definování výchozích hodnot pomocí metod ShouldSerialize a Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Ukazuje, jak definovat výchozí hodnoty vlastností pro vlastní ovládací prvek nebo komponenty.  
  
 [Události změny vlastnosti](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 Popisuje, jak povolit změnu vlastnosti oznámení při změně hodnoty vlastnosti.  
  
 [Postupy: Vystavení vlastností základních ovládacích prvků](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 Ukazuje, jak vystavení vlastností základních ovládacích prvků ve vlastní složeného ovládacího prvku.  
  
 [Implementace metody ve vlastních ovládacích prvcích](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 Popisuje, jak implementovat metody ve vlastních ovládacích prvků a komponent.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.UserControl>  
 Dokumenty základní třídu pro implementaci složených ovládacích prvků.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Atribut, který určuje dokumenty <xref:System.ComponentModel.TypeConverter> pro vlastní vlastnost typu.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Dokumenty atributu, který určuje, <xref:System.Drawing.Design.UITypeEditor> chcete použít pro vlastní vlastnost.  
  
## <a name="related-sections"></a>Související oddíly  
 [Atributy v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 Popisuje atributy, které můžete provést u vlastnosti nebo další členové vaší vlastní ovládací prvky a součásti.  
  
 [Atributy doby návrhu pro komponenty](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))  
 Obsahuje seznam atributy metadat použít na komponent a ovládacích prvků tak, aby se správně zobrazí v době návrhu v vizuální návrhářské nástroje.  
  
 [Rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))  
 Popisuje, jak implementovat třídy například editorů a návrhářů, které poskytují podpory během návrhu.
