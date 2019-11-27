---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350740"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Určuje, že nejmíň jedna deklarovaná členská proměnná odkazuje na instanci třídy, která může vyvolat události.

## <a name="remarks"></a>Poznámky

Pokud je proměnná definována pomocí `WithEvents`, lze deklarativně určit, že metoda zpracovává události proměnné pomocí klíčového slova `Handles`.

`WithEvents` můžete použít pouze na úrovni třídy nebo modulu. To znamená, že kontext deklarace pro proměnnou `WithEvents` musí být třída nebo modul a nemůže se jednat o zdrojový soubor, obor názvů, strukturu nebo proceduru.

Nelze použít `WithEvents` pro člena struktury.

Můžete deklarovat pouze jednotlivé proměnné – ne pole – s `WithEvents`.

## <a name="rules"></a>Pravidla

**Typy prvků.** Je nutné deklarovat `WithEvents` proměnné, aby byly proměnné objektu, aby mohly přijímat instance třídy. Nemůžete je však deklarovat jako `Object`. Je nutné je deklarovat jako konkrétní třídu, která může události vyvolat.

V tomto kontextu se dá použít modifikátor `WithEvents`: [příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md) .

## <a name="example"></a>Příklad

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Viz také:

- [Řeší](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
