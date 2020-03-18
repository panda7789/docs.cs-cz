---
title: Test publikovaný výstup s dotnet vstest
description: Naučte se, jak spustit testy na publikovaných knihoven, nikoli na zdrojový kód, s dotnet vstest příkazu.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714257"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Test publikovaný výstup s dotnet vstest

Testy již publikovaného výstupu můžete spustit `dotnet vstest` pomocí příkazu. To bude fungovat na xUnit, MSTest a NUnit testy. Jednoduše vyhledejte soubor DLL, který byl součástí publikovaného výstupu, a spusťte:

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

Kde `<MyPublishedTests>` je název publikovaného testovacího projektu.

## <a name="example"></a>Příklad

Níže uvedené příkazy ukazují spuštění testů na publikované dll.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Poznámka: Pokud vaše aplikace cílí na jiné rozhraní než `netcoreapp`, můžete příkaz spustit `dotnet vstest` předáním v cílovém rámci s příznakem architektury. Například, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`. V aktualizaci Visual Studio 2017 Update 5 a novější se automaticky zjistí požadovaný rámec.

## <a name="see-also"></a>Viz také

- [Testování částí s dotnetovým testem a xUnit](unit-testing-with-dotnet-test.md)
- [Testování částí s dotnetovým testem a NUnit](unit-testing-with-nunit.md)
- [Testování částí s dotnet testem a MSTest](unit-testing-with-mstest.md)
