---
title: Rozdíly mezi .NET Framework a .NET Core
description: Popisuje rozdíly mezi .NET Framework implementaci Windows Presentation Foundation (WPF) a .NET Core WPF. Při migraci aplikace byste měli tyto nekompatibility vzít v úvahu.
author: adegeo
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 3bedc30046c36d4c5430feedf5854276ebaef8aa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325684"
---
# <a name="differences-in-wpf"></a>Rozdíly v WPF

Tento článek popisuje rozdíly mezi Windows Presentation Foundation (WPF) na .NET Core a .NET Framework. WPF pro .NET Core je [Open Source platforma](https://github.com/dotnet/wpf) , která je rozvětvená z původního WPF pro .NET Framework zdrojový kód.

Existuje několik funkcí .NET Framework, které rozhraní .NET Core nepodporuje. Další informace o nepodporovaných technologiích najdete v tématu [.NET Framework technologie nedostupné v .NET Core](../../core/porting/net-framework-tech-unavailable.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>Projekty ve stylu sady SDK

.NET Core používá soubory projektu ve stylu sady SDK. Tyto soubory projektu se liší od tradičních .NET Framework souborů projektu spravovaných pomocí sady Visual Studio. Chcete-li migrovat aplikace .NET Framework WPF do .NET Core, je nutné převést projekty. Další informace najdete v tématu [migrace aplikací WPF do .NET Core 3,0](convert-project-from-net-framework.md).

## <a name="nuget-package-references"></a>Odkazy na balíček NuGet

Pokud vaše aplikace .NET Framework vypíše své závislosti NuGet v souboru *packages.config* , migrujte do [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) formátu:

1. V aplikaci Visual Studio otevřete podokno **Průzkumník řešení** .
1. V projektu WPF klikněte pravým tlačítkem na **packages.config**  >  **migrovat packages.config na PackageReference**.

![Upgrade na PackageReference](media/differences-from-net-framework/package-reference-migration.png)

Zobrazí se dialogové okno s vypočítanými závislostmi NuGet nejvyšší úrovně a s žádostí o další balíčky NuGet by se měly zvýšit na nejvyšší úroveň. Vyberte **OK** a soubor *packages.config* se odebere z projektu a `<PackageReference>` prvky se přidají do souboru projektu.

Když projekt používá `<PackageReference>` , balíčky nejsou místně uložené ve složce *balíčků* , ukládají se globálně. Otevřete soubor projektu a odeberte všechny `<Analyzer>` prvky, které jsou odkazovány do složky *Packages* . Tyto analyzátory jsou automaticky zahrnuty v odkazech na balíček NuGet.

## <a name="code-access-security"></a>Zabezpečení přístupu kódu

Rozhraní .NET Core ani WPF pro .NET Core nepodporuje zabezpečení přístupu kódu (CAS). Všechny funkce související se správou CAS se zpracují za předpokladem úplné důvěryhodnosti. WPF pro .NET Core odebírá kód týkající se CAS. Veřejné povrchy rozhraní API těchto typů stále existují, aby bylo zajištěno, že volání těchto typů budou úspěšná.

Veřejně definované typy související s CAS byly přesunuty ze sestavení WPF a do sestavení základní knihovny .NET. Sestavení WPF mají nastaveno přesměrování typu na nové umístění přesunutých typů.

| Zdrojové sestavení | Cílové sestavení | Typ                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *System.Security.Permissions.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System.Xaml.dll* | *System.Security.Permissions.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System.Xaml.dll* | *System.Windows.Extension.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> Aby bylo možné minimalizovat tření, funkce pro ukládání a načítání informací souvisejících s následujícími vlastnostmi byla v typu zachována `XamlAccessLevel` .
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>Další kroky

- [Naučte se, jak portovat .NET Framework aplikaci WPF do .NET Core.](convert-project-from-net-framework.md)
