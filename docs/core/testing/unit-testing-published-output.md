---
title: Testování publikované výstup s dotnet test
description: Zjistěte, jak spustit testy na publikované výstupu pomocí příkazu dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: e99000996f5dfa9f9d4f9b823e36ecbe325da835
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508130"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testování publikované výstup s dotnet test

Je možné spustit testy na výstupu už byla publikována s použitím `dotnet vstest` příkazu. Bude to fungovat u xUnit, MSTest a NUnit testy. Jednoduše vyhledejte soubor knihovny DLL, která byla součástí publikovaný výstup a spusťte:

```
dotnet vstest <MyPublishedTests>.dll
```

kde `<MyPublishedTests>` je název publikované testovacího projektu.

## <a name="example-of-running-tests-on-a-published-dll"></a>Příklad spouštění testů v publikované knihovny DLL

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Poznámka: Pokud vaše aplikace cílí na rozhraní než `netcoreapp` můžete nadále spouštět `dotnet vstest` příkaz předáním s příznakem framework cíleného rozhraní. Například `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. Ve verzi Visual Studio 2017 Update 5 je automaticky rozpoznán požadované rozhraní.

## <a name="see-also"></a>Viz také:
- [Testování částí pomocí příkazu dotnet test a xUnit](unit-testing-with-dotnet-test.md)
- [Testování částí pomocí příkazu dotnet test a NUnit](unit-testing-with-nunit.md)
- [Testování částí pomocí příkazu dotnet test a MSTest](unit-testing-with-mstest.md)
