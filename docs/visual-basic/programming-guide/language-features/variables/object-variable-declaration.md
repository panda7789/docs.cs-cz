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
ms.openlocfilehash: b6de52cf738a56a42c82978b54cef31574ab0bcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410358"
---
# <a name="object-variable-declaration-visual-basic"></a>Deklarace proměnné objektu (Visual Basic)
Použijete normální příkaz deklarace k deklaraci objektové proměnné. Pro datový typ zadáte buď `Object` (tj. [datový typ objektu](../../../language-reference/data-types/object-data-type.md)), nebo konkrétnější třídu, ze které má být objekt vytvořen.  
  
 Deklarace proměnné tak, jak `Object` je stejná jako deklarace jako <xref:System.Object?displayProperty=nameWithType> .  
  
 Pokud deklarujete proměnnou s konkrétní objektovou třídou, může získat přístup ke všem metodám a vlastnostem vystaveným touto třídou a třídám, ze kterých dědí. Pokud deklarujete proměnnou s <xref:System.Object> , může přistupovat pouze k členům <xref:System.Object> třídy, pokud nepovolíte `Option Strict Off` pozdní vazbu.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 K deklaraci objektové proměnné použijte následující syntax:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 V deklaraci můžete také zadat [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), `Protected Friend` , [Private](../../../language-reference/modifiers/private.md), [Shared](../../../language-reference/modifiers/shared.md)nebo [static](../../../language-reference/modifiers/static.md) . Následující příklady deklarací jsou platné:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Pozdní vazba a počáteční vazba  
 Někdy je konkrétní třída neznámá, dokud se váš kód nespustí. V takovém případě musíte deklarovat objektovou proměnnou s `Object` datovým typem. Tím se vytvoří obecný odkaz na jakýkoli typ objektu a specifická třída je přiřazena za běhu. Tato metoda se nazývá *pozdní vazba*. Pozdní vazba vyžaduje další čas spuštění. Také omezuje váš kód na metody a vlastnosti třídy, kterou jste nedávno přiřadili. To může způsobit chyby v době běhu, pokud se váš kód pokusí o přístup k členům jiné třídy.  
  
 Pokud znáte konkrétní třídu v době kompilace, měli byste deklarovat objektovou proměnnou, která má být danou třídou. Tato metoda se nazývá *časná vazba*. Předčasné vázání zvyšuje výkon a zaručuje přístup kódu ke všem metodám a vlastnostem konkrétní třídy. V předchozím příkladu deklarace, pokud proměnná `objA` používá pouze objekty třídy <xref:System.Windows.Forms.Label?displayProperty=nameWithType> , je vhodné zadat `As System.Windows.Forms.Label` v deklaraci.  
  
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
 Když `Option Strict` je tato `On` Proměnná zapnutá, má objektová proměnná přístup pouze k metodám a vlastnostem třídy, se kterou deklarujete. Toto dokládá následující příklad.  
  
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
  
 V tomto příkladu `p` může použít pouze členy <xref:System.Object> samotné třídy, které neobsahují `Left` vlastnost. Na druhé straně `q` byla deklarována jako typu <xref:System.Windows.Forms.Label> , takže může použít všechny metody a vlastnosti <xref:System.Windows.Forms.Label> třídy v <xref:System.Windows.Forms> oboru názvů.  
  
## <a name="flexibility-of-object-variables"></a>Flexibilita objektových proměnných  
 Při práci s objekty v hierarchii dědičnosti máte možnost výběru třídy, která se má použít pro deklaraci proměnných objektu. Při výběru této možnosti je nutné rovnováhu mezi přiřazením objektu a přístupem ke členům třídy. Zvažte například hierarchii dědičnosti, která vede na <xref:System.Windows.Forms.Form?displayProperty=nameWithType> třídu:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Předpokládejme, že vaše aplikace definuje třídu formuláře nazvanou `specialForm` , která dědí z třídy <xref:System.Windows.Forms.Form> . Můžete deklarovat objektovou proměnnou, která odkazuje konkrétně na `specialForm` , jak ukazuje následující příklad.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Deklarace v předchozím příkladu omezuje proměnnou `nextForm` na objekty třídy `specialForm` , ale také zpřístupňuje všechny metody a vlastnosti `specialForm` , které jsou k dispozici pro `nextForm` , a všechny členy všech tříd, ze kterých `specialForm` dědí.  
  
 Můžete nastavit obecnější objekt tak, že deklarujete, že má být typu <xref:System.Windows.Forms.Form> , jak ukazuje následující příklad.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Deklarace v předchozím příkladu umožňuje přiřadit libovolný formulář ve vaší aplikaci `anyForm` . I když ale `anyForm` má přístup ke všem členům třídy <xref:System.Windows.Forms.Form> , nemůže použít žádnou z dalších metod nebo vlastností definovaných pro konkrétní formuláře, jako je například `specialForm` .  
  
 Všichni členové základní třídy jsou k dispozici pro odvozené třídy, ale další členy odvozené třídy nejsou pro základní třídu k dispozici.  
  
## <a name="see-also"></a>Viz také

- [Proměnné objektu](object-variables.md)
- [Přiřazení proměnné objektu](object-variable-assignment.md)
- [Hodnoty proměnné objektu](object-variable-values.md)
- [Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Postupy: Přístup ke členům v objektu](how-to-access-members-of-an-object.md)
- [New – operátor](../../../language-reference/operators/new-operator.md)
- [Option Strict – příkaz](../../../language-reference/statements/option-strict-statement.md)
- [Odvození místního typu](local-type-inference.md)
