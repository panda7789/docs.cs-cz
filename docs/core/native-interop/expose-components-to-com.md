---
title: Vystavení součástí .NET Core pro COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 33574eeac5b1f7aa2067b1974f3f2e68fb22e8ff
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631128"
---
# <a name="exposing-net-core-components-to-com"></a>Vystavení součástí .NET Core pro COM

V .NET Core se proces pro vystavování objektů .NET do modelu COM významně zjednodušil v porovnání s .NET Framework. Následující postup vás provede postupem, jak vystavit třídu modelu COM. V tomto kurzu se dozvíte, jak:

- Zveřejňuje třídu modelu COM z .NET Core.
- Vygenerujte server COM jako součást sestavení knihovny .NET Core.
- Automatické generování manifestu souběžného serveru pro model COM bez registru.

## <a name="prerequisites"></a>Požadavky

- Nainstalujte [sadu .NET Core 3,0 Preview 7 SDK](https://www.microsoft.com/net/core) nebo novější verzi.

## <a name="create-the-library"></a>Vytvoření knihovny

Prvním krokem je vytvoření knihovny.

1. Vytvořte novou složku a v této složce spusťte `dotnet new classlib`.
2. Otevřít `Class1.cs`.
3. Přidejte `using System.Runtime.InteropServices;` na začátek souboru.
4. Vytvořte rozhraní s názvem `IServer`. Například:[!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]
5. `[Guid("<IID>")]` Přidejte atribut do rozhraní s identifikátorem GUID rozhraní pro rozhraní modelu COM, které implementujete. Například, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Všimněte si, že tento identifikátor GUID musí být jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní pro COM. V aplikaci Visual Studio můžete vygenerovat GUID tak, že kliknete na nástroje > vytvořit GUID a otevřete nástroj vytvořit GUID.
6. Přidejte do rozhraní atribut a určete, jaká základní rozhraní com by měla vaše rozhraní implementovat. `[InterfaceType]`
7. Vytvořte třídu s názvem `Server` , která `IServer`implementuje.
8. `[Guid("<CLSID>")]` Přidejte atribut do třídy s identifikátorem GUID třídy pro třídu com, kterou implementujete. Například, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Stejně jako u identifikátoru GUID rozhraní musí být tento identifikátor GUID jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní modelu COM.
9. `[ComVisible(true)]` Přidejte atribut do rozhraní i do třídy.

> [!IMPORTANT]
> Na rozdíl od .NET Framework vyžaduje .NET Core zadání identifikátoru CLSID libovolné třídy, kterou chcete aktivovatelné prostřednictvím modelu COM.

## <a name="generate-the-com-host"></a>Generování hostitele COM

1. Otevřete soubor `<EnableComHosting>true</EnableComHosting>` projektu a přidejte ho dovnitř `<PropertyGroup></PropertyGroup>` tagu. `.csproj`
2. Sestavte projekt.

Výsledný výstup `ProjectName.dll`bude obsahovat soubor `ProjectName.runtimeconfig.json` , `ProjectName.deps.json`a `ProjectName.comhost.dll` .

## <a name="register-the-com-host-for-com"></a>Registrace hostitele COM pro COM

Otevřete příkazový řádek se zvýšenými oprávněními `regsvr32 ProjectName.comhost.dll`a spusťte příkaz. Tím zaregistrujete všechny vystavené objekty .NET pomocí modelu COM.

## <a name="enabling-regfree-com"></a>Povolení RegFree COM

1. Otevřete soubor `<EnableRegFreeCom>true</EnableRegFreeCom>` projektu a přidejte ho dovnitř `<PropertyGroup></PropertyGroup>` tagu. `.csproj`
2. Sestavte projekt.

Výsledný výstup teď bude mít `ProjectName.X.manifest` i soubor. Tento soubor je souběžný manifest pro použití s modelem COM bez registru.

## <a name="sample"></a>Ukázka

V úložišti dotnet/Samples na GitHubu je plně funkční [Ukázka serveru com](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) .

## <a name="additional-notes"></a>Další poznámky

Na rozdíl od .NET Framework neexistuje žádná podpora v .NET Core pro generování knihovny typů COM (TLB) ze sestavení .NET Core. Buď budete muset ručně napsat soubor IDL nebo C++ hlavičku pro nativní deklarace vašich rozhraní.

Kromě toho se nepodporují načítání .NET Framework a .NET Core do stejného procesu a jako výsledek načtení serveru COM .NET Core do procesu klienta .NET Framework COM nebo naopak není podporována.
