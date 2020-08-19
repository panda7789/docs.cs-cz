---
title: Vystavení součástí .NET Core pro COM
description: V tomto kurzu se dozvíte, jak vystavit třídu modelu COM z .NET Core. Vygenerujete server COM a souběžný manifest serveru pro model COM bez registru.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 346776ebae3a6077fd39f26d5bd19d599d163db2
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608340"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="5e849-104">Vystavení součástí .NET Core pro COM</span><span class="sxs-lookup"><span data-stu-id="5e849-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="5e849-105">V .NET Core se proces pro vystavování objektů .NET do modelu COM významně zjednodušil v porovnání s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e849-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="5e849-106">Následující postup vás provede postupem, jak vystavit třídu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5e849-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="5e849-107">V tomto kurzu získáte informace o následujících postupech:</span><span class="sxs-lookup"><span data-stu-id="5e849-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="5e849-108">Zveřejňuje třídu modelu COM z .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e849-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="5e849-109">Vygenerujte server COM jako součást sestavení knihovny .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e849-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="5e849-110">Automatické generování manifestu souběžného serveru pro model COM bez registru.</span><span class="sxs-lookup"><span data-stu-id="5e849-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e849-111">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="5e849-111">Prerequisites</span></span>

- <span data-ttu-id="5e849-112">Nainstalujte [sadu .NET Core 3,0 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="5e849-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="5e849-113">Vytvoření knihovny</span><span class="sxs-lookup"><span data-stu-id="5e849-113">Create the library</span></span>

<span data-ttu-id="5e849-114">Prvním krokem je vytvoření knihovny.</span><span class="sxs-lookup"><span data-stu-id="5e849-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="5e849-115">Vytvořte novou složku a v této složce spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5e849-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="5e849-116">Otevřete `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="5e849-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="5e849-117">Přidejte `using System.Runtime.InteropServices;` na začátek souboru.</span><span class="sxs-lookup"><span data-stu-id="5e849-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="5e849-118">Vytvořte rozhraní s názvem `IServer` .</span><span class="sxs-lookup"><span data-stu-id="5e849-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="5e849-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5e849-119">For example:</span></span>

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

5. <span data-ttu-id="5e849-120">Přidejte `[Guid("<IID>")]` atribut do rozhraní s identifikátorem GUID rozhraní pro rozhraní modelu COM, které implementujete.</span><span class="sxs-lookup"><span data-stu-id="5e849-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="5e849-121">Například, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="5e849-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="5e849-122">Všimněte si, že tento identifikátor GUID musí být jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní pro COM.</span><span class="sxs-lookup"><span data-stu-id="5e849-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="5e849-123">V aplikaci Visual Studio můžete vygenerovat GUID tak, že kliknete na nástroje > vytvořit GUID a otevřete nástroj vytvořit GUID.</span><span class="sxs-lookup"><span data-stu-id="5e849-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="5e849-124">Přidejte `[InterfaceType]` do rozhraní atribut a určete, jaká základní rozhraní com by měla vaše rozhraní implementovat.</span><span class="sxs-lookup"><span data-stu-id="5e849-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="5e849-125">Vytvořte třídu s názvem `Server` , která implementuje `IServer` .</span><span class="sxs-lookup"><span data-stu-id="5e849-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="5e849-126">Přidejte `[Guid("<CLSID>")]` atribut do třídy s identifikátorem GUID třídy pro třídu com, kterou implementujete.</span><span class="sxs-lookup"><span data-stu-id="5e849-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="5e849-127">Například, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="5e849-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="5e849-128">Stejně jako u identifikátoru GUID rozhraní musí být tento identifikátor GUID jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5e849-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="5e849-129">Přidejte `[ComVisible(true)]` atribut do rozhraní i do třídy.</span><span class="sxs-lookup"><span data-stu-id="5e849-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e849-130">Na rozdíl od .NET Framework vyžaduje .NET Core zadání identifikátoru CLSID libovolné třídy, kterou chcete aktivovatelné prostřednictvím modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5e849-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="5e849-131">Generování hostitele COM</span><span class="sxs-lookup"><span data-stu-id="5e849-131">Generate the COM host</span></span>

1. <span data-ttu-id="5e849-132">Otevřete `.csproj` soubor projektu a přidejte ho `<EnableComHosting>true</EnableComHosting>` dovnitř `<PropertyGroup></PropertyGroup>` tagu.</span><span class="sxs-lookup"><span data-stu-id="5e849-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="5e849-133">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="5e849-133">Build the project.</span></span>

<span data-ttu-id="5e849-134">Výsledný výstup bude obsahovat `ProjectName.dll` `ProjectName.deps.json` soubor, `ProjectName.runtimeconfig.json` a `ProjectName.comhost.dll` .</span><span class="sxs-lookup"><span data-stu-id="5e849-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="5e849-135">Registrace hostitele COM pro COM</span><span class="sxs-lookup"><span data-stu-id="5e849-135">Register the COM host for COM</span></span>

<span data-ttu-id="5e849-136">Otevřete příkazový řádek se zvýšenými oprávněními a spusťte příkaz `regsvr32 ProjectName.comhost.dll` .</span><span class="sxs-lookup"><span data-stu-id="5e849-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="5e849-137">Tím zaregistrujete všechny vystavené objekty .NET pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5e849-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="5e849-138">Povolení RegFree COM</span><span class="sxs-lookup"><span data-stu-id="5e849-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="5e849-139">Otevřete `.csproj` soubor projektu a přidejte ho `<EnableRegFreeCom>true</EnableRegFreeCom>` dovnitř `<PropertyGroup></PropertyGroup>` tagu.</span><span class="sxs-lookup"><span data-stu-id="5e849-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="5e849-140">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="5e849-140">Build the project.</span></span>

<span data-ttu-id="5e849-141">Výsledný výstup teď bude mít i `ProjectName.X.manifest` soubor.</span><span class="sxs-lookup"><span data-stu-id="5e849-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="5e849-142">Tento soubor je souběžný manifest pro použití s modelem COM bez registru.</span><span class="sxs-lookup"><span data-stu-id="5e849-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="5e849-143">Ukázka</span><span class="sxs-lookup"><span data-stu-id="5e849-143">Sample</span></span>

<span data-ttu-id="5e849-144">V úložišti dotnet/Samples na GitHubu je plně funkční [Ukázka serveru com](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) .</span><span class="sxs-lookup"><span data-stu-id="5e849-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="5e849-145">Další poznámky</span><span class="sxs-lookup"><span data-stu-id="5e849-145">Additional notes</span></span>

<span data-ttu-id="5e849-146">Na rozdíl od .NET Framework neexistuje žádná podpora v .NET Core pro generování knihovny typů COM (TLB) ze sestavení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e849-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="5e849-147">Pokyny jsou buď k ručnímu zápisu souboru IDL nebo záhlaví jazyka C/C++ pro nativní deklarace rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="5e849-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="5e849-148">[Samostatně obsažená nasazení](../deploying/index.md#publish-self-contained) komponent modelu COM nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="5e849-148">[Self-contained deployments](../deploying/index.md#publish-self-contained) of COM components are not supported.</span></span> <span data-ttu-id="5e849-149">Podporovaná jsou jenom nasazení komponent modelu COM [závislá na rozhraní](../deploying/index.md#publish-framework-dependent) .</span><span class="sxs-lookup"><span data-stu-id="5e849-149">Only [framework-dependent deployments](../deploying/index.md#publish-framework-dependent) of COM components are supported.</span></span>

<span data-ttu-id="5e849-150">Kromě toho mají při načítání .NET Framework a .NET Core do stejného procesu diagnostické omezení.</span><span class="sxs-lookup"><span data-stu-id="5e849-150">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="5e849-151">Primární omezení je ladění spravovaných komponent, protože není možné současně ladit .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e849-151">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="5e849-152">Kromě toho tyto dvě instance modulu runtime nesdílejí spravovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="5e849-152">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="5e849-153">To znamená, že není možné sdílet skutečné typy .NET napříč dvěma moduly runtime a místo toho musí být všechny interakce omezeny na vystavené kontrakty COM rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5e849-153">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
