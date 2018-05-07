---
title: Testování publikované výstup s vstest dotnet.
description: Zjistěte, jak spustit testy na publikované výstup pomocí příkazu vstest dotnet.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: dbce1b6e616916e60e56318b773e8fcecbc55580
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
