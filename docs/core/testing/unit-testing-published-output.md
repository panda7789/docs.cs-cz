---
title: Testování publikované výstup s vstest dotnet.
description: Zjistěte, jak spustit testy na publikované výstup pomocí příkazu vstest dotnet.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 2f750a8bb0907069691c4a4491beeb4b1733df29
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testování publikované výstup s vstest dotnet.

Testy můžete spustit na výstupu již publikované pomocí `dotnet vstest` příkaz. To bude fungovat na xUnit, Mstestu a NUnit testy. Jednoduše vyhledejte soubor knihovny DLL, který byl součástí publikované výstupu a spusťte:

```
dotnet vstest <MyPublishedTests>.dll
```

kde `<MyPublishedTests>` je název publikované testovacího projektu.

## <a name="example-of-running-tests-on-a-published-dll"></a>Příklad spuštění testů na publikované knihovny DLL

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Poznámka: Pokud aplikace cílí rozhraní než `netcoreapp` pořád se dá spustit `dotnet vstest` příkaz předáním v cílové rozhraní s příznakem framework. Například `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. V sadě Visual Studio 2017 aktualizace 5 je automaticky zjišťován požadované rozhraní.

## <a name="see-also"></a>Viz také
 [Testování částí s dotnet test a xUnit](unit-testing-with-dotnet-test.md)  
 [Testování částí s dotnet test a Mstestu](unit-testing-with-mstest.md)  
