---
title: 'Postup: Instalace a odinstalace služeb systému Windows'
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 8937ef8b4007253b06444e59b292395084e4df2f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607916"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Postup: Instalace a odinstalace služeb systému Windows

Pokud vyvíjíte službu Windows s rozhraním .NET Framework, můžete aplikaci služby rychle nainstalovat pomocí nástroje příkazového řádku [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) nebo [prostředí PowerShell](/powershell/scripting/overview). Vývojáři, kteří chtějí uvolnit službu systému Windows, kterou mohou uživatelé nainstalovat a odinstalovat, by měli používat program InstallShield. Další informace naleznete [v tématu Vytvoření balíčku instalačního programu (plocha systému Windows).](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)

> [!WARNING]
> Pokud chcete odinstalovat službu z počítače, nepostupujte podle pokynů v tomto článku. Místo toho zjistěte, který program nebo softwarový balíček službu nainstaloval, a pak v nastavení odinstalujte tento program výběrem **možnosti Aplikace.** Všimněte si, že mnoho služeb jsou nedílnou součástí systému Windows; Pokud je odeberete, může dojít k nestabilitě systému.

Chcete-li použít postup uvedený v tomto článku, musíte nejprve přidat instalační službu služby do služby systému Windows. Další informace naleznete [v tématu Návod: Vytvoření aplikace služby Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Projekty služeb systému Windows nelze spustit přímo z vývojového prostředí sady Visual Studio stisknutím klávesy F5. Před spuštěním projektu je nutné nainstalovat službu v projektu.

> [!TIP]
> **Pomocí Průzkumníka serveru** můžete ověřit, zda jste službu nainstalovali nebo odinstalovali. Další informace naleznete v tématu [Použití Průzkumníka serveru v sadě Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually-using-installutilexe-utility"></a>Ruční instalace služby pomocí nástroje InstallUtil.exe

1. V nabídce **Start** vyberte adresář ** \< *verze* > sady Visual Studio** a pak vyberte **příkazový řádek pro vývojáře pro \< *verzi*>VS**.

     Zobrazí se příkazový řádek vývojáře pro visual studio.

2. Získejte přístup k adresáři, ve kterém je umístěn zkompilovaný spustitelný soubor projektu.

3. *Spusťte soubor InstallUtil.exe* z příkazového řádku s spustitelným souborem projektu jako parametrem:

    ```console
    installutil <yourproject>.exe
    ```

     Pokud používáte příkazový řádek pro vývojáře pro Visual Studio, *installutil.exe* by měl být na systémové cestě. V opačném případě jej můžete přidat do cesty nebo ji vyvolat pomocí plně kvalifikované cesty. Tento nástroj je nainstalován s rozhraním .NET Framework v *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.

     Příklad:
     - Pokud je instalační adresář systému Windows *C:\Windows,* je v 32bitové verzi rozhraní .NET Framework 4 nebo 4.5 a novějších výchozí cesta *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - Pro 64bitovou verzi rozhraní .NET Framework 4 nebo 4.5 a novější je výchozí cesta *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>Odinstalace služby ručně pomocí nástroje InstallUtil.exe

1. V nabídce **Start** vyberte adresář ** \< *verze* > sady Visual Studio** a pak vyberte **příkazový řádek pro vývojáře pro \< *verzi*>VS**.

     Zobrazí se příkazový řádek vývojáře pro visual studio.

2. *Spusťte soubor InstallUtil.exe* z příkazového řádku s výstupem projektu jako parametrem:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Po odstranění spustitelného souboru služby může být služba stále přítomna v registru. V takovém případě odeberte položku služby z registru pomocí příkazu [sc delete.](/windows-server/administration/windows-commands/sc-delete)

### <a name="install-your-service-manually-using-powershell"></a>Ruční instalace služby pomocí PowerShellu

1. V nabídce **Start** vyberte adresář **prostředí Windows PowerShell** a pak vyberte **Windows PowerShell**.

2. Získejte přístup k adresáři, ve kterém je umístěn zkompilovaný spustitelný soubor projektu.

3. Spusťte rutinu [**Nové služby**](/powershell/module/microsoft.powershell.management/new-service) s výstupem projektu a názvem služby jako parametry:

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>Odinstalace služby ručně pomocí prostředí PowerShell

1. V nabídce **Start** vyberte adresář **prostředí Windows PowerShell** a pak vyberte **Windows PowerShell**.

2. Spusťte rutinu [**Odebrat službu**](/powershell/module/microsoft.powershell.management/remove-service) s názvem služby jako parametrem:

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. Po odstranění spustitelného souboru služby může být služba stále přítomna v registru. V takovém případě odeberte položku služby z registru pomocí příkazu [sc delete.](/windows-server/administration/windows-commands/sc-delete)

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>Viz také

- [Úvod do aplikací služeb systému Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Postup: Vytvoření služeb systému Windows](../windows-services/how-to-create-windows-services.md)
- [Postup: Přidání instalačních programů do aplikace služby](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (instalační nástroj)](../tools/installutil-exe-installer-tool.md)
