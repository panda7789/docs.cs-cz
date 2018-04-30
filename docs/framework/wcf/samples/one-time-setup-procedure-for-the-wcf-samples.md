---
title: Jednorázový postup nastavení pro ukázky Windows Communication Foundation
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
caps.latest.revision: 83
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: acb89c8c1819024ebdb77720654ab7280333e456
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Jednorázový postup nastavení pro ukázky Windows Communication Foundation
Většina [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ukázky jsou hostované v Internetové informační služby (IIS) a spustit z běžných virtuální adresáře. Tento postup jednorázové instalační program vytvoří složku na disku; také přidá virtuální adresář pro službu IIS s názvem **ServiceModelSamples**.  
  
 **ServiceModelSamples** virtuální adresář se používá pro vytváření a spouštění všechny ukázky, které používají služby hostované službou IIS. Toto je pouze virtuálního adresáře, který se vyžaduje ke spuštění ukázky. Vytváření ukázku nahradí všechny dříve nasazené služby na tento virtuální adresář; pouze nedávno integrovaný Ukázka bude nasazen a dostupný v tento virtuální adresář.  
  
> [!NOTE]
>  Je nutné spustit všechny příkazy pod účtem místního správce. Pokud používáte systém Windows 7, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], nebo Windows Server 2008 R2, je nutné spustit také příkazovém řádku se zvýšenými oprávněními. Uděláte to tak, klikněte pravým tlačítkem na ikonu Příkazový řádek a pak klikněte na tlačítko **spustit jako správce**. Všechny příkazy v tomto tématu se musí spustit v příkazovém řádku, který má nastavení správnou cestu.  Nejjednodušší způsob, jak toho docílit, je pomocí příkazového řádku Visual Studio. Otevřete tuto výzvu klikněte na **spustit**, vyberte **všechny programy**, přejděte dolů k položce **Visual Studio 2010**, vyberte **nástroje sady Visual Studio**, Klikněte pravým tlačítkem na **Visual Studio – příkazový řádek (2010)** a potom klikněte na **spustit jako správce**. Pokud nemáte nainstalované v edicích sady Visual Studio Express, tento příkaz není k dispozici a budete muset přidat "C:\Windows\Microsoft.Net\Framework\v4.0" do systémové cesty.  
  
### <a name="one-time-setup-procedure-for-wcf-samples"></a>Jednorázový postup nastavení pro ukázky WCF  
  
1.  Ujistěte se, že [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] je nastavený. Další informace o tom, jak nastavit [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], najdete v části [Internetu informace o pokyny k hostování služby](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).  
  
2.  Ujistěte se, že [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] je nainstalovaná. Hledání následující adresář pro v4.0 (nebo novější): **\Windows\Microsoft.NET\Framework**  
  
3.  Pokud [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] není nainstalovaná, a operačního systému není Windows Server 2008 SP2 nebo novější, nainstalujte [251798 opravu Hotfix](http://go.microsoft.com/fwlink/?LinkId=184693).  
  
4.  Spusťte následující příkazy. Další informace o proč musíte spustit tyto příkazy najdete v tématu [IIS hostované služby nezdaří](http://msdn.microsoft.com/library/ee5499fc-1b10-4cda-a9b1-13dba70f05f8).  
  
    > [!WARNING]
    >  Pokud se znovu nainstaluje službu IIS, následující příkazy bude muset znovu spustit.  
  
    ```  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r  
    ```  
  
    > [!WARNING]
    >  Spuštěním příkazu `aspnet_regiis –i –enable` bude fond aplikací výchozí spuštění pomocí [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], který může vytvořit problémů s nekompatibilitou pro jiné aplikace na stejném počítači.  
  
5.  Postupujte podle [pokyny k bráně Firewall](../../../../docs/framework/wcf/samples/firewall-instructions.md) pro povolení porty používané při ukázky.  
  
6.  Zkontrolujte následující výchozí adresář: \<InstallDrive >:**\WF_WCF_Samples**. Pokud již byly nainstalovány ukázky, toto je výchozí adresář.  
  
7.  Pokud nejsou nainstalovány ukázky, nainstalujte je z umístění pro stažení ukázky [Visual C#](http://go.microsoft.com/fwlink/?LinkId=190939) nebo [jazyka Visual Basic](http://go.microsoft.com/fwlink/?LinkID=193373).  
  
8.  Po instalaci ukázky, přejděte na: \<InstallDrive >:**\WF_WCF_Samples\WCF\Setup\\**  
  
9. Spustit **Setupvroot.bat** dávkového souboru. Jsou prováděny následovně:  
  
    -   Virtuální adresář vytvořen ve službě IIS s názvem ServiceModelSamples.  
  
    -   Pojmenované %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples a % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin jsou vytvořeny nové adresáře disku.  
  
     Pokud chcete nastavit tyto adresáře ručně, najdete v článku [pokyny k instalaci virtuálního adresáře](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Chcete-li vraťte zpátky všechny změny provést v tomto kroku, spusťte cleanupvroot.bat po pomocí ukázky.  
  
    > [!NOTE]
    >  Tento postup je třeba provést pouze jednou v počítači, pokud cleanupvroot.bat běží.  
  
10. Musí udělit oprávnění k úpravám pro %SystemDrive%\inetpub\wwwroot k účtu, pod kterým jsou vytváření ukázky a uživatel síťové služby. Při vytváření, některé webové hostované ukázky může pokus o zkopírování kompilované binární soubory do výše uvedených umístění, a pokud jste nenastavili příslušná oprávnění, se build rozbije. Alternativně můžete ponechat oprávnění, jak jsou a spustit příkazový řádek SDK nebo příkazového řádku Visual Studia (2012) jako správce, nebo vytvořit ukázky [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]také spusťte jako správce.  
  
    > [!NOTE]
    >  Pokud není tento krok dokončen, všechny vzorky hostované službou IIS selže při sestavování. Zajistěte správné nastavení oprávnění nebo spustit příkazový řádek sady Visual Studio (2012) i SDK – příkazový řádek jako správce.  
  
11. Vytvořte adresář C:\logs v počítači. Některé ukázky může být očekávána ho. Ujistěte se, že odpovídající účet má oprávnění zápisu udělena do této složky. Pro systém Windows 7 [!INCLUDE[wv](../../../../includes/wv-md.md)], a Windows Server 2008 R2, tento účet je **síťové služby**. Pro [!INCLUDE[lserver](../../../../includes/lserver-md.md)], je účet NT Authority\Network Service. Pro [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], účet je ASPNET.  
  
12. Spusťte soubor Setupcerttool.bat. Tento soubor je umístěný v \<InstallPath > \WF_WCF_Samples\WCF\Setup\ složky.  Tento skript provede následující úlohy:  
  
    -   Sestavení nástroj FindPrivateKey.  
  
    -   Vytvořte adresář s názvem % ProgramFiles%\ServiceModelSampleTools.  
  
    -   Zkopírujte nový nástroj FindPrivateKey do tohoto adresáře.  
  
     Tento nástroj je požadován vzorků, které používají certifikáty a jsou hostované ve službě IIS.  
  
    > [!NOTE]
    >  Z bezpečnostních důvodů nezapomeňte odebrat definici virtuální adresář a oprávnění udělená ve výše uvedené kroky instalace spuštěním dávkový soubor s názvem Cleanupvroot.bat po skončení s ukázky.  
  
13. Ukázky, samoobslužných hostovaných (není hostovaný ve službě IIS) vyžadují oprávnění k registraci adresy protokolu HTTP na počítači pro naslouchání. Oprávnění pro rezervaci oboru názvů HTTP pochází z uživatelský účet použitý ke spuštění ukázky. Ve výchozím nastavení mají účty správců oprávnění k registraci žádné adresy protokolu HTTP. Účty správců jiné musí udělit oprávnění pro obory názvů HTTP používaný ukázky. Další informace o tom, jak nakonfigurovat vyhrazení oboru názvů najdete v tématu [konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).  
  
14. Některé ukázky vyžadují služby Řízení front zpráv. V tématu [instalaci řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) pokyny k instalaci.  
  
    > [!NOTE]
    >  Zajistěte spuštění služby MSMQ, před spuštěním jakékoli vzorků, které vyžadují služby Řízení front zpráv.  
  
15. Některé ukázky vyžadují certifikáty. V tématu [Internetová informační služba (IIS) pokyny k instalaci certifikátu serveru](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
## <a name="see-also"></a>Viz také
