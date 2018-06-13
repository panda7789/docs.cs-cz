---
title: Deklarace proměnné objektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: f5f77b81380d997e078a9f52ac4aae6f6e975575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656279"
---
# <a name="object-variable-declaration-visual-basic"></a>Deklarace proměnné objektu (Visual Basic)
Příkaz normální deklarace slouží k deklarace proměnné objektu. Pro datový typ, můžete buď zadat `Object` (který je [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md)) nebo více určité třídy, ze kterého má být vytvořen objekt.  
  
 Deklarace proměnné jako `Object` je stejný jako deklarace jej jako <xref:System.Object?displayProperty=nameWithType>.  
  
 Když je deklarovat proměnnou s konkrétní objekt třídy, má přístup všechny metody a vlastnosti, které jsou vystavené třídy a třídy, ze kterých dědí. Pokud deklarovat proměnnou s <xref:System.Object>, má přístup pouze členové <xref:System.Object> třídy, pokud vypnete `Option Strict Off` umožňující pozdní vazba.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Deklarace proměnné objektu použijte následující syntaxi:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Můžete také zadat [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [privátní](../../../../visual-basic/language-reference/modifiers/private.md), [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md), nebo [statické](../../../../visual-basic/language-reference/modifiers/static.md) v deklaraci. Následující příklad deklarace jsou platné:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Časná vazba a pozdní vazby  
 Někdy Neznámý určité třídy, dokud se nespustí vašeho kódu. V takovém případě je třeba deklarovat proměnnou objekt pomocí `Object` datového typu. Tím se vytvoří Obecné referenční informace k libovolnému typu objektu, a v době běhu je přiřazena určité třídy. To se označuje jako *pozdní vazby*. Pozdní vazba vyžaduje další čas spuštění. Omezení taky kód do metody a vlastnosti třídy, kterou jste naposledy přiřadili k němu. To může způsobit chyby, pokud kódu pokusí o přístup ke členům jinou třídu.  
  
 Pokud znáte určité třídy v době kompilace, by měly deklarovat objektová proměnná být této třídy. To se označuje jako *časné vazby*. Časná vazba vylepšuje výkon a zaručí se váš kód přístup pro všechny metody a vlastnosti konkrétní třídy. V deklaracích předchozí příklad, pokud je proměnná `objA` používá pouze objekty třídy <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, musíte zadat `As System.Windows.Forms.Label` v jeho deklaraci.  
  
### <a name="advantages-of-early-binding"></a>Výhody časná vazba  
 Deklarace proměnné objektu jako určité třídy nabízí několik výhod:  
  
-   Kontrola automatické typu  
  
-   Záruku, že přístup všichni členové určité třídy  
  
-   Podpora Microsoft IntelliSense v editoru kódu  
  
-   Lepší čitelnost kódu  
  
-   Menší počet chyb v kódu  
  
-   Chyby zachycena v doba kompilace spíše než čas spuštění  
  
-   Rychlejší provádění kódu  
  
## <a name="access-to-object-variable-members"></a>Přístup k objektu proměnné členů  
 Když `Option Strict` je zapnuta `On`, proměnné objektu získat přístup pouze k metody a vlastnosti třídy, se kterým je deklarovat. Toto dokládá následující příklad.  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 V tomto příkladu `p` můžete použít pouze členové <xref:System.Object> vlastní třídy, které nezahrnují `Left` vlastnost. Na druhé straně `q` byla deklarována jako typu <xref:System.Windows.Forms.Label>, takže můžete použít všechny metody a vlastnosti <xref:System.Windows.Forms.Label> třídy v <xref:System.Windows.Forms> oboru názvů.  
  
## <a name="flexibility-of-object-variables"></a>Flexibilita při objektové proměnné  
 Při práci s objekty v hierarchii dědičnosti, máte možnost volby které třídy pro deklarace objektových proměnných. Při vytvoření tato volba, musíte vyvážit flexibilitu přiřazení objektu proti přístupu ke členům třídy. Představte si třeba hierarchie dědičnosti, který vede k <xref:System.Windows.Forms.Form?displayProperty=nameWithType> třídy:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Předpokládejme, že vaše aplikace definuje třídu formulář s názvem `specialForm`, který dědí z třídy <xref:System.Windows.Forms.Form>. Je možné deklarovat objektová proměnná, která odkazuje konkrétně pro `specialForm`, jak ukazuje následující příklad.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Deklarace v předchozím příkladu omezuje proměnnou `nextForm` objektů třídy `specialForm`, ale také udržuje všechny metody a vlastnosti `specialForm` k dispozici pro `nextForm`, stejně jako všechny členy všechny třídy, ze kterého `specialForm` dědí.  
  
 Můžete provést další obecné proměnné objektu deklarováním mohla být typu <xref:System.Windows.Forms.Form>, jak ukazuje následující příklad.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Deklarace v předchozím příkladu umožňuje přiřadit všechny formuláře v aplikaci na `anyForm`. Nicméně i když `anyForm` k přístup všichni členové třídy <xref:System.Windows.Forms.Form>, nemůže používat další metody nebo vlastnosti definované pro konkrétní formulářů, jako `specialForm`.  
  
 Všechny členy základní třídy jsou k dispozici pro odvozené třídy, ale další členy odvozené třídy jsou k dispozici v základní třídě.  
  
## <a name="see-also"></a>Viz také  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Postupy: deklarace objektové proměnné a přiřazení objektu k v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Postupy: Přístup ke členům v objektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
