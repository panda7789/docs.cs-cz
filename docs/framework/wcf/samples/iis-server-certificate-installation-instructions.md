---
title: Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 8d0b80930424f0d8529f2b035a8e1167f361f99a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303935"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)
Ke spuštění ukázky, které zabezpečeně komunikovat s Internetové informační služby (IIS), musíte vytvořit a nainstalovat certifikát serveru.  
  
## <a name="step-1-creating-certificates"></a>Krok 1. Vytváření certifikátů  
 Chcete-li vytvořit certifikát pro počítač, otevřete Developer Command Prompt pro sadu Visual Studio s oprávněními správce a spusťte Setup.bat, který je součástí všech ukázek, které používají zabezpečené komunikace se službou IIS. Ujistěte se, že cesta obsahuje složku obsahující Makecert.exe předtím, než spustíte tento dávkový soubor. Následující příkaz se používá k vytvoření certifikátu v Setup.bat.  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>Krok 2. Instalace certifikátů  
 Kroky potřebné k instalaci certifikátů, které jste právě vytvořili, závisí na kterou verzi služby IIS, kterou používáte.  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>Instalace služby IIS na IIS 5.1 (Windows XP) a služby IIS 6.0 (Windows Server 2003)  
  
1. Otevřít Internetová informační služba modul Snap-In konzoly MMC správce.  
  
2. Klikněte pravým tlačítkem na výchozí web a vyberte **vlastnosti**.  
  
3. Vyberte **zabezpečení adresáře** kartu.  
  
4. Klikněte na tlačítko **certifikát serveru** tlačítko. Spustí se Průvodce certifikátem webového serveru.  
  
5. Dokončete průvodce. Vyberte možnost přiřadit certifikát. Vyberte ServiceModelSamples HTTPS Server certifikát ze seznamu certifikátů, které jsou zobrazeny.  
  
     ![Průvodce certifikátů služby IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6. Otestovat přístup k této službě v prohlížeči pomocí adresu HTTPS `https://localhost/servicemodelsamples/service.svc`.  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>Pokud byla dříve nakonfigurovaný protokol SSL s využitím Httpcfg.exe  
  
1. Použijte Makecert.exe (nebo spuštění Setup.bat) k vytvoření certifikátu serveru.  
  
2. Spusťte Správce služby IIS a nainstalovat certifikát podle předchozích kroků.  
  
3. Přidejte následující řádek kódu do klientské aplikace.  
  
> [!IMPORTANT]
>  Tento kód je potřeba jenom pro testovací certifikáty, jako jsou ty vytvořené Makecert.exe. To se nedoporučuje pro produkční kód.  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>Instalace služby IIS ve službě IIS 7.0 (Windows Vista a Windows Server 2008)  
  
1. Z **Start** nabídky, klikněte na tlačítko **spustit**, zadejte **inetmgr** otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).  
  
2. Klikněte pravým tlačítkem myši **výchozí webový server** a vyberte **Upravit vazby...**  
  
3. Klikněte na tlačítko **přidat** tlačítko **vazby webu** dialogové okno.  
  
4. Vyberte **HTTPS** z **typ** rozevíracího seznamu.  
  
5. Vyberte **ServiceModelSamples HTTPS Server** z **certifikát SSL** rozevíracího seznamu a klikněte na tlačítko **OK**.  
  
6. Otestovat přístup k této službě v prohlížeči pomocí adresu HTTPS `https://localhost/servicemodelsamples/service.svc`.  
  
> [!NOTE]
>  Vzhledem k tomu, že testovací certifikát, který jste právě nainstalovali není důvěryhodný certifikát, další upozornění zabezpečení aplikace Internet Explorer můžete narazit, při přechodu na místní webové adresy, které jsou zabezpečené pomocí tohoto certifikátu.  
  
## <a name="removing-certificates"></a>Odebírání certifikátů  
  
-   Pomocí Správce Internetové informační služby, jako dříve přesměruje, ale odebrat certifikát nebo vazby místo jeho přidání.  
  
-   Pomocí následujícího příkazu odeberte certifikát počítače.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
