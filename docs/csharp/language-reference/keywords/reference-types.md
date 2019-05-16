---
title: Odkazování na typy - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 4b3b1d5b27c3f6a88ce752243ab2d1389b168f0e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634064"
---
# <a name="reference-types-c-reference"></a>Odkazové typy (referenční dokumentace jazyka C#)

V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty. Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data. V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou. S typy hodnot, každá proměnná má svou vlastní kopii dat, a není možné pro operace v rámci jedné proměnné k ovlivnit další (s výjimkou v případě třídy v ref a out proměnných parametrů; viz [v](in-parameter-modifier.md), [ref](ref.md) a [si](out-parameter-modifier.md) modifikátor parametrů).

 Pro deklaraci typů odkazu se používají následující klíčová slova:

- [class](class.md)

- [interface](interface.md)

- [delegate](delegate.md)

 Jazyk C# nabízí také následující vestavěné typy odkazu:

- [dynamic](dynamic.md)

- [object](object.md)

- [string](string.md)

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typy](types.md)
- [Typy hodnot](value-types.md)
