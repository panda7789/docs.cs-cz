---
title: "Snižuje závislosti balíčků s project.json"
description: "Snížení závislosti balíčků, při vytváření obsahu na základě project.json knihovny."
keywords: "Rozhraní .NET, .NET core"
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 916251e3-87f9-4eee-81ec-94076215e6fa
ms.workload: dotnetcore
ms.openlocfilehash: 858fc77d9652bfa59ed0bb3159260f40c76156a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Snižuje závislosti balíčků s project.json

Tento článek popisuje, co potřebujete vědět o snižuje vaše závislosti balíčků, při vytváření `project.json` knihovny. Na konci tohoto článku se dozvíte, jak vytvořit knihovnu tak, že používá jenom závislosti, které potřebuje. 

## <a name="why-its-important"></a>Proč je důležité

.NET core je produkt skládá z balíčků NuGet.  Je nezbytné balíček [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), které se balíček NuGet skládá z dalších balíčků.  Poskytuje sadu balíčky, které zaručeně pracovat na více implementace rozhraní .NET, například rozhraní .NET Framework, .NET Core a Xamarin/Mono.

Je však dobré šance, že vaše knihovna nebude používat každý jeden balíček, které obsahuje.  Při vytváření knihovny a distribuci přes NuGet, je osvědčeným postupem "trim" závislostmi dolů jenom balíčky skutečně používáte.  Výsledkem je menší celkové nároky na balíčky NuGet.

## <a name="how-to-do-it"></a>Jak to udělat

V současné době není žádná oficiální `dotnet` příkaz, který ořízne balíček odkazuje.  Místo toho budete muset provést ručně.  Obecný postup vypadá takto:

1. Referenční dokumentace `NETStandard.Library` verze `1.6.0` v `dependencies` část vaší `project.json`.
2. Obnovení balíčků s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) z příkazového řádku.
3. Zkontrolujte `project.lock.json` souboru a najděte `NETSTandard.Library` části.  Je na začátku souboru.
4. Zkopírujte všechny balíčky uvedené v části `dependencies`.
5. Odeberte `.NETStandard.Library` odkazovat a nahraďte ji metodou zkopírovaný balíčky.
6. Odeberte odkazy na balíčky, které nepotřebujete.


Můžete zjistit balíčky, které nepotřebujete pomocí jedné z následujících způsobů:

1. Zkušební verze a došlo k chybě.  To zahrnuje odstranění balíčku, obnovení, zobrazuje, pokud vaše knihovna stále zkompiluje a opakováním tohoto procesu.
2. Pomocí některého nástroje, jako třeba [ILSpy](http://ilspy.net) nebo [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) k zobrazení náhledu odkazy na zjistit, co váš kód ve skutečnosti používá.  Potom můžete odebrat balíčky, které si odpovídají typy, které používáte.

## <a name="example"></a>Příklad 

Představte si, že jste napsali jste knihovnu, která poskytuje další funkce pro obecné typy kolekcí.  Tuto knihovnu by bylo potřeba závisí na balíčky, jako `System.Collections`, ale vůbec záviset na balíčky, jako `System.Net.Http`.  Jako takový bylo by dobré oříznout závislosti balíčků dolů co tato knihovna je požadován, pouze!

Abyste mohli trim této knihovny, spusťte s `project.json` souboru a přidejte odkaz na `NETStandard.Library` verze `1.6.0`.

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

V dalším kroku obnovení balíčků s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)), zkontrolujte `project.lock.json` souboru a najít všechny balíčky obnovit pro `NETSTandard.Library`.

Zde je v jaké v příslušné části `project.lock.json` soubor vypadá jako při cílení na `netstandard1.0`:

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

Zkopírujte přes odkazy na balíček do `dependencies` části knihovně `project.json` souboru, nahraďte `NETStandard.Library` odkaz:

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

To je velmi velký balíčky, řadu které který určitě nejsou potřebné pro rozšíření typy kolekcí.  Můžete odebrat balíčky ručně nebo pomocí nástroje, jako například [ILSpy](http://ilspy.net) nebo [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) používá k identifikaci, který ve skutečnosti balíčků kódu.

Zde je, jak může vypadat oříznutý balíčku:

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

Teď má menší nároky než pokud měl závisí na `NETStandard.Library` metapackage.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]