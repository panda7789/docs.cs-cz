---
title: Deklarace proměnné objektu
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
ms.openlocfilehash: d1964e3768124dde1deeabfada9006ff5a59def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351806"
---
# <a name="object-variable-declaration-visual-basic"></a>Deklarace proměnné objektu (Visual Basic)
Použijete normální příkaz deklarace k deklaraci objektové proměnné. Pro datový typ zadáte buď `Object` (tj. [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md)), nebo konkrétnější třídu, ze které má být objekt vytvořen.  
  
 Deklarace proměnné jako `Object` je stejná jako deklarace jako <xref:System.Object?displayProperty=nameWithType>.  
  
 Pokud deklarujete proměnnou s konkrétní objektovou třídou, může získat přístup ke všem metodám a vlastnostem vystaveným touto třídou a třídám, ze kterých dědí. Pokud deklarujete proměnnou s <xref:System.Object>, může přistupovat pouze k členům třídy <xref:System.Object>, pokud nezapnete `Option Strict Off` povolit pozdní vazby.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 K deklaraci objektové proměnné použijte následující syntax:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 V deklaraci můžete také zadat [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)nebo [static](../../../../visual-basic/language-reference/modifiers/static.md) . Následující příklady deklarací jsou platné:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Pozdní vazba a počáteční vazba  
 Někdy je konkrétní třída neznámá, dokud se váš kód nespustí. V takovém případě je nutné deklarovat objektovou proměnnou s datovým typem `Object`. Tím se vytvoří obecný odkaz na jakýkoli typ objektu a specifická třída je přiřazena za běhu. Tato metoda se nazývá *pozdní vazba*. Pozdní vazba vyžaduje další čas spuštění. Také omezuje váš kód na metody a vlastnosti třídy, kterou jste nedávno přiřadili. To může způsobit chyby v době běhu, pokud se váš kód pokusí o přístup k členům jiné třídy.  
  
 Pokud znáte konkrétní třídu v době kompilace, měli byste deklarovat objektovou proměnnou, která má být danou třídou. Tato metoda se nazývá *časná vazba*. Předčasné vázání zvyšuje výkon a zaručuje přístup kódu ke všem metodám a vlastnostem konkrétní třídy. V předchozím příkladu deklarace, pokud proměnná `objA` používá pouze objekty <xref:System.Windows.Forms.Label?displayProperty=nameWithType>třídy, měli byste zadat `As System.Windows.Forms.Label` ve své deklaraci.  
  
### <a name="advantages-of-early-binding"></a>Výhody prvotní vazby  
 Deklarování proměnné objektu jako konkrétní třídy poskytuje několik výhod:  
  
- Automatická kontrola typu  
  
- Zaručit přístup ke všem členům konkrétní třídy  
  
- Podpora technologie Microsoft IntelliSense v editoru kódu  
  
- Zlepšení čitelnosti kódu  
  
- Méně chyb v kódu  
  
- Chyby zachycené v době kompilace namísto běhu  
  
- Rychlejší provádění kódu  
  
## <a name="access-to-object-variable-members"></a>Přístup k členům proměnné objektu  
 Když je `Option Strict` `On`, proměnná objektu může přistupovat pouze k metodám a vlastnostem třídy, se kterou deklarujete. Toto dokládá následující příklad.  
  
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
  
 V tomto příkladu může `p` použít pouze členy <xref:System.Object> třídy, které neobsahují vlastnost `Left`. Na druhé straně `q` byla deklarována jako typu <xref:System.Windows.Forms.Label>, takže může použít všechny metody a vlastnosti třídy <xref:System.Windows.Forms.Label> v oboru názvů <xref:System.Windows.Forms>.  
  
## <a name="flexibility-of-object-variables"></a>Flexibilita objektových proměnných  
 Při práci s objekty v hierarchii dědičnosti máte možnost výběru třídy, která se má použít pro deklaraci proměnných objektu. Při výběru této možnosti je nutné rovnováhu mezi přiřazením objektu a přístupem ke členům třídy. Zvažte například hierarchii dědičnosti, která vede na třídu <xref:System.Windows.Forms.Form?displayProperty=nameWithType>:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Předpokládejme, že vaše aplikace definuje třídu formuláře nazvanou `specialForm`, která dědí z třídy <xref:System.Windows.Forms.Form>. Můžete deklarovat objektovou proměnnou, která odkazuje konkrétně na `specialForm`, jak ukazuje následující příklad.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Deklarace v předchozím příkladu omezuje proměnnou `nextForm` na objekty třídy `specialForm`, ale také zpřístupňuje všechny metody a vlastnosti `specialForm` k dispozici pro `nextForm`a také všechny členy všech tříd, ze kterých `specialForm` dědí.  
  
 Objekt, který je obecnější, lze vytvořit tak, že deklarujete, že je typu <xref:System.Windows.Forms.Form>, jak ukazuje následující příklad.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Deklarace v předchozím příkladu umožňuje přiřadit libovolný formulář v aplikaci k `anyForm`. I když ale `anyForm` mají přístup ke všem členům třídy <xref:System.Windows.Forms.Form>, nemůže použít žádnou z dalších metod nebo vlastností definovaných pro konkrétní formuláře, jako je například `specialForm`.  
  
 Všichni členové základní třídy jsou k dispozici pro odvozené třídy, ale další členy odvozené třídy nejsou pro základní třídu k dispozici.  
  
## <a name="see-also"></a>Viz také:

- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Postupy: deklarace objektové proměnné a přiřazení objektu k němu v Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Postupy: Přístup ke členům v objektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
