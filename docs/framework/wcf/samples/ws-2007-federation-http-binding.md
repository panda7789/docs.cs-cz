---
title: Prvek ws2007FederationHttpBinding
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 2f924bdcbf9082d9d43e02d82c9d00c32ebcaacf
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714973"
---
# <a name="ws-2007-federation-http-binding"></a>Prvek ws2007FederationHttpBinding

Tato ukázka demonstruje použití <xref:System.ServiceModel.WS2007FederationHttpBinding>, standardní vazby, kterou můžete použít k sestavení federovaných scénářů, které podporují verzi 1,3 specifikace WS-Trust.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Ukázka se skládá z klientského programu založeného na konzole (soubor*Client. exe*), programu služby tokenu zabezpečení založeného na konzole (*SecurityTokenService. exe*) a programu služby (*Service. exe*) založeném na konzole. Služba implementuje kontrakt definující způsob komunikace požadavků a odpovědí. Kontrakt je definován rozhraním `ICalculator`, které zpřístupňuje matematické operace (`Add`, `Subtract`, `Multiply`a `Divide`). Klient získá token zabezpečení ze služby tokenu zabezpečení (STS) a provede synchronní požadavky služby pro danou matematickou operaci. Služba pak odpoví s výsledkem. Aktivita klienta se zobrazí v okně konzoly.

Ukázka zpřístupní `ICalculator` kontraktu pomocí elementu `ws2007FederationHttpBinding`. Konfigurace této vazby na klientovi je uvedena v následujícím kódu:

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

V [> zabezpečení\<](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)určuje hodnota `security`, který režim zabezpečení má být použit. V této ukázce se používá `message` zabezpečení. to je důvod, proč je [\<zpráva](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) zadaná uvnitř [\<zabezpečení >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [> Element vystavitele\<](../../configure-apps/file-schema/wcf/issuer.md) v [\<zprávě >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Určuje adresu a vazbu pro STS, která vydává token zabezpečení pro klienta, aby se klient mohl ověřit pro `ICalculator` službu.
  
Konfigurace této vazby ve službě je uvedena v následujícím kódu:

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

V [> zabezpečení\<](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)určuje hodnota `security`, který režim zabezpečení má být použit. V této ukázce se používá `message` zabezpečení. to je důvod, proč je [\<zpráva](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) zadaná uvnitř [\<zabezpečení >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [\<issuerMetadata >](../../configure-apps/file-schema/wcf/issuermetadata.md) elementu `ws2007FederationHttpBinding` uvnitř [\<zprávy >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Určuje adresu a identitu koncového bodu, který lze použít k načtení metadat pro službu STS.

Chování služby se zobrazí v následujícím kódu:

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
  
[\<issuedTokenAuthentication >](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umožňuje službě určovat omezení pro tokeny, které umožňuje klientům prezentovat během ověřování. Tato konfigurace určuje, že služba přijímá tokeny podepsané certifikátem, jehož název subjektu je CN = STS.

Služba STS zpřístupňuje jeden koncový bod pomocí standardní <xref:System.ServiceModel.WS2007HttpBinding>. Služba reaguje na žádosti klientů o tokeny. Pokud je klient ověřený pomocí účtu systému Windows, služba vydá token, který obsahuje uživatelské jméno klienta jako deklaraci identity. V rámci vytváření tokenu token STS podepíše token pomocí privátního klíče přidruženého k certifikátu CN = STS. Kromě toho vytvoří symetrický klíč a zašifruje ho pomocí veřejného klíče přidruženého k certifikátu CN = localhost. Při vrácení tokenu klientovi vrátí služba tokenů zabezpečení také symetrický klíč. Klient prezentuje vydaný token službě `ICalculator` a potvrzuje, že zná symetrický klíč podepsáním zprávy pomocí tohoto klíče.

Při spuštění ukázky se v okně konzoly STS zobrazí požadavek na token zabezpečení. Požadavky a odpovědi operace operace se zobrazí v oknech konzoly klienta a služby. Ukončete aplikaci stisknutím klávesy ENTER v libovolném z oken konzoly.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

Soubor *Setup. bat* , který je součástí této ukázky, vám umožní nakonfigurovat server a STS s příslušnými certifikáty pro spuštění samoobslužné aplikace. Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů LocalMachine/TrustedPeople. První certifikát má název subjektu CN = STS a používá službu STS k podepisování tokenů zabezpečení, které vystaví klientovi. Druhý certifikát má název subjektu CN = localhost a používá službu STS k šifrování klíče způsobem, který může služba dešifrovat.

## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

2. Otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spuštěním souboru Setup. bat vytvořte požadované certifikáty.

 Tento dávkový soubor používá soubory *certmgr. exe* a Makecert. exe, které jsou distribuovány s Windows SDK. Je však nutné spustit *Setup. bat* z příkazového řádku sady Visual Studio, aby skript mohl tyto nástroje najít.

1. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

2. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md). Pokud používáte [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], musíte spustit *Service. exe*, *Client. exe*a *SecurityTokenService. exe* se zvýšenými oprávněními (pravým tlačítkem myši klikněte na soubory a pak klikněte na **Spustit jako správce**).

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář:
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři:
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
