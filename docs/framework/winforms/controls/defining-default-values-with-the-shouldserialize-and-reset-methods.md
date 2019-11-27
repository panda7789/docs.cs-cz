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
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definování výchozích hodnot pomocí metod ShouldSerialize a Reset
`ShouldSerialize` a `Reset` jsou volitelné metody, které lze zadat pro vlastnost, pokud vlastnost nemá jednoduchou výchozí hodnotu. Pokud má vlastnost jednoduchou výchozí hodnotu, měli byste použít <xref:System.ComponentModel.DefaultValueAttribute> a místo toho zadejte výchozí hodnotu konstruktoru třídy atributů. Jeden z těchto mechanismů v Návrháři povoluje následující funkce:

- Vlastnost poskytuje vizuální indikaci v prohlížeči vlastností, pokud byl změněn z výchozí hodnoty.

- Uživatel může kliknout pravým tlačítkem na vlastnost a zvolit **obnovit** pro obnovení výchozí hodnoty vlastnosti.

- Návrhář generuje efektivnější kód.

    > [!NOTE]
    > Buď použijte <xref:System.ComponentModel.DefaultValueAttribute> nebo poskytněte `Reset`metody *PropertyName* a `ShouldSerialize`*PropertyName* . Nepoužívejte obojí.

 Metoda `Reset`*PropertyName* nastaví vlastnost na její výchozí hodnotu, jak je znázorněno v následujícím fragmentu kódu.

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
> Pokud vlastnost nemá metodu `Reset`, není označena <xref:System.ComponentModel.DefaultValueAttribute>a nemá ve své deklaraci výchozí hodnotu, `Reset` možnost pro tuto vlastnost je zakázána v místní nabídce okna **vlastností** Návrhář formulářů v aplikaci Visual Studio.

 Návrháři, jako je například Visual Studio, používají metodu `ShouldSerialize`*PropertyName* ke kontrole, zda se vlastnost změnila z výchozí hodnoty, a zápis kódu do formuláře pouze v případě, že dojde ke změně vlastnosti, což umožňuje efektivnější generování kódu. Příklad:

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

 V tomto případě, a to i v případě, že je hodnota soukromé proměnné, ke které přistupovala vlastnost `MyFont` `null`, prohlížeč vlastností nezobrazuje `null`; místo toho zobrazí vlastnost <xref:System.Windows.Forms.Control.Font%2A> nadřazeného objektu, pokud není `null`nebo výchozí hodnota <xref:System.Windows.Forms.Control.Font%2A> definovaná v <xref:System.Windows.Forms.Control>. Výchozí hodnotu pro `MyFont` nelze jednoduše nastavit a <xref:System.ComponentModel.DefaultValueAttribute> nelze pro tuto vlastnost použít. Místo toho musí být pro vlastnost `MyFont` implementovány metody `ShouldSerialize` a `Reset`.

## <a name="see-also"></a>Viz také:

- [Vlastnosti v ovládacích prvcích Windows Forms](properties-in-windows-forms-controls.md)
- [Definování vlastnosti](defining-a-property-in-windows-forms-controls.md)
- [Události změny vlastnosti](property-changed-events.md)
