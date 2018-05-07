---
title: Prvek ws2007FederationHttpBinding
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 0fe4c0e62dbff3ae7f99f3a6dde34940abf90ae9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ws-2007-federation-http-binding"></a>Prvek ws2007FederationHttpBinding
Tento příklad znázorňuje použití <xref:System.ServiceModel.WS2007FederationHttpBinding>, standard, můžete použít k vytvoření této verze podpory 1.3 specifikace WS-Trust federovaných scénářích vazby.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Ukázka se skládá z programu pomocí konzoly klienta (Client.exe), programu služby tokenů zabezpečení na základě konzoly (Securitytokenservice.exe) a programu pomocí konzoly služby (Service.exe). Služba se implementuje kontrakt, který definuje komunikační vzor požadavek nebo odpověď. Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (`Add`, `Subtract`, `Multiply`, a `Divide`). Klient získá token zabezpečení ze zabezpečení tokenu služby (STS) a zadává synchronní požadavků službou pro danou matematické operace. Služby a odpovědi s výsledek. Činnost klienta je viditelný v okně konzoly.  
  
 Díky vzorku `ICalculator` kontrakt dostupné pomocí `ws2007FederationHttpBinding` element. Konfigurace této vazby v klientovi je zobrazena v následujícím kódu.  
  
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
  
 Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hodnota určuje, které režim zabezpečení by měl použít. V této ukázce `message` zabezpečení se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<Vystavitele >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) prvku v [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Určuje adresu a vydá token zabezpečení do klienta, takže klient může vazbu pro Služba tokenů zabezpečení ověření `ICalculator` služby.  
  
 Konfigurace tuto vazbu na službu je vidět v následujícím kódu.  
  
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
  
 Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hodnota určuje, které režim zabezpečení by měl použít. V této ukázce `message` zabezpečení se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<IssuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element `ws2007FederationHttpBinding` uvnitř [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) určuje adrese a identitě pro koncový bod, který slouží k načtení metadata pro Služba tokenů zabezpečení.  
  
 Chování pro službu je znázorněno v následujícím kódu.  
  
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
  
 [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umožňuje službě zadejte omezení umožňuje klientům k dispozici při ověřování tokenů. Tato konfigurace určuje, že tokeny podepsaný certifikát, jehož název subjektu CN = přijímat jsou služby tokenů zabezpečení.  
  
 Služba tokenů zabezpečení zpřístupní jeden koncový bod přes standardní <xref:System.ServiceModel.WS2007HttpBinding>. Služba odpovídá na požadavky od klientů pro tokeny. Pokud je klient ověřen pomocí účtu Windows, službu vystaví token, který obsahuje jméno uživatele klienta jako deklarace identity. Při vytváření tokenu služby tokenů zabezpečení přihlásí token pomocí privátní klíč přidružený CN = certifikát služby tokenů zabezpečení. Kromě toho vytvoří symetrického klíče a zašifruje pomocí veřejného klíče přidruženého CN = localhost certifikátu. Při vracení token do klienta, služby tokenů zabezpečení také vrátí symetrický klíč. Klient poskytne vystavený token, který má `ICalculator` služby a prokáže, že zná symetrický klíč podepsáním zprávu s tímto klíčem.  
  
 Při spuštění vzorového žádost o token zabezpečení se zobrazí v okně konzoly služby tokenů zabezpečení. Požadavky a odpovědi operace se zobrazují v oknech konzoly klienta a služby. Stisknutím klávesy ENTER v některém z okna konzoly vypnout aplikaci.  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Tato ukázka je součástí souboru Setup.bat umožňuje nakonfigurovat server a službu tokenů zabezpečení příslušné certifikáty, spuštění aplikace s vlastním hostováním. Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů LocalMachine/TrustedPeople. První certifikát obsahuje název subjektu z CN = služby tokenů zabezpečení a slouží k podepisování tokenů zabezpečení, které vystavuje klientovi službou tokenů zabezpečení. Druhý certifikát obsahuje název subjektu z CN = localhost a slouží k šifrování klíče tak, aby mohly dešifrovat službu službou tokenů zabezpečení.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte soubor Setup.bat k vytvoření požadované certifikáty.  
  
 Tento dávkový soubor používá Certmgr.exe a Makecert.exe, které jsou distribuovány sada Windows SDK. Setup.bat z však musíte spustit v rámci příkazového řádku Visual Studia povolit skript, který chcete najít těchto nástrojů.  
  
1.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], je nutné spustit Service.exe Client.exe, a SecurityTokenService.exe se zvýšenými oprávněními (pravým tlačítkem myši na a pak klikněte na **spustit jako správce**).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a>Viz také
