---
title: "Portování do .NET Core - analýza strany závislostmi třetích stran"
description: "Portování do .NET Core - analýza závislostmi třetích stran"
keywords: "Rozhraní .NET, .NET core"
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.workload: dotnetcore
ms.openlocfilehash: 70b39c9762e4ee7450d0f59455bace0ac728844c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a>Portování do .NET Core - analýza strany závislostmi třetích stran

Prvním krokem v procesu přenosem je pochopit závislostmi třetích stran.  Je třeba zjistit, kdo z nich, pokud existuje, není ještě spustit na .NET Core a vytvořte pohotovostní plán pro ty, které nechcete spustit na .NET Core.

## <a name="prerequisites"></a>Požadavky

V tomto článku bude předpokládat, používáte Windows Server a Visual Studio, a že máte kód, který běží na rozhraní .NET Framework ještě dnes.

## <a name="analyzing-nuget-packages"></a>Analýza balíčků NuGet

Analýza balíčků NuGet pro přenositelnost je velmi snadné.  Balíček NuGet je sám sadu složek, které obsahují sestavení specifické pro platformu, a proto všechny, které musíte udělat je zkontrolujte, zda je do složky, který obsahuje sestavení .NET Core.

Probíhá kontrola složky balíčku NuGet je nejjednodušší s [Explorer balíček NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) nástroj.  Chcete-li to provést.

1. Stáhněte a otevřete Průzkumníka balíček NuGet.
2. Klikněte na tlačítko "Otevřete balíček z online kanálu".
3. Vyhledejte název balíčku.
4. Rozbalte složku "lib" na pravé straně a podívejte se na názvy složek.

Můžete také zjistit, co balíček podporuje na [nuget.org](https://www.nuget.org/) pod **závislosti** části stránky pro tento balíček.

V obou případech budete muset najít složku nebo položku na [nuget.org](https://www.nuget.org/) s žádným z následujících názvů:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Jedná se o Monikery Framework cíl (TFM) které mapování na verzích [.NET Standard](../../standard/net-standard.md) a tradiční profily přenosných třída knihovny PCL (), které jsou slučitelné s .NET Core.  Všimněte si, že `netcoreapp1.0`, při kompatibilní, je pro aplikace a není knihovny.  I když není nic nesprávný s použitím knihovny, která je `netcoreapp1.0`– na základě, že knihovna nemusí být žádoucí pro všechno, co *jiných* než jiné spotřeba `netcoreapp1.0` aplikace.

Existují také některé starší verze TFMs v předběžné verze jádra rozhraní .NET, která je také možné kompatibilní:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

**Když to bude pravděpodobně pracovat s kódu, neexistuje žádná záruka kompatibility**.  Balíčky s tyto TFMs nebyly vytvořené s balíčky předběžné verze .NET Core.  Poznamenejte si při (nebo pokud) balíčky takto jsou aktualizovány být `netstandard`– na základě.

> [!NOTE]
> Chcete-li použít balíček cílení tradiční PCL nebo předběžné verze .NET Core cíl, musíte použít `imports` direktivy v vaší `project.json` souboru.

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co dělat, když vaše závislost balíčku NuGet nefunguje v .NET Core

Existuje několik věcí, které můžete provést, pokud balíček NuGet, které závisí na se nespustí na .NET Core.

1. Pokud projekt je open source a je hostovaná někde jako GitHub, můžete použít developer(s) přímo.
2. Obraťte se na autora přímo na [nuget.org](https://www.nuget.org/) vyhledávání pro balíček a kliknutím na možnost "Obraťte se na vlastníky" na levé straně stránky daného balíčku.
3. Můžete vyhledat jiný balíček, který běží na .NET Core, která má jako balíčku, který jste používali pro stejnou úlohu.
4. Můžete se pokusit napsat kód, že balíček dělal sami.
5. Závislost na balíček může eliminovat alespoň změnou funkce aplikace, dokud nebude k dispozici kompatibilní verzi balíčku.

Prosím pamatujte, že údržby opensourcový projekt programu a vydavatelé balíček NuGet jsou často kteří přispívat, protože zajímají pro danou doménu, provést zdarma a často mají různé denní úlohy. Pokud oslovení, můžete začít s kladné prohlášení o knihovně před výzvou týkající se podpory .NET Core.

Pokud nemůžete vyřešit problém s žádným z výše, budete muset port na .NET Core později.

Tým služby .NET chcete vědět, které knihovny jsou nejdůležitější pro další podporu s .NET Core. Můžete také nám poslat poštu na dotnet@microsoft.com o knihovny, které chcete použít.

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a>Analýza závislosti, které nejsou balíčků NuGet

Můžete mít závislost, která není balíčku NuGet, jako je například knihovny DLL v systému souborů.  Jediný způsob, jak určit přenositelnost této závislosti se ke spuštění [ApiPort nástroj](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).

## <a name="next-steps"></a>Další kroky

Pokud jste portování knihovnu, podívejte se na [portování knihovnách](libraries.md).
