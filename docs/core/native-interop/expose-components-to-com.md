---
title: Vystavení komponent .NET Core modelu COM
description: Tento kurz ukazuje, jak vystavit třídu com z .NET Core. Generujete server COM a manifest serveru vedle sebe pro server COM bez registru.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 98d303c99693a8aadb23da509a700772db69c0e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146655"
---
# <a name="exposing-net-core-components-to-com"></a>Vystavení komponent .NET Core modelu COM

V .NET Core proces pro vystavení objektů .NET com byl výrazně zjednodušen ve srovnání s rozhraním .NET Framework. Následující proces vás provede, jak vystavit třídu com. V tomto kurzu získáte informace o následujících postupech:

- Vystavit třídy com z .NET Core.
- Vygenerujte server COM jako součást vytváření knihovny .NET Core.
- Automaticky generovat manifest serveru vedle sebe pro com bez registru.

## <a name="prerequisites"></a>Požadavky

- Nainstalujte [sada .NET Core 3.0 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.

## <a name="create-the-library"></a>Vytvoření knihovny

Prvním krokem je vytvoření knihovny.

1. Vytvořte novou složku a v této složce spusťte následující příkaz:

    ```dotnetcli
    dotnet new classlib
    ```

2. Otevřete `Class1.cs`.
3. Přidat `using System.Runtime.InteropServices;` do horní části souboru.
4. Vytvořte rozhraní `IServer`s názvem . Například:

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. Přidejte `[Guid("<IID>")]` atribut do rozhraní pomocí identifikátoru GUID rozhraní pro rozhraní COM, které implementujete. Například, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Všimněte si, že tento identifikátor GUID musí být jedinečný, protože je jediným identifikátorem tohoto rozhraní pro kom. V sadě Visual Studio můžete vygenerovat identifikátor GUID tak, že přejdete na nástroje nástrojů > vytvořit identifikátor GUID a otevřete nástroj Vytvoření identifikátoru GUID.
6. Přidejte `[InterfaceType]` atribut do rozhraní a určete, jaká základní rozhraní COM by rozhraní mělo implementovat.
7. Vytvořte třídu s názvem, `Server` která implementuje `IServer`.
8. Přidejte `[Guid("<CLSID>")]` atribut do třídy pomocí identifikátoru identifikátoru třídy GUID pro třídu COM, kterou implementujete. Například, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Stejně jako u identifikátoru GUID rozhraní musí být tento identifikátor GUID jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní pro kom.
9. Přidejte `[ComVisible(true)]` atribut rozhraní a třídy.

> [!IMPORTANT]
> Na rozdíl od rozhraní .NET Framework vyžaduje rozhraní .NET Core zadání clsid libovolné třídy, kterou chcete aktivovat prostřednictvím com.

## <a name="generate-the-com-host"></a>Generovat hostitele COM

1. Otevřete `.csproj` soubor projektu `<EnableComHosting>true</EnableComHosting>` a `<PropertyGroup></PropertyGroup>` přidejte ji do značky.
2. Sestavte projekt.

Výsledný výstup bude mít `ProjectName.dll` `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` `ProjectName.comhost.dll` a soubor.

## <a name="register-the-com-host-for-com"></a>Registrace hostitele COM pro kom.

Otevřete příkazový řádek `regsvr32 ProjectName.comhost.dll`se zvýšenými oprávněními a spusťte . To bude registrovat všechny exponované objekty .NET s COM.

## <a name="enabling-regfree-com"></a>Povolení regfree COM

1. Otevřete `.csproj` soubor projektu `<EnableRegFreeCom>true</EnableRegFreeCom>` a `<PropertyGroup></PropertyGroup>` přidejte ji do značky.
2. Sestavte projekt.

Výsledný výstup bude nyní mít `ProjectName.X.manifest` také soubor. Tento soubor je manifest vedle sebe pro použití s com bez registru.

## <a name="sample"></a>Ukázka

V úložišti dotnet/samples na GitHubu je ukázka plně [funkčního serveru COM.](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)

## <a name="additional-notes"></a>Další poznámky

Na rozdíl od rozhraní .NET Framework neexistuje v rozhraní .NET Core žádná podpora pro generování knihovny typů COM (TLB) ze sestavení .NET Core. Pokyny je buď ručně napsat soubor IDL nebo hlavičky C/C++ pro nativní deklarace rozhraní COM.

Navíc načítání rozhraní .NET Framework a .NET Core do stejného procesu má diagnostická omezení. Primárním omezením je ladění spravovaných součástí, protože není možné ladit rozhraní .NET Framework i .NET Core současně. Kromě toho dvě instance runtime nesdílejí spravovaná sestavení. To znamená, že není možné sdílet skutečné typy .NET napříč dvěma moduly runtimes a místo toho musí být všechny interakce omezeny na vystavené kontrakty rozhraní COM.
