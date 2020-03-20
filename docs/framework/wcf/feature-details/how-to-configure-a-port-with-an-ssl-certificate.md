---
title: 'Postupy: Konfigurace portu s certifikátem SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185110"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Postupy: Konfigurace portu s certifikátem SSL

Při vytváření služby WCF (Windows Communication Foundation) <xref:System.ServiceModel.WSHttpBinding> s vlastní hospojnou službou Windows Communication Foundation (WCF) s třídou, která používá zabezpečení přenosu, je také nutné nakonfigurovat port s certifikátem X.509. Pokud nevytváříte samoobslužnou službu, můžete ji hostovat v Internetové informační službě (IIS). Další informace naleznete v tématu [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Chcete-li nakonfigurovat port, nástroj, který používáte, závisí na operačním systému spuštěném v počítači.  
  
 Pokud používáte systém Windows Server 2003, použijte nástroj HttpCfg.exe. V systému Windows Server 2003 je tento nástroj nainstalován. Další informace naleznete v tématu [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)). [Dokumentace nástroje podpory systému Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) vysvětluje syntaxi nástroje Httpcfg.exe.  
  
 Pokud používáte systém Windows Vista, použijte nástroj Netsh.exe, který je již nainstalován.
  
> [!NOTE]
> Úprava certifikátů uložených v počítači vyžaduje oprávnění správce.  
  
## <a name="determine-how-ports-are-configured"></a>Určení způsobu konfigurace portů  
  
1. V systému Windows Server 2003 nebo Windows XP můžete pomocí nástroje HttpCfg.exe zobrazit aktuální konfiguraci portu pomocí přepínačů **dotazu** a **ssl,** jak je znázorněno v následujícím příkladu.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. V systému Windows Vista použijte nástroj Netsh.exe k zobrazení aktuální konfigurace portu, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a>Získání kryptografického otisku certifikátu  
  
1. Pomocí modulu snap-in MMC certifikátů vyhledejte certifikát X.509, který má zamýšlený účel ověřování klienta. Další informace naleznete v [tématu How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2. Přístup k kryptografickému otisku certifikátu. Další informace naleznete v [tématu How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Zkopírujte kryptografický otisk certifikátu do textového editoru, například poznámkový blok.  
  
4. Odstraňte všechny mezery mezi šestnáctkovými znaky. Jedním ze způsobů, jak toho dosáhnout, je použít funkci hledání a nahrazení textového editoru a nahradit každou mezeru prázdným znakem.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a>Vazba certifikátu SSL na číslo portu  
  
1. V systému Windows Server 2003 nebo Windows XP použijte nástroj HttpCfg.exe v režimu sady v úložišti SSL (Secure Sockets Layer) k vytvoření svázání certifikátu s číslem portu. Nástroj používá kryptografický otisk k identifikaci certifikátu, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - Přepínač **-i** má `IP`syntaxi`port` : a instruuje nástroj pro nastavení certifikátu na port 8012 počítače. Volitelně čtyři nuly, které předcházejí číslo lze také nahradit skutečnou IP adresu počítače.  
  
    - Přepínač **-h** určuje kryptografický otisk certifikátu.  
  
2. V systému Windows Vista použijte nástroj Netsh.exe, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - Parametr **certhash** určuje kryptografický otisk certifikátu.  
  
    - Parametr **ipport** určuje IP adresu a port a funguje stejně jako přepínač **-i** popsaného nástroje Httpcfg.exe.  
  
    - **Appid** parametr je GUID, který lze použít k identifikaci vlastnící aplikace.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Vazba certifikátu SSL na číslo portu a podpora klientských certifikátů  
  
1. Chcete-li podporovat klienty, kteří se ověřují pomocí certifikátů X.509 v transportní vrstvě, postupujte podle předchozího postupu, ale předáte další parametr příkazového řádku programu HttpCfg.exe, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     Přepínač **-f** má syntaxi kde `n` n je číslo mezi 1 a 7. Hodnota 2, jak je znázorněno v předchozím příkladu, umožňuje klientské certifikáty na transportní vrstvě. Hodnota 3 umožňuje klientské certifikáty a mapuje tyto certifikáty na účet systému Windows. Viz HttpCfg.exe Nápověda pro chování jiných hodnot.  
  
2. Chcete-li v systému Windows Vista podporovat klienty, kteří se ověřují pomocí certifikátů X.509 ve vrstvě přenosu, postupujte podle předchozího postupu, ale s dalším parametrem, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a>Odstranění certifikátu SSL z čísla portu  
  
1. Pomocí nástroje HttpCfg.exe nebo Netsh.exe zobrazíte porty a kryptografické otisky všech vazeb v počítači. Chcete-li vytisknout informace na disk, použijte znak přesměrování ">", jak je znázorněno v následujícím příkladu.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. V systému Windows Server 2003 nebo Windows XP použijte nástroj HttpCfg.exe s klíčovými slovy **delete** a **ssl.** Pomocí přepínače **-i** `IP`určete :`port` number a **-h** switch pro určení kryptografického otisku.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. V systému Windows Vista použijte nástroj Netsh.exe, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Příklad  

 Následující kód ukazuje, jak vytvořit samoobslužnou službu <xref:System.ServiceModel.WSHttpBinding> pomocí třídy nastavené na zabezpečení přenosu. Při vytváření aplikace zadejte číslo portu v adrese.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
