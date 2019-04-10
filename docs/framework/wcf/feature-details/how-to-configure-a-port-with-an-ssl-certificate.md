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
ms.openlocfilehash: d709123895f361c1d2268a218b4163c8d195e1b4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345583"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Postupy: Konfigurace portu s certifikátem SSL
Při vytváření služby Windows Communication Foundation (WCF) v místním prostředí s <xref:System.ServiceModel.WSHttpBinding> třídy zabezpečení přenosu používá, musíte také nakonfigurovat port pomocí certifikátu X.509. Pokud vytváříte nejsou v místním prostředí služby, můžete hostovat vaše služba v Internetové informační služby (IIS). Další informace najdete v tématu [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Konfigurace portu, nástroj, který můžete použít závisí na operační systém, který běží na vašem počítači.  
  
 Pokud používáte [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe. S [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] tento nástroj je nainstalován. S [!INCLUDE[wxp](../../../../includes/wxp-md.md)], si můžete stáhnout nástroj na [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606). Další informace najdete v tématu [Httpcfg přehled](https://go.microsoft.com/fwlink/?LinkId=88605). [Dokumentace nástrojů podpory Windows Support Tools](https://go.microsoft.com/fwlink/?LinkId=94840) popisuje syntaxe pro nástroj Httpcfg.exe.  
  
 Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe, který je už nainstalovaný.  
  
 Toto téma popisuje, jak provádět několik postupů:  
  
-   Určení počítače aktuální konfiguraci portů.  
  
-   Načtení kryptografického otisku certifikátu (nezbytné pro následující dva postupy).  
  
-   Vytvoření vazby certifikátu SSL na konfiguraci portu.  
  
-   Vytvoření vazby certifikátu SSL na konfigurace portů a podpůrné klientské certifikáty.  
  
-   Odstraňuje se certifikát SSL od číslo portu.  
  
 Všimněte si, že změna certifikáty uložené v počítači vyžaduje oprávnění správce.  
  
### <a name="to-determine-how-ports-are-configured"></a>Chcete-li zjistit, jak jsou nakonfigurované porty  
  
1. V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe zobrazíte aktuální konfiguraci portů pomocí **dotazu** a **ssl** přepne, jak je znázorněno v následujícím příkladu.  
  
    ```  
    httpcfg query ssl  
    ```  
  
2. V [!INCLUDE[wv](../../../../includes/wv-md.md)], chcete-li zobrazit aktuální konfigurací portů, pomocí nástroje Netsh.exe, jak je znázorněno v následujícím příkladu.  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Chcete-li získat kryptografický otisk certifikátu  
  
1. Pomocí modulu snap-in Certifikáty konzoly MMC se najít certifikát X.509, který má zamýšleným účelem ověření klienta. Další informace najdete v tématu [jak: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2. Přístup k kryptografický otisk certifikátu. Další informace najdete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Zkopírujte kryptografický otisk certifikátu do textového editoru, jako je například Poznámkový blok.  
  
4. Odebere všechny mezery mezi hexadecimálních znaků. Jedním ze způsobů jak toho dosáhnout, je použít funkci Najít a nahradit text editoru a nahraďte každou mezeru znakem null.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>K vytvoření vazby certifikátu SSL na číslo portu  
  
1. V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe v režimu "set" v úložišti vrstvy SSL (Secure Sockets) k vytvoření vazby certifikátu na číslo portu. Nástroj používá k identifikaci certifikátu a kryptografický otisk, jak je znázorněno v následujícím příkladu.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   **-I** přepínač je syntaxe `IP`:`port` a dává pokyn nástroji a nastavte certifikát na port 8012 počítače. Volitelně můžete čtyři nuly, které předcházet číslo můžete také nahrazuje skutečné IP adresu počítače.  
  
    -   **-H** přepínač určuje kryptografický otisk certifikátu.  
  
2. V [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe, jak je znázorněno v následujícím příkladu.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   **Certhash** parametr určuje kryptografický otisk certifikátu.  
  
    -   **Ipport** parametr určuje IP adresu a port, a funguje stejně jako **-i** přepínač nástroj Httpcfg.exe popsané.  
  
    -   **Appid** parametr je identifikátor GUID, který slouží k identifikaci vlastnící aplikace.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Vytvoření vazby certifikátu SSL na číslo portu a podpoře klientské certifikáty  
  
1. V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aby podporovaly klienty, které ověřování pomocí certifikátů X.509 na transportní vrstvě, postupujte podle předchozího postupu, ale další parametr příkazového řádku předat HttpCfg.exe, jak je znázorněno v následujícím příkladu.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F** přepínač je syntaxe `n` kde n je číslo v rozsahu od 1 do 7. Hodnota 2, jak je znázorněno v předchozím příkladu povolí klientské certifikáty na transportní vrstvě. Hodnota 3 umožňuje klientské certifikáty a tyto certifikáty se mapuje na účet Windows. Pro chování ostatních hodnot naleznete v nápovědě HttpCfg.exe.  
  
2. V [!INCLUDE[wv](../../../../includes/wv-md.md)], klientům podporu ověřování pomocí certifikátů X.509 na transportní vrstvě, postupujte podle předchozího postupu, ale s dalším parametrem, jak je znázorněno v následujícím příkladu.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Odstranit certifikát SSL od číslo portu  
  
1. Použijte nástroj HttpCfg.exe nebo Netsh.exe zobrazíte portů a kryptografické otisky všechny vazby v počítači. Tisknout informace na disk, použijte znak přesměrování ">", jak je znázorněno v následujícím příkladu.  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2. V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe s **odstranit** a **ssl** klíčová slova. Použití **-i** přepínač k určení `IP`:`port` číslo a **-h** přepínač k určení kryptografického otisku.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. V [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí nástroje Netsh.exe, jak je znázorněno v následujícím příkladu.  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak vytvořit v místním prostředí pomocí <xref:System.ServiceModel.WSHttpBinding> třídy nastavenou na zabezpečení přenosu. Při vytváření aplikace, zadejte číslo portu adresy.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
