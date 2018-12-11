---
title: set – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 3020badc8b7873d7feb0b8133d3a181e1c051cbd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243735"
---
# <a name="set-c-reference"></a>set (Referenční dokumentace jazyka C#)

`set` Definuje – klíčové slovo *přistupující objekt* metoda ve vlastnosti nebo indexovacího člena, který se přiřadí hodnotu k vlastnosti nebo elementu indexeru. Další informace a příklady najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), a [indexery](../../programming-guide/indexers/index.md).

Následující příklad definuje i `get` a `set` přístupový objekt pro vlastnost s názvem `Seconds`. Používá soukromé pole s názvem `_seconds` zálohovat hodnotu vlastnosti.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Často se stává `set` přístupový objekt se skládá z jednoho příkazu, který vrací hodnotu, stejně jako v předchozím příkladu. Od verze C# 7.0, můžete implementovat `set` přístupového objektu jako člena s výrazem v těle. Následující příklad implementuje oba `get` a `set` přistupující objekty jako členy s výrazem v těle.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Pro jednoduché případech, ve kterém vlastnosti `get` a `set` přistupující objekty provádět žádné jiné operace než nastavení nebo načtení hodnoty v poli privátní zálohování, můžete využít výhod podpory kompilátor jazyka C# pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementované vlastnosti. 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)