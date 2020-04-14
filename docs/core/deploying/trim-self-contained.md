---
title: Oříznutí samostatných aplikací
description: Přečtěte si, jak oříznout samostatné aplikace, aby se zmenšila jejich velikost. .NET Core sdružuje runtime s aplikací, která je publikována samostatně a obecně obsahuje více runtime pak je nezbytné.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242900"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Odebrání nechtěných součástí a zachování pouze samostatně nasaditelných součástí a spustitelných souborů

Při publikování samostatné aplikace je runtime .NET Core dodáván společně s aplikací. Toto sdružování přidá značné množství obsahu do vaší balené aplikace. Pokud jde o nasazení aplikace, velikost je často důležitým faktorem. Zachování velikosti aplikace balíčku co nejmenší je obvykle cílem pro vývojáře aplikací.

V závislosti na složitosti aplikace je ke spuštění aplikace vyžadována pouze podmnožina runtime. Tyto nepoužívané části runtime jsou zbytečné a lze je oříznout z balené aplikace.

Funkce oříznutí funguje tak, že zkoumá binární soubory aplikace, aby zjistila a vytvořila graf požadovaných sestav za běhu. Zbývající sestavení za běhu, na která se neodkazuje, jsou vyloučena.

> [!NOTE]
> Oříznutí je experimentální funkce v rozhraní .NET Core 3.1 a je k dispozici _pouze_ pro aplikace, které jsou publikovány samostatně.

## <a name="prevent-assemblies-from-being-trimmed"></a>Zabránit oříznutí sestav

Existují scénáře, ve kterých funkce oříznutí se nezdaří rozpoznat odkazy. Například při odrazu se používá v sestavení za běhu, buď aplikace nebo knihovny, která je odkazována vaší aplikací, sestavení není přímo odkazuje. Oříznutí není vědoma těchto nepřímých odkazů a by vyloučit knihovnu z publikované složky.

Pokud kód nepřímo odkazuje na sestavení prostřednictvím reflexe, můžete zabránit oříznutí `<TrimmerRootAssembly>` sestavení s nastavením. Následující příklad ukazuje, jak zabránit `System.Security` oříznutí sestavení nazývaného sestavení:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>Oříznutí aplikace – CLI

Ořízněte aplikaci pomocí příkazu [dotnet publish.](../tools/dotnet-publish.md) Při publikování aplikace nastavte následující tři nastavení:

- Publikovat jako samostatné:`--self-contained true`
- Zakázat publikování na jednom souboru:`-p:PublishSingleFile=false`
- Povolit oříznutí:`p:PublishTrimmed=true`

Následující příklad publikuje aplikaci pro Windows 10 jako samostatnou a ořízne výstup.

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

Další informace naleznete v [tématu Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).

## <a name="trim-your-app---visual-studio"></a>Oříznutí aplikace – Visual Studio

Visual Studio vytvoří opakovaně použitelné publikování profily, které řídí, jak je vaše aplikace publikována.

01. V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt, který chcete publikovat. Vyberte **Publikovat...**.

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Průzkumník řešení s nabídkou po kliknutí pravým tlačítkem myši zvýrazňující možnost Publikovat.":::

    Pokud ještě nemáte profil publikování, postupujte podle pokynů k jeho vytvoření a zvolte typ cíle **složky.**

01. Zvolte **Upravit**.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual studio publikuje profil pomocí tlačítka upravit.":::

01. V dialogovém okně **Nastavení profilu** nastavte následující volby:

    - Nastavte **režim nasazení** na samostatný **.**
    - Nastavte **cílový čas runtime** na platformu, na kterou chcete publikovat.
    - Vyberte **Oříznout nepoužité sestavy (v náhledu).**

    Zvolte **Uložit,** chcete-li uložit nastavení a vrátit se do dialogového okna **Publikovat.**

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dialogové okno nastavení profilu se zvýrazněným režimem nasazení, cílovým časem běhu a oříznutím nepoužívaných sestav.":::

01. Zvolte **Publikovat,** chcete-li aplikaci publikovat oříznutou.

Další informace najdete [v tématu Publikování aplikací .NET Core pomocí sady Visual Studio](deploy-with-vs.md).

## <a name="trim-your-app---visual-studio-for-mac"></a>Oříznutí aplikace – Visual Studio pro Mac

Visual Studio pro Mac neposkytuje možnosti, jak aplikaci během publikování oříznout. Budete muset publikovat ručně podle pokynů v části [Oříznout aplikaci – CLI.](#trim-your-app---cli) Další informace naleznete v [tématu Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).

## <a name="see-also"></a>Viz také

- [Nasazení základní aplikace .NET](index.md).
- [Publikování aplikací .NET Core pomocí rozhraní CLI jádra .NET](deploy-with-cli.md).
- [Publikujte aplikace .NET Core pomocí sady Visual Studio](deploy-with-vs.md).
- [dotnet publish , příkaz](../tools/dotnet-publish.md).
