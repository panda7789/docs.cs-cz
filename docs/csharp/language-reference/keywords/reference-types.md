---
description: Typy odkazů – reference jazyka C#
title: Typy odkazů – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 1a9df3c95d6f5052821be8db5ecf5a8ed99a8ba7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137055"
---
# <a name="reference-types-c-reference"></a>Typy odkazů (Referenční dokumentace jazyka C#)

V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty. Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data. V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou. S typy hodnot každá proměnná má svou vlastní kopii dat a není možné, aby operace s jednou proměnnou ovlivnily jiný (s výjimkou proměnných parametrů ref a out, viz [v](in-parameter-modifier.md)tématu modifikátor [ref](ref.md) a [out](out-parameter-modifier.md) ).

 Pro deklaraci typů odkazu se používají následující klíčová slova:

- [Deník](class.md)

- [prostředí](interface.md)

- [dostával](../builtin-types/reference-types.md)

 Jazyk C# nabízí také následující vestavěné typy odkazu:

- [dynamic](../builtin-types/reference-types.md)

- [object](../builtin-types/reference-types.md)

- [řetezce](../builtin-types/reference-types.md)

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy hodnot](../builtin-types/value-types.md)
