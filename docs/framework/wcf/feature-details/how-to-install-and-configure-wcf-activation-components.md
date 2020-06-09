---
title: 'Postupy: Instalace a konfigurace aktivačních komponent WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: f7a846b076691394cb855e4978e890cdcac76eb2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597030"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Postupy: Instalace a konfigurace aktivačních komponent WCF

Toto téma popisuje kroky potřebné k nastavení aktivační služby procesů systému Windows (označované také jako) v systému Windows Vista pro hostování služby Windows Communication Foundation (WCF), které nekomunikují přes síťové protokoly HTTP. Následující části popisují kroky pro tuto konfiguraci:

- Nainstalujte (nebo potvrďte instalaci produktu) aktivační komponenty WCF.

- Konfigurace měla podporovat protokol jiného typu než HTTP. Následující postup nakonfiguruje Windows Vista pro aktivaci protokolem TCP.

Po instalaci a konfiguraci nástroje se podívejte na téma [Postupy: hostování služby WCF ve službě was](how-to-host-a-wcf-service-in-was.md) pro postupy vytvoření služby WCF, která zveřejňuje koncový bod bez http, který využívá.

## <a name="to-install-the-wcf-non-http-activation-components"></a>Instalace součástí technologie WCF pro aktivaci bez protokolu HTTP

1. Klikněte na tlačítko **Start** a potom klikněte na **Ovládací panely**.

2. Klikněte na **programy**a potom klikněte na **programy a funkce**.

3. V nabídce **úlohy** klikněte na **zapnout nebo vypnout funkce systému Windows**.

4. Vyhledejte uzel WinFX, vyberte a rozbalte ho.

5. Vyberte pole **součásti technologie WCF bez protokolu HTTP** a uložte nastavení.

## <a name="to-configure-the-was-to-support-tcp-activation"></a>Konfigurace nástroje WAS na podporu aktivace protokolem TCP

1. Aby bylo možné podporovat NET. TCP Activation, musí být výchozí webová stránka nejprve svázána s portem NET. TCP. To můžete provést pomocí nástroje Appcmd. exe, který se instaluje se sadou nástrojů pro správu služby IIS 7,0. V okně příkazového řádku na úrovni správce spusťte následující příkaz.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > Tento příkaz je jedním řádkem textu. Tento příkaz přidá vazbu sítě NET. TCP na výchozí webovou stránku, která naslouchá na portu TCP 808 s libovolným názvem hostitele.

2. I když všechny aplikace v rámci lokality sdílí společnou vazbu NET. TCP, každá aplikace může povolit podporu NET. TCP samostatně. Pokud chcete pro aplikaci povolit NET. TCP, spusťte následující příkaz z příkazového řádku na úrovni správce.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > Tento příkaz je jedním řádkem textu. Tento příkaz umožňuje, \<*WCF Application*> aby k aplikaci/aplikace bylo možné pracovat pomocí obou `http://localhost/<WCF Application>` i `net.tcp://localhost/<WCF Application>` .

     Odeberte vazbu na lokalitu NET. TCP, kterou jste přidali pro tuto ukázku.

     Následující dva kroky jsou implementovány v dávkovém souboru s názvem RemoveNetTcpSiteBinding. cmd, který je umístěn v ukázkovém adresáři.

    1. Ze seznamu povolených protokolů odeberte NET. TCP spuštěním následujícího příkazu v okně příkazového řádku na úrovni správce.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > Tento příkaz je jedním řádkem textu.

    2. Odeberte vazbu sítě NET. TCP spuštěním následujícího příkazu v okně příkazového řádku se zvýšenými oprávněními:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > Tento příkaz je jedním řádkem textu.

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Odebrání NET. TCP ze seznamu povolených protokolů

1. Chcete-li odebrat NET. TCP ze seznamu povolených protokolů, spusťte následující příkaz v okně příkazového řádku na úrovni správce.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > Tento příkaz je jedním řádkem textu.

## <a name="to-remove-the-nettcp-site-binding"></a>Postup odebrání vazby webu NET. TCP

1. Chcete-li odebrat vazbu sítě NET. TCP, spusťte následující příkaz v okně příkazového řádku na úrovni správce.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > Tento příkaz je jedním řádkem textu.

## <a name="see-also"></a>Viz také

- [Aktivace protokolem TCP](../samples/tcp-activation.md)
- [Aktivace MSMQ](../samples/msmq-activation.md)
- [Aktivace pojmenovaného kanálu](../samples/namedpipe-activation.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
