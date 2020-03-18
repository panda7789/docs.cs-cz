---
title: Typy odkazů – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744513"
---
# <a name="reference-types-c-reference"></a>Typy odkazů (odkaz jazyka C#

V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty. Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data. V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou. U typů hodnot má každá proměnná vlastní kopii dat a není možné, aby operace na jedné proměnné ovlivnily druhou proměnnou (s výjimkou v případě proměnných parametrů in, ref a out; [viz](in-parameter-modifier.md)modifikátor parametrů [, ref](ref.md) a [out).](out-parameter-modifier.md)

 Pro deklaraci typů odkazu se používají následující klíčová slova:

- [Třída](class.md)

- [Rozhraní](interface.md)

- [delegát](../builtin-types/reference-types.md)

 Jazyk C# nabízí také následující vestavěné typy odkazu:

- [Dynamické](../builtin-types/reference-types.md)

- [Objekt](../builtin-types/reference-types.md)

- [Řetězec](../builtin-types/reference-types.md)

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [C# Klíčová slova](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy hodnot](../builtin-types/value-types.md)
