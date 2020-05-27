---
title: Publikování aplikace Hello World .NET Core pomocí sady Visual Studio
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: e4ef8c12f3e52faa7cf09058a98abae65b0dcfce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005086"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio"></a>Kurz: publikování konzolové aplikace .NET Core pomocí sady Visual Studio

V tomto kurzu se dozvíte, jak publikovat konzolovou aplikaci, aby ji ostatní uživatelé mohli spustit. Publikování vytvoří sadu souborů, které jsou nutné ke spuštění vaší aplikace. Chcete-li nasadit soubory, zkopírujte je do cílového počítače.

## <a name="prerequisites"></a>Požadavky

- Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v sadě Visual Studio 2019](with-visual-studio.md).

## <a name="publish-the-app"></a>Publikování aplikace

1. Ujistěte se, že Visual Studio sestavuje prodejní verzi vaší aplikace. V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z části **ladit** na **verzi**.

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

Proces publikování vytvoří nasazení závislé na rozhraní, což je typ nasazení, ve kterém je publikovaná aplikace spuštěna na počítači s nainstalovanou modulem runtime .NET Core. Uživatelé můžou publikovanou aplikaci spustit dvojitým kliknutím na spustitelný soubor nebo vyvoláním `dotnet HelloWorld.dll` příkazu z příkazového řádku.

V následujících krocích se podíváte na soubory vytvořené procesem publikování.

1. V **Průzkumník řešení**vyberte možnost **Zobrazit všechny soubory**.

1. Ve složce projektu rozbalte *přihrádku/Release/netcoreapp 3.1/Publish*.

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Průzkumník řešení zobrazení publikovaných souborů":::

   Jak ukazuje obrázek, publikovaný výstup obsahuje následující soubory:

      * *HelloWorld. DEPS. JSON*

         Toto je soubor závislostí modulu runtime aplikace. Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaši aplikaci) potřebnou ke spuštění aplikace. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld. dll*

         Toto je verze [nasazení závislá na rozhraní](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace. Chcete-li spustit tuto dynamickou knihovnu, zadejte `dotnet HelloWorld.dll` na příkazovém řádku.

      * *Soubor HelloWorld. exe*

         Toto je [spustitelná](../deploying/deploy-with-cli.md#framework-dependent-executable) verze aplikace závislá na rozhraní. Pokud ho chcete spustit, zadejte `HelloWorld.exe` na příkazovém řádku.

      * *HelloWorld. pdb* (volitelné pro nasazení)

         Toto je soubor se symboly ladění. Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.

      * *HelloWorld. runtimeconfig. JSON*

         Toto je konfigurační soubor modulu runtime aplikace. Identifikuje verzi .NET Core, na které byla aplikace sestavena. Můžete také přidat možnosti konfigurace. Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Spuštění publikované aplikace

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku pro *publikování* a vyberte možnost **Kopírovat úplnou cestu**.

1. Otevřete příkazový řádek a přejděte do složky pro *publikování* . Zadejte `cd` a vložte úplnou cestu. Příklad:

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. Spusťte aplikaci pomocí spustitelného souboru:

   1. Zadejte `HelloWorld.exe` a stiskněte klávesu ENTER.

   1. Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.

1. Spusťte aplikaci pomocí `dotnet` příkazu:

   1. Zadejte `dotnet HelloWorld.dll` a stiskněte klávesu ENTER.

   1. Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.

## <a name="additional-resources"></a>Další zdroje

- [Nasazení aplikace .NET Core](../deploying/index.md)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste publikovali konzolovou aplikaci. V dalším kurzu vytvoříte knihovnu tříd.

> [!div class="nextstepaction"]
> [Vytvoření knihovny .NET Standard v sadě Visual Studio](library-with-visual-studio.md)
