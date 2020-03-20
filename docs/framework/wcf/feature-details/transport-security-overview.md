---
title: Přehled zabezpečení přenosu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: f30b2c587d7f9b21c1f19fa1c3943621fc2607cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184343"
---
# <a name="transport-security-overview"></a>Přehled zabezpečení přenosu
Mechanismy zabezpečení přenosu v nadaci Windows Communication Foundation (WCF) závisí na použité vazbě a přenosu. Například při použití <xref:System.ServiceModel.WSHttpBinding> třídy je přenos HTTP a primární mechanismus pro zabezpečení přenosu je SSL (Secure Sockets Layer) přes HTTP, běžně nazývané HTTPS. Toto téma popisuje hlavní mechanismy zabezpečení přenosu používané v systému WCF poskytovány vazby.  
  
> [!NOTE]
> Pokud je zabezpečení SSL používáno s rozhraním .NET Framework 3.5 a novějším, klient WCF používá zprostředkující certifikáty v úložišti certifikátů i zprostředkující certifikáty přijaté během vyjednávání SSL k ověření řetězu certifikátů Certifikát. Rozhraní .NET Framework 3.0 používá pouze zprostředkující certifikáty nainstalované v místním úložišti certifikátů.  
  
> [!WARNING]
> Při použití zabezpečení přenosu <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> může být vlastnost přepsána. Chcete-li tomu zabránit, nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> na . <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>je chování služby, které lze nastavit v popisu služby.  
  
## <a name="basichttpbinding"></a>Základní vazbahttp  
 Ve výchozím <xref:System.ServiceModel.BasicHttpBinding> nastavení třída neposkytuje zabezpečení. Tato vazba je určena pro interoperabilitu s poskytovateli webových služeb, kteří neimplementují zabezpečení. Zabezpečení však můžete zapnout <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> nastavením vlastnosti <xref:System.ServiceModel.BasicHttpSecurityMode.None>na libovolnou hodnotu s výjimkou . Chcete-li povolit zabezpečení <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>přenosu, nastavte vlastnost na .  
  
### <a name="interoperation-with-iis"></a>Spolupráce se svištinou IIS  
 Třída <xref:System.ServiceModel.BasicHttpBinding> se používá především ke spoluaktivitě s existujícími webovými službami a mnoho z těchto služeb je hostováno internetovou informační službou (IIS). V důsledku toho je zabezpečení přenosu pro tuto vazbu určeno pro bezproblémovou spolupráci se servery iis. To se provádí nastavením <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> režimu zabezpečení a potom nastavením typu pověření klienta. Hodnoty typu pověření odpovídají mechanismům zabezpečení adresáře služby IIS. Následující kód ukazuje nastavený režim a typ pověření nastavený na systém Windows. Tuto konfiguraci můžete použít, pokud jsou klient i server ve stejné doméně systému Windows.  
  
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
  
 Následující části popisují další typy pověření klienta.  
  
#### <a name="basic"></a>Basic  
 To odpovídá základní metodě ověřování ve službě IIS. Při použití tohoto režimu musí být server IIS nakonfigurován pomocí uživatelských účtů systému Windows a příslušných oprávnění systému souborů NTFS. Další informace o službě IIS 6.0 naleznete [v tématu Povolení základního ověřování a konfigurace názvu sféry](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc785293(v=ws.10)). Další informace o službě IIS 7.0 naleznete [v tématu Konfigurace základního ověřování (IIS 7).](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10))  
  
#### <a name="certificate"></a>Certifikát  
 IIS má možnost vyžadovat, aby se klienti přihlašovali pomocí certifikátu. Tato funkce také umožňuje službě IIS mapovat klientský certifikát na účet systému Windows. Další informace o službě IIS 6.0 naleznete [v tématu Povolení klientských certifikátů ve službě IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc727994(v=ws.10)). Další informace o službě IIS 7.0 naleznete [v tématu Konfigurace certifikátů serveru ve službě IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="digest"></a>Digest  
 Ověřování algoritmem Digest je podobné základnímu ověřování, ale nabízí výhodu odesílání pověření jako hodnotu hash namísto ve prostém textu. Další informace o službě IIS 6.0 naleznete [v tématu Digest Authentication in IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)). Další informace o službě IIS 7.0 naleznete [v tématu Konfigurace ověřování algoritmem Digest (IIS 7).](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10))  
  
#### <a name="windows"></a>Windows  
 To odpovídá integrovanému ověřování systému Windows ve službě IIS. Pokud je server nastaven na tuto hodnotu, očekává se, že bude existovat také v doméně systému Windows, která jako řadič domény používá protokol Kerberos. Pokud server není v doméně zálohované protokolem Kerberos nebo pokud systém Kerberos selže, můžete použít hodnotu NTLAN Manager (NTLM) popsanou v další části. Další informace o službě IIS 6.0 naleznete [v tématu Integrované ověřování systému Windows ve službě IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc738016(v=ws.10)). Další informace o službě IIS 7.0 naleznete [v tématu Konfigurace certifikátů serveru ve službě IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
#### <a name="ntlm"></a>NTLM  
 To umožňuje serveru používat ntlm pro ověřování, pokud protokol Kerberos selže. Další informace o konfiguraci služby IIS ve službě IIS 6.0 naleznete [v tématu Vynucení ověřování NTLM](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc786486(v=ws.10)). U služby IIS 7.0 zahrnuje ověřování systému Windows ověřování NTLM. Další informace naleznete [v tématu Konfigurace certifikátů serveru ve službě IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
## <a name="wshttpbinding"></a>Vazby WsHttp  
 Třída <xref:System.ServiceModel.WSHttpBinding> je určena pro spolupráci se službami, které implementují specifikace WS-*. Zabezpečení přenosu pro tuto vazbu je SSL (Secure Sockets L) přes HTTP nebo HTTPS. Chcete-li vytvořit aplikaci WCF, která používá ssl, použijte službu IIS k hostování aplikace. Případně pokud vytváříte samoobslužnou aplikaci, použijte nástroj HttpCfg.exe k vytvoření svázání certifikátu X.509 s určitým portem v počítači. Číslo portu je určeno jako součást aplikace WCF jako adresa koncového bodu. Při použití režimu přenosu musí adresa koncového bodu obsahovat protokol HTTPS nebo bude vyvolána výjimka za běhu. Další informace naleznete v tématu [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Pro ověřování klienta <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> nastavte <xref:System.ServiceModel.HttpTransportSecurity> vlastnost třídy <xref:System.ServiceModel.HttpClientCredentialType> na jednu z hodnot výčtu. Hodnoty výčtu jsou shodné s <xref:System.ServiceModel.BasicHttpBinding> typy pověření klienta a jsou navrženy tak, aby byly hostovány se službami IIS.  
  
 Následující příklad ukazuje vazbu používanou s typem pověření klienta systému Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualhttpVazba  
 Tato vazba poskytuje pouze zabezpečení na úrovni zprávy, nikoli zabezpečení na úrovni přenosu.  
  
## <a name="nettcpbinding"></a>Nettcpbinding  
 Třída <xref:System.ServiceModel.NetTcpBinding> používá TCP pro přenos zpráv. Zabezpečení pro režim přenosu je zajištěno implementací zabezpečení transportní vrstvy (TLS) přes TCP. Implementace TLS je poskytována operačním systémem.  
  
 Typ pověření klienta můžete také určit <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> nastavením <xref:System.ServiceModel.TcpTransportSecurity> vlastnosti třídy <xref:System.ServiceModel.TcpClientCredentialType> na jednu z hodnot, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Klient  
 Na straně klienta je nutné <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> zadat certifikát <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> pomocí metody třídy.  
  
> [!NOTE]
> Pokud používáte zabezpečení systému Windows, není vyžadován certifikát.  
  
 Následující kód používá kryptografický otisk certifikátu, který jej jednoznačně identifikuje. Další informace o certifikátech naleznete v [tématu Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Případně zadejte certifikát v konfiguraci klienta pomocí [ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) prvek v části chování.  
  
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
 Třída <xref:System.ServiceModel.NetNamedPipeBinding> je určena pro efektivní komunikaci v rámci počítače; To znamená pro procesy spuštěné ve stejném počítači, ačkoli pojmenované kanály kanálu lze vytvořit mezi dvěma počítači ve stejné síti. Tato vazba poskytuje pouze zabezpečení na úrovni přenosu. Při vytváření aplikací pomocí této vazby musí adresy koncového bodu obsahovat "net.pipe" jako protokol adresy koncového bodu.  
  
## <a name="wsfederationhttpbinding"></a>WsFederationhttpbinding  
 Při použití zabezpečení přenosu tato vazba používá SSL přes HTTP,<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>známý jako HTTPS s vydaným tokenem ( ). Další informace o federačních aplikacích naleznete v [tématu Federation and Issueed Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>Vazby NetPeerTcpBinding  
 Třída <xref:System.ServiceModel.NetPeerTcpBinding> je bezpečný přenos, který je určen pro efektivní komunikaci pomocí funkce peer-to-peer sítě. Jak je uvedeno v názvu třídy a vazby, TCP je protokol. Pokud je režim zabezpečení nastaven na přenos, vazba implementuje TLS přes TCP. Další informace o funkci peer-to-peer naleznete v [tématu Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding a NetMsmqBinding  
 Úplnou diskusi o zabezpečení přenosu pomocí služby Řízení front zpráv (dříve označované jako služba MSMQ) naleznete v tématu [Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Viz také

- [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
