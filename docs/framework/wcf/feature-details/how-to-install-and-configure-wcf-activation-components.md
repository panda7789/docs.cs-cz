---
title: 'Postupy: Instalace a konfigurace aktivačních komponent WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 2677c57c825675c884d057827e065f05d7c8bf30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039140"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Postupy: Instalace a konfigurace aktivačních komponent WCF
Toto téma popisuje kroky potřebné k nastavení služby Aktivace procesu Windows (WAS) na [!INCLUDE[wv](../../../../includes/wv-md.md)] k hostování Windows Communication Foundation (WCF) služby, které nekomunikují přes protokol HTTP síťových protokolů. Následující oddíly popisují kroky pro tuto konfiguraci:  
  
- Nainstalovat (nebo potvrďte instalaci) aktivačních komponent WCF.  
  
- Konfigurace WAS pro podporu protokolu jiným protokolem než HTTP. Následující postup umožňuje konfiguraci [!INCLUDE[wv](../../../../includes/wv-md.md)] pro Aktivace protokolem TCP.  
  
 Po instalaci a konfiguraci služby WAS, naleznete v tématu [jak: Hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) postupy k vytvoření služby WCF, který zpřístupňuje koncový bod jiným protokolem než HTTP, která používá WAS.  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a>Chcete-li nainstalovat jiným protokolem než HTTP aktivačních komponent WCF  
  
1. Klikněte na tlačítko **Start** tlačítko a pak klikněte na tlačítko **ovládací panely**.  
  
2. Klikněte na tlačítko **programy**a potom klikněte na tlačítko **programy a funkce**.  
  
3. Na **úlohy** nabídky, klikněte na tlačítko **Windows zapnout nebo vypnout funkce**.  
  
4. Najít [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] uzlu, vyberte a pak ji rozbalte.  
  
5. Vyberte **aktivačních komponent WCF jiným protokolem než Http** pole a uložení nastavení.  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a>Konfigurace WAS pro podporu Aktivace protokolem TCP  
  
1. Kvůli podpoře aktivace net.tcp, musíte ji nejdřív svázat výchozí webový server k portu net.tcp. Můžete to provést pomocí Appcmd.exe, která se instaluje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] sada nástrojů pro správu. V okně příkazového řádku na úrovni správce spusťte následující příkaz.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Tento příkaz je jeden řádek textu. Tento příkaz přidá vazbu webu net.tcp výchozí webový server naslouchá na portu TCP 808 s názvem hostitele.  
  
2. Přestože všechny aplikace v rámci lokality sdílejí společné vazby net.tcp, každá aplikace můžete povolit podporu net.tcp jednotlivě. Pokud chcete povolit net.tcp pro aplikaci, spusťte následující příkaz z příkazového řádku na úrovni správce.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  Tento příkaz je jeden řádek textu. Tento příkaz povolí /\<*aplikace WCF*> aplikace přistupovat pomocí obou `http://localhost/<WCF Application>` a `net.tcp://localhost/<WCF Application>`.
  
     Odeberte net.tcp vazby webu, kterou jste přidali pro tuto ukázku.  
  
     V zájmu usnadnění práce následující dva kroky jsou implementovány v dávkovém souboru volá RemoveNetTcpSiteBinding.cmd nachází v adresáři ukázkové.  
  
    1. Odeberte net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu v okně příkazového řádku úrovni správce.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je jeden řádek textu.  
  
    2. Odeberte vazbu webu net.tcp spuštěním následujícího příkazu v okně příkazového řádku se zvýšenými oprávněními:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je jeden řádek textu.  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Chcete-li odebrat ze seznamu povolených protokolů net.tcp  
  
1. Chcete-li odebrat ze seznamu povolených protokolů net.tcp, spusťte následující příkaz v okně příkazového řádku úrovni správce.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  Tento příkaz je jeden řádek textu.  
  
### <a name="to-remove-the-nettcp-site-binding"></a>Chcete-li odebrat vazbu webu net.tcp  
  
1. Odeberte lokalitu net.tcp vazby spusťte následující příkaz v okně příkazového řádku úrovni správce.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Tento příkaz je jeden řádek textu.  
  
## <a name="see-also"></a>Viz také:

- [Aktivace protokolu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Aktivace služby MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [Aktivace pojmenovaného kanálu](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
