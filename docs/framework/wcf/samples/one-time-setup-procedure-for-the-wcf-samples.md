---
title: Jednorázový postup nastavení pro ukázky Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 7dbc4a1b5235c0cb6aa154379358c7761bc4ab1d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141854"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Jednorázový postup nastavení pro ukázky Windows Communication Foundation

Většina ukázek Windows Communication Foundation (WCF) se hostuje v Internetová informační služba (IIS) a spouští se ze společného virtuálního adresáře. Tento jednorázový postup nastavení vytvoří složku na disku. také přidá virtuální adresář do služby IIS s názvem **ServiceModelSamples**.

Virtuální adresář **ServiceModelSamples** se používá k sestavování a spouštění všech ukázek, které používají službu HOSTOVANOU službou IIS. Toto je jediný virtuální adresář, který je nutný ke spuštění ukázek. Při vytváření ukázky se nahradí všechny dříve nasazené služby v tomto virtuálním adresáři. v tomto virtuálním adresáři bude nasazená a dostupná jenom naposledy vytvořená ukázka.

> [!NOTE]
> Všechny příkazy musíte spustit pod účtem místního správce. Pokud používáte Windows 7, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]nebo Windows Server 2008 R2, musíte spustit taky příkazový řádek se zvýšenými oprávněními. Provedete to tak, že kliknete pravým tlačítkem myši na ikonu příkazového řádku a potom kliknete na **Spustit jako správce**. Všechny příkazy v tomto tématu musí být spuštěny v příkazovém řádku, který má odpovídající nastavení cesty.  Nejjednodušší způsob, jak to zajistit, je použít příkazový řádek sady Visual Studio. Chcete-li otevřít tuto výzvu, klikněte na tlačítko **Start**, vyberte možnost **všechny programy**, přejděte dolů k **aplikaci Visual studio 2010**, vyberte možnost **Visual Studio Tools**, klikněte pravým tlačítkem myši na položku **Visual Studio Command Prompt (2010)** a poté klikněte na příkaz **Spustit jako správce** . Pokud máte nainstalovánu jednu z nainstalovaných edicí Visual Studio Express, Tento příkazový řádek není k dispozici a bude nutné přidat "C:\Windows\Microsoft.Net\Framework\v4.0" do systémové cesty.

### <a name="one-time-setup-procedure-for-wcf-samples"></a>Jednorázový postup nastavení pro ukázky WCF

1. Ujistěte se, že je nastavené ASP.NET. Další informace o tom, jak nastavit ASP.NET, najdete v tématu [pokyny pro hostování internetové informační služby](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).

2. Ujistěte se, že je nainstalovaná .NET Framework 4. V tomto adresáři vyhledejte v 4.0 (nebo novějším): **\WINDOWS\Microsoft.NET\Framework**

3. Pokud není nainstalováno Visual Studio 2012 a váš operační systém není Windows Server 2008 SP2 nebo novější, nainstalujte [opravu Hotfix 251798](https://go.microsoft.com/fwlink/?LinkId=184693).

4. Spusťte následující příkazy. Další informace o tom, proč je nutné tyto příkazy spustit, najdete v tématu [služba hostovaná službou IIS se nezdařila](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).

    > [!WARNING]
    > Pokud dojde k přeinstalování služby IIS, bude nutné znovu spustit následující příkazy.

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > Spuštěním příkazu `aspnet_regiis –i –enable` nastavíte výchozí fond aplikací s využitím .NET Framework 4, což může způsobit problémy s nekompatibilitou pro jiné aplikace ve stejném počítači.

5. Pokud chcete povolit porty používané ukázkami, postupujte podle [pokynů pro bránu firewall](../../../../docs/framework/wcf/samples/firewall-instructions.md) .

6. Ověřte následující výchozí adresář: \<InstallDrive >: **\ WF_WCF_Samples**. Pokud byly ukázky dříve nainstalovány, jedná se o výchozí adresář.

7. Pokud ukázky nejsou nainstalovány, nainstalujte je z umístění pro stažení ukázek pro [C#](https://go.microsoft.com/fwlink/?LinkId=190939).

8. Po instalaci ukázek použijte: \<InstallDrive >: **\ WF_WCF_Samples \wcf\setup\\**

9. Spusťte dávkový soubor **Setupvroot. bat** . Provedou se následující kroky:

    - Virtuální adresář se vytvoří ve službě IIS s názvem ServiceModelSamples.

    - Vytvoří se nové adresáře disků s názvem%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples a%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.

    Pokud dáváte přednost ručnímu nastavení těchto adresářů, přečtěte si [pokyny pro instalaci virtuálního adresáře](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Chcete-li vrátit všechny změny provedené v tomto kroku, spusťte cleanupvroot. bat po dokončení používání ukázek.

    > [!NOTE]
    > Tento postup je třeba provést v počítači pouze jednou, pokud není spuštěn cleanupvroot. bat.

10. Musíte udělit oprávnění ke změně%SystemDrive%\inetpub\wwwroot účtu, pod kterým sestavíte ukázky a uživatele síťové služby. Při sestavování se některé ukázky hostované na webu mohou pokusit zkopírovat zkompilované binární soubory do výše zmíněného umístění a pokud jste nestavili příslušná oprávnění, sestavení se přeruší. Případně můžete ponechat oprávnění tak, jak jsou, a spustit příkazový řádek sady SDK nebo příkazový řádek sady Visual Studio (2012) jako správce nebo sestavit ukázky v sadě Visual Studio 2012, a to také spustit jako správce.

    > [!NOTE]
    > Pokud tento krok není dokončený, všechny ukázky hostované službou IIS při sestavování nebudou úspěšné. Ujistěte se, že jste správně nastavili oprávnění, nebo spusťte příkazový řádek sady SDK a příkazový řádek sady Visual Studio (2012) jako správce.

11. Vytvořte v počítači adresář C:\Logs.; může to očekávat několik ukázek. Ujistěte se, že příslušný účet má udělený přístup pro zápis do této složky. Pro Windows 7, [!INCLUDE[wv](../../../../includes/wv-md.md)]a Windows Server 2008 R2 je tento účet **Network Service**. Pro [!INCLUDE[lserver](../../../../includes/lserver-md.md)]účet je NT Authority\Network Service. Pro [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]je účet ASPNET.

12. Spusťte soubor setupCertTool. bat. Tento soubor je umístěný ve složce \<InstallPath > \ WF_WCF_Samples \WCF\Setup\.  Tento skript provede následující úlohy:

    - Sestavte Nástroj FindPrivateKey.

    - Vytvoření adresáře s názvem%ProgramFiles%\ServiceModelSampleTools.

    - Zkopírujte nový nástroj FindPrivateKey do tohoto adresáře.

    Tento nástroj je vyžadován ukázkami, které používají certifikáty a jsou hostovány ve službě IIS.

    > [!NOTE]
    > Z bezpečnostních důvodů nezapomeňte odebrat definici virtuálního adresáře a oprávnění udělená v krocích nastavení výše spuštěním dávkového souboru s názvem cleanupvroot. bat po dokončení práce s ukázkami.

13. Ukázky, které jsou v místním prostředí (nejsou hostované ve službě IIS), vyžadují oprávnění k registraci adres HTTP v počítači pro naslouchání. Oprávnění k rezervaci oboru názvů HTTP přichází z uživatelského účtu, který se používá ke spuštění ukázky. Ve výchozím nastavení mají účty správců oprávnění k registraci jakékoli adresy HTTP. Účtům bez oprávnění správce musí být udělena oprávnění pro obory názvů HTTP používané ukázkami. Další informace o tom, jak nakonfigurovat rezervace oboru názvů, najdete v tématu [Konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).

14. Některé ukázky vyžadují službu Řízení front zpráv. Pokyny k instalaci najdete v tématu [instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) .

    > [!NOTE]
    > Před spuštěním všech ukázek, které vyžadují službu Řízení front zpráv, se ujistěte, že jste spustili službu MSMQ.

15. Některé ukázky vyžadují certifikáty. Viz [pokyny k instalaci certifikátu serveru Internetová informační služba (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).
