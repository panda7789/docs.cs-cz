---
title: Vlastnosti ovládacích prvků
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 82bfab15cef4946661a37d2d88fbe1b797f3d816
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741177"
---
# <a name="properties-in-windows-forms-controls"></a>Vlastnosti v ovládacích prvcích Windows Forms
Ovládací prvek model Windows Forms zdědí mnoho vlastností <xref:System.Windows.Forms.Control?displayProperty=nameWithType>základní třídy. Mezi tyto vlastnosti patří například <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>a mnoho dalších. Podrobnosti o děděných vlastnostech naleznete v tématu <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Můžete přepsat děděné vlastnosti v ovládacím prvku a také definovat nové vlastnosti.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Definování vlastnosti](defining-a-property-in-windows-forms-controls.md)  
 Ukazuje, jak implementovat vlastnost pro vlastní ovládací prvek nebo komponentu a ukazuje, jak integrovat vlastnost do návrhového prostředí.  
  
 [Definování výchozích hodnot pomocí metod ShouldSerialize a Reset](defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Ukazuje, jak definovat výchozí hodnoty vlastností pro vlastní ovládací prvek nebo komponentu.  
  
 [Události změny vlastnosti](property-changed-events.md)  
 Popisuje, jak povolit oznámení o změně vlastností při změně hodnoty vlastnosti.  
  
 [Postupy: Vystavení vlastností základních ovládacích prvků](how-to-expose-properties-of-constituent-controls.md)  
 Ukazuje, jak vystavit vlastnosti ovládacích prvků prvku ve vlastním složeném ovládacím prvku.  
  
 [Implementace metody ve vlastních ovládacích prvcích](method-implementation-in-custom-controls.md)  
 Popisuje, jak implementovat metody ve vlastních ovládacích prvcích a komponentách.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Windows.Forms.UserControl>  
 Dokumentuje základní třídu pro implementaci složených ovládacích prvků.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Dokumentuje atribut určující <xref:System.ComponentModel.TypeConverter>, který se má použít pro typ vlastní vlastnosti.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Dokumentuje atribut určující <xref:System.Drawing.Design.UITypeEditor>, který se má použít pro vlastní vlastnost.  
  
## <a name="related-sections"></a>Související oddíly  
 [Atributy v ovládacích prvcích Windows Forms](attributes-in-windows-forms-controls.md)  
 Popisuje atributy, které lze použít pro vlastnosti nebo jiné členy vašich vlastních ovládacích prvků a komponent.  
  
 [Atributy pro dobu návrhu pro součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))  
 Seznam atributů metadat, které se mají použít u komponent a ovládacích prvků tak, aby se v době návrhu v vizuálních návrhářích zobrazovaly správně.  
  
 [Rozšíření podpory pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))  
 Popisuje, jak implementovat třídy, jako jsou editory a návrháři, které poskytují podporu při návrhu.
