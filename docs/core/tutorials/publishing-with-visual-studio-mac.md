---
title: Publikování konzolové aplikace .NET Core pomocí Visual Studio pro Mac
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
ms.date: 06/08/2020
ms.openlocfilehash: 38b656ac919dfb8b710a97c5d7fc63479e3fa367
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811402"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-for-mac"></a>Kurz: publikování konzolové aplikace .NET Core pomocí Visual Studio pro Mac

V tomto kurzu se dozvíte, jak publikovat konzolovou aplikaci, aby ji ostatní uživatelé mohli spustit. Publikování vytvoří sadu souborů, které jsou nutné ke spuštění vaší aplikace. Chcete-li nasadit soubory, zkopírujte je do cílového počítače.

## <a name="prerequisites"></a>Předpoklady

- Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v Visual Studio pro Mac](with-visual-studio-mac.md).

## <a name="publish-the-app"></a>Publikování aplikace

1. Spusťte Visual Studio pro Mac.

1. Otevřete projekt HelloWorld, který jste vytvořili v [části Vytvoření konzolové aplikace .NET Core v Visual Studio pro Mac](with-visual-studio-mac.md).

1. Ujistěte se, že Visual Studio sestavuje prodejní verzi vaší aplikace. V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z části **ladit** na **verzi**.

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="Panel nástrojů sady Visual Studio s vybraným sestavením pro vydání":::

1. V hlavní nabídce vyberte **sestavení**  >  **publikovat do složky...**.

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Místní nabídka publikování Visual studia":::

1. V dialogovém okně **publikovat do složky** vyberte **publikovat**.

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Dialog publikovat do složky v aplikaci Visual Studio":::

   Otevře se složka pro publikování zobrazující soubory, které byly vytvořeny.

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="Složka pro publikování":::

1. Vyberte ikonu ozubeného kolečka a v místní nabídce vyberte **Kopírovat "publikovat" jako cestu** .

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="Kopírovat cestu pro složku pro publikování":::

## <a name="inspect-the-files"></a>Kontrola souborů

Proces publikování vytvoří nasazení závislé na rozhraní, což je typ nasazení, ve kterém je publikovaná aplikace spuštěna na počítači s nainstalovanou modulem runtime .NET Core. Uživatelé mohou spustit publikovanou aplikaci spuštěním `dotnet HelloWorld.dll` příkazu z příkazového řádku.

Jak ukazuje předchozí obrázek, publikovaný výstup obsahuje následující soubory:

* *HelloWorld.deps.jsna*

  Toto je soubor závislostí modulu runtime aplikace. Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaši aplikaci) potřebnou ke spuštění aplikace. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

* *HelloWorld.dll*

   Toto je verze [nasazení závislá na rozhraní](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace. Chcete-li spustit tuto dynamickou knihovnu, zadejte `dotnet HelloWorld.dll` na příkazovém řádku. Tato metoda spuštění aplikace funguje na libovolné platformě, na které je nainstalovaný modul runtime .NET Core.

* *HelloWorld. pdb* (volitelné pro nasazení)

   Toto je soubor se symboly ladění. Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.

* *HelloWorld.runtimeconfig.jsna*

   Toto je konfigurační soubor modulu runtime aplikace. Identifikuje verzi .NET Core, na které byla aplikace sestavena. Můžete také přidat možnosti konfigurace. Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Spuštění publikované aplikace

1. Otevřete terminál a přejděte do složky pro *publikování* . Provedete to tak, že zadáte `cd` a pak vložíte cestu, kterou jste zkopírovali dříve. Příklad:

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/netcoreapp3.1/publish/
   ```

1. Spusťte aplikaci pomocí `dotnet` příkazu:

   1. Zadejte `dotnet HelloWorld.dll` a stiskněte klávesu <kbd>ENTER</kbd>.

   1. Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.

## <a name="additional-resources"></a>Další zdroje

- [Nasazení aplikace .NET Core](../deploying/index.md)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste publikovali konzolovou aplikaci. V dalším kurzu vytvoříte knihovnu tříd.

> [!div class="nextstepaction"]
> [Vytvoření knihovny .NET Standard v aplikaci Visual Studio pro Mac](library-with-visual-studio-mac.md)
