---
title: "Definování vlastnosti v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c3c25b9c408e5b8f0b76cdf87375875cdb06a13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="25ea0-102">Definování vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25ea0-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="25ea0-103">Přehled vlastností najdete v tématu [přehled vlastností](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="25ea0-103">For an overview of properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="25ea0-104">Existuje několik důležitých rozhodnutí při definování vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="25ea0-104">There are a few important considerations when defining a property:</span></span>  
  
-   <span data-ttu-id="25ea0-105">Je nutné použít atributy pro vlastnosti, které definujete.</span><span class="sxs-lookup"><span data-stu-id="25ea0-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="25ea0-106">Atributy určují, jak by měla návrhář zobrazit vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="25ea0-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="25ea0-107">Podrobnosti najdete v tématu [atributy doby návrhu pro součásti](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="25ea0-107">For details, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
-   <span data-ttu-id="25ea0-108">Změna vlastnosti ovlivní visual zobrazení ovládacího prvku, kontaktujte <xref:System.Windows.Forms.Control.Invalidate%2A> – metoda (která vlastního ovládacího prvku dědí z <xref:System.Windows.Forms.Control>) z `set` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="25ea0-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="25ea0-109"><xref:System.Windows.Forms.Control.Invalidate%2A>volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která ho překreslí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="25ea0-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="25ea0-110">Více volá, aby se <xref:System.Windows.Forms.Control.Invalidate%2A> mít za následek jediné volání <xref:System.Windows.Forms.Control.OnPaint%2A> pro efektivitu.</span><span class="sxs-lookup"><span data-stu-id="25ea0-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
-   <span data-ttu-id="25ea0-111">Knihovna tříd rozhraní .NET Framework poskytuje převaděčů typů pro běžné typy dat jako celá čísla, desetinná čísla, logické hodnoty a dalších.</span><span class="sxs-lookup"><span data-stu-id="25ea0-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="25ea0-112">Účelem převaděče typů je obecně zajistit převod řetězcovou hodnotu (z dat řetězců na jiné datové typy).</span><span class="sxs-lookup"><span data-stu-id="25ea0-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="25ea0-113">Běžné typy dat jsou přidruženy k výchozí převaděče typů, které převodu hodnoty na řetězce a řetězců do příslušné datové typy.</span><span class="sxs-lookup"><span data-stu-id="25ea0-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="25ea0-114">Pokud definujete vlastnosti, která je vlastní (to znamená, nestandardní) datového typu, budete muset použít atribut, který určuje typ převaděč přidružení k této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="25ea0-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="25ea0-115">Atribut také můžete přiřadit k vlastnosti vlastní editor typů uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="25ea0-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="25ea0-116">Editor typů uživatelského rozhraní poskytuje uživatelské rozhraní pro úpravu typu vlastnost nebo data.</span><span class="sxs-lookup"><span data-stu-id="25ea0-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="25ea0-117">Výběr barvy a je příkladem editor typů uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="25ea0-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="25ea0-118">Na konci tohoto tématu jsou uvedeny příklady atributů.</span><span class="sxs-lookup"><span data-stu-id="25ea0-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="25ea0-119">Pokud není k dispozici pro vlastní vlastnost převaděče typů nebo editor typů uživatelského rozhraní, můžete implementovat jednu jak je popsáno v [rozšíření podpory návrhu](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span><span class="sxs-lookup"><span data-stu-id="25ea0-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span></span>  
  
 <span data-ttu-id="25ea0-120">Následující fragment kódu definuje vlastní vlastnost s názvem `EndColor` pro vlastní ovládací prvek `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="25ea0-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="25ea0-121">Následující fragment kódu přidruží převaděče typů a editor typů uživatelského rozhraní s vlastností `Value`.</span><span class="sxs-lookup"><span data-stu-id="25ea0-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="25ea0-122">V takovém případě `Value` je celé číslo a má převodník výchozí typ, ale <xref:System.ComponentModel.TypeConverterAttribute> platí převaděč vlastního typu atributu (`FlashTrackBarValueConverter`) umožňující návrháře zobrazíte v procentech.</span><span class="sxs-lookup"><span data-stu-id="25ea0-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="25ea0-123">Editor typů uživatelského rozhraní `FlashTrackBarValueEditor`, umožňuje procento, který se má zobrazit vizuálně.</span><span class="sxs-lookup"><span data-stu-id="25ea0-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="25ea0-124">Tento příklad také ukazuje, že převaděče typů nebo editor určeného <xref:System.ComponentModel.TypeConverterAttribute> nebo <xref:System.ComponentModel.EditorAttribute> atribut přepíše výchozí převaděč.</span><span class="sxs-lookup"><span data-stu-id="25ea0-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25ea0-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="25ea0-125">See Also</span></span>  
 [<span data-ttu-id="25ea0-126">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25ea0-126">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="25ea0-127">Definování výchozích hodnot pomocí metod ShouldSerialize a Reset</span><span class="sxs-lookup"><span data-stu-id="25ea0-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [<span data-ttu-id="25ea0-128">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25ea0-128">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [<span data-ttu-id="25ea0-129">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25ea0-129">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
