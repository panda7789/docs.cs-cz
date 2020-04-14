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
ms.openlocfilehash: 17d85b9e9734fae0bb69f94da8c08669216ab0ae
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242865"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="605b3-104">Vystavení komponent .NET Core modelu COM</span><span class="sxs-lookup"><span data-stu-id="605b3-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="605b3-105">V .NET Core proces pro vystavení objektů .NET com byl výrazně zjednodušen ve srovnání s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="605b3-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="605b3-106">Následující proces vás provede, jak vystavit třídu com.</span><span class="sxs-lookup"><span data-stu-id="605b3-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="605b3-107">V tomto kurzu získáte informace o následujících postupech:</span><span class="sxs-lookup"><span data-stu-id="605b3-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="605b3-108">Vystavit třídy com z .NET Core.</span><span class="sxs-lookup"><span data-stu-id="605b3-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="605b3-109">Vygenerujte server COM jako součást vytváření knihovny .NET Core.</span><span class="sxs-lookup"><span data-stu-id="605b3-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="605b3-110">Automaticky generovat manifest serveru vedle sebe pro com bez registru.</span><span class="sxs-lookup"><span data-stu-id="605b3-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="605b3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="605b3-111">Prerequisites</span></span>

- <span data-ttu-id="605b3-112">Nainstalujte [sada .NET Core 3.0 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="605b3-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="605b3-113">Vytvoření knihovny</span><span class="sxs-lookup"><span data-stu-id="605b3-113">Create the library</span></span>

<span data-ttu-id="605b3-114">Prvním krokem je vytvoření knihovny.</span><span class="sxs-lookup"><span data-stu-id="605b3-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="605b3-115">Vytvořte novou složku a v této složce spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="605b3-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="605b3-116">Otevřete `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="605b3-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="605b3-117">Přidat `using System.Runtime.InteropServices;` do horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="605b3-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="605b3-118">Vytvořte rozhraní `IServer`s názvem .</span><span class="sxs-lookup"><span data-stu-id="605b3-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="605b3-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="605b3-119">For example:</span></span>

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

5. <span data-ttu-id="605b3-120">Přidejte `[Guid("<IID>")]` atribut do rozhraní pomocí identifikátoru GUID rozhraní pro rozhraní COM, které implementujete.</span><span class="sxs-lookup"><span data-stu-id="605b3-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="605b3-121">Například, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="605b3-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="605b3-122">Všimněte si, že tento identifikátor GUID musí být jedinečný, protože je jediným identifikátorem tohoto rozhraní pro kom.</span><span class="sxs-lookup"><span data-stu-id="605b3-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="605b3-123">V sadě Visual Studio můžete vygenerovat identifikátor GUID tak, že přejdete na nástroje nástrojů > vytvořit identifikátor GUID a otevřete nástroj Vytvoření identifikátoru GUID.</span><span class="sxs-lookup"><span data-stu-id="605b3-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="605b3-124">Přidejte `[InterfaceType]` atribut do rozhraní a určete, jaká základní rozhraní COM by rozhraní mělo implementovat.</span><span class="sxs-lookup"><span data-stu-id="605b3-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="605b3-125">Vytvořte třídu s názvem, `Server` která implementuje `IServer`.</span><span class="sxs-lookup"><span data-stu-id="605b3-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="605b3-126">Přidejte `[Guid("<CLSID>")]` atribut do třídy pomocí identifikátoru identifikátoru třídy GUID pro třídu COM, kterou implementujete.</span><span class="sxs-lookup"><span data-stu-id="605b3-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="605b3-127">Například, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="605b3-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="605b3-128">Stejně jako u identifikátoru GUID rozhraní musí být tento identifikátor GUID jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní pro kom.</span><span class="sxs-lookup"><span data-stu-id="605b3-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="605b3-129">Přidejte `[ComVisible(true)]` atribut rozhraní a třídy.</span><span class="sxs-lookup"><span data-stu-id="605b3-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="605b3-130">Na rozdíl od rozhraní .NET Framework vyžaduje rozhraní .NET Core zadání clsid libovolné třídy, kterou chcete aktivovat prostřednictvím com.</span><span class="sxs-lookup"><span data-stu-id="605b3-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="605b3-131">Generovat hostitele COM</span><span class="sxs-lookup"><span data-stu-id="605b3-131">Generate the COM host</span></span>

1. <span data-ttu-id="605b3-132">Otevřete `.csproj` soubor projektu `<EnableComHosting>true</EnableComHosting>` a `<PropertyGroup></PropertyGroup>` přidejte ji do značky.</span><span class="sxs-lookup"><span data-stu-id="605b3-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="605b3-133">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="605b3-133">Build the project.</span></span>

<span data-ttu-id="605b3-134">Výsledný výstup bude mít `ProjectName.dll` `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` `ProjectName.comhost.dll` a soubor.</span><span class="sxs-lookup"><span data-stu-id="605b3-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="605b3-135">Registrace hostitele COM pro kom.</span><span class="sxs-lookup"><span data-stu-id="605b3-135">Register the COM host for COM</span></span>

<span data-ttu-id="605b3-136">Otevřete příkazový řádek `regsvr32 ProjectName.comhost.dll`se zvýšenými oprávněními a spusťte .</span><span class="sxs-lookup"><span data-stu-id="605b3-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="605b3-137">To bude registrovat všechny exponované objekty .NET s COM.</span><span class="sxs-lookup"><span data-stu-id="605b3-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="605b3-138">Povolení regfree COM</span><span class="sxs-lookup"><span data-stu-id="605b3-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="605b3-139">Otevřete `.csproj` soubor projektu `<EnableRegFreeCom>true</EnableRegFreeCom>` a `<PropertyGroup></PropertyGroup>` přidejte ji do značky.</span><span class="sxs-lookup"><span data-stu-id="605b3-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="605b3-140">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="605b3-140">Build the project.</span></span>

<span data-ttu-id="605b3-141">Výsledný výstup bude nyní mít `ProjectName.X.manifest` také soubor.</span><span class="sxs-lookup"><span data-stu-id="605b3-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="605b3-142">Tento soubor je manifest vedle sebe pro použití s com bez registru.</span><span class="sxs-lookup"><span data-stu-id="605b3-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="605b3-143">Ukázka</span><span class="sxs-lookup"><span data-stu-id="605b3-143">Sample</span></span>

<span data-ttu-id="605b3-144">V úložišti dotnet/samples na GitHubu je ukázka plně [funkčního serveru COM.](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)</span><span class="sxs-lookup"><span data-stu-id="605b3-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="605b3-145">Další poznámky</span><span class="sxs-lookup"><span data-stu-id="605b3-145">Additional notes</span></span>

<span data-ttu-id="605b3-146">Na rozdíl od rozhraní .NET Framework neexistuje v rozhraní .NET Core žádná podpora pro generování knihovny typů COM (TLB) ze sestavení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="605b3-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="605b3-147">Pokyny je buď ručně napsat soubor IDL nebo hlavičky C/C++ pro nativní deklarace rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="605b3-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="605b3-148">[Samostatná nasazení](../deploying/index.md#publish-self-contained) součástí modelu COM nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="605b3-148">[Self-contained deployments](../deploying/index.md#publish-self-contained) of COM components are not supported.</span></span> <span data-ttu-id="605b3-149">Podporována jsou pouze nasazení součástí modelu COM [závislá na modulu runtime.](../deploying/index.md#publish-runtime-dependent)</span><span class="sxs-lookup"><span data-stu-id="605b3-149">Only [runtime-dependent deployments](../deploying/index.md#publish-runtime-dependent) of COM components are supported.</span></span>

<span data-ttu-id="605b3-150">Navíc načítání rozhraní .NET Framework a .NET Core do stejného procesu má diagnostická omezení.</span><span class="sxs-lookup"><span data-stu-id="605b3-150">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="605b3-151">Primárním omezením je ladění spravovaných součástí, protože není možné ladit rozhraní .NET Framework i .NET Core současně.</span><span class="sxs-lookup"><span data-stu-id="605b3-151">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="605b3-152">Kromě toho dvě instance runtime nesdílejí spravovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="605b3-152">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="605b3-153">To znamená, že není možné sdílet skutečné typy .NET napříč dvěma moduly runtimes a místo toho musí být všechny interakce omezeny na vystavené kontrakty rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="605b3-153">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
