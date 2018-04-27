---
title: Definování výchozích hodnot pomocí metod ShouldSerialize a Reset
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a28cd84c88cd7434eaca3fdaa7b4406006c44dad
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definování výchozích hodnot pomocí metod ShouldSerialize a Reset
`ShouldSerialize` a `Reset` jsou volitelné metody, které můžete zadat u vlastnosti, pokud vlastnost nemá mají jednoduchý výchozí hodnotu. Pokud má vlastnost jednoduché výchozí hodnotu, byste měli použít <xref:System.ComponentModel.DefaultValueAttribute> a místo toho zadat výchozí hodnotu atributu konstruktoru třídy. Některé z těchto mechanismů povoluje následující funkce v Návrháři:  
  
-   Vlastnost poskytuje vizuální označení v prohlížeči vlastností, pokud se změnila z výchozí hodnoty.  
  
-   Uživatel můžete kliknout pravým tlačítkem na vlastnosti a zvolte **resetovat** vlastnost obnovíte jeho výchozí hodnotu.  
  
-   Návrhář generuje efektivnější kód.  
  
    > [!NOTE]
    >  Buď použít <xref:System.ComponentModel.DefaultValueAttribute> nebo zadejte `Reset` *PropertyName* a `ShouldSerialize` *PropertyName* metody. Nepoužívejte obě.  
  
 `Reset` *PropertyName* metoda vlastnost nastaví na výchozí hodnotu, jak je znázorněno v následující fragment kódu.  
  
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
>  Pokud vlastnost nemá `Reset` metoda, není označen atributem <xref:System.ComponentModel.DefaultValueAttribute>a nemá výchozí hodnotu. zadaná v jeho deklaraci `Reset` možnost pro tuto vlastnost je zakázána v místní nabídce **vlastnosti** okno Windows Forms designerem v sadě Visual Studio.  
  
 Návrháři třeba v sadě Visual Studio používají `ShouldSerialize` *PropertyName* metoda zkontrolujte, zda vlastnost byl změněn z výchozí hodnoty a napsat kód do formuláře pouze tehdy, pokud vlastnost mění, což umožňuje efektivnější kódu generování. Příklad:  
  
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
  
 Následuje příklad dokončení kódu.  
  
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
  
 V tomto případě i v případě, že hodnota soukromé proměnné přístup `MyFont` vlastnost je `null`, prohlížeč vlastností nezobrazí `null`; místo toho se zobrazí <xref:System.Windows.Forms.Control.Font%2A> vlastnost nadřazeným prvkem, pokud není `null`, nebo výchozí <xref:System.Windows.Forms.Control.Font%2A> hodnota definovaná v <xref:System.Windows.Forms.Control>. Proto výchozí hodnota pro `MyFont` nelze jednoduše nastavit a <xref:System.ComponentModel.DefaultValueAttribute> nelze použít pro tuto vlastnost. Místo toho `ShouldSerialize` a `Reset` metod, musí být implementována pro `MyFont` vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Vlastnosti v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Definování vlastnosti](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [Události změny vlastnosti](../../../../docs/framework/winforms/controls/property-changed-events.md)
