---
title: Rozdíly mezi rozhraním .NET Framework a .NET Core
description: Popisuje rozdíly mezi implementací rozhraní .NET Framework systému Windows Presentation Foundation (WPF) a .NET Core WPF. Při migraci aplikace byste měli zvážit tyto nekompatibility.
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
# <a name="differences-in-wpf"></a><span data-ttu-id="b9e58-104">Rozdíly v WPF</span><span class="sxs-lookup"><span data-stu-id="b9e58-104">Differences in WPF</span></span>

<span data-ttu-id="b9e58-105">Tento článek popisuje rozdíly mezi Windows Presentation Foundation (WPF) na .NET Core a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9e58-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="b9e58-106">WPF pro .NET Core je [open source framework](https://github.com/dotnet/wpf) rozčleněný z původního wpf pro zdrojový kód rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9e58-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="b9e58-107">Existuje několik funkcí rozhraní .NET Framework, které rozhraní .NET Core nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="b9e58-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="b9e58-108">Další informace o nepodporovaných technologiích naleznete v [tématu .NET Framework technologií, které nejsou k dispozici na .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="b9e58-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="b9e58-109">Projekty ve stylu SDK</span><span class="sxs-lookup"><span data-stu-id="b9e58-109">SDK-style projects</span></span>

<span data-ttu-id="b9e58-110">Jádro .NET používá soubory projektu ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="b9e58-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="b9e58-111">Tyto soubory projektu se liší od tradičních souborů projektu rozhraní .NET Framework spravovaných souborem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9e58-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="b9e58-112">Chcete-li migrovat aplikace WPF rozhraní .NET Framework na jádro .NET Core, je nutné převést projekty.</span><span class="sxs-lookup"><span data-stu-id="b9e58-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="b9e58-113">Další informace naleznete [v tématu Migrace aplikací WPF do rozhraní .NET Core 3.0](convert-project-from-net-framework.md).</span><span class="sxs-lookup"><span data-stu-id="b9e58-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="b9e58-114">Odkazy na balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="b9e58-114">NuGet package references</span></span>

<span data-ttu-id="b9e58-115">Pokud vaše aplikace rozhraní .NET Framework uvádí své závislosti NuGet v [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) souboru *packages.config,* migrujte do formátu:</span><span class="sxs-lookup"><span data-stu-id="b9e58-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="b9e58-116">V sadě Visual Studio otevřete podokno **Průzkumník řešení.**</span><span class="sxs-lookup"><span data-stu-id="b9e58-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="b9e58-117">V projektu WPF klepněte pravým tlačítkem myši na **soubor packages.config.** > **Migrate packages.config to PackageReference**</span><span class="sxs-lookup"><span data-stu-id="b9e58-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![Upgrade na odkaz na balíček](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="b9e58-119">Zobrazí se dialogové okno zobrazující vypočtené závislosti NuGet nejvyšší úrovně a dotaz, které další balíčky NuGet by měly být povýšeny na nejvyšší úroveň.</span><span class="sxs-lookup"><span data-stu-id="b9e58-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="b9e58-120">Vyberte **OK** a soubor *packages.config* bude `<PackageReference>` odebrán z projektu a prvky budou přidány do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="b9e58-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="b9e58-121">Pokud váš `<PackageReference>`projekt používá , balíčky nejsou uloženy místně ve složce *Balíčky,* jsou uloženy globálně.</span><span class="sxs-lookup"><span data-stu-id="b9e58-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="b9e58-122">Otevřete soubor projektu `<Analyzer>` a odeberte všechny prvky, které odkazovaly na složku *Packages.*</span><span class="sxs-lookup"><span data-stu-id="b9e58-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="b9e58-123">Tyto analyzátory jsou automaticky součástí nuget balíček odkazy.</span><span class="sxs-lookup"><span data-stu-id="b9e58-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="b9e58-124">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="b9e58-124">Code Access Security</span></span>

<span data-ttu-id="b9e58-125">Zabezpečení přístupu kódu (CAS) není podporováno rozhraním .NET Core nebo WPF pro jádro .NET.</span><span class="sxs-lookup"><span data-stu-id="b9e58-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="b9e58-126">Všechny funkce související s CAS jsou zpracovány za předpokladu plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="b9e58-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="b9e58-127">WPF pro .NET Core odebere kód související s CAS.</span><span class="sxs-lookup"><span data-stu-id="b9e58-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="b9e58-128">Veřejné rozhraní API povrchu těchto typů stále existuje zajistit, že volání do těchto typů úspěšné.</span><span class="sxs-lookup"><span data-stu-id="b9e58-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="b9e58-129">Veřejně definované typy související s CAS byly přesunuty ze sestavení WPF do sestavení knihovny Core .NET.</span><span class="sxs-lookup"><span data-stu-id="b9e58-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="b9e58-130">Sestavení WPF mají typ-forwarding nastavit na nové umístění přesunutých typů.</span><span class="sxs-lookup"><span data-stu-id="b9e58-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="b9e58-131">Zdrojové sestavení</span><span class="sxs-lookup"><span data-stu-id="b9e58-131">Source assembly</span></span> | <span data-ttu-id="b9e58-132">Cílová sestava</span><span class="sxs-lookup"><span data-stu-id="b9e58-132">Target assembly</span></span> | <span data-ttu-id="b9e58-133">Typ</span><span class="sxs-lookup"><span data-stu-id="b9e58-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="b9e58-134">*Soubor WindowsBase.dll*</span><span class="sxs-lookup"><span data-stu-id="b9e58-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="b9e58-135">*Soubor System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="b9e58-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="b9e58-136">*Soubor System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="b9e58-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="b9e58-137">*Soubor System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="b9e58-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="b9e58-138">*Soubor System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="b9e58-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="b9e58-139">*Soubor System.Windows.Extension.dll*</span><span class="sxs-lookup"><span data-stu-id="b9e58-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="b9e58-140">Aby se minimalizovalo tření portů, byly v typu zachovány funkce pro ukládání a `XamlAccessLevel` načítání informací týkajících se následujících vlastností.</span><span class="sxs-lookup"><span data-stu-id="b9e58-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="b9e58-141">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b9e58-141">Next steps</span></span>

- [<span data-ttu-id="b9e58-142">Přečtěte si, jak přenést aplikaci WPF rozhraní .NET Framework do jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="b9e58-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)
