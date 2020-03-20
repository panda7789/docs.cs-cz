---
title: Definování vlastností ovládacího prvku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: 7223f8c88bee4ee9c1db621cc39bbcf70d0c4589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182376"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Definování vlastnosti v ovládacích prvcích Windows Forms
Přehled vlastností naleznete v tématu [Přehled vlastností](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)). Existuje několik důležitých aspektů při definování vlastnosti:  
  
- Atributy je nutné použít na vlastnosti, které definujete. Atributy určují, jak má návrhář zobrazit vlastnost. Podrobnosti naleznete v [tématu Atributy návrhu v době pro součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).  
  
- Pokud změna vlastnosti ovlivňuje vizuální zobrazení ovládacího prvku, volání <xref:System.Windows.Forms.Control.Invalidate%2A> metody <xref:System.Windows.Forms.Control>(které `set` váš ovládací prvek dědí z) z přistupujícího objektu. <xref:System.Windows.Forms.Control.Invalidate%2A>na zase <xref:System.Windows.Forms.Control.OnPaint%2A> volá metodu, která překreslí ovládací prvek. Více volání, které má <xref:System.Windows.Forms.Control.Invalidate%2A> <xref:System.Windows.Forms.Control.OnPaint%2A> za následek jedno volání pro efektivitu.  
  
- Knihovna tříd rozhraní .NET Framework poskytuje převaděče typů pro běžné datové typy, jako jsou celá čísla, desetinná čísla, logické hodnoty a další. Účelem převaděče typu je obecně poskytnout převod na hodnotu řetězce (z dat řetězce do jiných datových typů). Běžné datové typy jsou přidruženy k výchozí převaděčům typů, které převádějí hodnoty na řetězce a řetězce na příslušné datové typy. Pokud definujete vlastnost, která je vlastní (to znamená nestandardní) datový typ, budete muset použít atribut, který určuje převaděč typu přidružit k této vlastnosti. Atribut můžete také použít k přidružení vlastního editoru typů ui k vlastnosti. Editor typů uživatelského rozhraní poskytuje uživatelské rozhraní pro úpravy vlastnosti nebo datového typu. Výběr barvy je příkladem editoru typů ui. Příklady atributů jsou uvedeny na konci tohoto tématu.  
  
    > [!NOTE]
    > Pokud převaděč typu nebo editor typů ui není k dispozici pro vlastní vlastnost, můžete implementovat jeden, jak je popsáno v [rozšíření podpory návrhu čas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).  
  
 Následující fragment kódu definuje vlastní `EndColor` vlastnost pojmenovanou pro vlastní ovládací prvek `FlashTrackBar`.  
  
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
  
 Následující fragment kódu přidruží převaděč typu a `Value`editor typů u vlastností . V tomto `Value` případě je celé číslo a má výchozí <xref:System.ComponentModel.TypeConverterAttribute> převaděč typu, ale`FlashTrackBarValueConverter`atribut použije vlastní převaděč typu ( ), který umožňuje návrháři zobrazit v procentech. Editor typů ui `FlashTrackBarValueEditor`, umožňuje procento, které mají být zobrazeny vizuálně. Tento příklad také ukazuje, že převaděč nebo editor typů určený atributem <xref:System.ComponentModel.TypeConverterAttribute> nebo <xref:System.ComponentModel.EditorAttribute> přepíše výchozí převaděč.  
  
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

- [Vlastnosti v ovládacích prvcích Windows Forms](properties-in-windows-forms-controls.md)
- [Definování výchozích hodnot pomocí metod ShouldSerialize a Reset](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [Události změny vlastnosti](property-changed-events.md)
- [Atributy v ovládacích prvcích Windows Forms](attributes-in-windows-forms-controls.md)
