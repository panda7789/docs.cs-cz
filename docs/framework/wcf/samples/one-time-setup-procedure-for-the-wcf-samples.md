---
title: Jednorázový postup nastavení pro ukázky Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 954ec04d2ef1ca7667b4f75a8a6652010b5dbd33
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121621"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Jednorázový postup nastavení pro ukázky Windows Communication Foundation

Většina ukázek WCF (Windows Communication Foundation) je hostována v Internetové informační službě (IIS) a je spuštěna ze společného virtuálního adresáře. Tento jednorázový postup nastavení vytvoří složku na disku. přidá také virtuální adresář do služby IIS s názvem **ServiceModelSamples**.

Virtuální adresář **ServiceModelSamples** se používá pro vytváření a spouštění všech ukázek, které používají službu hostovací služby IIS. Toto je jediný virtuální adresář, který je nutný ke spuštění ukázek. Vytvoření ukázky nahradí všechny dříve nasazené služby v tomto virtuálním adresáři; v tomto virtuálním adresáři budou nasazeny a k dispozici pouze naposledy sestavené ukázky.

> [!NOTE]
> Je nutné spustit všechny příkazy pod účtem místního správce. Používáte-li systém Windows 7, Windows Vista nebo Windows Server 2008 R2, je třeba spustit také příkazový řádek se zvýšenými oprávněními. Chcete-li tak učinit, klepněte pravým tlačítkem myši na ikonu příkazového řádku a potom klepněte na příkaz **Spustit jako správce**. Všechny příkazy v tomto tématu musí být spuštěny v příkazovém řádku, který má odpovídající nastavení cesty.  Nejjednodušší způsob, jak to zajistit, je pomocí příkazového řádku sady Visual Studio. Chcete-li otevřít tuto výzvu, klepněte na tlačítko **Start**, vyberte **položku Všechny programy**, přejděte dolů do sady Visual Studio **2010**, vyberte **položku Nástroje sady Visual Studio**, klepněte pravým tlačítkem myši na **příkazový řádek sady Visual Studio (2010)** a potom klepněte na příkaz **Spustit jako správce**. Pokud máte nainstalovanou jednu z edic sady Visual Studio Express, není tento příkazový řádek k dispozici a do systémové cesty bude nutné přidat "C:\Windows\Microsoft.Net\Framework\v4.0".

### <a name="one-time-setup-procedure-for-wcf-samples"></a>Jednorázový postup nastavení vzorků WCF

1. Ujistěte se, že je nastaveno ASP.NET. Další informace o nastavení ASP.NET naleznete v tématu [Pokyny k hostování internetové informační služby](internet-information-service-hosting-instructions.md).

2. Ujistěte se, že je nainstalována rozhraní .NET Framework 4. Vyhledejte v následujícím adresáři soubor v4.0 (nebo novější): **\Windows\Microsoft.NET\Framework**

3. Ujistěte se, že máte nainstalovanou visual studio 2012 nebo novější, nebo je váš operační systém Windows Server 2008 SP2 nebo novější.

4. Spusťte následující příkazy. Další informace o tom, proč je nutné tyto příkazy spustit, naleznete v [tématu Selhání hostované služby služby IIS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > Pokud je iis přeinstalován, bude nutné znovu spustit následující příkazy.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > Spuštění příkazu `aspnet_regiis –i –enable` způsobí spuštění výchozího fondu aplikací pomocí rozhraní .NET Framework 4, což může způsobit problémy s nekompatibilitou pro jiné aplikace ve stejném počítači.

5. Podle [pokynů brány firewall](firewall-instructions.md) povolte porty používané ukázkami.

6. Zkontrolujte následující výchozí \<adresář: InstallDrive>:**\WF_WCF_Samples**. Pokud byly ukázky dříve nainstalovány, jedná se o výchozí adresář.

7. Pokud ukázky nejsou nainstalovány, nainstalujte je z [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

8. Po instalaci ukázek přejděte na : \<InstallDrive>:**\WF_WCF_Samples\WCF\Setup\\ **

9. Spusťte dávkový soubor **Setupvroot.bat.** Jsou prováděny následující kroky:

    - Virtuální adresář je vytvořen ve službě IIS s názvem ServiceModelSamples.

    - Nové diskové adresáře jsou vytvořeny s názvem %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples a %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.

    Pokud chcete tyto adresáře nastavit ručně, přečtěte si [pokyny k instalaci virtuálního adresáře](virtual-directory-setup-instructions.md). Chcete-li vrátit všechny změny provedené v tomto kroku, spusťte cleanupvroot.bat po dokončení použití vzorků.

    > [!NOTE]
    > Tento postup musí být proveden pouze jednou v počítači, pokud není spuštěn soubor cleanupvroot.bat.

10. Je nutné udělit oprávnění k úpravám %SystemDrive%\inetpub\wwwroot k účtu, pod kterým vytváříte vzorky, a pro uživatele síťové služby. Při vytváření, některé webové hostované ukázky se může pokusit zkopírovat zkompilované binární soubory do výše uvedeného umístění a pokud jste nenastavili příslušná oprávnění, sestavení se přeruší. Případně můžete ponechat oprávnění tak, jak jsou, a spustit příkazový řádek sady SDK nebo příkazový řádek sady Visual Studio (2012) jako správce nebo vytvořit ukázky v sadě Visual Studio 2012, která jsou také spuštěna jako správce.

    > [!NOTE]
    > Pokud tento krok není dokončen, všechny ukázky hostované ve správě iis se nezdaří při vytváření. Ujistěte se, že jste správně nastavili oprávnění, nebo spusťte příkazový řádek sady SDK i příkazový řádek sady Visual Studio (2012) jako správce.

11. Vytvořte v počítači adresář C:\logs; některé vzorky by to mohly očekávat. Ujistěte se, že příslušný účet má přístup pro zápis udělený této složce. V systémech Windows 7, Windows Vista a Windows Server 2008 R2 je tento účet **síťovým účtem**. V systému Windows Server 2008 je účet NT Authority\Network Service. V systémech Windows XP a Windows Server 2003 je účet aspnet.

12. Spusťte soubor Setupcerttool.bat. Tento soubor je \<umístěn ve složce InstallPath>\WF_WCF_Samples\WCF\Setup\.  Tento skript provede následující úkoly:

    - Vytvořte nástroj FindPrivateKey.

    - Vytvořte adresář s názvem %ProgramFiles%\ServiceModelSampleTools.

    - Zkopírujte nový nástroj FindPrivateKey do tohoto adresáře.

    Tento nástroj je vyžadován ukázkami, které používají certifikáty a jsou hostovány ve službách IIS.

    > [!NOTE]
    > Z bezpečnostních důvodů nezapomeňte odebrat definici virtuálního adresáře a oprávnění udělená ve výše uvedených krocích nastavení spuštěním dávkového souboru s názvem Cleanupvroot.bat po dokončení vzorků.

13. Ukázky, které jsou hostované samostatně (nejsou hostovány ve službě IIS), vyžadují oprávnění k registraci adres HTTP v počítači pro naslouchání. Oprávnění pro rezervaci oboru názvů HTTP pochází z uživatelského účtu použitého ke spuštění ukázky. Ve výchozím nastavení mají účty správce oprávnění k registraci libovolné adresy HTTP. Účty bez oprávnění správce musí mít oprávnění pro obory názvů HTTP používané ukázkami. Další informace o konfiguraci rezervací oboru názvů naleznete v [tématu Konfigurace protokolů HTTP a HTTPS](../feature-details/configuring-http-and-https.md).

14. Některé ukázky vyžadují službu Řízení front zpráv. Pokyny k instalaci naleznete [v tématu Instalace služby Řízení front zpráv (MSMQ).](installing-message-queuing-msmq.md)

    > [!NOTE]
    > Před spuštěním všech ukázek, které vyžadují službu Řízení front zpráv, se ujistěte, že spustíte službu MSMQ.

15. Některé ukázky vyžadují certifikáty. Informace o [instalaci certifikátu serveru Internetové informační služby (IIS) naleznete v pokynech k instalaci certifikátu serveru](iis-server-certificate-installation-instructions.md).
