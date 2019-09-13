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
ms.openlocfilehash: 6e21311802b0a3ce4e415b14686b101d31f18035
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893310"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Postupy: Konfigurace portu s certifikátem SSL
Při vytváření služby Windows Communication Foundation v místním prostředí (WCF) s <xref:System.ServiceModel.WSHttpBinding> třídou, která používá zabezpečení přenosu, je také nutné nakonfigurovat port s certifikátem X. 509. Pokud nevytváříte samoobslužně hostované služby, můžete službu hostovat na Internetová informační služba (IIS). Další informace najdete v tématu [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 K nakonfigurování portu závisí nástroj, který použijete, na operačním systému, který běží na vašem počítači.  
  
 Pokud používáte systém [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj Httpcfg. exe. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Tento nástroj je nainstalován. Pomocí [!INCLUDE[wxp](../../../../includes/wxp-md.md)]nástroje můžete stáhnout nástroj v [nástroji podpory systému Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606). Další informace najdete v tématu [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605). Dokumentace k nástrojům [podpory systému Windows](https://go.microsoft.com/fwlink/?LinkId=94840) vysvětluje syntaxi nástroje HttpCfg. exe.  
  
 Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], použijte nástroj Netsh. exe, který je už nainstalovaný.  
  
 Toto téma popisuje, jak provést několik postupů:  
  
- Určení aktuální konfigurace portu počítače.  
  
- Získávání kryptografického otisku certifikátu (nutné pro následující dva postupy).  
  
- Naváže certifikát SSL na konfiguraci portu.  
  
- Vytvořte vazbu certifikátu SSL s konfigurací portu a podpůrnými klientskými certifikáty.  
  
- Odstraňuje se certifikát SSL z čísla portu.  
  
 Nezapomeňte, že změna certifikátů uložených v počítači vyžaduje oprávnění správce.  
  
### <a name="to-determine-how-ports-are-configured"></a>Určení způsobu konfigurace portů  
  
1. V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)]použijte nástroj Httpcfg. exe k zobrazení aktuální konfigurace portu pomocí přepínačů **dotaz** a **SSL** , jak je znázorněno v následujícím příkladu.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. V [!INCLUDE[wv](../../../../includes/wv-md.md)]nástroji pomocí nástroje Netsh. exe zobrazte aktuální konfiguraci portů, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Získání kryptografického otisku certifikátu  
  
1. Pomocí modulu snap-in Certifikáty konzoly MMC Najděte certifikát X. 509, který má zamýšlený účel ověřování klienta. Další informace najdete v tématu [jak: Zobrazení certifikátů pomocí modulu snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)konzoly MMC.  
  
2. Přístup k kryptografickému otisku certifikátu. Další informace najdete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Zkopírujte kryptografický otisk certifikátu do textového editoru, například do poznámkového bloku.  
  
4. Odebere všechny mezery mezi šestnáctkovými znaky. Jedním ze způsobů, jak toho dosáhnout, je použít funkci Find-and-nahrazování textového editoru a nahradit každou mezeru znakem null.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>Vytvoření vazby certifikátu SSL k číslu portu  
  
1. V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] systému [!INCLUDE[wxp](../../../../includes/wxp-md.md)]nebo použijte nástroj Httpcfg. exe v režimu "Set" v úložišti SSL (Secure Sockets Layer) (SSL) k navázání certifikátu na číslo portu. Nástroj používá kryptografický otisk k identifikaci certifikátu, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - Přepínač **-i** má syntaxi `IP`:`port` a instruuje nástroj, aby nastavil certifikát na port 8012 počítače. Volitelně se čtyřmi nulami, které předcházejí číslu, může nahradit také skutečnou IP adresou počítače.  
  
    - Přepínač **-h** určuje kryptografický otisk certifikátu.  
  
2. V [!INCLUDE[wv](../../../../includes/wv-md.md)]nástroji použijte nástroj Netsh. exe, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - Parametr **certhash** určuje kryptografický otisk certifikátu.  
  
    - Parametr **ipport** určuje IP adresu a port a funguje stejně jako přepínač **-i** nástroje HttpCfg. exe, který je popsán.  
  
    - Parametr **AppID** je identifikátor GUID, který lze použít k identifikaci vlastnící aplikace.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Vytvoření vazby certifikátu SSL k číslu portu a podpora klientských certifikátů  
  
1. V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] systému [!INCLUDE[wxp](../../../../includes/wxp-md.md)]nebo pro podporu klientů, kteří se ověřují pomocí certifikátů X. 509 na transportní vrstvě, postupujte podle předchozího postupu, ale předejte další parametr příkazového řádku Httpcfg. exe, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     Přepínač **-f** má syntaxi `n` , kde n je číslo v rozmezí od 1 do 7. Hodnota 2, jak je znázorněno v předchozím příkladu, umožňuje klientské certifikáty na transportní vrstvě. Hodnota 3 povolí klientským certifikátům a mapuje tyto certifikáty na účet systému Windows. Chování dalších hodnot naleznete v nápovědě k HttpCfg. exe.  
  
2. [!INCLUDE[wv](../../../../includes/wv-md.md)]Pro podporu klientů, kteří se ověřují pomocí certifikátů X. 509 na transportní vrstvě, postupujte podle předchozího postupu, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Odstranění certifikátu SSL z čísla portu  
  
1. Pomocí nástroje HttpCfg. exe nebo Netsh. exe zobrazte porty a kryptografické otisky všech vazeb v počítači. Chcete-li vytisknout informace na disk, použijte znak přesměrování ">", jak je znázorněno v následujícím příkladu.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)]použijte nástroj Httpcfg. exe s klíčovými slovy **Delete** a **SSL** . Použijte přepínač **-i** k určení `IP``port` kryptografického otisku a parametru **-h** .  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. V [!INCLUDE[wv](../../../../includes/wv-md.md)]nástroji použijte nástroj Netsh. exe, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak vytvořit samoobslužnou službu s použitím <xref:System.ServiceModel.WSHttpBinding> třídy nastavenou na zabezpečení přenosu. Při vytváření aplikace zadejte číslo portu v adrese.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
