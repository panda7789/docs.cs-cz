---
title: Publikování aplikace .NET Core Hello World pomocí sady Visual Studio
description: Publikování vytvoří sadu souborů, které jsou potřebné ke spuštění aplikace .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156631"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>Publikování aplikace .NET Core Hello World pomocí sady Visual Studio

V [při vytváření aplikace Hello World s rozhraním .NET Core v sadě Visual Studio](with-visual-studio.md)jste vytvořili konzolovou aplikaci Hello World. V [ladění aplikace Hello World s Visual Studio](debugging-with-visual-studio.md), jste testovali pomocí ladicího programu Visual Studio. Nyní, když jste si jisti, že funguje podle očekávání, můžete publikovat tak, aby ostatní uživatelé mohli spustit. Publikování vytvoří sadu souborů, které jsou potřebné ke spuštění aplikace. Chcete-li nasadit soubory, zkopírujte je do cílového počítače.

## <a name="publish-the-app"></a>Publikování aplikace

1. Ujistěte se, že Visual Studio vytváří verzi aplikace. V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z **Ladění** na **Uvolnit**.

   ![Panel nástrojů sady Visual Studio s vybranou verzí](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Klikněte pravým tlačítkem myši na projekt **HelloWorld** (ne na řešení HelloWorld) a z nabídky vyberte **Publikovat.** (Můžete také vybrat **Publikovat HelloWorld** z hlavní nabídky **sestavení.)**

   ![Kontextová nabídka Publikování v sadě Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. Na stránce **Vybrat cílovou** publikování vyberte **Složku**a pak **vyberte Vytvořit profil**.

   ![Výběr cíle publikování v Sadě Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. Na stránce **Publikovat** vyberte **Publikovat**.

   ![Okno Publikování v sadě Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>Kontrola souborů

Proces publikování vytvoří nasazení závislé na rozhraní, což je typ nasazení, kde publikovaná aplikace běží na libovolné platformě podporované rozhraním .NET Core s rozhraním .NET Core nainstalovaným v systému. Uživatelé mohou publikovanou aplikaci spustit poklepáním na `dotnet HelloWorld.dll` spustitelný soubor nebo vydáním příkazu z příkazového řádku.

V následujících krocích se podíváte na soubory vytvořené procesem publikování.

1. Otevřete příkazový řádek.

   Jedním ze způsobů, jak otevřít příkazový řádek, je zadat **příkazový řádek** (nebo **zkráceně cmd)** do vyhledávacího pole na hlavním panelu systému Windows. Vyberte aplikaci **Command Prompt** desktop nebo stiskněte **Enter,** pokud už je ve výsledcích hledání vybraná.

1. Přejděte do publikované aplikace v *přihrádce\Release\netcoreapp3.1\publikovat* podadresář adresáře projektu aplikace.

   ![Okno konzoly zobrazující publikované soubory](media/publishing-with-visual-studio/published-files-output.png)

   Jak ukazuje obrázek, publikovaný výstup obsahuje následující soubory:

      * *HelloWorld.deps.json*

         Toto je soubor závislostí runtime aplikace. Definuje součásti .NET Core a knihovny (včetně knihovny dynamických odkazů, která obsahuje vaši aplikaci) potřebné ke spuštění aplikace. Další informace naleznete v [tématu Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld.dll*

         Toto je [verze nasazení závislé na rámci](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace. Chcete-li spustit tuto `dotnet HelloWorld.dll` dynamickou knihovnu odkazů, zadejte na příkazovém řádku.

      * *HelloWorld.exe*

         Toto je spustitelná verze aplikace [závislá na rozhraní.](../deploying/deploy-with-cli.md#framework-dependent-executable) Chcete-li jej `HelloWorld.exe` spustit, zadejte příkazový řádek.

      * *HelloWorld.pdb* (volitelné pro nasazení)

         Toto je soubor ladicí symboly. Není nutné nasadit tento soubor spolu s vaší aplikací, i když byste měli uložit v případě, že budete muset ladit publikovanou verzi aplikace.

      * *HelloWorld.runtimeconfig.json*

         Toto je konfigurační soubor aplikace za běhu. Identifikuje verzi .NET Core, na které byla vaše aplikace vytvořena. Můžete také přidat možnosti konfigurace. Další informace naleznete v [tématu Nastavení konfigurace rozhraní .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).

## <a name="additional-resources"></a>Další zdroje

- [Nasazení aplikace .NET Core](../deploying/index.md)
