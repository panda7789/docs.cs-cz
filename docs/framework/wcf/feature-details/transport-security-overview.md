---
title: Přehled zabezpečení přenosu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 345b5028ccc5c24bd60cf7ecbd2610b27f44b8b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968663"
---
# <a name="transport-security-overview"></a>Přehled zabezpečení přenosu
Mechanismy zabezpečení přenosu v Windows Communication Foundation (WCF) závisí na používané vazbě a přenosu. Například při použití <xref:System.ServiceModel.WSHttpBinding> třídy je přenos HTTP a primární mechanismus pro zabezpečení přenosu je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP, obvykle se označuje jako https. Toto téma popisuje hlavní mechanismy zabezpečení přenosu používané v rámci vazeb poskytovaných systémem WCF.  
  
> [!NOTE]
> Když se zabezpečení SSL používá s .NET Framework 3,5 a novějším, používá klient služby WCF jak zprostředkující certifikáty v úložišti certifikátů, tak zprostředkující certifikáty přijaté během vyjednávání SSL k provedení ověření řetězu certifikátů na úrovni služby. certifikát. .NET Framework 3,0 používá pouze zprostředkující certifikáty nainstalované v místním úložišti certifikátů.  
  
> [!WARNING]
>  Je-li použito zabezpečení přenosu, <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> vlastnost může být přepsána. Chcete-li zabránit tomu, aby <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> se <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType>to stalo, nastavte na. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>je chování služby, které lze nastavit v popisu služby.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> Třída neposkytuje zabezpečení. Tato vazba je navržena pro interoperabilitu s poskytovateli webových služeb, kteří neimplementují zabezpečení. Můžete však přepnout na zabezpečení <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> nastavením vlastnosti na libovolnou hodnotu s výjimkou. <xref:System.ServiceModel.BasicHttpSecurityMode.None> Chcete-li povolit zabezpečení přenosu, nastavte vlastnost <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>na hodnotu.  
  
### <a name="interoperation-with-iis"></a>Spolupráce se službou IIS  
 Tato <xref:System.ServiceModel.BasicHttpBinding> třída se primárně používá pro spolupráci s existujícími webovými službami a mnohé z těchto služeb jsou hostovány službou Internetová informační služba (IIS). V důsledku toho je zabezpečení přenosu této vazby navržené pro bezproblémové prochodování s weby služby IIS. To se provádí nastavením režimu zabezpečení na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> a pak nastavením typu pověření klienta. Hodnoty typu přihlašovacích údajů odpovídají mechanismům zabezpečení adresáře služby IIS. Následující kód ukazuje nastavený režim a typ přihlašovacích údajů nastavený na Windows. Tuto konfiguraci můžete použít, pokud jsou klienti i servery ve stejné doméně systému Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Nebo v konfiguraci:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 Následující části popisují další typy přihlašovacích údajů klienta.  
  
#### <a name="basic"></a>Základní  
 To odpovídá metodě základního ověřování ve službě IIS. Při použití tohoto režimu musí být server IIS nakonfigurovaný pomocí uživatelských účtů Windows a odpovídajících oprávnění systému souborů NTFS. Další informace o službě IIS 6,0 najdete v tématu [Povolení základního ověřování a konfigurace názvu sféry](https://go.microsoft.com/fwlink/?LinkId=88592). Další informace o službě IIS 7,0 najdete v tématu [Konfigurace základního ověřování (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10)).  
  
#### <a name="certificate"></a>Certifikát  
 Služba IIS má možnost vyžadovat, aby se klienti přihlásili pomocí certifikátu. Tato funkce také umožňuje službě IIS mapovat klientský certifikát na účet systému Windows. Další informace o službě IIS 6,0 najdete v tématu [Povolení klientských certifikátů ve službě iis 6,0](https://go.microsoft.com/fwlink/?LinkId=88594). Další informace o službě IIS 7,0 najdete v tématu [Konfigurace certifikátů serveru ve službě IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="digest"></a>Otisk  
 Ověřování hodnotou hash se podobá základnímu ověřování, ale nabízí výhodu odeslání přihlašovacích údajů jako hodnoty hash namísto nešifrovaných textů. Další informace o službě IIS 6,0 najdete v tématu [ověřování algoritmem Digest ve službě iis 6,0](https://go.microsoft.com/fwlink/?LinkID=88443). Další informace o službě IIS 7,0 najdete v tématu [Konfigurace ověřování algoritmem Digest (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10)).  
  
#### <a name="windows"></a>Windows  
 To odpovídá integrovanému ověřování systému Windows ve službě IIS. Pokud je tato hodnota nastavená na tuto hodnotu, očekává se, že server existuje v doméně systému Windows, která jako svůj řadič domény používá protokol Kerberos. Pokud server není na doméně zálohovaný protokolem Kerberos nebo pokud dojde k chybě systému Kerberos, můžete použít hodnotu protokolu NTLM (NT LAN Manager) popsanou v následující části. Další informace o službě IIS 6,0 najdete [v tématu integrované ověřování systému Windows ve službě iis 6,0](https://go.microsoft.com/fwlink/?LinkId=88597). Další informace o službě IIS 7,0 najdete v tématu [Konfigurace certifikátů serveru ve službě IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
#### <a name="ntlm"></a>NTLM  
 To umožňuje serveru používat pro ověřování protokol NTLM, pokud dojde k chybě protokolu Kerberos. Další informace o konfiguraci služby IIS ve službě IIS 6,0 najdete v tématu [vynucení ověřování NTLM](https://go.microsoft.com/fwlink/?LinkId=88598). Pro IIS 7,0 ověřování systému Windows zahrnuje ověřování protokolem NTLM. Další informace najdete v tématu [Konfigurace certifikátů serveru ve službě IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding> Třída je navržena pro zajištění spolupráce se službami, které implementují specifikace WS-*. Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS. Chcete-li vytvořit aplikaci WCF, která používá protokol SSL, použijte k hostování aplikace službu IIS. Případně, pokud vytváříte samoobslužnou aplikaci, použijte nástroj HttpCfg. exe k vytvoření vazby certifikátu X. 509 na konkrétní port v počítači. Číslo portu je zadáno jako součást aplikace WCF jako adresa koncového bodu. Při použití transportního režimu musí adresa koncového bodu zahrnovat protokol HTTPS, jinak se za běhu vyvolá výjimka. Další informace najdete v tématu [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Pro ověřování klienta nastavte <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.HttpTransportSecurity> <xref:System.ServiceModel.HttpClientCredentialType> třídy na jednu z hodnot výčtu. Hodnoty výčtu jsou stejné jako typy přihlašovacích údajů klienta pro <xref:System.ServiceModel.BasicHttpBinding> a jsou navržené pro hostování se službami IIS.  
  
 Následující příklad ukazuje vazbu, která se používá s typem pověření klienta Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Tato vazba poskytuje pouze zabezpečení na úrovni zprávy, nikoli zabezpečení na úrovni přenosu.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding> Třída používá protokol TCP pro přenos zpráv. Zabezpečení pro transportní režim zajišťuje implementace protokolu TLS (Transport Layer Security) přes protokol TCP. Implementaci protokolu TLS poskytuje operační systém.  
  
 Můžete také zadat typ přihlašovacích údajů klienta nastavením <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> vlastnosti <xref:System.ServiceModel.TcpTransportSecurity> <xref:System.ServiceModel.TcpClientCredentialType> třídy na jednu z hodnot, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Klient  
 Na straně klienta je nutné zadat certifikát pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> třídy.  
  
> [!NOTE]
> Pokud používáte zabezpečení systému Windows, certifikát se nevyžaduje.  
  
 Následující kód používá kryptografický otisk certifikátu, který jej jednoznačně identifikuje. Další informace o certifikátech najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Případně můžete zadat certifikát v konfiguraci klienta pomocí [ \<elementu ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) v části chování.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 <xref:System.ServiceModel.NetNamedPipeBinding> Třída je navržena pro efektivní komunikaci uvnitř počítače, tedy pro procesy spuštěné ve stejném počítači, i když kanály pojmenovaného kanálu lze vytvořit mezi dvěma počítači ve stejné síti. Tato vazba poskytuje pouze zabezpečení na úrovni přenosu. Při vytváření aplikací pomocí této vazby musí adresy koncových bodů zahrnovat "NET. pipe" jako protokol adresy koncového bodu.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Při použití zabezpečení přenosu používá tato vazba protokol SSL přes protokol HTTP, který se označuje jako HTTPS s vydaným tokenem (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). Další informace o federačních aplikacích najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding> Třída je zabezpečený přenos, který je navržený pro efektivní komunikaci pomocí funkce sítě peer-to-peer. Jak je uvedeno v názvu třídy a vazby, protokol TCP je protokol. Pokud je režim zabezpečení nastavený na přenos, vazba implementuje TLS přes TCP. Další informace o funkci peer-to-peer najdete v tématu [sítě peer-](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)to-peer.  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding a NetMsmqBinding  
 Kompletní diskuzi o zabezpečení přenosu pomocí služby Řízení front zpráv (dříve nazývané služby MSMQ) najdete v tématu [zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Viz také:

- [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
