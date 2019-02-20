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
ms.openlocfilehash: 8d040d4de566ea750b9a9d14531061a63524e668
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441889"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="11182-102">Definování vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11182-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="11182-103">Přehled vlastností naleznete v tématu [přehled vlastností](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="11182-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="11182-104">Při definování vlastnosti se několik důležité aspekty:</span><span class="sxs-lookup"><span data-stu-id="11182-104">There are a few important considerations when defining a property:</span></span>  
  
-   <span data-ttu-id="11182-105">Musíte použít atributy k vlastnosti, které definujete.</span><span class="sxs-lookup"><span data-stu-id="11182-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="11182-106">Atributy určují, jak má návrhář zobrazit vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="11182-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="11182-107">Podrobnosti najdete v tématu [atributy doby návrhu pro komponenty](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="11182-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
-   <span data-ttu-id="11182-108">Při změně hodnoty vlastnosti ovlivňuje vizuální zobrazení ovládacího prvku, kontaktujte <xref:System.Windows.Forms.Control.Invalidate%2A> – metoda (ovládací prvek dědící z <xref:System.Windows.Forms.Control>) z `set` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="11182-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="11182-109"><xref:System.Windows.Forms.Control.Invalidate%2A> volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která překreslí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11182-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="11182-110">Více volání <xref:System.Windows.Forms.Control.Invalidate%2A> výsledkem jednoho volání <xref:System.Windows.Forms.Control.OnPaint%2A> efektivitu.</span><span class="sxs-lookup"><span data-stu-id="11182-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
-   <span data-ttu-id="11182-111">Knihovna tříd rozhraní .NET Framework poskytuje převaděčů typů pro běžné typy dat, jako je například celých čísel, desetinná čísla, logické hodnoty a dalších.</span><span class="sxs-lookup"><span data-stu-id="11182-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="11182-112">Účelem konvertor typu je obecně poskytují převod řetězcovou hodnotu (od data řetězce na jiné datové typy).</span><span class="sxs-lookup"><span data-stu-id="11182-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="11182-113">Běžné typy dat jsou spojeny s výchozí převodníky typů, které provádějí převod hodnot do řetězce a řetězce do příslušné datové typy.</span><span class="sxs-lookup"><span data-stu-id="11182-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="11182-114">Je-li definovat vlastnost, která je vlastní (to znamená, používá se nestandardní) datový typ, budete muset použít atribut, který určuje typ převaděče pro přidružení k této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="11182-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="11182-115">Atribut také můžete přiřadit k vlastnosti vlastního editoru typů uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="11182-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="11182-116">Editor typu uživatelského rozhraní poskytuje uživatelské rozhraní pro úpravu vlastností nebo datového typu.</span><span class="sxs-lookup"><span data-stu-id="11182-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="11182-117">Výběr barev je příkladem editoru typů uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="11182-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="11182-118">Na konci tohoto tématu jsou uvedeny příklady atributů.</span><span class="sxs-lookup"><span data-stu-id="11182-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="11182-119">Pokud není k dispozici pro vaši vlastní vlastnost konvertor typu nebo editoru typů uživatelského rozhraní, můžete implementovat jednu jak je popsáno v [rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="11182-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="11182-120">Následující fragment kódu definuje vlastní vlastnost s názvem `EndColor` pro vlastní ovládací prvek `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="11182-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="11182-121">Následující fragment kódu Přidruží konvertor typu a editoru typů uživatelského rozhraní s vlastností `Value`.</span><span class="sxs-lookup"><span data-stu-id="11182-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="11182-122">V tomto případě `Value` je celé číslo a má výchozí převaděč typu, ale <xref:System.ComponentModel.TypeConverterAttribute> platí konvertor typu pro vlastní atribut (`FlashTrackBarValueConverter`), která umožňuje návrháře zobrazení v procentech.</span><span class="sxs-lookup"><span data-stu-id="11182-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="11182-123">Editor typu uživatelského rozhraní `FlashTrackBarValueEditor`, umožňuje možné zobrazit vizuálně, procentuální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="11182-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="11182-124">Tento příklad také ukazuje, že konvertor typu nebo editor určené <xref:System.ComponentModel.TypeConverterAttribute> nebo <xref:System.ComponentModel.EditorAttribute> atribut přepíše výchozí převaděč.</span><span class="sxs-lookup"><span data-stu-id="11182-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11182-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11182-125">See also</span></span>
- [<span data-ttu-id="11182-126">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11182-126">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
- [<span data-ttu-id="11182-127">Definování výchozích hodnot pomocí metod ShouldSerialize a Reset</span><span class="sxs-lookup"><span data-stu-id="11182-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="11182-128">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="11182-128">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)
- [<span data-ttu-id="11182-129">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11182-129">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
