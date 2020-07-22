---
title: Vlastnosti rozhraní – Průvodce programováním v C#
description: Vlastnosti lze deklarovat v rozhraní v jazyce C#. Tento příklad deklaruje přistupující objekt vlastnosti rozhraní.
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 920381ae804a6a968bfd667171269377f3d7e448
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864966"
---
# <a name="interface-properties-c-programming-guide"></a>Vlastnosti rozhraní (Průvodce programováním v C#)

Vlastnosti lze deklarovat v [rozhraní](../../language-reference/keywords/interface.md). Následující příklad deklaruje přistupující objekt vlastnosti rozhraní:

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

Vlastnosti rozhraní obvykle nemají tělo. Přistupující objekty označují, zda je vlastnost určena pro čtení i zápis, jen pro čtení nebo jen pro zápis. Na rozdíl od tříd a struktur deklaruje přistupující objekty bez těla deklarace [automaticky implementované vlastnosti](auto-implemented-properties.md). Počínaje jazykem C# 8,0 může rozhraní definovat výchozí implementaci pro členy, včetně vlastností. Definice výchozí implementace pro vlastnost v rozhraní je vzácná, protože rozhraní nemůžou definovat datová pole instance.

## <a name="example"></a>Příklad

V tomto příkladu `IEmployee` má rozhraní vlastnost pro čtení i zápis, `Name` a vlastnost určenou jen pro čtení `Counter` . Třída `Employee` implementuje `IEmployee` rozhraní a používá tyto dvě vlastnosti. Program přečte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí název zaměstnance a vypočtené číslo zaměstnance.

Můžete použít plně kvalifikovaný název vlastnosti, který odkazuje na rozhraní, ve kterém je člen deklarován. Příklad:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

Předchozí příklad ukazuje [explicitní implementaci rozhraní](../interfaces/explicit-interface-implementation.md). Například pokud třída `Employee` implementuje dvě rozhraní `ICitizen` a `IEmployee` a obě rozhraní mají `Name` vlastnost, bude nutná implementace explicitního člena rozhraní. To znamená, že následující deklarace vlastnosti:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

implementuje `Name` vlastnost na `IEmployee` rozhraní a následující deklaraci:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

implementuje `Name` vlastnost na `ICitizen` rozhraní.

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

- [Průvodce programováním v C#](../index.md)
- [Vlastnosti](./properties.md)
- [Použití vlastností](./using-properties.md)
- [Porovnání mezi vlastnostmi a indexery](../indexers/comparison-between-properties-and-indexers.md)
- [Indexery](../indexers/index.md)
- [Rozhraní](../interfaces/index.md)
