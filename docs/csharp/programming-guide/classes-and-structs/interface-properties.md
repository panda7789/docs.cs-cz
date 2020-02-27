---
title: Vlastnosti rozhraní – C# Průvodce programováním
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626617"
---
# <a name="interface-properties-c-programming-guide"></a>Vlastnosti rozhraní (Průvodce programováním v C#)

Vlastnosti lze deklarovat v [rozhraní](../../language-reference/keywords/interface.md). Následující příklad deklaruje přistupující objekt vlastnosti rozhraní:

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

Vlastnosti rozhraní obvykle nemají tělo. Přistupující objekty označují, zda je vlastnost určena pro čtení i zápis, jen pro čtení nebo jen pro zápis. Na rozdíl od tříd a struktur deklaruje přistupující objekty bez těla deklarace [automaticky implementované vlastnosti](auto-implemented-properties.md). Počínaje C# 8,0 může rozhraní definovat výchozí implementaci pro členy, včetně vlastností. Definice výchozí implementace pro vlastnost v rozhraní je vzácná, protože rozhraní nemůžou definovat datová pole instance.

## <a name="example"></a>Příklad

V tomto příkladu rozhraní `IEmployee` má vlastnost pro čtení i zápis, `Name`a vlastnost jen pro čtení `Counter`. Třída `Employee` implementuje rozhraní `IEmployee` a používá tyto dvě vlastnosti. Program přečte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí název zaměstnance a vypočtené číslo zaměstnance.

Můžete použít plně kvalifikovaný název vlastnosti, který odkazuje na rozhraní, ve kterém je člen deklarován. Příklad:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

Předchozí příklad ukazuje [explicitní implementaci rozhraní](../interfaces/explicit-interface-implementation.md). Například pokud `Employee` třídy implementuje dvě rozhraní `ICitizen` a `IEmployee` a obě rozhraní mají vlastnost `Name`, bude nutná implementace explicitního člena rozhraní. To znamená, že následující deklarace vlastnosti:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

implementuje vlastnost `Name` v rozhraní `IEmployee`, zatímco následující deklarace:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

implementuje vlastnost `Name` v rozhraní `ICitizen`.

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

- [Průvodce programováním v C#](../index.md)
- [Vlastnosti](./properties.md)
- [Použití vlastností](./using-properties.md)
- [Porovnání mezi vlastnostmi a indexery](../indexers/comparison-between-properties-and-indexers.md)
- [Indexery](../indexers/index.md)
- [Rozhraní](../interfaces/index.md)
