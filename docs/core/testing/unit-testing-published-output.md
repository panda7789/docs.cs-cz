---
title: "Testování publikované výstup s vstest dotnet."
description: "Zjistěte, jak spustit testy na publikované výstup pomocí příkazu vstest dotnet."
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 373c557d3fc640ed9071a732bba9f082ca6a4d33
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
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
