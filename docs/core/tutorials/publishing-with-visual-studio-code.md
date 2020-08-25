---
title: Publikování konzolové aplikace .NET Core pomocí Visual Studio Code
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
ms.date: 07/04/2020
ms.openlocfilehash: 04dfbae85f196ca4c8f8eb593637a801aa9773f2
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811389"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-code"></a>Kurz: publikování konzolové aplikace .NET Core pomocí Visual Studio Code

V tomto kurzu se dozvíte, jak publikovat konzolovou aplikaci, aby ji ostatní uživatelé mohli spustit. Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace. Chcete-li nasadit soubory, zkopírujte je do cílového počítače.

.NET Core CLI slouží k publikování aplikace, takže můžete postupovat podle tohoto kurzu s jiným editorem kódu, než Visual Studio Code, pokud dáváte přednost.

## <a name="prerequisites"></a>Předpoklady

- Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v Visual Studio Code](with-visual-studio-code.md).

## <a name="publish-the-app"></a>Publikování aplikace

1. Spuštění nástroje Visual Studio Code

1. Otevřete složku projektu *HelloWorld* , kterou jste vytvořili v [části Vytvoření konzolové aplikace .net Core v Visual Studio Code](with-visual-studio-code.md).

1. V hlavní nabídce vyberte **Zobrazit**  >  **terminál** .

   Terminál se otevře ve složce *HelloWorld* .

1. Spusťte následující příkaz:

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   Výchozí konfigurace sestavení je *ladění*, takže tento příkaz určuje konfiguraci sestavení pro *vydání* . Výstup konfigurace sestavení verze obsahuje minimální symbolické informace o ladění a je plně optimalizován.

   Výstup příkazu je podobný následujícímu příkladu:

   ```output
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a>Kontrola souborů

Ve výchozím nastavení vytvoří proces publikování nasazení závislé na rozhraní, což je typ nasazení, ve kterém je publikovaná aplikace spuštěna na počítači s nainstalovanou modulem runtime .NET Core. Pokud chcete spustit publikovanou aplikaci, můžete použít spustitelný soubor nebo spustit `dotnet HelloWorld.dll` příkaz z příkazového řádku.

V následujících krocích se podíváte na soubory vytvořené procesem publikování.

1. Vyberte **Průzkumníka** v levém navigačním panelu.

1. Rozbalte položku *Přihrádka/Release/netcoreapp 3.1/Publish*.

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Průzkumník zobrazující publikované soubory":::

   Jak ukazuje obrázek, publikovaný výstup obsahuje následující soubory:

   * *HelloWorld.deps.jsna*

      Toto je soubor závislostí modulu runtime aplikace. Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaši aplikaci) potřebnou ke spuštění aplikace. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

   * *HelloWorld.dll*

      Toto je verze [nasazení závislá na rozhraní](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace. Chcete-li spustit tuto dynamickou knihovnu, zadejte `dotnet HelloWorld.dll` na příkazovém řádku. Tato metoda spuštění aplikace funguje na libovolné platformě, na které je nainstalovaný modul runtime .NET Core.

   * *HelloWorld.exe* (*HelloWorld* v systému Linux, nevytvoří se v MacOS.)

      Toto je [spustitelná](../deploying/deploy-with-cli.md#framework-dependent-executable) verze aplikace závislá na rozhraní. Soubor je specifický pro operační systém.

   * *HelloWorld. pdb* (volitelné pro nasazení)

      Toto je soubor se symboly ladění. Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.

   * *HelloWorld.runtimeconfig.jsna*

      Toto je konfigurační soubor modulu runtime aplikace. Identifikuje verzi .NET Core, na které byla aplikace sestavena. Můžete také přidat možnosti konfigurace. Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Spuštění publikované aplikace

1. V **Průzkumníkovi**klikněte pravým tlačítkem na složku pro *publikování* (<kbd>stisknutím klávesy CTRL</kbd>a kliknutím na MacOS) a vyberte **otevřít v terminálu**.

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Místní nabídka, která zobrazuje otevření v terminálu":::

1. V systému Windows nebo Linux spusťte aplikaci pomocí spustitelného souboru.

   1. V systému Windows zadejte `.\HelloWorld.exe` a stiskněte klávesu <kbd>ENTER</kbd>.

   1. V systému Linux zadejte `./HelloWorld` a stiskněte klávesu <kbd>ENTER</kbd>.

   1. Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.

1. Na libovolné platformě spusťte aplikaci pomocí  [`dotnet`](../tools/dotnet.md) příkazu:

   1. Zadejte `dotnet HelloWorld.dll` a stiskněte klávesu <kbd>ENTER</kbd>.

   1. Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.

## <a name="additional-resources"></a>Další zdroje

- [Nasazení aplikace .NET Core](../deploying/index.md)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste publikovali konzolovou aplikaci. V dalším kurzu vytvoříte knihovnu tříd.

> [!div class="nextstepaction"]
> [Vytvoření knihovny .NET Standard v Visual Studio Code](library-with-visual-studio-code.md)
