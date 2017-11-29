---
title: "Definování výchozích hodnot pomocí metod ShouldSerialize a Reset"
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
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d082b0e3db1e1c115d28446cf515cf6acf60a7d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="90e4e-102">Definování výchozích hodnot pomocí metod ShouldSerialize a Reset</span><span class="sxs-lookup"><span data-stu-id="90e4e-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="90e4e-103">`ShouldSerialize`a `Reset` jsou volitelné metody, které můžete zadat u vlastnosti, pokud vlastnost nemá mají jednoduchý výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90e4e-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="90e4e-104">Pokud má vlastnost jednoduché výchozí hodnotu, byste měli použít <xref:System.ComponentModel.DefaultValueAttribute> a místo toho zadat výchozí hodnotu atributu konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="90e4e-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="90e4e-105">Některé z těchto mechanismů povoluje následující funkce v Návrháři:</span><span class="sxs-lookup"><span data-stu-id="90e4e-105">Either of these mechanisms enables the following features in the designer:</span></span>  
  
-   <span data-ttu-id="90e4e-106">Vlastnost poskytuje vizuální označení v prohlížeči vlastností, pokud se změnila z výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="90e4e-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>  
  
-   <span data-ttu-id="90e4e-107">Uživatel můžete kliknout pravým tlačítkem na vlastnosti a zvolte **resetovat** vlastnost obnovíte jeho výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90e4e-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>  
  
-   <span data-ttu-id="90e4e-108">Návrhář generuje efektivnější kód.</span><span class="sxs-lookup"><span data-stu-id="90e4e-108">The designer generates more efficient code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="90e4e-109">Buď použít <xref:System.ComponentModel.DefaultValueAttribute> nebo zadejte `Reset` *PropertyName* a `ShouldSerialize` *PropertyName* metody.</span><span class="sxs-lookup"><span data-stu-id="90e4e-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="90e4e-110">Nepoužívejte obě.</span><span class="sxs-lookup"><span data-stu-id="90e4e-110">Do not use both.</span></span>  
  
 <span data-ttu-id="90e4e-111">`Reset` *PropertyName* metoda vlastnost nastaví na výchozí hodnotu, jak je znázorněno v následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="90e4e-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>  
  
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
>  <span data-ttu-id="90e4e-112">Pokud vlastnost nemá `Reset` metoda, není označen atributem <xref:System.ComponentModel.DefaultValueAttribute>a nemá výchozí hodnotu. zadaná v jeho deklaraci `Reset` možnost pro tuto vlastnost je zakázána v místní nabídce **vlastnosti** okno Windows Forms designerem v [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="90e4e-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="90e4e-113">Návrháři jako [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] použít `ShouldSerialize` *PropertyName* metoda zkontrolujte, zda vlastnost byl změněn z výchozí hodnoty a napsat kód do formuláře pouze tehdy, pokud vlastnost mění, což umožňuje označení efektivnější generování kódu.</span><span class="sxs-lookup"><span data-stu-id="90e4e-113">Designers such as [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="90e4e-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="90e4e-114">For example:</span></span>  
  
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
  
 <span data-ttu-id="90e4e-115">Následuje příklad dokončení kódu.</span><span class="sxs-lookup"><span data-stu-id="90e4e-115">A complete code example follows.</span></span>  
  
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
  
 <span data-ttu-id="90e4e-116">V tomto případě i v případě, že hodnota soukromé proměnné přístup `MyFont` vlastnost je `null`, prohlížeč vlastností nezobrazí `null`; místo toho se zobrazí <xref:System.Windows.Forms.Control.Font%2A> vlastnost nadřazeným prvkem, pokud není `null`, nebo výchozí <xref:System.Windows.Forms.Control.Font%2A> hodnota definovaná v <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="90e4e-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="90e4e-117">Proto výchozí hodnota pro `MyFont` nelze jednoduše nastavit a <xref:System.ComponentModel.DefaultValueAttribute> nelze použít pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="90e4e-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="90e4e-118">Místo toho `ShouldSerialize` a `Reset` metod, musí být implementována pro `MyFont` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="90e4e-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e4e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="90e4e-119">See Also</span></span>  
 [<span data-ttu-id="90e4e-120">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90e4e-120">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="90e4e-121">Definování vlastnosti</span><span class="sxs-lookup"><span data-stu-id="90e4e-121">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [<span data-ttu-id="90e4e-122">Události změny vlastnosti</span><span class="sxs-lookup"><span data-stu-id="90e4e-122">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)
