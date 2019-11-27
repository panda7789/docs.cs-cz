---
title: Přiřazení proměnné objektu
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 93de17490935d6d5cad01000e9ee3e2fe55bd16c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351821"
---
# <a name="object-variable-assignment-visual-basic"></a>Přiřazení proměnné objektu (Visual Basic)

Použijete normální příkaz přiřazení k přiřazení objektu proměnné objektu. Můžete přiřadit výraz objektu nebo klíčové slovo [Nothing](../../../../visual-basic/language-reference/nothing.md) , jak ukazuje následující příklad.

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

`Nothing` znamená, že k proměnné není aktuálně přiřazen žádný objekt.

## <a name="initialization"></a>Inicializace

Když váš kód začíná běžet, vaše proměnné objektu jsou inicializovány na `Nothing`. Ty, jejichž deklarace zahrnují inicializaci, jsou znovu inicializovány na hodnoty, které zadáte při spuštění příkazů deklarace.

Do své deklarace můžete přidat inicializaci pomocí klíčového slova [New](../../../../visual-basic/language-reference/operators/new-operator.md) . Následující příkazy deklarace deklaruje proměnné objektu `testUri` a `ver` a přiřadí jim konkrétní objekty. Každý používá jeden z přetížených konstruktorů příslušné třídy pro inicializaci objektu.

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>Zrušení přidružení

Nastavení proměnné objektu pro `Nothing` přestane přidružení proměnné k jakémukoli konkrétnímu objektu. Tím zabráníte nechtěné změně objektu změnou proměnné. Také umožňuje otestovat, zda proměnná objektu odkazuje na platný objekt, jak ukazuje následující příklad.

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

Pokud objekt, na který proměnná odkazuje, je v jiné aplikaci, nemůže tento test určit, zda byla daná aplikace ukončena nebo zda právě neověřovala objekt.

Proměnná objektu s hodnotou `Nothing` se také označuje jako *odkaz s hodnotou null*.

## <a name="current-instance"></a>Aktuální instance

*Aktuální instance* objektu je ten, ve kterém je aktuálně spuštěn kód. Vzhledem k tomu, že veškerý kód provede v rámci procedury, aktuální instance je ta, ve které byl procedura vyvolána.

Klíčové slovo `Me` funguje jako proměnná objektu odkazující na aktuální instanci. Pokud procedura není [sdílená](../../../../visual-basic/language-reference/modifiers/shared.md), může pomocí klíčového slova `Me` získat ukazatel na aktuální instanci. Sdílené procedury nelze přidružit ke konkrétní instanci třídy.

Použití `Me` je zvláště užitečné pro předání aktuální instance do procedury v jiném modulu. Předpokládejme například, že máte několik dokumentů XML a chcete do nich přidat nějaký standardní text. Následující příklad definuje proceduru, která to provede.

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

Každý objekt dokumentu XML pak může zavolat proceduru a předat aktuální instanci jako argument. Následující příklad ukazuje to.

```vb
addStandardText(Me)
```

## <a name="see-also"></a>Viz také:

- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Postupy: deklarace objektové proměnné a přiřazení objektu k němu v Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Postupy: Nastavení objektové proměnné tak, aby neodkazovala na žádnou instanci](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
