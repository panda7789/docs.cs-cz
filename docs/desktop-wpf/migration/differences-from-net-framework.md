---
title: Rozdíly mezi .NET Framework a .NET Core
description: Popisuje rozdíly mezi .NET Framework implementaci Windows Presentation Foundation (WPF) a .NET Core WPF. Při migraci aplikace byste měli tyto nekompatibility vzít v úvahu.
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072205"
---
# <a name="differences-in-wpf"></a><span data-ttu-id="aac6d-104">Rozdíly v WPF</span><span class="sxs-lookup"><span data-stu-id="aac6d-104">Differences in WPF</span></span>

<span data-ttu-id="aac6d-105">Tento článek popisuje rozdíly mezi Windows Presentation Foundation (WPF) na .NET Core a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aac6d-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="aac6d-106">WPF pro .NET Core je [Open Source platforma](https://github.com/dotnet/wpf) , která je rozvětvená z původního WPF pro .NET Framework zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="aac6d-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="aac6d-107">Existuje několik funkcí .NET Framework, které rozhraní .NET Core nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="aac6d-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="aac6d-108">Další informace o nepodporovaných technologiích najdete v tématu [.NET Framework technologie nedostupné v .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="aac6d-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="aac6d-109">Projekty ve stylu sady SDK</span><span class="sxs-lookup"><span data-stu-id="aac6d-109">SDK-style projects</span></span>

<span data-ttu-id="aac6d-110">.NET Core používá soubory projektu ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="aac6d-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="aac6d-111">Tyto soubory projektu se liší od tradičních .NET Framework souborů projektu spravovaných pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aac6d-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="aac6d-112">Chcete-li migrovat aplikace .NET Framework WPF do .NET Core, je nutné převést projekty.</span><span class="sxs-lookup"><span data-stu-id="aac6d-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="aac6d-113">Další informace najdete v tématu [migrace aplikací WPF do .NET Core 3,0](convert-project-from-net-framework.md).</span><span class="sxs-lookup"><span data-stu-id="aac6d-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="aac6d-114">Odkazy na balíček NuGet</span><span class="sxs-lookup"><span data-stu-id="aac6d-114">NuGet package references</span></span>

<span data-ttu-id="aac6d-115">Pokud vaše aplikace .NET Framework vypíše své závislosti NuGet v souboru *Packages. config* , migrujte [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) do formátu:</span><span class="sxs-lookup"><span data-stu-id="aac6d-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="aac6d-116">V aplikaci Visual Studio otevřete podokno **Průzkumník řešení** .</span><span class="sxs-lookup"><span data-stu-id="aac6d-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="aac6d-117">V projektu WPF klikněte pravým tlačítkem na soubor **Packages. config** > . soubor Packages. config**migrujte do PackageReference**.</span><span class="sxs-lookup"><span data-stu-id="aac6d-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![Upgrade na PackageReference](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="aac6d-119">Zobrazí se dialogové okno s vypočítanými závislostmi NuGet nejvyšší úrovně a s žádostí o další balíčky NuGet by se měly zvýšit na nejvyšší úroveň.</span><span class="sxs-lookup"><span data-stu-id="aac6d-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="aac6d-120">Vyberte **OK** a soubor *Packages. config* se odebere z projektu a `<PackageReference>` prvky se přidají do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="aac6d-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="aac6d-121">Když projekt používá `<PackageReference>`, balíčky nejsou místně uložené ve složce *balíčků* , ukládají se globálně.</span><span class="sxs-lookup"><span data-stu-id="aac6d-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="aac6d-122">Otevřete soubor projektu a odeberte všechny `<Analyzer>` prvky, které jsou odkazovány do složky *Packages* .</span><span class="sxs-lookup"><span data-stu-id="aac6d-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="aac6d-123">Tyto analyzátory jsou automaticky zahrnuty v odkazech na balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="aac6d-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="aac6d-124">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="aac6d-124">Code Access Security</span></span>

<span data-ttu-id="aac6d-125">Rozhraní .NET Core ani WPF pro .NET Core nepodporuje zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="aac6d-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="aac6d-126">Všechny funkce související se správou CAS se zpracují za předpokladem úplné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="aac6d-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="aac6d-127">WPF pro .NET Core odebírá kód týkající se CAS.</span><span class="sxs-lookup"><span data-stu-id="aac6d-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="aac6d-128">Veřejné povrchy rozhraní API těchto typů stále existují, aby bylo zajištěno, že volání těchto typů budou úspěšná.</span><span class="sxs-lookup"><span data-stu-id="aac6d-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="aac6d-129">Veřejně definované typy související s CAS byly přesunuty ze sestavení WPF a do sestavení základní knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="aac6d-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="aac6d-130">Sestavení WPF mají nastaveno přesměrování typu na nové umístění přesunutých typů.</span><span class="sxs-lookup"><span data-stu-id="aac6d-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="aac6d-131">Zdrojové sestavení</span><span class="sxs-lookup"><span data-stu-id="aac6d-131">Source assembly</span></span> | <span data-ttu-id="aac6d-132">Cílové sestavení</span><span class="sxs-lookup"><span data-stu-id="aac6d-132">Target assembly</span></span> | <span data-ttu-id="aac6d-133">Typ</span><span class="sxs-lookup"><span data-stu-id="aac6d-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="aac6d-134">*WindowsBase. dll*</span><span class="sxs-lookup"><span data-stu-id="aac6d-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="aac6d-135">*System. Security. Permissions. dll*</span><span class="sxs-lookup"><span data-stu-id="aac6d-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="aac6d-136">*System. XAML. dll*</span><span class="sxs-lookup"><span data-stu-id="aac6d-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="aac6d-137">*System. Security. Permissions. dll*</span><span class="sxs-lookup"><span data-stu-id="aac6d-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="aac6d-138">*System. XAML. dll*</span><span class="sxs-lookup"><span data-stu-id="aac6d-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="aac6d-139">*System. Windows. extension. dll*</span><span class="sxs-lookup"><span data-stu-id="aac6d-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="aac6d-140">Aby bylo možné minimalizovat tření, funkce pro ukládání a načítání informací souvisejících s následujícími vlastnostmi byla v `XamlAccessLevel` typu zachována.</span><span class="sxs-lookup"><span data-stu-id="aac6d-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="aac6d-141">Další kroky</span><span class="sxs-lookup"><span data-stu-id="aac6d-141">Next steps</span></span>

- [<span data-ttu-id="aac6d-142">Naučte se, jak portovat .NET Framework aplikaci WPF do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aac6d-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)
