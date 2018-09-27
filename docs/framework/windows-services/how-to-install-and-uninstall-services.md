---
title: 'Postupy: Instalace a odinstalace služeb'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: eb68809909c0550ea5fa5eab1f9d5ca6a069e314
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232726"
---
# <a name="how-to-install-and-uninstall-services"></a>Postupy: Instalace a odinstalace služeb
Vyvíjíte služby Windows s použitím rozhraní .NET Framework, můžete rychle nainstalovat aplikaci služby pomocí nástroje příkazového řádku InstallUtil.exe volána. Pokud jste vývojář, kdo chce vydání služby Windows, mohou uživatelé nainstalovat a odinstalovat jste používali InstallShield. Zobrazit [nasazení Instalační služby systému Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
> [!WARNING]
>  Pokud chcete z počítače odinstalovat službu, není postupujte podle kroků v tomto článku. Místo toho zjistit službu nainstalované balíčky, které program nebo software a pak zvolte **přidat nebo odebrat programy** v Ovládacích panelech odinstalujte tohoto programu. Všimněte si, že mnoho služeb jsou nedílnou součástí Windows; Pokud je odstraníte, může způsobit nestabilitu systému.  
  
 Chcete-li použít postup v tomto článku, musíte nejprve přidat instalační program služby do služby Windows. Zobrazit [návod: vytváření Windows aplikace v Návrháři součástí služby](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Projekty služeb Windows nelze spustit přímo z vývojového prostředí sady Visual Studio stisknutím klávesy F5. Je to proto musí být nainstalována služba v projektu, abyste mohli spustit projekt.  
  
> [!TIP]
>  Můžete spustit **Průzkumníka serveru** a ověřte, zda má vaše služba nainstalovat nebo odinstalovat. Další informace najdete v tématu Postupy: přístup a inicializace Průzkumníka serveru Průzkumníka databáze.  
  
### <a name="to-install-your-service-manually"></a>Ruční instalace služby  
  
1.  V Windows **Start** nabídky nebo **Start** obrazovce **sady Visual Studio** , **Visual Studio Tools**, **pro vývojáře Příkazový řádek**.  
  
     Zobrazí se příkazový řádek sady Visual Studio.  
  
2.  Přístup k adresáři, kde se nachází zkompilovaný spustitelný soubor projektu.  
  
3.  Spusťte InstallUtil.exe z příkazového řádku s projektem spustitelného souboru jako parametru:  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Pokud používáte příkazový řádek sady Visual Studio, InstallUtil.exe by měla být v systémové cestě. Pokud ne, můžete ho přidat do cesty nebo použijte plně kvalifikovanou cestu k vyvolání ho. Tento nástroj je nainstalován pomocí rozhraní .NET Framework a je jeho cesta `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`. Například pro 32bitovou verzi rozhraní .NET Framework 4 nebo 4.5. *, pokud váš instalační adresář Windows C:\Windows, cesta je `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`. Pro 64bitové verze rozhraní .NET Framework 4 nebo 4.5. \*, výchozí cesta je `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.  
  
### <a name="to-uninstall-your-service-manually"></a>Ruční odinstalování služby  
  
1.  V Windows **Start** nabídky nebo **Start** obrazovce **sady Visual Studio**, **Visual Studio Tools**, **pro vývojáře Příkazový řádek**.  
  
     Zobrazí se příkazový řádek sady Visual Studio.  
  
2.  Spusťte InstallUtil.exe z příkazového řádku s výstupy projektu jako parametr:  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  V některých případech po odstranění spustitelný soubor pro službu služby může být v registru. V takovém případě použijte příkaz [sc delete](https://technet.microsoft.com/library/cc742045.aspx) pro odebrání položky služby z registru.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Installutil.exe (instalační nástroj)](../../../docs/framework/tools/installutil-exe-installer-tool.md)
