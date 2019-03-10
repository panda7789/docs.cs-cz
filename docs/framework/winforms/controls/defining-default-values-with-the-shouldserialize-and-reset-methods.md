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
ms.openlocfilehash: 2cb23220be2b4a3564c4869016c05065afe7c27c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704442"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definování výchozích hodnot pomocí metod ShouldSerialize a Reset
`ShouldSerialize` a `Reset` jsou volitelné metody, které můžete zadat vlastnosti, pokud vlastnost není máte jednoduchý výchozí hodnotu. Pokud má vlastnost jednoduchý výchozí hodnotu, byste měli použít <xref:System.ComponentModel.DefaultValueAttribute> a místo toho zadat výchozí hodnotu pro atribut konstruktoru třídy. Některé z těchto mechanismů povoluje následující funkce v Návrháři:  
  
-   Vlastnost poskytuje vizuální označení v prohlížeči vlastností, pokud se změnila od jeho výchozí hodnotu.  
  
-   Uživatel může kliknout pravým tlačítkem na vlastnosti a zvolte **resetování** obnovíte jeho výchozí hodnota vlastnosti.  
  
-   Návrhář vytvoří efektivnějšího kódu.  
  
    > [!NOTE]
    >  Buď použijte <xref:System.ComponentModel.DefaultValueAttribute> nebo zadejte `Reset` *PropertyName* a `ShouldSerialize` *PropertyName* metody. Nepoužívejte obojí.  
  
 `Reset` *PropertyName* metoda nastaví vlastnost na výchozí hodnotu, jak je znázorněno v následujícím fragmentu kódu.  
  
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
>  Pokud nemá žádné vlastnosti `Reset` metoda, není označena třídou <xref:System.ComponentModel.DefaultValueAttribute>a výchozí hodnota zadaná v jeho deklaraci, nemá `Reset` možnost pro tuto vlastnost je zakázaný v místní nabídce **vlastnosti** okna Návrháře formulářů Windows v sadě Visual Studio.  
  
 Použití návrháře, jako je Visual Studio `ShouldSerialize` *PropertyName* metodu ke kontrole, zda má došlo ke změně vlastnosti z výchozí hodnoty a napsat kód do formuláře pouze tehdy, pokud vlastnost změnit, což umožňuje mnohem efektivnější kódu generování. Příklad:  
  
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
  
 Následuje příklad úplného kódu.  
  
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
  
 V takovém případě i v případě, že hodnota soukromé proměnné přistupuje `MyFont` vlastnost je `null`, vlastnost prohlížeče nezobrazí `null`; místo toho se zobrazí <xref:System.Windows.Forms.Control.Font%2A> vlastnosti nadřazeného objektu, pokud není `null`, nebo výchozí hodnotu <xref:System.Windows.Forms.Control.Font%2A> hodnota definovaná v <xref:System.Windows.Forms.Control>. Proto výchozí hodnota pro `MyFont` nelze jednoduše nastavit a <xref:System.ComponentModel.DefaultValueAttribute> nelze použít pro tuto vlastnost. Místo toho `ShouldSerialize` a `Reset` metod je nutné implementovat pro `MyFont` vlastnost.  
  
## <a name="see-also"></a>Viz také:
- [Vlastnosti v ovládacích prvcích Windows Forms](properties-in-windows-forms-controls.md)
- [Definování vlastnosti](defining-a-property-in-windows-forms-controls.md)
- [Události změny vlastnosti](property-changed-events.md)
