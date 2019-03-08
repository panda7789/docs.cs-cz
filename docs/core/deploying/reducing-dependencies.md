---
title: Omezení závislosti balíčku s project.json
description: Omezte závislosti balíčků, při vytváření knihovny project.json založené.
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 9d4f9d7f6e7a736b7d07062f3cd31d6f45176cb1
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674962"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Omezení závislosti balíčku s project.json

Tento článek popisuje, co potřebujete vědět o snižování závislosti balíčků při vytváření `project.json` knihovny. Na konci tohoto článku se dozvíte, jak sestavit knihovnu tak, aby používal jenom závislosti, které potřebuje.

## <a name="why-its-important"></a>Proč je důležité

.NET core je produkt tvořené balíčky NuGet.  Základní balíček je [. NETStandard.Library Microsoft.aspnetcore.all](https://www.nuget.org/packages/NETStandard.Library), který se balíček NuGet skládá z dalších balíčků.  To vám poskytuje sadu balíčků, které jsou zaručeny pracovat na více implementací rozhraní .NET, jako je například rozhraní .NET Framework, .NET Core a Xamarin/Mono.

Je však vhodné šance, že vaše knihovna nebudeme používat každý jeden balíček, který obsahuje.  Při vytváření knihovny a jejich distribuci přes NuGet, je osvědčeným postupem "trim" závislostí dolů pouze balíčky skutečně využíváte.  Výsledkem je menší celkové nároky na místo pro balíčky NuGet.

## <a name="how-to-do-it"></a>Jak na to

V současné době neexistuje žádné oficiální `dotnet` příkazu, který ořízne odkazy na balíček.  Místo toho budete muset provést ručně.  Obecný postup vypadá takto:

1. Referenční dokumentace `NETStandard.Library` verze `1.6.0` v `dependencies` část vaší `project.json`.
2. Obnovení balíčků s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) z příkazového řádku.
3. Zkontrolujte `project.lock.json` souborů a vyhledejte `NETStandard.Library` oddílu.  Je na začátku souboru.
4. Zkopírujte všechny balíčky uvedené v části `dependencies`.
5. Odeberte `.NETStandard.Library` odkazovat a nahraďte ji metodou zkopírovaný balíčky.
6. Odeberte odkazy na balíčky, které nepotřebujete.

Můžete zjistit, které balíčky, není nutné pomocí jedné z následujících způsobů:

1. Došlo k chybě a zkušební verze.  To zahrnuje odebrání balíčku, obnovení, zobrazuje, pokud se stále zkompiluje knihovnu a opakováním tohoto procesu.
2. Pomocí nástroje, jako například [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) a prohlédněte si odkazy, které chcete zjistit, co váš kód skutečně.  Následně můžete odebrat balíčky, které neodpovídají na typy, které používáte.

## <a name="example"></a>Příklad

Představte si, že jste napsali knihovnu, která poskytuje další funkce do obecných typů kolekce.  Tyto knihovny by bylo potřeba závisí na balíčky, jako `System.Collections`, ale vůbec záviset na balíčky, jako `System.Net.Http`.  V důsledku toho by bylo dobré mají být odebrány závislosti balíčků dolů pouze co tuto knihovnu požadovanou!

Oříznout této knihovny, začínat `project.json` a přidejte odkaz na `NETStandard.Library` verze `1.6.0`.

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

V dalším kroku obnovit balíčky s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)), zkontrolujte `project.lock.json` souboru a vyhledání všech balíčků byl obnoven pro `NETStandard.Library`.

Zde je co příslušné části v `project.lock.json` souboru vypadá podobně jako při cílení na `netstandard1.0`:

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

V dalším kroku zkopírujte odkazy na balíčky do `dependencies` části knihovny `project.json` souboru, nahradí `NETStandard.Library` odkaz:

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

To je poměrně velké balíčky, z nichž mnohá jistě nejsou potřebné pro rozšíření typy kolekcí.  Můžete odebrat balíčky, které ručně nebo pomocí nástroje, jako [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) používá k identifikaci, který ve skutečnosti balíčky kódu.

Tady je oříznutý balíčku by mohla vypadat:

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

Teď má menší nároky na místo než pokud měl závisí na `NETStandard.Library` Microsoft.aspnetcore.all.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
