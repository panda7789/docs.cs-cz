---
title: "Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfb168ae60765a57017aaec6bdedaf796491f602
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a>Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)
Ke spuštění ukázky, které zabezpečeně komunikovat s Internetové informační služby (IIS), musíte vytvořit a nainstalovat certifikát serveru.  
  
## <a name="step-1-creating-certificates"></a>Krok 1. Vytváření certifikátů  
 Chcete-li vytvořit certifikát pro počítač, otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte Setup.bat, která je zahrnuta v každé vzorků, které používají zabezpečené komunikace se službou IIS. Ujistěte se, že cesta obsahuje složku, která obsahuje Makecert.exe předtím, než spustíte tento dávkový soubor. Tento příkaz slouží k vytvoření certifikátu v Setup.bat.  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a>Krok 2. Instalace certifikátů  
 Kroky potřebné k instalaci certifikátů, který jste právě vytvořili závisí na které verze služby IIS, kterou používáte.  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a>Chcete-li nainstalovat službu IIS do služby IIS 5.1 (Windows XP) a služby IIS 6.0 (Windows Server 2003)  
  
1.  Otevřete Internetová informační služba modul Snap-In konzoly MMC správce.  
  
2.  Klikněte pravým tlačítkem na výchozí web a vyberte **vlastnosti**.  
  
3.  Vyberte **zabezpečení adresáře** kartě.  
  
4.  Klikněte **certifikát serveru** tlačítko. Spustí se Průvodce certifikátem webového serveru.  
  
5.  Dokončete průvodce. Vyberte možnost přiřadit certifikát. Vyberte ServiceModelSamples HTTPS Server certifikát ze seznamu certifikátů, které jsou zobrazeny.  
  
     ![Služba IIS certifikátu průvodce](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")  
  
6.  Otestovat přístup ke službě v prohlížeči pomocí https://localhost/servicemodelsamples/service.svc adresa HTTPS.  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a>Pokud pomocí Httpcfg.exe byl dříve nakonfigurovaný protokol SSL  
  
1.  Použijte Makecert.exe (nebo spuštění Setup.bat) k vytvoření certifikátu serveru.  
  
2.  Spusťte Správce služby IIS a nainstalujte certifikát podle předchozích kroků.  
  
3.  Přidejte následující řádek kódu do klientské aplikace.  
  
> [!IMPORTANT]
>  Tento kód je potřeba jenom pro testovací certifikáty jsou vytvořené Makecert.exe. Nedoporučuje pro produkční kód.  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a>Instalace služby IIS ve službě IIS 7.0 (Windows Vista a Windows Server 2008)  
  
1.  Z **spustit** nabídky, klikněte na tlačítko **spustit**, pak zadejte **inetmgr** otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).  
  
2.  Klikněte pravým tlačítkem myši **Default Web Site** a vyberte **Upravit vazby...**  
  
3.  Klikněte **přidat** tlačítko **vazby webu** dialogové okno.  
  
4.  Vyberte **HTTPS** z **typ** rozevíracího seznamu.  
  
5.  Vyberte **ServiceModelSamples HTTPS Server** z **certifikát SSL** rozevíracího seznamu a klikněte na tlačítko **OK**.  
  
6.  Otestovat přístup ke službě v prohlížeči pomocí https://localhost/servicemodelsamples/service.svc adresa HTTPS.  
  
> [!NOTE]
>  Vzhledem k tomu, že testovací certifikát, který jste právě nainstalovali není důvěryhodný certifikát, kterým může dojít další upozornění zabezpečení aplikace Internet Explorer při procházení k místní webové adresy, které jsou zabezpečené s tímto certifikátem.  
  
## <a name="removing-certificates"></a>Odebrání certifikátů  
  
-   Pomocí Správce Internetové informační služby, jako dříve směrované, ale odebrat certifikát nebo vazba nepřidávat ho.  
  
-   Pomocí následujícího příkazu odeberte certifikát počítače.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
