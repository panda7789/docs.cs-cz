---
title: Prvek ws2007FederationHttpBinding
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 7dffe56cf5593f1cd59cccd7ea9b6b0e173e0c2c
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221281"
---
# <a name="ws-2007-federation-http-binding"></a>Prvek ws2007FederationHttpBinding
Tato ukázka demonstruje použití <xref:System.ServiceModel.WS2007FederationHttpBinding>, standardní vazbu, že můžete použít k sestavení federovaných scénářích podporu verzi 1.3 specifikaci WS-Trust.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Ukázka se skládá z klienta na základě konzoly programu (Client.exe), programu služby tokenů zabezpečení na základě konzoly (Securitytokenservice.exe) a programu pomocí konzoly služby (Service.exe). Služba implementuje kontrakt, který definuje vzor komunikace požadavku/odpovědi. Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (`Add`, `Subtract`, `Multiply`, a `Divide`). Klient získá token zabezpečení z tokenu služba zabezpečení (STS) a umožňuje synchronní žádosti o službu pro dané matematické operace. Služba potom odpovědi k výsledku. Činnost klienta je vidět v okně konzoly.  
  
 Ukázka vytvoří `ICalculator` dostupná pomocí kontraktu `ws2007FederationHttpBinding` elementu. Konfiguraci této vazby v klientovi je znázorněno v následujícím kódu.  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Endpoint address and binding for Security Token Service -->  
          <issuer address ="http://localhost:8000/sts/windows"   
                  binding ="ws2007HttpBinding" />                
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hodnota určuje, který režim zabezpečení by měl sloužit. V této ukázce `message` zabezpečení se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<Issuer >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element v rámci [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Určuje adresu a vazbu pro službu STS, která vydá token zabezpečení do klienta, takže klient může ověření `ICalculator` služby.  
  
 Konfiguraci této vazby ve službě je znázorněno v následujícím kódu.  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Metadata address for Security Token Service -->  
          <issuerMetadata address ="http://localhost:8000/sts/mex" >  
            <identity>  
              <certificateReference storeLocation ="CurrentUser"   
                                    storeName="TrustedPeople"   
                                    x509FindType ="FindBySubjectDistinguishedName"   
                                    findValue ="CN=STS" />  
            </identity>  
          </issuerMetadata>  
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hodnota určuje, který režim zabezpečení by měl sloužit. V této ukázce `message` zabezpečení se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<IssuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) prvek `ws2007FederationHttpBinding` uvnitř [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) určuje adrese a identitě pro koncový bod, který slouží k načtení metadata pro službu STS.  
  
 Chování služby je uvedeno v následujícím kódu.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name ="ServiceBehaviour" >  
      <serviceDebug includeExceptionDetailInFaults ="true"/>  
      <serviceMetadata httpGetEnabled ="true"/>  
      <serviceCredentials>  
        <issuedTokenAuthentication>  
          <knownCertificates>  
            <add storeLocation ="LocalMachine"  
                 storeName="TrustedPeople"  
                 x509FindType="FindBySubjectDistinguishedName"  
                 findValue="CN=STS" />  
          </knownCertificates>  
        </issuedTokenAuthentication>  
        <serviceCertificate storeLocation ="LocalMachine"  
                            storeName ="My"  
                            x509FindType ="FindBySubjectDistinguishedName"  
                            findValue ="CN=localhost"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umožňuje zadat omezení na tokeny, umožňuje klientům k dispozici během ověřování služby. Tato konfigurace určuje, že tokeny podepsán certifikátem, jehož název subjektu je CN = služby STS jsou změna přijata službou.  
  
 Služba STS jeden koncový bod k dispozici prostřednictvím standardních <xref:System.ServiceModel.WS2007HttpBinding>. Služby jsou reaguje na požadavky od klientů pro tokeny. Pokud klient je ověřený pomocí účtu Windows, služby vystaví token, který obsahuje jméno uživatele klienta jako deklarace identity. Jako součást vytváření token příznaky STS token pomocí soukromého klíče přidružené k CN = certifikátu STS. Kromě toho vytvoří symetrický klíč a zašifruje pomocí veřejného klíče přidruženého CN = localhost certifikát. V vrácením tokenu klientovi, služba tokenů zabezpečení také vrátí hodnotu symetrický klíč. Klient poskytne vydaný token `ICalculator` služby a prokáže, že zná symetrický klíč pomocí podepsání zprávy s tímto klíčem.  
  
 Když spustíte ukázku, požadavek na token zabezpečení se zobrazí v okně konzoly služby tokenů zabezpečení. Požadavky a odpovědi operace se zobrazují v oknech konzoly klienta a služby. Stisknutím klávesy ENTER v některém z okna konzoly vypnout aplikaci.  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Soubor Setup.bat zahrnuté v této ukázce umožňuje nakonfigurovat server a služba tokenů zabezpečení pomocí příslušné certifikáty, které budou spouštět aplikace v místním prostředí. Dávkový soubor se vytvoří dva certifikáty v úložišti LocalMachine/TrustedPeople certifikátů. První certifikát má název předmětu CN = STS a služba tokenů zabezpečení používá k podepisování tokenů zabezpečení, které vystavuje do klienta. Druhý certifikát má název předmětu CN = localhost a služba tokenů zabezpečení používá k šifrování klíče tak, aby mohly dešifrovat služby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Otevřete příkazový řádek vývojáře pro sadu Visual Studio s oprávněními správce a spusťte soubor Setup.bat vytvořit požadované certifikáty.  
  
 Tento dávkový soubor používá Certmgr.exe a Makecert.exe, které jsou distribuovány v sadě Windows SDK. Však musíte spustit Setup.bat z v rámci příkazový řádek sady Visual Studio umožňuje skript, který chcete najít těchto nástrojů.  
  
1.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], je nutné spustit Service.exe, Client.exe, a SecurityTokenService.exe s se zvýšenými oprávněními (pravým tlačítkem myši na soubory a pak klikněte na tlačítko **spustit jako správce**).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a>Viz také
