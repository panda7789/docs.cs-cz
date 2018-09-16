---
title: Přehled zabezpečení přenosu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 9a04b8aaf9c6263a8935099963aaa1dc8d9100fd
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664667"
---
# <a name="transport-security-overview"></a>Přehled zabezpečení přenosu
Přenos mechanismy zabezpečení ve Windows Communication Foundation (WCF) závisí na vazby a přenosu používána. Například při použití <xref:System.ServiceModel.WSHttpBinding> třídy, je přenos protokolu HTTP a hlavní mechanismus pro zabezpečení přenosu je vrstva SSL (Secure Sockets) přes protokol HTTP, říká protokolu HTTPS. Toto téma popisuje mechanismy zabezpečení hlavní přenosu používána vazeb poskytovaných systémem WCF.  
  
> [!NOTE]
>  Při použití zabezpečení SSL v rozhraní .NET Framework 3.5 a novější klient WCF používá zprostředkující certifikáty ve své vlastní úložiště certifikátů a zprostředkujících certifikátů přijatých během vyjednávání SSL k provedení ověřování řetězu certifikátů na služby certifikát. Rozhraní .NET framework 3.0 využívá jenom nainstalované v místním úložišti certifikátů zprostředkující certifikáty.  
  
> [!WARNING]
>  Při použití zabezpečení přenosu <!--zz <xref:System.Treading.Thread.CurrentPrincipal%2A> --> `CurrentPrincipal` mohou být přepsány vlastnosti. Abyste tomu zabránili sadě děje <!--zz <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermission%2A> --> `PrincipalPermission` na hodnotu None. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> je chování služby, které lze nastavit v popisu služby.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> třída neposkytuje zabezpečení. Tato vazba je určená pro interoperabilitu se webových služeb, které neimplementují zabezpečení. Však můžete přepnout na zabezpečení tak, že nastavíte <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> vlastnost na hodnotu s výjimkou <xref:System.ServiceModel.BasicHttpSecurityMode.None>. Pokud chcete povolit zabezpečení přenosu, nastavte vlastnost na <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
### <a name="interoperation-with-iis"></a>Vzájemná spolupráce se službou IIS  
 <xref:System.ServiceModel.BasicHttpBinding> Třída se používá především pro spolupráci s existující webové služby a mnohé z těchto služeb jsou hostované v Internetové informační služby (IIS). Zabezpečení přenosu pro tuto vazbu v důsledku toho je navržená pro bezproblémovou spolupráci s weby služby IIS. Uděláte to pomocí nastavení režimu zabezpečení rozhraní <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> a upravením typ pověření klienta. Typ hodnot přihlašovacích údajů odpovídají mechanismy zabezpečení adresář služby IIS. Následující kód ukazuje režimu nastavování a nastavte typ přihlašovacích údajů Windows. Tuto konfiguraci můžete použít, když klient i server jsou ve stejné doméně Windows.  
  
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
 To odpovídá metodu základního ověřování ve službě IIS. Při použití tohoto režimu, musí se nakonfigurovat server služby IIS Windows uživatelské účty a příslušná oprávnění systému souborů NTFS. Další informace o [!INCLUDE[iis601](../../../../includes/iis601-md.md)], naleznete v tématu [povolení základního ověřování a konfigurace název sféry](https://go.microsoft.com/fwlink/?LinkId=88592). Další informace o [!INCLUDE[iisver](../../../../includes/iisver-md.md)], naleznete v tématu [IIS 7.0 Beta: Nakonfigurujte základní ověřování](https://go.microsoft.com/fwlink/?LinkId=88593).  
  
#### <a name="certificate"></a>Certifikát  
 Služba IIS má možnost, aby klienti k přihlášení pomocí certifikátu. Tato funkce také umožňuje službě IIS mapování klientského certifikátu pro účet Windows. Další informace o [!INCLUDE[iis601](../../../../includes/iis601-md.md)], naleznete v tématu [povolení klientských certifikátů ve službě IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88594). Další informace o [!INCLUDE[iisver](../../../../includes/iisver-md.md)], naleznete v tématu [IIS 7.0 Beta: Konfigurace certifikátů serveru ve službě IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="digest"></a>ověřování algoritmem Digest  
 Ověřování hodnotou hash se podobá základní ověřování, ale nabízí výhodu v podobě odesílání přihlašovací údaje jako hodnotu hash, nikoli ve formátu prostého textu. Další informace o [!INCLUDE[iis601](../../../../includes/iis601-md.md)], naleznete v tématu [ověřování algoritmem Digest ve službě IIS 6.0](https://go.microsoft.com/fwlink/?LinkID=88443). Další informace o [!INCLUDE[iisver](../../../../includes/iisver-md.md)], naleznete v tématu [IIS 7.0 Beta: Konfigurace ověřování algoritmem Digest](https://go.microsoft.com/fwlink/?LinkId=88596).  
  
#### <a name="windows"></a>Windows  
 To odpovídá integrované ověřování Windows služby IIS. Pokud nastavíte tuto hodnotu, serveru také by měl existovat v doméně Windows, která používá protokol Kerberos jako řadič domény. Pokud server není v doméně s podporou protokolu Kerberos nebo pokud systému Kerberos nezdaří, můžete použít hodnoty NT LAN Manager (NTLM) popsané v další části. Další informace o [!INCLUDE[iis601](../../../../includes/iis601-md.md)], naleznete v tématu [integrované ověřování Windows ve službě IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88597). Další informace o [!INCLUDE[iisver](../../../../includes/iisver-md.md)], naleznete v tématu [IIS 7.0 Beta: Konfigurace certifikátů serveru ve službě IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="ntlm"></a>NTLM  
 To umožňuje, aby server pro ověřování pomocí protokolu NTLM, pokud protokol Kerberos nezdaří. Další informace o konfiguraci služby IIS v [!INCLUDE[iis601](../../../../includes/iis601-md.md)], naleznete v tématu [vynucení ověřování protokolem NTLM](https://go.microsoft.com/fwlink/?LinkId=88598). Pro [!INCLUDE[iisver](../../../../includes/iisver-md.md)], ověřování Windows zahrnuje ověřování protokolem NTLM. Další informace najdete v tématu [IIS 7.0 Beta: Konfigurace certifikátů serveru ve službě IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=88595).  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding> Třídy je navržena pro spolupráci se službami, které implementují WS-* specifikace. Zabezpečení přenosu pro tuto vazbu je vrstva SSL (Secure Sockets) prostřednictvím protokolu HTTP nebo HTTPS. Chcete-li vytvořit aplikaci WCF, která používá protokol SSL, pomocí služby IIS pro hostování aplikace. Při vytváření aplikace v místním prostředí, můžete také použijte nástroj HttpCfg.exe k vytvoření vazby certifikátu X.509 na konkrétní port na počítači. Číslo portu je zadaný jako součást aplikace WCF jako adresy koncového bodu. Když používáte režim přenosu, adresu koncového bodu musí obsahovat protokol HTTPS nebo bude vyvolána výjimka za běhu. Další informace najdete v tématu [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Pro ověřování klientů, nastavte <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.HttpTransportSecurity> třídy do jednoho z <xref:System.ServiceModel.HttpClientCredentialType> hodnot výčtu. Hodnoty výčtu jsou shodné s typy přihlašovacích údajů klienta pro <xref:System.ServiceModel.BasicHttpBinding> a jsou navrženy pro hostované službou IIS.  
  
 Následující příklad ukazuje vazba používá typ pověření klienta Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Tato vazba poskytuje pouze zprávy na úrovni zabezpečení, ne zabezpečení transportní vrstvy.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding> Třída používá TCP pro přenos zpráv. Implementace zabezpečení TLS (Transport Layer) přes protokol TCP poskytuje zabezpečení pro režim přenosu. Operační systém poskytuje implementaci TLS.  
  
 Můžete také určit typ přihlašovacích údajů klienta tak, že nastavíte <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.TcpTransportSecurity> třídy do jednoho z <xref:System.ServiceModel.TcpClientCredentialType> hodnoty, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Klient  
 Na straně klienta, je nutné zadat certifikát pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> třídy.  
  
> [!NOTE]
>  Pokud používáte Windows security, certifikát se nevyžaduje.  
  
 Následující kód používá kryptografický otisk certifikátu, který ji jednoznačně identifikuje. Další informace o certifikátech najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Můžete také zadat certifikát v konfiguraci klienta pomocí [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu v oddílu chování.  
  
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
 <xref:System.ServiceModel.NetNamedPipeBinding> Třídy je navržené pro efektivní komunikace uvnitř počítači; to znamená pro procesy běžící na stejný počítač, i když kanály pojmenovaného kanálu lze vytvořit mezi dvěma počítači ve stejné síti. Tato vazba obsahuje pouze zabezpečení na úrovni přenosu. Při vytváření aplikace používá tuto vazbu, adresy koncových bodů musí obsahovat "net.pipe" jako protokol adresu koncového bodu.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Při použití zabezpečení přenosu, tato vazba používá protokol SSL přes protokol HTTP, označuje se jako protokol HTTPS s vydaný token (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). Další informace o federovanými aplikacemi najdete v tématu [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding> Třída je zabezpečeného přenosu, která je navržena pro efektivní komunikaci pomocí funkce sítě peer-to-peer. Jak je uvedeno podle názvu třídy a vazbu, je TCP protokolu. Pokud režim zabezpečení je nastavený na přenos, vazba implementuje protokol TLS přes protokol TCP. Další informace o funkci peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding a NetMsmqBinding  
 Úplné informace o přenosu zabezpečení pomocí služby Řízení front zpráv (dříve nazývané služby MSMQ), najdete v části [zabezpečení zabezpečení zprávy přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Viz také  
 [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
