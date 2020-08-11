---
title: 'Postupy: instalace a odinstalace služeb systému Windows'
description: Viz jak nainstalovat a odinstalovat služby systému Windows. Pokud vyvíjíte službu systému Windows s rozhraním .NET, můžete použít InstallUtil.exe nebo PowerShell.
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
ms.openlocfilehash: 883b587a7ef60bc686d6f453c775f6651f0ccb7f
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063819"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Postupy: instalace a odinstalace služeb systému Windows

Pokud vyvíjíte službu pro Windows s .NET Framework, můžete rychle nainstalovat aplikaci služby pomocí nástroje příkazového řádku [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) nebo [PowerShellu](/powershell/scripting/overview). Vývojáři, kteří chtějí uvolnit službu systému Windows, kterou mohou uživatelé instalovat a odinstalovat, můžou používat bezplatné sady [nástrojů WIX](https://wixtoolset.org/) nebo komerční nástroje, jako je [pokročilý instalační program](https://www.advancedinstaller.com/), [InstallShield](https://www.revenera.com/install/products/installshield.html)nebo jiné. Další informace najdete v tématu [Vytvoření instalačního balíčku (Desktop Windows)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

> [!WARNING]
> Pokud chcete odinstalovat službu z počítače, neprovádějte postup v tomto článku. Místo toho Zjistěte, který program nebo softwarový balíček službu nainstaloval, a pak zvolte možnost **aplikace** v nastavení pro odinstalaci tohoto programu. Všimněte si, že mnoho služeb je nedílnou součástí Windows. Pokud je odstraníte, může to způsobit nestabilitu systému.

Chcete-li použít kroky v tomto článku, musíte nejprve přidat do služby systému Windows Instalační program služby. Další informace najdete v tématu [Návod: Vytvoření aplikace služby systému Windows](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Nemůžete spustit projekty služby Windows přímo z vývojového prostředí sady Visual Studio stisknutím klávesy F5. Předtím, než můžete spustit projekt, je nutné nainstalovat službu do projektu.

> [!TIP]
> Pomocí **Průzkumník serveru** můžete ověřit, že jste nainstalovali nebo odinstalovali vaši službu. Další informace najdete v tématu [Jak používat Průzkumník serveru v aplikaci Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually-using-installutilexe-utility"></a>Ruční instalace služby pomocí nástroje InstallUtil.exe

1. V nabídce **Start** vyberte adresář sady **Visual Studio \<*version*> ** a potom vyberte **Developer Command Prompt pro vs \<*version*> **.

     Zobrazí se Developer Command Prompt pro Visual Studio.

2. Přejděte do adresáře, kde se nachází kompilovaný spustitelný soubor projektu.

3. Spusťte *InstallUtil.exe* z příkazového řádku se spustitelným souborem projektu jako parametr:

    ```console
    installutil <yourproject>.exe
    ```

     Pokud používáte Developer Command Prompt pro Visual Studio, *InstallUtil.exe* by měla být v systémové cestě. V opačném případě ji můžete přidat do cesty nebo použít úplnou cestu k jejímu vyvolání. Tento nástroj se instaluje s .NET Framework v *%windir%\Microsoft.NET\Framework [64] \\<framework_version \> *.

     Příklad:
     - Pro 32 verze .NET Framework 4 nebo 4,5 a novější, pokud je instalační adresář systému Windows *C:\Windows*, je výchozí cesta *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - Pro 64 verze .NET Framework 4 nebo 4,5 a novější je výchozí cesta *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>Ruční odinstalace služby pomocí nástroje InstallUtil.exe

1. V nabídce **Start** vyberte adresář sady **Visual Studio \<*version*> ** a potom vyberte **Developer Command Prompt pro vs \<*version*> **.

     Zobrazí se Developer Command Prompt pro Visual Studio.

2. Spusťte *InstallUtil.exe* z příkazového řádku s výstupem projektu jako parametr:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Po odstranění spustitelného souboru pro službu může být služba v registru stále k dispozici. V takovém případě pomocí příkazu [sc delete](/windows-server/administration/windows-commands/sc-delete) odeberte položku služby z registru.

### <a name="install-your-service-manually-using-powershell"></a>Ruční instalace služby pomocí PowerShellu

1. V nabídce **Start** vyberte adresář **Windows PowerShell** a pak vyberte **Windows PowerShell**.

2. Přejděte do adresáře, kde se nachází kompilovaný spustitelný soubor projektu.

3. Spusťte rutinu [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) s výstupem vašeho projektu a názvem služby jako parametry:

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>Ruční odinstalace služby pomocí PowerShellu

1. V nabídce **Start** vyberte adresář **Windows PowerShell** a pak vyberte **Windows PowerShell**.

2. Spusťte rutinu [**remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) s názvem vaší služby jako parametr:

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. Po odstranění spustitelného souboru pro službu může být služba v registru stále k dispozici. V takovém případě pomocí příkazu [sc delete](/windows-server/administration/windows-commands/sc-delete) odeberte položku služby z registru.

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>Viz také

- [Úvod do aplikací služby systému Windows](introduction-to-windows-service-applications.md)
- [Postupy: vytváření služeb systému Windows](how-to-create-windows-services.md)
- [Postupy: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (instalační nástroj)](../tools/installutil-exe-installer-tool.md)
