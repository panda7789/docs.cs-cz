---
title: Seřazení testů jednotek
description: Přečtěte si, jak objednat testy jednotek pomocí .NET Core.
author: IEvangelist
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 3400ae440a828054624d67c14807ee72783e466a
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989260"
---
# <a name="order-unit-tests"></a>Seřazení testů jednotek

V některých případech možná budete chtít, aby testy jednotek běžely v určitém pořadí. V ideálním případě pořadí, ve _kterém by testy_ jednotek běžely, nezáleží a je [osvědčeným postupem](unit-testing-best-practices.md) vyhnout se řazení jednotek. Bez ohledu na to může být potřeba. V takovém případě tento článek ukazuje, jak objednat testovací běhy.

Pokud dáváte přednost procházení zdrojového kódu, přečtěte si téma úložiště ukázkového úložiště [test jednotek .NET Core](/samples/dotnet/samples/order-unit-tests-cs) .

> [!TIP]
> Kromě možností řazení uvedených v tomto článku zvažte možnost [vytvořit vlastní seznamy stop v aplikaci Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) jako alternativu.

:::zone pivot="mstest"

## <a name="order-alphabetically"></a>Seřadit abecedně

Pomocí MSTest jsou testy automaticky seřazeny podle názvu testu.

> [!NOTE]
> Test s názvem `Test14` bude spuštěn před, `Test2` i když `2` je číslo menší než `14` . Důvodem je, že řazení názvu testu používá textový název testu.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

Testovací rozhraní xUnit umožňuje více členitosti a kontrolu nad pořadím testovacích běhů. `ITestCaseOrderer`Rozhraní a implementujete `ITestCollectionOrderer` pro řízení pořadí testovacích případů pro třídu nebo kolekce testů.

## <a name="order-by-test-case-alphabetically"></a>Objednat podle abecedy podle testovacího případu

Pro seřazení testovacích případů podle jejich názvu metody implementujete `ITestCaseOrderer` a zadáte mechanizmus pro řazení.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

Poté v testovací třídě, kterou nastavíte pořadí testovacího případu s `TestCaseOrdererAttribute` .

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a>Seřadit podle kolekce abecedně

Pro seřazení kolekcí testů podle zobrazovaného názvu implementujete `ITestCollectionOrderer` a poskytněte mechanizmus.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

Vzhledem k tomu, že kolekce testů mohou být potenciálně spouštěny paralelně, je nutné explicitně zakázat test paralelismu kolekcí pomocí `CollectionBehaviorAttribute` . Pak zadejte implementaci do `TestCollectionOrdererAttribute` .

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a>Seřadit podle vlastního atributu

Chcete-li seřadit xUnit testy s vlastními atributy, budete nejprve potřebovat atribut, který by měl být závislý. Definujte a `TestPriorityAttribute` následujícím způsobem:

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

Dále zvažte následující `PriorityOrderer` implementaci `ITestCaseOrderer` rozhraní.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

Poté v testovací třídě, kterou nastavíte pořadí testovacího případu s na `TestCaseOrdererAttribute` `PriorityOrderer` .

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a>Pořadí podle priority

Pro explicitní seřazení testů NUnit poskytuje [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) . Testy s tímto atributem jsou spuštěny před testy bez. Hodnota pořadí se používá ke zjištění pořadí spuštění testů jednotek.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Pokrytí kódu testu jednotek](unit-testing-code-coverage.md)
