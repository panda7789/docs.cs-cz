---
title: Snížení závislostí balíčků pomocí souboru project.json
description: Při vytváření knihoven založených na souboru project.json snižte závislosti na balíčcích.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740824"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Snížení závislostí balíčků pomocí souboru project.json

Tento článek popisuje, co potřebujete vědět o snížení závislostí balíčků při `project.json` vytváření knihoven. Na konci tohoto článku se dozvíte, jak vytvořit knihovnu tak, aby používá pouze závislosti, které potřebuje.

## <a name="why-its-important"></a>Proč je to důležité

.NET Core je produkt tvořený balíčky NuGet.  Základním balíčkem je [. METAbalíček NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library), což je balíček NuGet složený z jiných balíčků. Poskytuje sadu balíčků, které mají zaručeně pracovat na více implementacích rozhraní .NET, jako je například rozhraní .NET Framework, .NET Core a Xamarin/Mono.

Existuje však velká šance, že vaše knihovna nebude používat každý balíček, který obsahuje.  Při vytváření knihovny a distribuci přes NuGet, je osvědčeným postupem "trim" vaše závislosti až na pouze balíčky, které skutečně používáte.  To má za následek menší celkové nároky na půdu pro balíčky NuGet.

## <a name="how-to-do-it"></a>Jak na to

V současné době neexistuje `dotnet` žádný oficiální příkaz, který ořízne odkazy na balíček.  Místo toho to budete muset udělat ručně.  Obecný proces vypadá takto:

1. Referenční `NETStandard.Library` `1.6.0` verze `dependencies` v části `project.json`vašeho .
2. Obnovte `dotnet restore` balíčky pomocí příkazového řádku ([viz poznámka).](#dotnet-restore-note)
3. Zkontrolujte `project.lock.json` soubor a `NETStandard.Library` vyhledejte oddíl.  Je to blízko začátku složky.
4. Zkopírujte všechny uvedené `dependencies`balíčky v části .
5. Odeberte `.NETStandard.Library` odkaz a nahraďte jej zkopírovanými balíčky.
6. Odeberte odkazy na balíčky, které nepotřebujete.

Které balíčky nepotřebujete, můžete zjistit jedním z následujících způsobů:

1. Pokus a omyl. To zahrnuje odebrání balíčku, obnovení, zjištění, zda vaše knihovna stále kompiluje, a opakování tohoto procesu.
2. Pomocí nástroje, jako je [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) nahlédnout na odkazy vidět, co váš kód je skutečně používá. Potom můžete odebrat balíčky, které neodpovídají typům, které používáte.

## <a name="example"></a>Příklad

Představte si, že jste napsali knihovnu, která poskytuje další funkce pro obecné typy kolekcí. Taková knihovna by musela záviset `System.Collections`na balíčcích, jako je `System.Net.Http`například , ale nemusí záviset na balíčcích, jako je . Jako takový, bylo by dobré zkrátit balíček závislosti pouze na to, co tato knihovna vyžaduje!

Chcete-li tuto knihovnu `project.json` oříznout, začněte `NETStandard.Library` `1.6.0`se souborem a přidejte odkaz na verzi .

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

Dále `dotnet restore` obnovíte balíčky s ( viz[poznámka](#dotnet-restore-note)), zkontrolujte `project.lock.json` soubor `NETStandard.Library`a vyhledejte všechny balíčky obnovené pro .

Tady je, jak vypadá `project.lock.json` příslušná část `netstandard1.0`v souboru při cílení :

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

Dále zkopírujte odkazy na balíček do `dependencies` části `project.json` souboru knihovny `NETStandard.Library` a nahrazte odkaz:

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

To je docela dost balíčků, z nichž mnohé rozhodně nejsou nezbytné pro rozšíření typů sběru.  Můžete buď odebrat balíčky ručně, nebo použít nástroj, jako je [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) k identifikaci, které balíčky váš kód skutečně používá.

Zde je to, co zdobené balíček by mohl vypadat takto:

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

Nyní má menší půdorys, než kdyby `NETStandard.Library` závisel na metabalíčku.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
