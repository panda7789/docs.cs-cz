---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 48261e27de302c1809c9725e6e2fc0705a803930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386773"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Určuje, že nejmíň jedna deklarovaná členská proměnná odkazuje na instanci třídy, která může vyvolat události.

## <a name="remarks"></a>Poznámky

Pokud je proměnná definována pomocí `WithEvents` , lze deklarativně určit, že metoda zpracovává události proměnné pomocí `Handles` klíčového slova.

Můžete použít `WithEvents` pouze na úrovni třídy nebo modulu. To znamená, že kontext deklarace `WithEvents` proměnné musí být třída nebo modul a nemůže se jednat o zdrojový soubor, obor názvů, strukturu nebo proceduru.

Nemůžete použít `WithEvents` u člena struktury.

Můžete deklarovat pouze jednotlivé proměnné – ne pole – s `WithEvents` .

## <a name="rules"></a>Pravidla

**Typy prvků.** Je nutné deklarovat `WithEvents` proměnné, aby byly proměnné objektu, aby mohly přijímat instance třídy. Nemůžete je však deklarovat jako `Object` . Je nutné je deklarovat jako konkrétní třídu, která může události vyvolat.

`WithEvents`Modifikátor se dá použít v tomto kontextu: [příkaz Dim](../statements/dim-statement.md) .

## <a name="example"></a>Příklad

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Viz také

- [Handles](../statements/handles-clause.md)
- [Klíčová slova](../keywords/index.md)
- [Události](../../programming-guide/language-features/events/index.md)
