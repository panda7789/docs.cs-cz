---
title: 'Postupy: Instalace a konfigurace aktivačních komponent WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 0a7be97ec157638db3eb2d656fe263b37b8d676c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837412"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Postupy: Instalace a konfigurace aktivačních komponent WCF

Toto téma popisuje kroky potřebné k nastavení aktivační služby procesů systému Windows (označované také jako) v systému Windows Vista pro hostování služby Windows Communication Foundation (WCF), které nekomunikují přes síťové protokoly HTTP. Následující části popisují kroky pro tuto konfiguraci:

- Nainstalujte (nebo potvrďte instalaci produktu) aktivační komponenty WCF.

- Konfigurace měla podporovat protokol jiného typu než HTTP. Následující postup nakonfiguruje Windows Vista pro aktivaci protokolem TCP.

Po instalaci a konfiguraci nástroje se podívejte na téma [Postupy: hostování služby WCF ve službě was](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) pro postupy vytvoření služby WCF, která zveřejňuje koncový bod bez http, který využívá.

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
    > Tento příkaz je jedním řádkem textu. Tento příkaz umožňuje, aby se aplikace/\<*WCF aplikace*> k dispozici pomocí `http://localhost/<WCF Application>` i `net.tcp://localhost/<WCF Application>`.

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

## <a name="see-also"></a>Viz také:

- [Aktivace protokolu TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Aktivace služby MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [Aktivace pojmenovaného kanálu](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [Funkce hostování technologie Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
