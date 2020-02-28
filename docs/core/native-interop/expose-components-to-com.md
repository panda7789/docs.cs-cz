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
ms.openlocfilehash: 301177113f67748b62ea2686615cfe5378fdc2fd
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157541"
---
# <a name="exposing-net-core-components-to-com"></a>Vystavení součástí .NET Core pro COM

V .NET Core se proces pro vystavování objektů .NET do modelu COM významně zjednodušil v porovnání s .NET Framework. Následující postup vás provede postupem, jak vystavit třídu modelu COM. V tomto kurzu získáte informace o následujících postupech:

- Zveřejňuje třídu modelu COM z .NET Core.
- Vygenerujte server COM jako součást sestavení knihovny .NET Core.
- Automatické generování manifestu souběžného serveru pro model COM bez registru.

## <a name="prerequisites"></a>Předpoklady

- Nainstalujte [sadu .NET Core 3,0 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.

## <a name="create-the-library"></a>Vytvoření knihovny

Prvním krokem je vytvoření knihovny.

1. Vytvořte novou složku a v této složce spusťte následující příkaz:

    ```dotnetcli
    dotnet new classlib
    ```

2. Otevřete `Class1.cs`.
3. Do horní části souboru přidejte `using System.Runtime.InteropServices;`.
4. Vytvořte rozhraní s názvem `IServer`. Příklad:

   [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]

5. Přidejte atribut `[Guid("<IID>")]` do rozhraní s identifikátorem GUID rozhraní pro rozhraní modelu COM, které implementujete. například `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Všimněte si, že tento identifikátor GUID musí být jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní pro COM. V aplikaci Visual Studio můžete vygenerovat GUID tak, že kliknete na nástroje > vytvořit GUID a otevřete nástroj vytvořit GUID.
6. Přidejte atribut `[InterfaceType]` do rozhraní a určete, jaká základní rozhraní COM by měla vaše rozhraní implementovat.
7. Vytvořte třídu s názvem `Server`, která implementuje `IServer`.
8. Přidejte atribut `[Guid("<CLSID>")]` do třídy s identifikátorem GUID třídy pro třídu COM, kterou implementujete. například `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Stejně jako u identifikátoru GUID rozhraní musí být tento identifikátor GUID jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní modelu COM.
9. Přidejte atribut `[ComVisible(true)]` do rozhraní i do třídy.

> [!IMPORTANT]
> Na rozdíl od .NET Framework vyžaduje .NET Core zadání identifikátoru CLSID libovolné třídy, kterou chcete aktivovatelné prostřednictvím modelu COM.

## <a name="generate-the-com-host"></a>Generování hostitele COM

1. Otevřete `.csproj` soubor projektu a přidejte `<EnableComHosting>true</EnableComHosting>` dovnitř značky `<PropertyGroup></PropertyGroup>`.
2. Sestavte projekt.

Výsledný výstup bude mít `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` a soubor `ProjectName.comhost.dll`.

## <a name="register-the-com-host-for-com"></a>Registrace hostitele COM pro COM

Otevřete příkazový řádek se zvýšenými oprávněními a spusťte `regsvr32 ProjectName.comhost.dll`. Tím zaregistrujete všechny vystavené objekty .NET pomocí modelu COM.

## <a name="enabling-regfree-com"></a>Povolení RegFree COM

1. Otevřete `.csproj` soubor projektu a přidejte `<EnableRegFreeCom>true</EnableRegFreeCom>` dovnitř značky `<PropertyGroup></PropertyGroup>`.
2. Sestavte projekt.

Výsledný výstup teď bude mít taky soubor `ProjectName.X.manifest`. Tento soubor je souběžný manifest pro použití s modelem COM bez registru.

## <a name="sample"></a>Ukázka

V úložišti dotnet/Samples na GitHubu je plně funkční [Ukázka serveru com](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) .

## <a name="additional-notes"></a>Další poznámky

Na rozdíl od .NET Framework neexistuje žádná podpora v .NET Core pro generování knihovny typů COM (TLB) ze sestavení .NET Core. Pokyny jsou buď k ručnímu zápisu souboru IDL, nebo C/C++ hlavičku pro nativní deklarace rozhraní com.

Kromě toho mají při načítání .NET Framework a .NET Core do stejného procesu diagnostické omezení. Primární omezení je ladění spravovaných komponent, protože není možné současně ladit .NET Framework i .NET Core. Kromě toho tyto dvě instance modulu runtime nesdílejí spravovaná sestavení. To znamená, že není možné sdílet skutečné typy .NET napříč dvěma moduly runtime a místo toho musí být všechny interakce omezeny na vystavené kontrakty COM rozhraní.
