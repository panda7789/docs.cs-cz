---
title: Zmenšení závislostí balíčku pomocí Project. JSON
description: Zmenšení závislostí balíčku při vytváření knihoven založených na Project. JSON.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740824"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Zmenšení závislostí balíčku pomocí Project. JSON

Tento článek popisuje, co potřebujete znát o omezení závislostí balíčku při vytváření `project.json`ch knihoven. Na konci tohoto článku se naučíte, jak vytvořit knihovnu tak, aby používala pouze závislosti, které potřebuje.

## <a name="why-its-important"></a>Proč je důležité

.NET Core je produkt vytvořený z balíčků NuGet.  Základní balíček je [. NETStandard. Library Metapackage](https://www.nuget.org/packages/NETStandard.Library), což je balíček NuGet tvořený jinými balíčky. Poskytuje sadu balíčků, u kterých je zaručena práce s více implementacemi .NET, například .NET Framework, .NET Core a Xamarin/mono.

Existuje však velmi pravděpodobné, že vaše knihovna nebude používat každý balíček, který obsahuje.  Když vytváříte knihovnu a distribuujete ji přes NuGet, je osvědčeným postupem, jak vyčistit závislosti až na balíčky, které skutečně používáte.  Výsledkem je menší celkové nároky na balíčky NuGet.

## <a name="how-to-do-it"></a>Jak na to

V současné době není k dispozici žádný oficiální `dotnet` příkaz, který ořízne odkazy na balíčky.  Místo toho ho budete muset provést ručně.  Obecný proces vypadá takto:

1. Referenční `NETStandard.Library` verze `1.6.0` v části `dependencies` `project.json`.
2. Obnovte balíčky pomocí `dotnet restore` ([Viz poznámku](#dotnet-restore-note)) z příkazového řádku.
3. Zkontrolujte soubor `project.lock.json` a najděte oddíl `NETStandard.Library`.  Je poblíž začátku souboru.
4. Zkopírujte všechny uvedené balíčky pod `dependencies`.
5. Odeberte odkaz na `.NETStandard.Library` a nahraďte ho zkopírovanými balíčky.
6. Odeberte odkazy na balíčky, které nepotřebujete.

Balíčky, které nepotřebujete, můžete zjistit jedním z následujících způsobů:

1. Zkušební verze a chyba. To zahrnuje odebrání balíčku, obnovení a zjištění, zda je vaše knihovna stále zkompilována, a zopakování tohoto procesu.
2. Použití nástroje, jako je [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [reflektor .NET](https://www.red-gate.com/products/dotnet-development/reflector) , k prohlížení odkazů k zobrazení, co váš kód skutečně používá. Pak můžete odebrat balíčky, které neodpovídají typům, které používáte.

## <a name="example"></a>Příklad

Představte si, že jste napsali knihovnu, která poskytuje další funkce pro obecné typy kolekcí. Taková knihovna by musela záviset na balíčcích, jako je `System.Collections`, ale nemusí být vůbec závislé na balíčcích, jako je `System.Net.Http`. V takovém případě by bylo vhodné oříznout závislosti balíčků a snížit tak pouze to, co tato knihovna vyžaduje.

Chcete-li tuto knihovnu oříznout, začněte se souborem `project.json` a přidejte odkaz na verzi `NETStandard.Library` `1.6.0`.

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

V dalším kroku obnovíte balíčky pomocí `dotnet restore` ([Viz poznámku](#dotnet-restore-note)), zkontrolujete soubor `project.lock.json` a vyhledáte všechny balíčky obnovené pro `NETStandard.Library`.

V takovém případě se v souboru `project.lock.json` zdá, že při cílení `netstandard1.0`vypadá nějak takto:

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

V dalším kroku zkopírujte odkazy na balíček do oddílu `dependencies` `project.json` souboru knihovny a nahraďte `NETStandard.Library` odkaz:

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

To je poměrně velké množství balíčků, z nichž mnoho není nezbytné pro rozšíření typů kolekcí.  Můžete buď odebrat balíčky ručně, nebo použít nástroj, jako je [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [reflektor .NET](https://www.red-gate.com/products/dotnet-development/reflector/) , k určení balíčků, které váš kód skutečně používá.

V tomto příkladu může být oříznutý balíček vypadat takto:

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

Teď má menší nároky, než kdyby byla závislá na `NETStandard.Library` Metapackage.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
