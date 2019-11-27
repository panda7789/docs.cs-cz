---
title: Definování výchozích hodnot pomocí metod ShouldSerialize a Reset
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: 11181bacdb919693ffc82c48c061357463a6343b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336752"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="efc9c-102">Definování výchozích hodnot pomocí metod ShouldSerialize a Reset</span><span class="sxs-lookup"><span data-stu-id="efc9c-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="efc9c-103">`ShouldSerialize` a `Reset` jsou volitelné metody, které lze zadat pro vlastnost, pokud vlastnost nemá jednoduchou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="efc9c-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="efc9c-104">Pokud má vlastnost jednoduchou výchozí hodnotu, měli byste použít <xref:System.ComponentModel.DefaultValueAttribute> a místo toho zadejte výchozí hodnotu konstruktoru třídy atributů.</span><span class="sxs-lookup"><span data-stu-id="efc9c-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="efc9c-105">Jeden z těchto mechanismů v Návrháři povoluje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="efc9c-105">Either of these mechanisms enables the following features in the designer:</span></span>

- <span data-ttu-id="efc9c-106">Vlastnost poskytuje vizuální indikaci v prohlížeči vlastností, pokud byl změněn z výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="efc9c-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>

- <span data-ttu-id="efc9c-107">Uživatel může kliknout pravým tlačítkem na vlastnost a zvolit **obnovit** pro obnovení výchozí hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="efc9c-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>

- <span data-ttu-id="efc9c-108">Návrhář generuje efektivnější kód.</span><span class="sxs-lookup"><span data-stu-id="efc9c-108">The designer generates more efficient code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="efc9c-109">Buď použijte <xref:System.ComponentModel.DefaultValueAttribute> nebo poskytněte `Reset`metody *PropertyName* a `ShouldSerialize`*PropertyName* .</span><span class="sxs-lookup"><span data-stu-id="efc9c-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="efc9c-110">Nepoužívejte obojí.</span><span class="sxs-lookup"><span data-stu-id="efc9c-110">Do not use both.</span></span>

 <span data-ttu-id="efc9c-111">Metoda `Reset`*PropertyName* nastaví vlastnost na její výchozí hodnotu, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="efc9c-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>

```vb
Public Sub ResetMyFont()
   MyFont = Nothing
End Sub
```

```csharp
public void ResetMyFont() {
   MyFont = null;
}
```

> [!NOTE]
> <span data-ttu-id="efc9c-112">Pokud vlastnost nemá metodu `Reset`, není označena <xref:System.ComponentModel.DefaultValueAttribute>a nemá ve své deklaraci výchozí hodnotu, `Reset` možnost pro tuto vlastnost je zakázána v místní nabídce okna **vlastností** Návrhář formulářů v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="efc9c-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>

 <span data-ttu-id="efc9c-113">Návrháři, jako je například Visual Studio, používají metodu `ShouldSerialize`*PropertyName* ke kontrole, zda se vlastnost změnila z výchozí hodnoty, a zápis kódu do formuláře pouze v případě, že dojde ke změně vlastnosti, což umožňuje efektivnější generování kódu.</span><span class="sxs-lookup"><span data-stu-id="efc9c-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="efc9c-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="efc9c-114">For example:</span></span>

```vb
'Returns true if the font has changed; otherwise, returns false.
' The designer writes code to the form only if true is returned.
Public Function ShouldSerializeMyFont() As Boolean
   Return Not (thefont Is Nothing)
End Function
```

```csharp
// Returns true if the font has changed; otherwise, returns false.
// The designer writes code to the form only if true is returned.
public bool ShouldSerializeMyFont() {
   return thefont != null;
}
```

 <span data-ttu-id="efc9c-115">Příklad úplného kódu:</span><span class="sxs-lookup"><span data-stu-id="efc9c-115">A complete code example follows.</span></span>

```vb
Option Explicit
Option Strict

Imports System.Drawing
Imports System.Windows.Forms

Public Class MyControl
   Inherits Control

   ' Declare an instance of the Font class
   ' and set its default value to Nothing.
   Private thefont As Font = Nothing

   ' The MyFont property.
   Public Property MyFont() As Font
      ' Note that the Font property never
      ' returns null.
      Get
         If Not (thefont Is Nothing) Then
            Return thefont
         End If
         If Not (Parent Is Nothing) Then
            Return Parent.Font
         End If
         Return Control.DefaultFont
      End Get
      Set
         thefont = value
      End Set
   End Property

   Public Function ShouldSerializeMyFont() As Boolean
      Return Not (thefont Is Nothing)
   End Function

   Public Sub ResetMyFont()
      MyFont = Nothing
   End Sub
End Class
```

```csharp
using System;
using System.Drawing;
using System.Windows.Forms;

public class MyControl : Control {
   // Declare an instance of the Font class
   // and set its default value to null.
   private Font thefont = null;

   // The MyFont property.
   public Font MyFont {
      // Note that the MyFont property never
      // returns null.
      get {
         if (thefont != null) return thefont;
         if (Parent != null) return Parent.Font;
         return Control.DefaultFont;
      }
      set {
         thefont = value;
      }
   }

   public bool ShouldSerializeMyFont() {
      return thefont != null;
   }

   public void ResetMyFont() {
      MyFont = null;
   }
}
```

 <span data-ttu-id="efc9c-116">V tomto případě, a to i v případě, že je hodnota soukromé proměnné, ke které přistupovala vlastnost `MyFont` `null`, prohlížeč vlastností nezobrazuje `null`; místo toho zobrazí vlastnost <xref:System.Windows.Forms.Control.Font%2A> nadřazeného objektu, pokud není `null`nebo výchozí hodnota <xref:System.Windows.Forms.Control.Font%2A> definovaná v <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="efc9c-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="efc9c-117">Výchozí hodnotu pro `MyFont` nelze jednoduše nastavit a <xref:System.ComponentModel.DefaultValueAttribute> nelze pro tuto vlastnost použít.</span><span class="sxs-lookup"><span data-stu-id="efc9c-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="efc9c-118">Místo toho musí být pro vlastnost `MyFont` implementovány metody `ShouldSerialize` a `Reset`.</span><span class="sxs-lookup"><span data-stu-id="efc9c-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>

## <a name="see-also"></a><span data-ttu-id="efc9c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="efc9c-119">See also</span></span>

- [<span data-ttu-id="efc9c-120">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="efc9c-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="efc9c-121">Definování vlastnosti</span><span class="sxs-lookup"><span data-stu-id="efc9c-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="efc9c-122">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="efc9c-122">Property-Changed Events</span></span>](property-changed-events.md)
