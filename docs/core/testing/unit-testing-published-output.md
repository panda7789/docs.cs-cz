---
title: Testování publikovaného výstupu pomocí dotnet VSTest
description: Naučte se spouštět testy publikovaných knihoven místo ve zdrojovém kódu pomocí příkazu dotnet VSTest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714257"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testování publikovaného výstupu pomocí dotnet VSTest

Můžete spustit testy na již publikovaný výstup pomocí příkazu `dotnet vstest`. To bude fungovat na testech xUnit, MSTest a NUnit. Jednoduše Najděte soubor DLL, který byl součástí publikovaného výstupu a spusťte:

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

Kde `<MyPublishedTests>` je název vašeho publikovaného testovacího projektu.

## <a name="example"></a>Příklad

Následující příkazy ukazují spuštění testů na publikované knihovně DLL.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Poznámka: Pokud se vaše aplikace zaměřuje na jiný rámec než `netcoreapp`, můžete přesto spustit příkaz `dotnet vstest` předáním cílového rozhraní s příznakem rozhraní. Například `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`. V aplikaci Visual Studio 2017 Update 5 a novějších se požadované rozhraní detekuje automaticky.

## <a name="see-also"></a>Viz také:

- [Testování částí pomocí příkazu dotnet test a xUnit](unit-testing-with-dotnet-test.md)
- [Testování částí pomocí příkazu dotnet test a NUnit](unit-testing-with-nunit.md)
- [Testování částí pomocí příkazu dotnet test a MSTest](unit-testing-with-mstest.md)
