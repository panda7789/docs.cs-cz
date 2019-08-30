---
title: Testování publikovaného výstupu pomocí dotnet VSTest
description: Naučte se spouštět testy publikovaných knihoven místo ve zdrojovém kódu pomocí příkazu dotnet VSTest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 9ac03053bc762d0176e087545871ca8a145cd41e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168296"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testování publikovaného výstupu pomocí dotnet VSTest

Můžete spustit testy na již publikovaný výstup pomocí `dotnet vstest` příkazu. To bude fungovat na testech xUnit, MSTest a NUnit. Jednoduše Najděte soubor DLL, který byl součástí publikovaného výstupu a spusťte:

```console
dotnet vstest <MyPublishedTests>.dll
```

Kde `<MyPublishedTests>` je název vašeho publikovaného testovacího projektu.

## <a name="example"></a>Příklad

Následující příkazy ukazují spuštění testů na publikované knihovně DLL.

```console
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Poznámka: Pokud je vaše aplikace cílena na jiné než `netcoreapp` tento rámec, můžete přesto `dotnet vstest` spustit příkaz předáním cílového rozhraní s příznakem rozhraní. Například, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. V aplikaci Visual Studio 2017 Update 5 se požadované rozhraní automaticky detekuje.

## <a name="see-also"></a>Viz také:

- [Testování částí pomocí příkazu dotnet test a xUnit](unit-testing-with-dotnet-test.md)
- [Testování částí pomocí příkazu dotnet test a NUnit](unit-testing-with-nunit.md)
- [Testování částí pomocí příkazu dotnet test a MSTest](unit-testing-with-mstest.md)
