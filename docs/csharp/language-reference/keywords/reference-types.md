---
title: Odkazové typy C# – referenční informace
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 16e7cdc624979f9a35e287ea5274bd9398c83132
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715167"
---
# <a name="reference-types-c-reference"></a>Typy odkazů (C# referenční)

V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty. Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data. V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou. S typy hodnot každá proměnná má svou vlastní kopii dat a není možné, aby operace s jednou proměnnou ovlivnily jiný (s výjimkou proměnných parametrů ref a out, viz [v](in-parameter-modifier.md)tématu modifikátor [ref](ref.md) a [out](out-parameter-modifier.md) ).

 Pro deklaraci typů odkazu se používají následující klíčová slova:

- [class](class.md)

- [interface](interface.md)

- [delegate](../builtin-types/reference-types.md)

 Jazyk C# nabízí také následující vestavěné typy odkazu:

- [dynamic](../builtin-types/reference-types.md)

- [object](../builtin-types/reference-types.md)

- [string](../builtin-types/reference-types.md)

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy hodnot](value-types.md)
