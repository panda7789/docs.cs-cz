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
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="2ca08-102">Definování výchozích hodnot pomocí metod ShouldSerialize a Reset</span><span class="sxs-lookup"><span data-stu-id="2ca08-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="2ca08-103">`ShouldSerialize` a `Reset` jsou volitelné metody, které můžete zadat vlastnosti, pokud vlastnost není máte jednoduchý výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2ca08-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="2ca08-104">Pokud má vlastnost jednoduchý výchozí hodnotu, byste měli použít <xref:System.ComponentModel.DefaultValueAttribute> a místo toho zadat výchozí hodnotu pro atribut konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="2ca08-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="2ca08-105">Některé z těchto mechanismů povoluje následující funkce v Návrháři:</span><span class="sxs-lookup"><span data-stu-id="2ca08-105">Either of these mechanisms enables the following features in the designer:</span></span>  
  
-   <span data-ttu-id="2ca08-106">Vlastnost poskytuje vizuální označení v prohlížeči vlastností, pokud se změnila od jeho výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2ca08-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>  
  
-   <span data-ttu-id="2ca08-107">Uživatel může kliknout pravým tlačítkem na vlastnosti a zvolte **resetování** obnovíte jeho výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2ca08-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>  
  
-   <span data-ttu-id="2ca08-108">Návrhář vytvoří efektivnějšího kódu.</span><span class="sxs-lookup"><span data-stu-id="2ca08-108">The designer generates more efficient code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ca08-109">Buď použijte <xref:System.ComponentModel.DefaultValueAttribute> nebo zadejte `Reset` *PropertyName* a `ShouldSerialize` *PropertyName* metody.</span><span class="sxs-lookup"><span data-stu-id="2ca08-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="2ca08-110">Nepoužívejte obojí.</span><span class="sxs-lookup"><span data-stu-id="2ca08-110">Do not use both.</span></span>  
  
 <span data-ttu-id="2ca08-111">`Reset` *PropertyName* metoda nastaví vlastnost na výchozí hodnotu, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="2ca08-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>  
  
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
>  <span data-ttu-id="2ca08-112">Pokud nemá žádné vlastnosti `Reset` metoda, není označena třídou <xref:System.ComponentModel.DefaultValueAttribute>a výchozí hodnota zadaná v jeho deklaraci, nemá `Reset` možnost pro tuto vlastnost je zakázaný v místní nabídce **vlastnosti** okna Návrháře formulářů Windows v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ca08-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>  
  
 <span data-ttu-id="2ca08-113">Použití návrháře, jako je Visual Studio `ShouldSerialize` *PropertyName* metodu ke kontrole, zda má došlo ke změně vlastnosti z výchozí hodnoty a napsat kód do formuláře pouze tehdy, pokud vlastnost změnit, což umožňuje mnohem efektivnější kódu generování.</span><span class="sxs-lookup"><span data-stu-id="2ca08-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="2ca08-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2ca08-114">For example:</span></span>  
  
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
  
 <span data-ttu-id="2ca08-115">Následuje příklad úplného kódu.</span><span class="sxs-lookup"><span data-stu-id="2ca08-115">A complete code example follows.</span></span>  
  
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
  
 <span data-ttu-id="2ca08-116">V takovém případě i v případě, že hodnota soukromé proměnné přistupuje `MyFont` vlastnost je `null`, vlastnost prohlížeče nezobrazí `null`; místo toho se zobrazí <xref:System.Windows.Forms.Control.Font%2A> vlastnosti nadřazeného objektu, pokud není `null`, nebo výchozí hodnotu <xref:System.Windows.Forms.Control.Font%2A> hodnota definovaná v <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="2ca08-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="2ca08-117">Proto výchozí hodnota pro `MyFont` nelze jednoduše nastavit a <xref:System.ComponentModel.DefaultValueAttribute> nelze použít pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2ca08-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="2ca08-118">Místo toho `ShouldSerialize` a `Reset` metod je nutné implementovat pro `MyFont` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2ca08-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca08-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ca08-119">See also</span></span>
- [<span data-ttu-id="2ca08-120">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ca08-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="2ca08-121">Definování vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2ca08-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="2ca08-122">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2ca08-122">Property-Changed Events</span></span>](property-changed-events.md)
