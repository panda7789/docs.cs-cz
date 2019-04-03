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
ms.openlocfilehash: 4a3ef3a8254153fa8695ffacd9829ca9316d77a5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837647"
---
# <a name="object-variable-declaration-visual-basic"></a>Deklarace proměnné objektu (Visual Basic)
Pomocí příkazu normální deklarace můžete deklarovat proměnné objektu. Pro datový typ, můžete zadat buď `Object` (to znamená, [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md)) nebo konkrétnější třídy, ze kterého má být vytvořen objekt.  
  
 Deklarace proměnné jako `Object` je stejné jako deklarování jako <xref:System.Object?displayProperty=nameWithType>.  
  
 Pokud deklarujete proměnnou s konkrétní objekt třídy, má přístup k všechny metody a vlastnosti, které jsou vystavené třídy a třídy, ze které dědí. Pokud deklarujete proměnnou <xref:System.Object>, má přístup pouze členové <xref:System.Object> třídy, pokud posunete `Option Strict Off` umožňující pozdní vazbu.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Použijte následující syntaxi pro deklaraci proměnné objektu:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Můžete také určit [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [privátní](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), nebo [statické](../../../../visual-basic/language-reference/modifiers/static.md) v deklaraci. Následující příklad deklarace jsou platné:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Časné vazby a pozdní vazby  
 Někdy Neznámý určité třídy, dokud váš kód běží. V takovém případě je třeba deklarovat proměnnou objektu s `Object` datového typu. Tím se vytvoří Obecné referenční informace pro libovolný typ objektu a v době běhu je přiřazena určité třídy. Tento postup se nazývá *pozdní vazby*. Pozdní vazba vyžaduje další čas spuštění. Také omezuje kód do metody a vlastnosti třídy, které jste přiřadili naposledy k němu. To může způsobit chyby za běhu, pokud váš kód se pokusí o přístup ke členům jiné třídy.  
  
 Pokud znáte konkrétní třídu v době kompilace, by měla deklarovat proměnnou objekt této třídy. Tento postup se nazývá *časné vazby*. Časná vazba zlepšuje výkon a garantuje váš kód přístup k metodám a vlastnostem konkrétní třídy. V předchozím příkladu deklarace, pokud proměnné `objA` používá jenom objekty třídy <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, měli byste zadat `As System.Windows.Forms.Label` v jeho deklaraci.  
  
### <a name="advantages-of-early-binding"></a>Výhody časná vazba  
 Deklarace proměnné objektu jako konkrétní třídy přináší řadu výhod:  
  
-   Kontrola automatické typu  
  
-   Zaručeno, že přístup všech členů určité třídy  
  
-   Podpora Microsoft IntelliSense v editoru kódu  
  
-   Lepší čitelnost kódu  
  
-   Méně chyb v kódu  
  
-   Chyby zachycena v době kompilace spíše než čas spuštění  
  
-   Rychlejší provádění kódu  
  
## <a name="access-to-object-variable-members"></a>Přístup k proměnné členů objektu  
 Když `Option Strict` zapnuté `On`, proměnné objektu přístupné pouze metody a vlastnosti třídy, se kterým se deklaruje. Toto dokládá následující příklad.  
  
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
  
 V tomto příkladu `p` lze použít pouze členové <xref:System.Object> třídu, která nejsou zahrnuté `Left` vlastnost. Na druhé straně `q` byl deklarován jako typ <xref:System.Windows.Forms.Label>, takže ho můžete použít všechny metody a vlastnosti <xref:System.Windows.Forms.Label> třídy v <xref:System.Windows.Forms> oboru názvů.  
  
## <a name="flexibility-of-object-variables"></a>Flexibilita objektových proměnných  
 Při práci s objekty v hierarchii dědičnosti, máte možnost volby z třídy pro deklarace objektových proměnných. Při vytváření tohoto výběru, musí zajistit rovnováhu mezi flexibilitu přiřazení objektu pro přístup k členům třídy. Představte si třeba, který vede k hierarchii dědičnosti <xref:System.Windows.Forms.Form?displayProperty=nameWithType> třídy:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Předpokládejme, že vaše aplikace definuje třídu formulář s názvem `specialForm`, který dědí z třídy <xref:System.Windows.Forms.Form>. Můžete deklarovat proměnné objektu, který se vztahuje konkrétně pro `specialForm`, jak ukazuje následující příklad.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Deklarace v předchozím příkladu omezuje proměnnou `nextForm` pro objekty třídy `specialForm`, ale také umožní všechny metody a vlastnosti `specialForm` k dispozici `nextForm`, stejně jako všechny členy všechny třídy, ze kterého `specialForm` dědí.  
  
 Provedete proměnné objektu obecnější deklarováním typu <xref:System.Windows.Forms.Form>, jak ukazuje následující příklad.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Deklarace v předchozím příkladu umožňuje přiřadit libovolného formuláře v aplikaci k `anyForm`. Nicméně i když `anyForm` můžete přístup ke všem členům třídy <xref:System.Windows.Forms.Form>, se nemůže používat žádné další metody nebo vlastnosti, které jsou definovány pro konkrétní formulářů, jako `specialForm`.  
  
 Všechny členy základní třídy jsou k dispozici k odvozeným třídám, ale další členy odvozené třídy nejsou k dispozici pro základní třídy.  
  
## <a name="see-also"></a>Viz také:

- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Postupy: Deklarace objektové proměnné a přiřazení objektu k v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Postupy: Přístup k členům v objektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
