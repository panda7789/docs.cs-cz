---
title: Publikování konzolové aplikace .NET Core pomocí sady Visual Studio
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: e0033d52ab54259ce5e4ccf2a25bf4e3d4f244de
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867552"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio"></a>Kurz: publikování konzolové aplikace .NET Core pomocí sady Visual Studio

V tomto kurzu se dozvíte, jak publikovat konzolovou aplikaci, aby ji ostatní uživatelé mohli spustit. Publikování vytvoří sadu souborů, které jsou nutné ke spuštění vaší aplikace. Chcete-li nasadit soubory, zkopírujte je do cílového počítače.

## <a name="prerequisites"></a>Předpoklady

- Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core pomocí sady Visual Studio](with-visual-studio.md).

## <a name="publish-the-app"></a>Publikování aplikace

1. Spusťte Visual Studio.

1. Otevřete projekt *HelloWorld* , který jste vytvořili v [části Vytvoření konzolové aplikace .NET Core pomocí sady Visual Studio](with-visual-studio.md).

1. Ujistěte se, že aplikace Visual Studio používá konfiguraci sestavení pro vydání. V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z části **ladit** na **verzi**.

   ![Panel nástrojů sady Visual Studio s vybraným sestavením pro vydání](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Klikněte pravým tlačítkem na projekt **HelloWorld** (ne na řešení HelloWorld) a v nabídce vyberte **publikovat** .

   ![Místní nabídka publikování Visual studia](media/publishing-with-visual-studio/publish-context-menu.png)

1. Na kartě **cíl** stránky **publikování** vyberte možnost **Složka**a potom vyberte možnost **Další**.

   ![Výběr cíle publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. Na kartě **umístění** stránky **publikovat** vyberte **Dokončit**.

   ![Karta umístění stránky pro publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. Na kartě **publikovat** okna **publikovat** vyberte **publikovat**.

   ![Okno pro publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>Kontrola souborů

Ve výchozím nastavení vytvoří proces publikování nasazení závislé na rozhraní, což je typ nasazení, ve kterém je publikovaná aplikace spuštěna na počítači s nainstalovaným modulem runtime .NET Core. Uživatelé můžou publikovanou aplikaci spustit dvojitým kliknutím na spustitelný soubor nebo vyvoláním `dotnet HelloWorld.dll` příkazu z příkazového řádku.

V následujících krocích se podíváte na soubory vytvořené procesem publikování.

1. V **Průzkumník řešení**vyberte možnost **Zobrazit všechny soubory**.

1. Ve složce projektu rozbalte *přihrádku/Release/netcoreapp 3.1/Publish*.

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Průzkumník řešení zobrazení publikovaných souborů":::

   Jak ukazuje obrázek, publikovaný výstup obsahuje následující soubory:

   * *HelloWorld.deps.jsna*

      Toto je soubor závislostí modulu runtime aplikace. Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaši aplikaci) potřebnou ke spuštění aplikace. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

   * *HelloWorld.dll*

      Toto je verze [nasazení závislá na rozhraní](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace. Chcete-li spustit tuto dynamickou knihovnu, zadejte `dotnet HelloWorld.dll` na příkazovém řádku. Tato metoda spuštění aplikace funguje na libovolné platformě, na které je nainstalovaný modul runtime .NET Core.

   * *HelloWorld.exe*

      Toto je [spustitelná](../deploying/deploy-with-cli.md#framework-dependent-executable) verze aplikace závislá na rozhraní. Pokud ho chcete spustit, zadejte `HelloWorld.exe` na příkazovém řádku. Soubor je specifický pro operační systém.

   * *HelloWorld. pdb* (volitelné pro nasazení)

      Toto je soubor se symboly ladění. Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.

   * *HelloWorld.runtimeconfig.jsna*

      Toto je konfigurační soubor modulu runtime aplikace. Identifikuje verzi .NET Core, na které byla aplikace sestavena. Můžete také přidat možnosti konfigurace. Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Spuštění publikované aplikace

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku pro *publikování* a vyberte možnost **Kopírovat úplnou cestu**.

1. Otevřete příkazový řádek a přejděte do složky pro *publikování* . Provedete to tak, že zadáte `cd` a pak vložíte úplnou cestu. Příklad:

   ```console
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. Spusťte aplikaci pomocí spustitelného souboru:

   1. Zadejte `HelloWorld.exe` a stiskněte klávesu <kbd>ENTER</kbd>.

   1. Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.

1. Spusťte aplikaci pomocí `dotnet` příkazu:

   1. Zadejte `dotnet HelloWorld.dll` a stiskněte klávesu <kbd>ENTER</kbd>.

   1. Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.

## <a name="additional-resources"></a>Další zdroje

- [Nasazení aplikace .NET Core](../deploying/index.md)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste publikovali konzolovou aplikaci. V dalším kurzu vytvoříte knihovnu tříd.

> [!div class="nextstepaction"]
> [Vytvoření knihovny .NET Standard pomocí sady Visual Studio](library-with-visual-studio.md)
