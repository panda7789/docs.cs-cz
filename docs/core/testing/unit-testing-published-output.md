---
title: Testování publikovaného výstupu pomocí dotnet VSTest
description: Naučte se spouštět testy publikovaných knihoven místo ve zdrojovém kódu pomocí příkazu dotnet VSTest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 93b2e1a433b5d5b9694257d4d12e47d9107f4cd7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117032"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testování publikovaného výstupu pomocí dotnet VSTest

Můžete spustit testy na již publikovaný výstup pomocí `dotnet vstest` příkazu. To bude fungovat na testech xUnit, MSTest a NUnit. Jednoduše Najděte soubor DLL, který byl součástí publikovaného výstupu a spusťte:

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
> Poznámka: Pokud je vaše aplikace cílena na jiné než `netcoreapp` tento rámec, můžete přesto `dotnet vstest` spustit příkaz předáním cílového rozhraní s příznakem rozhraní. Například, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. V aplikaci Visual Studio 2017 Update 5 se požadované rozhraní automaticky detekuje.

## <a name="see-also"></a>Viz také:

- [Testování částí pomocí příkazu dotnet test a xUnit](unit-testing-with-dotnet-test.md)
- [Testování částí pomocí příkazu dotnet test a NUnit](unit-testing-with-nunit.md)
- [Testování částí pomocí příkazu dotnet test a MSTest](unit-testing-with-mstest.md)
