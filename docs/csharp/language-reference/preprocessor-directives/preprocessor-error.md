---
description: '#chyba – Referenční dokumentace jazyka C#'
title: '#chyba – Referenční dokumentace jazyka C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 76325901c5e39f340545b186a0aa9546cd853ff8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138095"
---
# <a name="error-c-reference"></a>#error (referenční dokumentace jazyka C#)

`#error` umožňuje generovat [CS1029](../compiler-messages/cs1029.md) uživatelem definované chyby z konkrétního umístění v kódu. Příklad:

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> Kompilátor zpracovává `#error version` speciální způsob a hlásí chybu kompilátoru CS8304 se zprávou obsahující použitou kompilátor a jazykové verze.

## <a name="remarks"></a>Poznámky

Běžné použití `#error` je v podmíněných direktivách.

Je také možné vygenerovat upozornění definované uživatelem pomocí [#warning](./preprocessor-warning.md).

## <a name="example"></a>Příklad

```csharp
// preprocessor_error.cs
// CS1029 expected
#define DEBUG
class MainClass
{
    static void Main()
    {
#if DEBUG
#error DEBUG is defined
#endif
    }
}
```

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [C# – direktivy preprocesoru](./index.md)
