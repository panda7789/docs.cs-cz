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
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="010c0-102">Vystavení součástí .NET Core pro COM</span><span class="sxs-lookup"><span data-stu-id="010c0-102">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="010c0-103">V .NET Core se proces pro vystavování objektů .NET do modelu COM významně zjednodušil v porovnání s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="010c0-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="010c0-104">Následující postup vás provede postupem, jak vystavit třídu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="010c0-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="010c0-105">V tomto kurzu získáte informace o následujících postupech:</span><span class="sxs-lookup"><span data-stu-id="010c0-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="010c0-106">Zveřejňuje třídu modelu COM z .NET Core.</span><span class="sxs-lookup"><span data-stu-id="010c0-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="010c0-107">Vygenerujte server COM jako součást sestavení knihovny .NET Core.</span><span class="sxs-lookup"><span data-stu-id="010c0-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="010c0-108">Automatické generování manifestu souběžného serveru pro model COM bez registru.</span><span class="sxs-lookup"><span data-stu-id="010c0-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="010c0-109">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="010c0-109">Prerequisites</span></span>

- <span data-ttu-id="010c0-110">Nainstalujte [sadu .NET Core 3,0 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="010c0-110">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="010c0-111">Vytvoření knihovny</span><span class="sxs-lookup"><span data-stu-id="010c0-111">Create the library</span></span>

<span data-ttu-id="010c0-112">Prvním krokem je vytvoření knihovny.</span><span class="sxs-lookup"><span data-stu-id="010c0-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="010c0-113">Vytvořte novou složku a v této složce spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="010c0-113">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="010c0-114">Otevřete `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="010c0-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="010c0-115">Do horní části souboru přidejte `using System.Runtime.InteropServices;`.</span><span class="sxs-lookup"><span data-stu-id="010c0-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="010c0-116">Vytvořte rozhraní s názvem `IServer`.</span><span class="sxs-lookup"><span data-stu-id="010c0-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="010c0-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="010c0-117">For example:</span></span>

   [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]

5. <span data-ttu-id="010c0-118">Přidejte atribut `[Guid("<IID>")]` do rozhraní s identifikátorem GUID rozhraní pro rozhraní modelu COM, které implementujete.</span><span class="sxs-lookup"><span data-stu-id="010c0-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="010c0-119">například `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="010c0-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="010c0-120">Všimněte si, že tento identifikátor GUID musí být jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní pro COM.</span><span class="sxs-lookup"><span data-stu-id="010c0-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="010c0-121">V aplikaci Visual Studio můžete vygenerovat GUID tak, že kliknete na nástroje > vytvořit GUID a otevřete nástroj vytvořit GUID.</span><span class="sxs-lookup"><span data-stu-id="010c0-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="010c0-122">Přidejte atribut `[InterfaceType]` do rozhraní a určete, jaká základní rozhraní COM by měla vaše rozhraní implementovat.</span><span class="sxs-lookup"><span data-stu-id="010c0-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="010c0-123">Vytvořte třídu s názvem `Server`, která implementuje `IServer`.</span><span class="sxs-lookup"><span data-stu-id="010c0-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="010c0-124">Přidejte atribut `[Guid("<CLSID>")]` do třídy s identifikátorem GUID třídy pro třídu COM, kterou implementujete.</span><span class="sxs-lookup"><span data-stu-id="010c0-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="010c0-125">například `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="010c0-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="010c0-126">Stejně jako u identifikátoru GUID rozhraní musí být tento identifikátor GUID jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="010c0-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="010c0-127">Přidejte atribut `[ComVisible(true)]` do rozhraní i do třídy.</span><span class="sxs-lookup"><span data-stu-id="010c0-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="010c0-128">Na rozdíl od .NET Framework vyžaduje .NET Core zadání identifikátoru CLSID libovolné třídy, kterou chcete aktivovatelné prostřednictvím modelu COM.</span><span class="sxs-lookup"><span data-stu-id="010c0-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="010c0-129">Generování hostitele COM</span><span class="sxs-lookup"><span data-stu-id="010c0-129">Generate the COM host</span></span>

1. <span data-ttu-id="010c0-130">Otevřete `.csproj` soubor projektu a přidejte `<EnableComHosting>true</EnableComHosting>` dovnitř značky `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="010c0-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="010c0-131">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="010c0-131">Build the project.</span></span>

<span data-ttu-id="010c0-132">Výsledný výstup bude mít `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` a soubor `ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="010c0-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="010c0-133">Registrace hostitele COM pro COM</span><span class="sxs-lookup"><span data-stu-id="010c0-133">Register the COM host for COM</span></span>

<span data-ttu-id="010c0-134">Otevřete příkazový řádek se zvýšenými oprávněními a spusťte `regsvr32 ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="010c0-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="010c0-135">Tím zaregistrujete všechny vystavené objekty .NET pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="010c0-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="010c0-136">Povolení RegFree COM</span><span class="sxs-lookup"><span data-stu-id="010c0-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="010c0-137">Otevřete `.csproj` soubor projektu a přidejte `<EnableRegFreeCom>true</EnableRegFreeCom>` dovnitř značky `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="010c0-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="010c0-138">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="010c0-138">Build the project.</span></span>

<span data-ttu-id="010c0-139">Výsledný výstup teď bude mít taky soubor `ProjectName.X.manifest`.</span><span class="sxs-lookup"><span data-stu-id="010c0-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="010c0-140">Tento soubor je souběžný manifest pro použití s modelem COM bez registru.</span><span class="sxs-lookup"><span data-stu-id="010c0-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="010c0-141">Ukázka</span><span class="sxs-lookup"><span data-stu-id="010c0-141">Sample</span></span>

<span data-ttu-id="010c0-142">V úložišti dotnet/Samples na GitHubu je plně funkční [Ukázka serveru com](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) .</span><span class="sxs-lookup"><span data-stu-id="010c0-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="010c0-143">Další poznámky</span><span class="sxs-lookup"><span data-stu-id="010c0-143">Additional notes</span></span>

<span data-ttu-id="010c0-144">Na rozdíl od .NET Framework neexistuje žádná podpora v .NET Core pro generování knihovny typů COM (TLB) ze sestavení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="010c0-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="010c0-145">Pokyny jsou buď k ručnímu zápisu souboru IDL, nebo C/C++ hlavičku pro nativní deklarace rozhraní com.</span><span class="sxs-lookup"><span data-stu-id="010c0-145">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

<span data-ttu-id="010c0-146">Kromě toho mají při načítání .NET Framework a .NET Core do stejného procesu diagnostické omezení.</span><span class="sxs-lookup"><span data-stu-id="010c0-146">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="010c0-147">Primární omezení je ladění spravovaných komponent, protože není možné současně ladit .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="010c0-147">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="010c0-148">Kromě toho tyto dvě instance modulu runtime nesdílejí spravovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="010c0-148">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="010c0-149">To znamená, že není možné sdílet skutečné typy .NET napříč dvěma moduly runtime a místo toho musí být všechny interakce omezeny na vystavené kontrakty COM rozhraní.</span><span class="sxs-lookup"><span data-stu-id="010c0-149">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
