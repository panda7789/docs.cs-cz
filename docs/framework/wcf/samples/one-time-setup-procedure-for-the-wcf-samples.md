---
title: Jednorázový postup nastavení pro ukázky Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 3c3c5934cbbc7dd68f03d888aa0594f9ff61c225
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137665"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Jednorázový postup nastavení pro ukázky Windows Communication Foundation
Většina ukázek Windows Communication Foundation (WCF) jsou hostované v Internetové informační služby (IIS) a spustit z běžných virtuální adresář. Tento postup jednorázová nastavení vytvoří složku na disk. také přidá virtuální adresář služby IIS s názvem **ServiceModelSamples**.  
  
 **ServiceModelSamples** je použit virtuální adresář pro vytváření a spouštění všech ukázek, které používají služby hostované v IIS. Toto je jenom virtuální adresář, který se vyžaduje pro spuštění ukázky. Vytváření ukázku nahradí všechny dříve nasazené služby na tento virtuální adresář; pouze nedávno vytvořených vzorku bude nasazen a dostupný v tento virtuální adresář.  
  
> [!NOTE]
>  Je nutné spustit všechny příkazy v rámci místního účtu správce. Pokud používáte Windows 7, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], nebo Windows Server 2008 R2, musíte také spustit příkazový řádek se zvýšenými oprávněními. Uděláte to tak, klikněte pravým tlačítkem na ikonu příkazového řádku a potom klikněte na tlačítko **spustit jako správce**. Všechny příkazy v tomto tématu musí být spuštěn v příkazovém řádku, který má nastavení správnou cestu.  Nejjednodušší způsob, jak toho docílit, je pomocí příkazový řádek sady Visual Studio. Tato výzva, klikněte na tlačítko **Start**vyberte **všechny programy**, přejděte dolů k položce **Visual Studio 2010**vyberte **Visual Studio Tools**, Klikněte pravým tlačítkem na **příkazový řádek sady Visual Studio (2010)** a potom klikněte na tlačítko **spustit jako správce**. Pokud máte některou z edicí sady Visual Studio Express nainstalován tento příkazový řádek není k dispozici a budete muset přidat "C:\Windows\Microsoft.Net\Framework\v4.0" do systémové cesty.  
  
### <a name="one-time-setup-procedure-for-wcf-samples"></a>Jednorázový postup nastavení pro ukázky WCF  
  
1.  Ujistěte se, že [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nastaven. Další informace o tom, jak nastavit [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], naleznete v tématu [Internet Information Service pokyny k hostování](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).  
  
2.  Ujistěte se, že [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] je nainstalována. Hledat následující adresáře pro verzi 4.0 (nebo novější): **\Windows\Microsoft.NET\Framework**  
  
3.  Pokud [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] není nainstalovaná, a váš operační systém není Windows Server 2008 SP2 nebo novější, nainstalujte [opravu Hotfix 251798](https://go.microsoft.com/fwlink/?LinkId=184693).  
  
4.  Spusťte následující příkazy. Další informace o proč musí spustit tyto příkazy najdete v tématu [IIS hostované služby nezdaří](https://msdn.microsoft.com/library/ee5499fc-1b10-4cda-a9b1-13dba70f05f8).  
  
    > [!WARNING]
    >  Pokud se znovu nainstaluje službu IIS, následující příkazy muset znovu spustit.  
  
    ```  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r  
    ```  
  
    > [!WARNING]
    >  Spuštění příkazu `aspnet_regiis –i –enable` způsobí, že výchozí fond aplikací spusťte pomocí [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], což může způsobit potíže s nekompatibilitou pro jiné aplikace na stejném počítači.  
  
5.  Postupujte podle [pokyny k bráně Firewall](../../../../docs/framework/wcf/samples/firewall-instructions.md) umožňující použití portů používaných ukázky.  
  
6.  Vyhledejte následující výchozí adresář: \<InstallDrive >:**\WF_WCF_Samples**. Pokud byly dříve nainstalovány ukázky, toto je výchozí adresář.  
  
7.  Pokud nejsou nainstalovány ukázky, je nainstalovat z umístění pro stažení ukázky [Visual C#](https://go.microsoft.com/fwlink/?LinkId=190939) nebo [jazyka Visual Basic](https://go.microsoft.com/fwlink/?LinkID=193373).  
  
8.  Po instalaci ukázky, přejděte na: \<InstallDrive >:**\WF_WCF_Samples\WCF\Setup\\**  
  
9. Spustit **Setupvroot.bat** dávkového souboru. Jsou prováděny následovně:  
  
    -   Ve službě IIS s názvem ServiceModelSamples je vytvořen virtuální adresář.  
  
    -   Pojmenované %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples a % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin jsou vytvořeny nové adresáře disku.  
  
     Pokud chcete nastavit tyto adresáře ručně, najdete v článku [pokyny k instalaci virtuálního adresáře](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Vrátit zpět všechny změny provedené v tomto kroku, spusťte po dokončení práce ukázky cleanupvroot.bat.  
  
    > [!NOTE]
    >  Tento postup je třeba provést pouze jednou v počítači, není-li spustit cleanupvroot.bat.  
  
10. Je nutné udělit oprávnění ke změně pro %SystemDrive%\inetpub\wwwroot k účtu, pod kterým jsou vytváření ukázek a uživatel Network Service. Během sestavování, některé ukázky hostovaný Web se může pokusit kopírovat zkompilované binární soubory do výše uvedené umístění, a pokud jste nenastavili příslušná oprávnění, se build rozbije. Alternativně můžete ponechat oprávnění, jak jsou a spustit příkazový řádek sady SDK nebo příkazový řádek sady Visual Studio (2012) jako správce, nebo sestavení ukázky v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]také spusťte jako správce.  
  
    > [!NOTE]
    >  Pokud tento krok není dokončen, všechny ukázky hostované službou IIS selže během sestavování. Ujistěte se, že správně nastavená oprávnění, nebo spustit jako správce příkazový řádek sady SDK i příkazový řádek sady Visual Studio (2012).  
  
11. Vytvořte adresář C:\logs v počítači. Některé ukázky můžou očekává ho. Ujistěte se, že příslušný účet má oprávnění k zápisu do této složky udělit. Pro Windows 7 [!INCLUDE[wv](../../../../includes/wv-md.md)], a tento účet systému Windows Server 2008 R2, je **síťová služba**. Pro [!INCLUDE[lserver](../../../../includes/lserver-md.md)], je účet NT Authority\Network Service. Pro [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], účet se ASPNET.  
  
12. Spusťte soubor Setupcerttool.bat. Tento soubor je umístěn v \<InstallPath > \WF_WCF_Samples\WCF\Setup\ složky.  Tento skript provede následující úlohy:  
  
    -   Nástroj FindPrivateKey sestavení.  
  
    -   Vytvořte adresář s názvem % ProgramFiles%\ServiceModelSampleTools.  
  
    -   Nové FindPrivateKey nástroj pro kopírování do tohoto adresáře.  
  
     Tento nástroj vyžaduje ukázky, které používají certifikáty a jsou hostované ve službě IIS.  
  
    > [!NOTE]
    >  Z bezpečnostních důvodů nezapomeňte odebrat definici virtuální adresář a oprávnění udělená ve výše uvedené kroky instalace spuštěním dávkového souboru s názvem Cleanupvroot.bat, až budete hotovi s ukázkami.  
  
13. Ukázky, které jsou v místním prostředí (ne hostované ve službě IIS) vyžadují oprávnění k registraci adresami protokolu HTTP na počítači pro naslouchání. Oprávnění pro rezervace oboru názvů HTTP pochází z uživatelský účet použitý ke spuštění ukázky. Účty správců mají standardně oprávnění k registraci libovolnou adresu HTTP. Účty bez oprávnění správce musí udělit oprávnění pro obory názvů HTTP používaný ukázky. Další informace o tom, jak konfigurace rezervace oboru názvů najdete v tématu [konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).  
  
14. Některé ukázky vyžadují služby Řízení front zpráv. Zobrazit [instalace řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) pokyny k instalaci.  
  
    > [!NOTE]
    >  Zajistěte spuštění služby MSMQ předtím, než spustíte všechny ukázky, které vyžadují služby Řízení front zpráv.  
  
15. Některé ukázky vyžadují certifikáty. Zobrazit [Internetové informační služby (IIS) pokyny k instalaci certifikátu serveru](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
## <a name="see-also"></a>Viz také
