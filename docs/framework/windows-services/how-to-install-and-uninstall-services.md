---
title: 'Postupy: Instalace a odinstalace služeb Windows'
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
ms.openlocfilehash: 4f6e25467e713263ab5cdecc08078153098fdede
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690688"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Postupy: Instalace a odinstalace služeb Windows

Pokud vytváříte službu Windows s použitím rozhraní .NET Framework, můžete rychle nainstalovat aplikaci služby pomocí [ *InstallUtil.exe* ](../tools/installutil-exe-installer-tool.md) nástroj příkazového řádku. Vývojáři, kteří chtějí vydání služby Windows, které mohou uživatelé nainstalovat a odinstalovat používali InstallShield. Další informace najdete v tématu [vytvoření instalačního balíčku (Windows klient)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).

> [!WARNING]
> Pokud chcete z počítače odinstalovat službu, není postupujte podle kroků v tomto článku. Místo toho zjistit službu nainstalované balíčky, které program nebo software a pak zvolte **aplikace** v nastavení k odinstalaci tohoto programu. Všimněte si, že mnoho služeb jsou nedílnou součástí Windows; Pokud je odstraníte, může způsobit nestabilitu systému.

Pokud chcete použít kroky v tomto článku, musíte nejprve přidat instalační program služby do služby Windows. Další informace najdete v tématu [názorný postup: Vytvoření aplikace služby Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Projekty služeb Windows nelze spustit přímo z vývojového prostředí sady Visual Studio stisknutím klávesy F5. Předtím, než spustíte projekt, je nutné nainstalovat službu v projektu.

> [!TIP]
> Můžete použít **Průzkumníka serveru** k ověření, že jste nainstalována nebo odinstalována vaší služby. Další informace najdete v tématu [použití Průzkumníku serveru v sadě Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually"></a>Ruční instalace služby

1. Z **Start** nabídku, vyberte **sady Visual Studio \< *verze* >**  adresář a potom vyberte **Developer Command Prompt pro VS \< *verze*>** .

     Zobrazí se příkazový řádek pro vývojáře pro sadu Visual Studio.

2. Přístup k adresáři, kde se nachází zkompilovaný spustitelný soubor projektu.

3. Spustit *InstallUtil.exe* příkazovém řádku s projektem spustitelného souboru jako parametr:

    ```console
    installutil <yourproject>.exe
    ```

     Pokud používáte Developer Command Prompt pro sadu Visual Studio *InstallUtil.exe* by měly být v systémové cestě. V opačném případě můžete přidat do cesty nebo použijte plně kvalifikovanou cestu k vyvolání jeho. Tento nástroj je nainstalován pomocí rozhraní .NET Framework v *% WINDIR%\Microsoft.NET\Framework[64]\\< framework_version\>* .

     Příklad:
     - Pro 32bitové verze rozhraní .NET Framework 4 nebo 4.5 nebo novější, pokud je váš instalační adresář Windows *C:\Windows*, výchozí cesta je *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - Pro 64bitové verze rozhraní .NET Framework 4 nebo 4.5 nebo novější, výchozí cesta je *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually"></a>Ruční odinstalování služby

1. Z **Start** nabídku, vyberte **sady Visual Studio \< *verze* >**  adresář a potom vyberte **Developer Command Prompt pro VS \< *verze*>** .

     Zobrazí se příkazový řádek pro vývojáře pro sadu Visual Studio.

2. Spustit *InstallUtil.exe* z příkazového řádku s výstupy projektu jako parametr:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Služba může být v registru po odstranění spustitelný soubor pro službu. Pokud je to tento případ, použijte příkaz [sc delete](/windows-server/administration/windows-commands/sc-delete) pro odebrání položky služby z registru.

## <a name="see-also"></a>Viz také:

- [Úvod do aplikace služby Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Postupy: Vytvoření služeb Windows](../windows-services/how-to-create-windows-services.md)
- [Postupy: Přidání instalačních programů do aplikace služby](../windows-services/how-to-add-installers-to-your-service-application.md)
- [InstallUtil.exe (instalační nástroj)](../tools/installutil-exe-installer-tool.md)
