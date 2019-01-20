---
title: Vyberte verzi jazyka Visual Basic
description: Nakonfigurujte kompilátor provést ověření syntaxe pomocí specifické verzi kompilátoru.
ms.date: 05/24/2018
ms.openlocfilehash: 3b6d8055dbf64f2a5c38f46b6d66794fc48a1cea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415101"
---
# <a name="select-the-visual-basic-language-version"></a><span data-ttu-id="2b13e-103">Vyberte verzi jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b13e-103">Select the Visual Basic language version</span></span>

<span data-ttu-id="2b13e-104">Kompilátor jazyka Visual Basic výchozí nejnovější hlavní verzi jazyka, který byl vydán.</span><span class="sxs-lookup"><span data-stu-id="2b13e-104">The Visual Basic compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="2b13e-105">Můžete se rozhodnout pro kompilaci libovolného projektu pomocí nové verze bodu jazyka.</span><span class="sxs-lookup"><span data-stu-id="2b13e-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="2b13e-106">Výběr novější verzi jazyka umožňuje svým projektem zajistíte využívají nejnovější funkce jazyků.</span><span class="sxs-lookup"><span data-stu-id="2b13e-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="2b13e-107">V jiných případech budete muset ověřit, že projekt zkompiluje čistě při používání starší verze jazyka.</span><span class="sxs-lookup"><span data-stu-id="2b13e-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="2b13e-108">Tato funkce odděluje rozhodnutí pro instalaci nové verze sady SDK a nástroje ve vašem vývojovém prostředí od rozhodnutí začlenit nové funkce jazyků v projektu.</span><span class="sxs-lookup"><span data-stu-id="2b13e-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="2b13e-109">Nejnovější sady SDK a nástroje můžete nainstalovat na počítače pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="2b13e-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="2b13e-110">Každý projekt se dá použít konkrétní verzi jazyka pro jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="2b13e-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="2b13e-111">Existují tři způsoby, jak nastavit jazykovou verzi:</span><span class="sxs-lookup"><span data-stu-id="2b13e-111">There are three ways to set the language version:</span></span>

- <span data-ttu-id="2b13e-112">Ručně upravit vaše [ **.vbproj** souboru](#edit-the-vbproj-file)</span><span class="sxs-lookup"><span data-stu-id="2b13e-112">Manually edit your [**.vbproj** file](#edit-the-vbproj-file)</span></span>
- <span data-ttu-id="2b13e-113">Nastavit jazykovou verzi [pro více projektů v podadresáři](#configure-multiple-projects)</span><span class="sxs-lookup"><span data-stu-id="2b13e-113">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects)</span></span>
- <span data-ttu-id="2b13e-114">Konfigurace [ `-langversion` – možnost kompilátoru](#set-the-langversion-compiler-option)</span><span class="sxs-lookup"><span data-stu-id="2b13e-114">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option)</span></span>

## <a name="edit-the-vbproj-file"></a><span data-ttu-id="2b13e-115">Upravte soubor vbproj</span><span class="sxs-lookup"><span data-stu-id="2b13e-115">Edit the vbproj file</span></span>

<span data-ttu-id="2b13e-116">Můžete nastavit jazykovou verzi vašeho **.vbproj** souboru.</span><span class="sxs-lookup"><span data-stu-id="2b13e-116">You can set the language version in your **.vbproj** file.</span></span> <span data-ttu-id="2b13e-117">Přidejte následující element:</span><span class="sxs-lookup"><span data-stu-id="2b13e-117">Add the following element:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="2b13e-118">Hodnota `latest` používá nejnovější dílčí verzi jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2b13e-118">The value `latest` uses the latest minor version of the Visual Basic language.</span></span> <span data-ttu-id="2b13e-119">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="2b13e-119">Valid values are:</span></span>

|<span data-ttu-id="2b13e-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2b13e-120">Value</span></span>|<span data-ttu-id="2b13e-121">Význam</span><span class="sxs-lookup"><span data-stu-id="2b13e-121">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="2b13e-122">default</span><span class="sxs-lookup"><span data-stu-id="2b13e-122">default</span></span>|<span data-ttu-id="2b13e-123">Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější hlavní verzi, která může podporovat.</span><span class="sxs-lookup"><span data-stu-id="2b13e-123">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="2b13e-124">9</span><span class="sxs-lookup"><span data-stu-id="2b13e-124">9</span></span>|<span data-ttu-id="2b13e-125">Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 9.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="2b13e-125">The compiler accepts only syntax that is included in Visual Basic 9.0 or lower.</span></span>|
|<span data-ttu-id="2b13e-126">10</span><span class="sxs-lookup"><span data-stu-id="2b13e-126">10</span></span>|<span data-ttu-id="2b13e-127">Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 10.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="2b13e-127">The compiler accepts only syntax that is included in Visual Basic 10.0 or lower.</span></span>|
|<span data-ttu-id="2b13e-128">11</span><span class="sxs-lookup"><span data-stu-id="2b13e-128">11</span></span>|<span data-ttu-id="2b13e-129">Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 11.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="2b13e-129">The compiler accepts only syntax that is included in Visual Basic 11.0 or lower.</span></span>|
|<span data-ttu-id="2b13e-130">12</span><span class="sxs-lookup"><span data-stu-id="2b13e-130">12</span></span>|<span data-ttu-id="2b13e-131">Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 12.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="2b13e-131">The compiler accepts only syntax that is included in Visual Basic 12.0 or lower.</span></span>|
|<span data-ttu-id="2b13e-132">14</span><span class="sxs-lookup"><span data-stu-id="2b13e-132">14</span></span>|<span data-ttu-id="2b13e-133">Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 14.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="2b13e-133">The compiler accepts only syntax that is included in Visual Basic 14.0 or lower.</span></span>|
|<span data-ttu-id="2b13e-134">15</span><span class="sxs-lookup"><span data-stu-id="2b13e-134">15</span></span>|<span data-ttu-id="2b13e-135">Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 15.0 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="2b13e-135">The compiler accepts only syntax that is included in Visual Basic 15.0 or lower.</span></span>|
|<span data-ttu-id="2b13e-136">15.3</span><span class="sxs-lookup"><span data-stu-id="2b13e-136">15.3</span></span>|<span data-ttu-id="2b13e-137">Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 15.3 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="2b13e-137">The compiler accepts only syntax that is included in Visual Basic 15.3 or lower.</span></span>|
|<span data-ttu-id="2b13e-138">15.5</span><span class="sxs-lookup"><span data-stu-id="2b13e-138">15.5</span></span>|<span data-ttu-id="2b13e-139">Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce Visual Basic 15.5 nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="2b13e-139">The compiler accepts only syntax that is included in Visual Basic 15.5 or lower.</span></span>|
|<span data-ttu-id="2b13e-140">nejnovější</span><span class="sxs-lookup"><span data-stu-id="2b13e-140">latest</span></span>|<span data-ttu-id="2b13e-141">Kompilátor přijímá všechny platné syntaxe jazyka, který může podporovat.</span><span class="sxs-lookup"><span data-stu-id="2b13e-141">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="2b13e-142">Speciální řetězce `default` a `latest` přeložit na nejnovější hlavní a dílčí jazykové verze nainstalovaná v počítači sestavení, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="2b13e-142">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="2b13e-143">Konfigurace více projektů</span><span class="sxs-lookup"><span data-stu-id="2b13e-143">Configure multiple projects</span></span>

<span data-ttu-id="2b13e-144">Můžete vytvořit **Directory.build.props** soubor, který obsahuje `<LangVersion>` prvek, který chcete nakonfigurovat více adresářů.</span><span class="sxs-lookup"><span data-stu-id="2b13e-144">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="2b13e-145">Obvykle to uděláte ve svém adresáři řešení.</span><span class="sxs-lookup"><span data-stu-id="2b13e-145">You typically do that in your solution directory.</span></span> <span data-ttu-id="2b13e-146">Přidejte následující text do **Directory.build.props** soubor v adresáři řešení:</span><span class="sxs-lookup"><span data-stu-id="2b13e-146">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="2b13e-147">Nyní sestavení v každé podadresáře adresáře, který obsahuje tento soubor se syntaxí jazyka Visual Basic verze 15.5.</span><span class="sxs-lookup"><span data-stu-id="2b13e-147">Now, builds in every subdirectory of the directory containing that file will use Visual Basic version 15.5 syntax.</span></span> <span data-ttu-id="2b13e-148">Další informace najdete v článku na [přizpůsobení sestavení](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="2b13e-148">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="2b13e-149">Nastavte langversion – možnost kompilátoru</span><span class="sxs-lookup"><span data-stu-id="2b13e-149">Set the langversion compiler option</span></span>

<span data-ttu-id="2b13e-150">Můžete použít `-langversion` možnost příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2b13e-150">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="2b13e-151">Další informace najdete v článku na [- langversion](../reference/command-line-compiler/langversion.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2b13e-151">For more information, see the article on the [-langversion](../reference/command-line-compiler/langversion.md) compiler option.</span></span> <span data-ttu-id="2b13e-152">Seznam platných hodnot najdete tak, že zadáte `vbc -langversion:?` .</span><span class="sxs-lookup"><span data-stu-id="2b13e-152">You can see a list of the valid values by typing  `vbc -langversion:?` .</span></span>
