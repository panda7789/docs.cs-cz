---
title: Vlastnosti rozhraní – průvodce programováním jazyka C#
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626617"
---
# <a name="interface-properties-c-programming-guide"></a>Vlastnosti rozhraní (Průvodce programováním v C#)

Vlastnosti lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md). Následující příklad deklaruje přistupující objekt vlastnosti rozhraní:

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

Vlastnosti rozhraní obvykle nemají tělo. Přistupující objekty označují, zda je vlastnost jen pro čtení, jen pro čtení nebo jen pro zápis. Na rozdíl od tříd a struktur deklarování přístupových objektů bez těla nedeklaruje [automaticky implementovanou vlastnost](auto-implemented-properties.md). Počínaje C# 8.0 rozhraní může definovat výchozí implementaci pro členy, včetně vlastností. Definování výchozí implementace vlastnosti v rozhraní je vzácné, protože rozhraní nemusí definovat datová pole instancí.

## <a name="example"></a>Příklad

V tomto příkladu `IEmployee` rozhraní má vlastnost `Name`pro čtení a zápis `Counter`a vlastnost jen pro čtení . Třída `Employee` implementuje `IEmployee` rozhraní a používá tyto dvě vlastnosti. Program přečte jméno nového zaměstnance a aktuální počet zaměstnanců a zobrazí jméno zaměstnance a číslo vypočítaného zaměstnance.

Můžete použít plně kvalifikovaný název vlastnosti, která odkazuje na rozhraní, ve kterém je deklarován člen. Například:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

Předchozí příklad ukazuje [explicitní implementace rozhraní](../interfaces/explicit-interface-implementation.md). Například pokud třída `Employee` implementuje dvě `ICitizen` `IEmployee` rozhraní a obě `Name` rozhraní mají vlastnost, bude nutné explicitní implementace člena rozhraní. To znamená následující prohlášení o vlastnostech:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

implementuje `Name` vlastnost `IEmployee` na rozhraní, zatímco následující prohlášení:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

implementuje `Name` vlastnost `ICitizen` na rozhraní.

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a>Ukázkový výstup

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Vlastnosti](./properties.md)
- [Použití vlastností](./using-properties.md)
- [Porovnání vlastností a indexerů](../indexers/comparison-between-properties-and-indexers.md)
- [Indexery](../indexers/index.md)
- [Rozhraní](../interfaces/index.md)
