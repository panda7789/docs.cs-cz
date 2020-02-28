---
title: Publikování aplikace Hello World .NET Core pomocí sady Visual Studio
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156631"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>Publikování aplikace Hello World .NET Core pomocí sady Visual Studio

V části [vytvoření Hello World aplikace pomocí .NET Core v aplikaci Visual Studio](with-visual-studio.md)jste vytvořili konzolovou aplikaci Hello World. V části [ladění aplikace Hello World pomocí aplikace Visual Studio](debugging-with-visual-studio.md)jste otestovali pomocí ladicího programu sady Visual Studio. Teď, když jste si jisti, že funguje podle očekávání, můžete ji publikovat, aby ji ostatní uživatelé mohli spustit. Publikování vytvoří sadu souborů, které jsou nutné ke spuštění vaší aplikace. Chcete-li nasadit soubory, zkopírujte je do cílového počítače.

## <a name="publish-the-app"></a>Publikování aplikace

1. Ujistěte se, že Visual Studio sestavuje prodejní verzi vaší aplikace. V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z části **ladit** na **verzi**.

   ![Panel nástrojů sady Visual Studio s vybraným sestavením pro vydání](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Klikněte pravým tlačítkem na projekt **HelloWorld** (ne na řešení HelloWorld) a v nabídce vyberte **publikovat** . (Můžete také vybrat **publikovat HelloWorld** z hlavní nabídky **sestavení** .)

   ![Místní nabídka publikování Visual studia](media/publishing-with-visual-studio/publish-context-menu.png)

1. Na stránce **Vyberte cíl publikování** vyberte **Složka**a pak vyberte **vytvořit profil**.

   ![Výběr cíle publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. Na stránce **publikovat** vyberte **publikovat**.

   ![Okno pro publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>Kontrola souborů

Proces publikování vytvoří nasazení závislé na rozhraní, což je typ nasazení, ve kterém je publikovaná aplikace spuštěna na libovolné platformě podporované rozhraním .NET Core s nainstalovaným rozhraním .NET Core v systému. Uživatelé můžou publikovanou aplikaci spustit dvojitým kliknutím na spustitelný soubor nebo vyvoláním příkazu `dotnet HelloWorld.dll` z příkazového řádku.

V následujících krocích se podíváte na soubory vytvořené procesem publikování.

1. Otevřete příkazový řádek.

   Jedním ze způsobů, jak otevřít příkazový řádek, je zadat **příkazový řádek** (nebo program **cmd** pro krátké) do vyhledávacího pole na hlavním panelu Windows. Vyberte desktopovou aplikaci na **příkazovém řádku** nebo stiskněte klávesu **ENTER** , pokud už je ve výsledcích hledání vybraná.

1. Přejděte k publikované aplikaci v podadresáři *bin\Release\netcoreapp3.1\publish* adresáře projektu aplikace.

   ![Okno konzoly zobrazující publikované soubory](media/publishing-with-visual-studio/published-files-output.png)

   Jak ukazuje obrázek, publikovaný výstup obsahuje následující soubory:

      * *HelloWorld. DEPS. JSON*

         Toto je soubor závislostí modulu runtime aplikace. Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaši aplikaci) potřebnou ke spuštění aplikace. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld. dll*

         Toto je verze [nasazení závislá na rozhraní](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace. Chcete-li spustit tuto dynamickou knihovnu, zadejte `dotnet HelloWorld.dll` do příkazového řádku.

      * *Soubor HelloWorld. exe*

         Toto je [spustitelná](../deploying/deploy-with-cli.md#framework-dependent-executable) verze aplikace závislá na rozhraní. Pokud ho chcete spustit, zadejte `HelloWorld.exe` do příkazového řádku.

      * *HelloWorld. pdb* (volitelné pro nasazení)

         Toto je soubor se symboly ladění. Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.

      * *HelloWorld. runtimeconfig. JSON*

         Toto je konfigurační soubor modulu runtime aplikace. Identifikuje verzi .NET Core, na které byla aplikace sestavena. Můžete také přidat možnosti konfigurace. Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="additional-resources"></a>Další zdroje

- [Nasazení aplikace .NET Core](../deploying/index.md)
