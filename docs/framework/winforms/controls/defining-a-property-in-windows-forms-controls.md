---
title: Definování vlastnosti v ovládacích prvcích Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: dc47d7152419d55b3e52aec70257e2b39e9aaca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528320"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Definování vlastnosti v ovládacích prvcích Windows Forms
Přehled vlastností najdete v tématu [přehled vlastností](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Existuje několik důležitých rozhodnutí při definování vlastnosti:  
  
-   Je nutné použít atributy pro vlastnosti, které definujete. Atributy určují, jak by měla návrhář zobrazit vlastnosti. Podrobnosti najdete v tématu [atributy doby návrhu pro součásti](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).  
  
-   Změna vlastnosti ovlivní visual zobrazení ovládacího prvku, kontaktujte <xref:System.Windows.Forms.Control.Invalidate%2A> – metoda (která vlastního ovládacího prvku dědí z <xref:System.Windows.Forms.Control>) z `set` přistupujícího objektu. <xref:System.Windows.Forms.Control.Invalidate%2A> volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která ho překreslí ovládacího prvku. Více volá, aby se <xref:System.Windows.Forms.Control.Invalidate%2A> mít za následek jediné volání <xref:System.Windows.Forms.Control.OnPaint%2A> pro efektivitu.  
  
-   Knihovna tříd rozhraní .NET Framework poskytuje převaděčů typů pro běžné typy dat jako celá čísla, desetinná čísla, logické hodnoty a dalších. Účelem převaděče typů je obecně zajistit převod řetězcovou hodnotu (z dat řetězců na jiné datové typy). Běžné typy dat jsou přidruženy k výchozí převaděče typů, které převodu hodnoty na řetězce a řetězců do příslušné datové typy. Pokud definujete vlastnosti, která je vlastní (to znamená, nestandardní) datového typu, budete muset použít atribut, který určuje typ převaděč přidružení k této vlastnosti. Atribut také můžete přiřadit k vlastnosti vlastní editor typů uživatelského rozhraní. Editor typů uživatelského rozhraní poskytuje uživatelské rozhraní pro úpravu typu vlastnost nebo data. Výběr barvy a je příkladem editor typů uživatelského rozhraní. Na konci tohoto tématu jsou uvedeny příklady atributů.  
  
    > [!NOTE]
    >  Pokud není k dispozici pro vlastní vlastnost převaděče typů nebo editor typů uživatelského rozhraní, můžete implementovat jednu jak je popsáno v [rozšíření podpory návrhu](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Následující fragment kódu definuje vlastní vlastnost s názvem `EndColor` pro vlastní ovládací prvek `FlashTrackBar`.  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 Následující fragment kódu přidruží převaděče typů a editor typů uživatelského rozhraní s vlastností `Value`. V takovém případě `Value` je celé číslo a má převodník výchozí typ, ale <xref:System.ComponentModel.TypeConverterAttribute> platí převaděč vlastního typu atributu (`FlashTrackBarValueConverter`) umožňující návrháře zobrazíte v procentech. Editor typů uživatelského rozhraní `FlashTrackBarValueEditor`, umožňuje procento, který se má zobrazit vizuálně. Tento příklad také ukazuje, že převaděče typů nebo editor určeného <xref:System.ComponentModel.TypeConverterAttribute> nebo <xref:System.ComponentModel.EditorAttribute> atribut přepíše výchozí převaděč.  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Vlastnosti v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Definování výchozích hodnot pomocí metod ShouldSerialize a Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [Události změny vlastnosti](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [Atributy v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
