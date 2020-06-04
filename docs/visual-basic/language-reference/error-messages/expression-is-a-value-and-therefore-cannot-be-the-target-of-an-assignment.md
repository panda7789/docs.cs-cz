---
title: Výraz je hodnota, a proto nemůže být cílem přiřazení.
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 9e4dbaf2f2800454c673cd58ddec4cf0f6e5c6b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409504"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Výraz je hodnota, a proto nemůže být cílem přiřazení.

Příkaz se pokusí přiřadit hodnotu k výrazu. V době běhu můžete přiřadit hodnotu pouze k zapisovatelné proměnné, vlastnosti nebo prvku Array. Následující příklad ukazuje, jak k této chybě může dojít.

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

Podobné příklady mohou být použity pro vlastnosti a prvky pole.

**Nepřímý přístup.** Tuto chybu může generovat také nepřímý přístup prostřednictvím typu hodnoty. Vezměte v úvahu následující příklad kódu, který se pokusí nastavit hodnotu přímým <xref:System.Drawing.Point> přístupem prostřednictvím <xref:System.Windows.Forms.Control.Location%2A> .

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

Poslední příkaz v předchozím příkladu se nezdařil, protože vytváří pouze dočasné přidělení pro <xref:System.Drawing.Point> strukturu vrácenou <xref:System.Windows.Forms.Control.Location%2A> vlastností. Struktura je typ hodnoty a dočasná struktura není po spuštění příkazu uchována. Problém je vyřešen deklarováním a použitím proměnné pro <xref:System.Windows.Forms.Control.Location%2A> , která vytvoří pro strukturu trvalé přidělení <xref:System.Drawing.Point> . Následující příklad ukazuje kód, který může nahradit poslední příkaz v předchozím příkladu.

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

**ID chyby:** BC30068

## <a name="to-correct-this-error"></a>Oprava této chyby

- Pokud příkaz přiřadí hodnotu výrazu, nahraďte výraz jedinou zapisovatelnou proměnnou, vlastností nebo elementem pole.

- Pokud příkaz vytvoří nepřímý přístup prostřednictvím typu hodnoty (obvykle struktury), vytvořte proměnnou pro uchování typu hodnoty.

- Přiřaďte proměnné příslušnou strukturu (nebo jiný typ hodnoty).

- Pro přístup k vlastnosti použijte proměnnou k přiřazení hodnoty.

## <a name="see-also"></a>Viz také

- [Operátory a výrazy](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
- [Řešení potíží s procedurami](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
