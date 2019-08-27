---
title: Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 1bb9c8bb2fedc846f46f665fbfd00178e5c72975
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044913"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)
Chcete-li spustit ukázky, které bezpečně komunikují s Internetová informační služba (IIS), je nutné vytvořit a nainstalovat certifikát serveru.  
  
## <a name="step-1-creating-certificates"></a>Krok 1. Vytváření certifikátů  
 Chcete-li vytvořit certifikát pro váš počítač, otevřete Developer Command Prompt pro sadu Visual Studio s oprávněním správce a spusťte instalační program. bat, který je součástí všech ukázek, které používají zabezpečenou komunikaci se službou IIS. Před spuštěním tohoto dávkového souboru zajistěte, aby cesta obsahovala složku, která obsahuje nástroj Makecert. exe. Následující příkaz slouží k vytvoření certifikátu v Setup. bat.  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>Krok 2. Instalace certifikátů  
 Postup potřebný k instalaci certifikátů, které jste právě vytvořili, závisí na verzi služby IIS, kterou používáte.  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>Instalace služby IIS na IIS 5,1 (Windows XP) a IIS 6,0 (Windows Server 2003)  
  
1. Otevřete modul snap-in konzoly MMC Internetová informační služba správce.  
  
2. Klikněte pravým tlačítkem na výchozí web a vyberte **vlastnosti**.  
  
3. Vyberte kartu **zabezpečení adresáře** .  
  
4. Klikněte na tlačítko **certifikát serveru** . Spustí se Průvodce certifikátem webového serveru.  
  
5. Dokončete průvodce. Vyberte možnost přiřazení certifikátu. V seznamu zobrazených certifikátů vyberte certifikát ServiceModelSamples-HTTPS-Server.  
  
     ![Průvodce certifikátem služby IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6. Otestujte přístup ke službě v prohlížeči pomocí adresy `https://localhost/servicemodelsamples/service.svc`https.  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>Pokud byl protokol SSL dřív nakonfigurovaný pomocí Httpcfg. exe  
  
1. Pomocí nástroje MakeCert. exe (nebo spuštěním souboru Setup. bat) vytvořte certifikát serveru.  
  
2. Spusťte Správce služby IIS a nainstalujte certifikát podle předchozích kroků.  
  
3. Do klientského programu přidejte následující řádek kódu.  
  
> [!IMPORTANT]
> Tento kód je vyžadován pouze pro testovací certifikáty, například ty, které byly vytvořeny pomocí nástroje MakeCert. exe. Nedoporučuje se pro produkční kód.  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>Instalace služby IIS na IIS 7,0 (Windows Vista a Windows Server 2008)  
  
1. V nabídce **Start** klikněte na tlačítko **Spustit**a zadejte příkaz **inetmgr** . tím otevřete modul snap-in konzoly MMC Internetová informační služba (IIS).  
  
2. Klikněte pravým tlačítkem na **výchozí web** a vyberte **Upravit vazby...**  
  
3. Klikněte na tlačítko **Přidat** v dialogovém okně **vazby webu** .  
  
4. V rozevíracím seznamu **typ** vyberte **https** .  
  
5. V rozevíracím seznamu **certifikát SSL** vyberte **ServiceModelSamples-https-Server** a klikněte na **OK**.  
  
6. Otestujte přístup ke službě v prohlížeči pomocí adresy `https://localhost/servicemodelsamples/service.svc`https.  
  
> [!NOTE]
> Vzhledem k tomu, že testovací certifikát, který jste právě nainstalovali, není důvěryhodný certifikát, můžete při prohlížení místních webových adres zabezpečených pomocí tohoto certifikátu narazit na další upozornění zabezpečení aplikace Internet Explorer.  
  
## <a name="removing-certificates"></a>Odebírání certifikátů  
  
- Použijte Internetová informační služba Manager jako dříve směrovaný, ale odeberte certifikát nebo vazbu místo přidávání.  
  
- Pomocí následujícího příkazu odeberte certifikát počítače.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
