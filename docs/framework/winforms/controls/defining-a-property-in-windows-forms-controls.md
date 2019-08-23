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
ms.openlocfilehash: a641b1e7565842a1edf6aeec88bdc37ee0786ab4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969120"
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="b95e8-102">Definování vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b95e8-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="b95e8-103">Přehled vlastností najdete v tématu [Přehled vlastností](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="b95e8-103">For an overview of properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="b95e8-104">Při definování vlastnosti je potřeba několik důležitých otázek:</span><span class="sxs-lookup"><span data-stu-id="b95e8-104">There are a few important considerations when defining a property:</span></span>  
  
- <span data-ttu-id="b95e8-105">Je nutné použít atributy pro vlastnosti, které definujete.</span><span class="sxs-lookup"><span data-stu-id="b95e8-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="b95e8-106">Atributy určují, jak má Návrhář zobrazit vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b95e8-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="b95e8-107">Podrobnosti najdete v tématu [atributy pro dobu návrhu pro součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="b95e8-107">For details, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>  
  
- <span data-ttu-id="b95e8-108">Pokud změna vlastnosti ovlivňuje vizuální zobrazení ovládacího prvku, zavolejte <xref:System.Windows.Forms.Control.Invalidate%2A> metodu (kterou ovládací prvek dědí z <xref:System.Windows.Forms.Control>) z `set` přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="b95e8-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="b95e8-109"><xref:System.Windows.Forms.Control.Invalidate%2A>zase volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která překreslí ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b95e8-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="b95e8-110">Vícenásobné volání <xref:System.Windows.Forms.Control.Invalidate%2A> , které má za následek jedno <xref:System.Windows.Forms.Control.OnPaint%2A> volání kvůli efektivitě.</span><span class="sxs-lookup"><span data-stu-id="b95e8-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
- <span data-ttu-id="b95e8-111">Knihovna tříd .NET Framework poskytuje převaděče typů pro běžné datové typy, jako jsou celá čísla, desetinná čísla, logické hodnoty a další.</span><span class="sxs-lookup"><span data-stu-id="b95e8-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="b95e8-112">Účelem převaděče typu je obecně poskytnout převod řetězce na hodnotu (z řetězcových dat na jiné datové typy).</span><span class="sxs-lookup"><span data-stu-id="b95e8-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="b95e8-113">Společné datové typy jsou přidruženy k výchozím převaděčům typů, které převádějí hodnoty na řetězce a řetězce na příslušné datové typy.</span><span class="sxs-lookup"><span data-stu-id="b95e8-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="b95e8-114">Definujete-li vlastnost, která je vlastní (tj. nestandardní) datový typ, bude nutné použít atribut, který určuje konvertor typu k přidružení k této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b95e8-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="b95e8-115">Můžete také použít atribut k přidružení vlastního editoru typů uživatelského rozhraní k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b95e8-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="b95e8-116">Editor typu uživatelského rozhraní poskytuje uživatelské rozhraní pro úpravu vlastnosti nebo datového typu.</span><span class="sxs-lookup"><span data-stu-id="b95e8-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="b95e8-117">Výběr barvy je příkladem editoru typů uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b95e8-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="b95e8-118">Příklady atributů jsou uvedené na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b95e8-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b95e8-119">Pokud není pro vlastní vlastnost převaděč typu nebo Editor typů uživatelského rozhraní k dispozici, můžete implementovat jeden, jak je popsáno v tématu [rozšíření podpory při návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="b95e8-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120)).</span></span>  
  
 <span data-ttu-id="b95e8-120">Následující fragment kódu definuje vlastní vlastnost pojmenovanou `EndColor` pro vlastní ovládací prvek. `FlashTrackBar`</span><span class="sxs-lookup"><span data-stu-id="b95e8-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="b95e8-121">Následující fragment kódu přidruží konvertor typu a Editor typů uživatelského rozhraní s vlastností `Value`.</span><span class="sxs-lookup"><span data-stu-id="b95e8-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="b95e8-122">V tomto případě `Value` je celé číslo a má výchozí konvertor typu, <xref:System.ComponentModel.TypeConverterAttribute> ale atribut používá vlastní konvertor typu (`FlashTrackBarValueConverter`), který umožňuje návrháři zobrazit ho jako procento.</span><span class="sxs-lookup"><span data-stu-id="b95e8-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="b95e8-123">Editor `FlashTrackBarValueEditor`typu uživatelského rozhraní umožňuje zobrazit zobrazené procento vizuálně.</span><span class="sxs-lookup"><span data-stu-id="b95e8-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="b95e8-124">Tento příklad také ukazuje, že převaděč typu nebo editor určený <xref:System.ComponentModel.TypeConverterAttribute> atributem nebo <xref:System.ComponentModel.EditorAttribute> přepisuje výchozí převaděč.</span><span class="sxs-lookup"><span data-stu-id="b95e8-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b95e8-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b95e8-125">See also</span></span>

- [<span data-ttu-id="b95e8-126">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b95e8-126">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="b95e8-127">Definování výchozích hodnot pomocí metod ShouldSerialize a Reset</span><span class="sxs-lookup"><span data-stu-id="b95e8-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](defining-default-values-with-the-shouldserialize-and-reset-methods.md)
- [<span data-ttu-id="b95e8-128">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b95e8-128">Property-Changed Events</span></span>](property-changed-events.md)
- [<span data-ttu-id="b95e8-129">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b95e8-129">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
