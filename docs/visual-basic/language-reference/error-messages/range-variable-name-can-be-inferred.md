---
title: Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6b155de0bb62f667ca76ec9454dec1466976a9b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400406"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.

Programovací prvek, který používá jeden nebo více argumentů, je obsažen v dotazu LINQ. Kompilátor nemůže odvodit proměnnou rozsahu z tohoto programovacího prvku.

**ID chyby:** BC36599

## <a name="to-correct-this-error"></a>Oprava této chyby

Zadejte explicitní název proměnné pro programový element, jak je znázorněno v následujícím kódu:

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Klauzule SELECT](../queries/select-clause.md)
