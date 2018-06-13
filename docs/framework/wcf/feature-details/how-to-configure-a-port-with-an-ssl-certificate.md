---
title: 'Postupy: Konfigurace portu certifikát protokolu SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: c3cede1eb90b963f4c0b567a8df48925bca9b02d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494826"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Postupy: Konfigurace portu certifikát protokolu SSL
Při vytváření samoobslužných hostovaná služba Windows Communication Foundation (WCF) se <xref:System.ServiceModel.WSHttpBinding> třídy zabezpečení přenosu tohoto používá, musíte taky nakonfigurovat port společně s certifikátem X.509. Pokud nejsou vytváření samoobslužných hostované služby, můžete hostovat služby v Internetové informační služby (IIS). Další informace najdete v tématu [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Konfigurace portu, na nástroj, který používáte závisí na operační systém, který běží na vašem počítači.  
  
 Pokud používáte [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe. S [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] tento nástroj je nainstalován. S [!INCLUDE[wxp](../../../../includes/wxp-md.md)], si můžete stáhnout nástroj na [nástrojů podpory systému Windows XP Service Pack 2](http://go.microsoft.com/fwlink/?LinkId=88606). Další informace najdete v tématu [Httpcfg přehled](http://go.microsoft.com/fwlink/?LinkId=88605). [Dokumentace nástrojů podpory systému Windows](http://go.microsoft.com/fwlink/?LinkId=94840) vysvětluje syntaxe pro nástroj Httpcfg.exe.  
  
 Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe, který už je nainstalovaný.  
  
 Toto téma popisuje, jak provést několik postupů:  
  
-   Určení počítače aktuální konfiguraci portů.  
  
-   Získávání kryptografický otisk certifikátu (potřeby pro tyto dva postupy).  
  
-   Vytvoření vazby certifikátu SSL na konfiguraci portů.  
  
-   Vytvoření vazby certifikátu SSL na konfiguraci portů a podpůrné klientské certifikáty.  
  
-   Odstranění certifikátu protokolu SSL z číslo portu.  
  
 Všimněte si, že úprava certifikáty uložené v počítači vyžaduje oprávnění správce.  
  
### <a name="to-determine-how-ports-are-configured"></a>Chcete-li zjistit, jak jsou nakonfigurované porty  
  
1.  V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], pomocí nástroje HttpCfg.exe zobrazíte aktuální konfiguraci portů pomocí **dotazu** a **ssl** přepne, jak je znázorněno v následujícím příkladu.  
  
    ```  
    httpcfg query ssl  
    ```  
  
2.  V [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe zobrazíte aktuální konfiguraci portu, jak je znázorněno v následujícím příkladu.  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Chcete-li získat kryptografický otisk certifikátu  
  
1.  Pomocí modulu snap-in Certifikáty konzoly MMC najít certifikát X.509, který je zamýšlený účel ověřování klienta. Další informace najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Přístup k kryptografický otisk certifikátu. Další informace najdete v tématu [postupy: načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3.  Zkopírujte kryptografický otisk certifikátu do textového editoru, například Poznámkový blok.  
  
4.  Odebere všechny mezery mezi hexadecimálních znaků. Jedním ze způsobů k tomu je pomocí funkce hledání a nahrazování textovém editoru a nahraďte každý prostor znak hodnoty null.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>K vytvoření vazby certifikátu SSL. číslo portu  
  
1.  V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], pomocí nástroje HttpCfg.exe v režimu "nastavení" v úložišti Secure Sockets Layer (SSL) vytvořte vazbu certifikátu k číslo portu. Nástroj kryptografický otisk používá k identifikaci certifikátu, jak je znázorněno v následujícím příkladu.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   **-I** má přepínač syntaxe `IP`:`port` a dává pokyn nástroji a nastavte certifikát na port 8012 počítače. Volitelně čtyři nuly, které předcházet číslo lze také nahradit skutečným IP adresu počítače.  
  
    -   **-H** přepínač určuje kryptografický otisk certifikátu.  
  
2.  V [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe, jak je znázorněno v následujícím příkladu.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   **Certhash** parametr určuje kryptografický otisk certifikátu.  
  
    -   **Ipport** parametr určuje IP adresu a port, a funguje stejně jako **-i** přepínač nástroj Httpcfg.exe popsané.  
  
    -   **Appid** parametr je identifikátor GUID, který slouží k identifikaci vlastnícím aplikace.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Vytvoření vazby certifikátu SSL na číslo portu a podporu klientské certifikáty  
  
1.  V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aby podporovaly klienty, které ověřování pomocí certifikátů X.509 v přenosové vrstvě, postupujte podle předchozích pokynů, ale další parametr příkazového řádku předat HttpCfg.exe, jak je znázorněno v následujícím příkladu.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F** má přepínač syntaxe `n` kde n je číslo mezi 1 a 7. Hodnota 2, jak je uvedeno v předchozím příkladu povolí klientské certifikáty v přenosové vrstvě. Hodnota 3 umožňuje klientské certifikáty a tyto certifikáty se mapuje na účet systému Windows. Naleznete v nápovědě HttpCfg.exe chování jiných hodnot.  
  
2.  V [!INCLUDE[wv](../../../../includes/wv-md.md)], na podporu klienty, kteří ověřování pomocí certifikátů X.509 v přenosové vrstvě, postupujte podle předchozích pokynů, ale s dalším parametrem, jak je znázorněno v následujícím příkladu.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Chcete-li odstranit certifikát SSL od číslo portu  
  
1.  Pomocí nástroje HttpCfg.exe nebo Netsh.exe najdete v části Nastavení portů a kryptografické otisky všechny vazby v počítači. Tisknout informace na disk, použijte znak přesměrování ">", jak je znázorněno v následujícím příkladu.  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2.  V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte aplikaci HttpCfg.exe nástroj s **odstranit** a **ssl** klíčová slova. Použití **-i** přepínač tak, aby zadejte `IP`:`port` číslo a **-h** přepínač tak, aby zadejte kryptografický otisk.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3.  V [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak vytvořit služba s vlastním hostováním pomocí <xref:System.ServiceModel.WSHttpBinding> třídy nastaven na zabezpečení přenosu. Při vytváření aplikace, zadejte číslo portu v adrese.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
