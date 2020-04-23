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
# <a name="differences-in-wpf"></a>Rozdíly v WPF

Tento článek popisuje rozdíly mezi Windows Presentation Foundation (WPF) na .NET Core a .NET Framework. WPF pro .NET Core je [open source framework](https://github.com/dotnet/wpf) rozčleněný z původního wpf pro zdrojový kód rozhraní .NET Framework.

Existuje několik funkcí rozhraní .NET Framework, které rozhraní .NET Core nepodporuje. Další informace o nepodporovaných technologiích naleznete v [tématu .NET Framework technologií, které nejsou k dispozici na .NET Core](../../core/porting/net-framework-tech-unavailable.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>Projekty ve stylu SDK

Jádro .NET používá soubory projektu ve stylu sady SDK. Tyto soubory projektu se liší od tradičních souborů projektu rozhraní .NET Framework spravovaných souborem Visual Studio. Chcete-li migrovat aplikace WPF rozhraní .NET Framework na jádro .NET Core, je nutné převést projekty. Další informace naleznete [v tématu Migrace aplikací WPF do rozhraní .NET Core 3.0](convert-project-from-net-framework.md).

## <a name="nuget-package-references"></a>Odkazy na balíčky NuGet

Pokud vaše aplikace rozhraní .NET Framework uvádí své závislosti NuGet v [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) souboru *packages.config,* migrujte do formátu:

1. V sadě Visual Studio otevřete podokno **Průzkumník řešení.**
1. V projektu WPF klepněte pravým tlačítkem myši na **soubor packages.config.** > **Migrate packages.config to PackageReference**

![Upgrade na odkaz na balíček](media/differences-from-net-framework/package-reference-migration.png)

Zobrazí se dialogové okno zobrazující vypočtené závislosti NuGet nejvyšší úrovně a dotaz, které další balíčky NuGet by měly být povýšeny na nejvyšší úroveň. Vyberte **OK** a soubor *packages.config* bude `<PackageReference>` odebrán z projektu a prvky budou přidány do souboru projektu.

Pokud váš `<PackageReference>`projekt používá , balíčky nejsou uloženy místně ve složce *Balíčky,* jsou uloženy globálně. Otevřete soubor projektu `<Analyzer>` a odeberte všechny prvky, které odkazovaly na složku *Packages.* Tyto analyzátory jsou automaticky součástí nuget balíček odkazy.

## <a name="code-access-security"></a>Zabezpečení přístupu kódu

Zabezpečení přístupu kódu (CAS) není podporováno rozhraním .NET Core nebo WPF pro jádro .NET. Všechny funkce související s CAS jsou zpracovány za předpokladu plné důvěryhodnosti. WPF pro .NET Core odebere kód související s CAS. Veřejné rozhraní API povrchu těchto typů stále existuje zajistit, že volání do těchto typů úspěšné.

Veřejně definované typy související s CAS byly přesunuty ze sestavení WPF do sestavení knihovny Core .NET. Sestavení WPF mají typ-forwarding nastavit na nové umístění přesunutých typů.

| Zdrojové sestavení | Cílová sestava | Typ                |
| --------------- | --------------- | ------------------- |
| *Soubor WindowsBase.dll* | *Soubor System.Security.Permissions.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *Soubor System.Xaml.dll* | *Soubor System.Security.Permissions.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *Soubor System.Xaml.dll* | *Soubor System.Windows.Extension.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> Aby se minimalizovalo tření portů, byly v typu zachovány funkce pro ukládání a `XamlAccessLevel` načítání informací týkajících se následujících vlastností.
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>Další kroky

- [Přečtěte si, jak přenést aplikaci WPF rozhraní .NET Framework do jádra .NET.](convert-project-from-net-framework.md)
