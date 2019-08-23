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
ms.openlocfilehash: 609fe4896a2b01b8a69ff8a3d0854c85ddbd6a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969097"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definování výchozích hodnot pomocí metod ShouldSerialize a Reset
`ShouldSerialize`a `Reset` jsou volitelné metody, které lze zadat pro vlastnost, pokud vlastnost nemá jednoduchou výchozí hodnotu. Pokud má vlastnost jednoduchou výchozí hodnotu, měli byste použít <xref:System.ComponentModel.DefaultValueAttribute> a dodat výchozí hodnotu konstruktoru třídy atributů. Jeden z těchto mechanismů v Návrháři povoluje následující funkce:

- Vlastnost poskytuje vizuální indikaci v prohlížeči vlastností, pokud byl změněn z výchozí hodnoty.

- Uživatel může kliknout pravým tlačítkem na vlastnost a zvolit **obnovit** pro obnovení výchozí hodnoty vlastnosti.

- Návrhář generuje efektivnější kód.

    > [!NOTE]
    > <xref:System.ComponentModel.DefaultValueAttribute> Buď použijte nebo poskytněte `Reset`metody *PropertyName* a `ShouldSerialize` *PropertyName* . Nepoužívejte obojí.

 Metoda propertyName nastaví vlastnost na výchozí hodnotu, jak je znázorněno v následujícím fragmentu kódu. `Reset`

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
> Pokud vlastnost `Reset` neobsahuje metodu, není označena jako <xref:System.ComponentModel.DefaultValueAttribute>a nemá `Reset` ve své deklaraci výchozí hodnotu, je možnost pro tuto vlastnost zakázána v místní nabídce okna **vlastnosti** . Návrhář formulářů v aplikaci Visual Studio.

 Návrháři, jako je například Visual Studio `ShouldSerialize`, používají metodu *PropertyName* k ověření, zda se vlastnost změnila z výchozí hodnoty, a zápis kódu do formuláře pouze v případě, že dojde ke změně vlastnosti, což umožňuje efektivnější generování kódu. Příklad:

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

 Příklad úplného kódu:

```vb
Option Explicit
Option Strict

Imports System
Imports System.Windows.Forms
Imports System.Drawing

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
using System.Windows.Forms;
using System.Drawing;

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

 V tomto případě, a to i `MyFont` v případě `null`, že je hodnota soukromé proměnné, ke které má vlastnost přistupovaná, `null`nezobrazuje prohlížeč vlastností, ale <xref:System.Windows.Forms.Control.Font%2A> zobrazuje vlastnost nadřazeného objektu, pokud `null`není, nebo výchozí <xref:System.Windows.Forms.Control.Font%2A> hodnota definovaná v <xref:System.Windows.Forms.Control>. Proto nelze nastavit výchozí hodnotu `MyFont` pro tuto vlastnost <xref:System.ComponentModel.DefaultValueAttribute> a nelze ji použít pro tuto vlastnost. Místo toho `Reset`musíbýt pro `ShouldSerialize` vlastnostimplementovány`MyFont` metody a.

## <a name="see-also"></a>Viz také:

- [Vlastnosti v ovládacích prvcích Windows Forms](properties-in-windows-forms-controls.md)
- [Definování vlastnosti](defining-a-property-in-windows-forms-controls.md)
- [Události změny vlastnosti](property-changed-events.md)
