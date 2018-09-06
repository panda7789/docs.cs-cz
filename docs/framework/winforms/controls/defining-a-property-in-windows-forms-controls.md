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
ms.openlocfilehash: c21aee867fc78c55e62eb183bb1a12ebf1c472e8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858663"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Definování vlastnosti v ovládacích prvcích Windows Forms
Přehled vlastností naleznete v tématu [přehled vlastností](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Při definování vlastnosti se několik důležité aspekty:  
  
-   Musíte použít atributy k vlastnosti, které definujete. Atributy určují, jak má návrhář zobrazit vlastnosti. Podrobnosti najdete v tématu [atributy doby návrhu pro komponenty](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).  
  
-   Při změně hodnoty vlastnosti ovlivňuje vizuální zobrazení ovládacího prvku, kontaktujte <xref:System.Windows.Forms.Control.Invalidate%2A> – metoda (ovládací prvek dědící z <xref:System.Windows.Forms.Control>) z `set` přistupujícího objektu. <xref:System.Windows.Forms.Control.Invalidate%2A> volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která překreslí ovládacího prvku. Více volání <xref:System.Windows.Forms.Control.Invalidate%2A> výsledkem jednoho volání <xref:System.Windows.Forms.Control.OnPaint%2A> efektivitu.  
  
-   Knihovna tříd rozhraní .NET Framework poskytuje převaděčů typů pro běžné typy dat, jako je například celých čísel, desetinná čísla, logické hodnoty a dalších. Účelem konvertor typu je obecně poskytují převod řetězcovou hodnotu (od data řetězce na jiné datové typy). Běžné typy dat jsou spojeny s výchozí převodníky typů, které provádějí převod hodnot do řetězce a řetězce do příslušné datové typy. Je-li definovat vlastnost, která je vlastní (to znamená, používá se nestandardní) datový typ, budete muset použít atribut, který určuje typ převaděče pro přidružení k této vlastnosti. Atribut také můžete přiřadit k vlastnosti vlastního editoru typů uživatelského rozhraní. Editor typu uživatelského rozhraní poskytuje uživatelské rozhraní pro úpravu vlastností nebo datového typu. Výběr barev je příkladem editoru typů uživatelského rozhraní. Na konci tohoto tématu jsou uvedeny příklady atributů.  
  
    > [!NOTE]
    >  Pokud není k dispozici pro vaši vlastní vlastnost konvertor typu nebo editoru typů uživatelského rozhraní, můžete implementovat jednu jak je popsáno v [rozšíření podpory během návrhu](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
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
  
 Následující fragment kódu Přidruží konvertor typu a editoru typů uživatelského rozhraní s vlastností `Value`. V tomto případě `Value` je celé číslo a má výchozí převaděč typu, ale <xref:System.ComponentModel.TypeConverterAttribute> platí konvertor typu pro vlastní atribut (`FlashTrackBarValueConverter`), která umožňuje návrháře zobrazení v procentech. Editor typu uživatelského rozhraní `FlashTrackBarValueEditor`, umožňuje možné zobrazit vizuálně, procentuální hodnotu. Tento příklad také ukazuje, že konvertor typu nebo editor určené <xref:System.ComponentModel.TypeConverterAttribute> nebo <xref:System.ComponentModel.EditorAttribute> atribut přepíše výchozí převaděč.  
  
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
