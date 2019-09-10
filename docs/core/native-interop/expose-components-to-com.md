---
title: Vystavení komponent .NET Core pro COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 686d1b31478121a8b2c907d99672a5fcc3438a71
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849029"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="3385d-102">Vystavení komponent .NET Core pro COM</span><span class="sxs-lookup"><span data-stu-id="3385d-102">Exposing .NET Core Components to COM</span></span>

<span data-ttu-id="3385d-103">V .NET Core se proces pro vystavování objektů .NET do modelu COM významně zjednodušil v porovnání s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3385d-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="3385d-104">Následující postup vás provede postupem, jak vystavit třídu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3385d-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="3385d-105">V tomto kurzu se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="3385d-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="3385d-106">Zveřejňuje třídu modelu COM z .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3385d-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="3385d-107">Vygenerujte server COM jako součást sestavení knihovny .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3385d-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="3385d-108">Automatické generování manifestu souběžného serveru pro model COM bez registru.</span><span class="sxs-lookup"><span data-stu-id="3385d-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3385d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3385d-109">Prerequisites</span></span>

- <span data-ttu-id="3385d-110">Nainstalujte [sadu .NET Core 3,0 Preview 7 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="3385d-110">Install the [.NET Core 3.0 Preview 7 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="3385d-111">Vytvoření knihovny</span><span class="sxs-lookup"><span data-stu-id="3385d-111">Create the library</span></span>

<span data-ttu-id="3385d-112">Prvním krokem je vytvoření knihovny.</span><span class="sxs-lookup"><span data-stu-id="3385d-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="3385d-113">Vytvořte novou složku a v této složce spusťte `dotnet new classlib`.</span><span class="sxs-lookup"><span data-stu-id="3385d-113">Create a new folder, and in that folder run `dotnet new classlib`.</span></span>
2. <span data-ttu-id="3385d-114">Otevřít `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="3385d-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="3385d-115">Přidejte `using System.Runtime.InteropServices;` na začátek souboru.</span><span class="sxs-lookup"><span data-stu-id="3385d-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="3385d-116">Vytvořte rozhraní s názvem `IServer`.</span><span class="sxs-lookup"><span data-stu-id="3385d-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="3385d-117">Například:[!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]</span><span class="sxs-lookup"><span data-stu-id="3385d-117">For example: [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]</span></span>
5. <span data-ttu-id="3385d-118">`[Guid("<IID>")]` Přidejte atribut do rozhraní s identifikátorem GUID rozhraní pro rozhraní modelu COM, které implementujete.</span><span class="sxs-lookup"><span data-stu-id="3385d-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="3385d-119">Například, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="3385d-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="3385d-120">Všimněte si, že tento identifikátor GUID musí být jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní pro COM.</span><span class="sxs-lookup"><span data-stu-id="3385d-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="3385d-121">V aplikaci Visual Studio můžete vygenerovat GUID tak, že kliknete na nástroje > vytvořit GUID a otevřete nástroj vytvořit GUID.</span><span class="sxs-lookup"><span data-stu-id="3385d-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="3385d-122">Přidejte do rozhraní atribut a určete, jaká základní rozhraní com by měla vaše rozhraní implementovat. `[InterfaceType]`</span><span class="sxs-lookup"><span data-stu-id="3385d-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="3385d-123">Vytvořte třídu s názvem `Server` , která `IServer`implementuje.</span><span class="sxs-lookup"><span data-stu-id="3385d-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="3385d-124">`[Guid("<CLSID>")]` Přidejte atribut do třídy s identifikátorem GUID třídy pro třídu com, kterou implementujete.</span><span class="sxs-lookup"><span data-stu-id="3385d-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="3385d-125">Například, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="3385d-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="3385d-126">Stejně jako u identifikátoru GUID rozhraní musí být tento identifikátor GUID jedinečný, protože se jedná o jediný identifikátor tohoto rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3385d-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="3385d-127">`[ComVisible(true)]` Přidejte atribut do rozhraní i do třídy.</span><span class="sxs-lookup"><span data-stu-id="3385d-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3385d-128">Na rozdíl od .NET Framework vyžaduje .NET Core zadání identifikátoru CLSID libovolné třídy, kterou chcete aktivovatelné prostřednictvím modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3385d-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="3385d-129">Generování hostitele COM</span><span class="sxs-lookup"><span data-stu-id="3385d-129">Generate the COM host</span></span>

1. <span data-ttu-id="3385d-130">Otevřete soubor `<EnableComHosting>true</EnableComHosting>` projektu a přidejte ho dovnitř `<PropertyGroup></PropertyGroup>` tagu. `.csproj`</span><span class="sxs-lookup"><span data-stu-id="3385d-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="3385d-131">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="3385d-131">Build the project.</span></span>

<span data-ttu-id="3385d-132">Výsledný výstup `ProjectName.dll`bude obsahovat soubor `ProjectName.runtimeconfig.json` , `ProjectName.deps.json`a `ProjectName.comhost.dll` .</span><span class="sxs-lookup"><span data-stu-id="3385d-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="3385d-133">Registrace hostitele COM pro COM</span><span class="sxs-lookup"><span data-stu-id="3385d-133">Register the COM host for COM</span></span>

<span data-ttu-id="3385d-134">Otevřete příkazový řádek se zvýšenými oprávněními `regsvr32 ProjectName.comhost.dll`a spusťte příkaz.</span><span class="sxs-lookup"><span data-stu-id="3385d-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="3385d-135">Tím zaregistrujete všechny vystavené objekty .NET pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3385d-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="3385d-136">Povolení RegFree COM</span><span class="sxs-lookup"><span data-stu-id="3385d-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="3385d-137">Otevřete soubor `<EnableRegFreeCom>true</EnableRegFreeCom>` projektu a přidejte ho dovnitř `<PropertyGroup></PropertyGroup>` tagu. `.csproj`</span><span class="sxs-lookup"><span data-stu-id="3385d-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="3385d-138">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="3385d-138">Build the project.</span></span>

<span data-ttu-id="3385d-139">Výsledný výstup teď bude mít `ProjectName.X.manifest` i soubor.</span><span class="sxs-lookup"><span data-stu-id="3385d-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="3385d-140">Tento soubor je souběžný manifest pro použití s modelem COM bez registru.</span><span class="sxs-lookup"><span data-stu-id="3385d-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="3385d-141">Ukázka</span><span class="sxs-lookup"><span data-stu-id="3385d-141">Sample</span></span>

<span data-ttu-id="3385d-142">V úložišti dotnet/Samples na GitHubu je plně funkční [Ukázka serveru com](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) .</span><span class="sxs-lookup"><span data-stu-id="3385d-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="3385d-143">Další poznámky</span><span class="sxs-lookup"><span data-stu-id="3385d-143">Additional Notes</span></span>

<span data-ttu-id="3385d-144">Na rozdíl od .NET Framework neexistuje žádná podpora v .NET Core pro generování knihovny typů COM (TLB) ze sestavení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3385d-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="3385d-145">Buď budete muset ručně napsat soubor IDL nebo C++ hlavičku pro nativní deklarace vašich rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3385d-145">You will either have to manually write an IDL file or a C++ header for the native declarations of your interfaces.</span></span>

<span data-ttu-id="3385d-146">Kromě toho se nepodporují načítání .NET Framework a .NET Core do stejného procesu a jako výsledek načtení serveru COM .NET Core do procesu klienta .NET Framework COM nebo naopak není podporována.</span><span class="sxs-lookup"><span data-stu-id="3385d-146">Additionally, loading both .NET Framework and .NET Core into the same process is unsupported, and as a result loading a .NET Core COM server into a .NET Framework COM client process or vice versa is not supported.</span></span>
