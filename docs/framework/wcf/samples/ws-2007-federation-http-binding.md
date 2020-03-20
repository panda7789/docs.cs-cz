---
title: Prvek ws2007FederationHttpBinding
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183176"
---
# <a name="ws-2007-federation-http-binding"></a>Prvek ws2007FederationHttpBinding

Tato ukázka ukazuje <xref:System.ServiceModel.WS2007FederationHttpBinding>použití , standardní vazby, které můžete použít k vytvoření federované scénáře, které podporují verzi 1.3 specifikace WS-Trust.

> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.

Ukázka se skládá z klientského programu založeného na konzoli (*Client.exe*), programu služby tokenů zabezpečení založených na konzoli (*Securitytokenservice.exe*) a servisního programu založeného na konzoli (*Service.exe*). Služba implementuje smlouvu, která definuje vzor komunikace požadavek/odpověď. Kontrakt je definován `ICalculator` rozhraním, které zveřejňuje`Add`matematické `Subtract` `Multiply`operace `Divide`( , , , a ). Klient získá token zabezpečení ze služby TOKEN zabezpečení (STS) a provede synchronní požadavky na službu pro danou matematickou operaci. Služba pak odpoví s výsledkem. Aktivita klienta je viditelná v okně konzoly.

Ukázka zpřístupní `ICalculator` kontrakt `ws2007FederationHttpBinding` pomocí prvku. Konfigurace této vazby na straně klienta je zobrazena v následujícím kódu:

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

Na [ \<>zabezpečení ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` určuje hodnota, který má být použit režim zabezpečení. V této `message` ukázce se používá zabezpečení, což je důvod, proč je [ \<zpráva>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) zadána [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)uvnitř>zabezpečení . [ \<Vystavitel>](../../configure-apps/file-schema/wcf/issuer.md) prvek uvnitř [ \<zprávy>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) určuje adresu a vazbu pro STS, která vydává token `ICalculator` zabezpečení klientovi tak, aby klient může ověřit službu.
  
Konfigurace této vazby na službu je zobrazena v následujícím kódu:

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

Na [ \<>zabezpečení ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` určuje hodnota, který má být použit režim zabezpečení. V této `message` ukázce se používá zabezpečení, což je důvod, proč je [ \<zpráva>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) zadána [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)uvnitř>zabezpečení . [ \<IssuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) prvek `ws2007FederationHttpBinding` uvnitř [ \<zprávy>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) určuje adresu a identitu pro koncový bod, který lze použít k načtení metadat pro STS.

Chování služby je zobrazeno v následujícím kódu:

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
  
[ \<IssuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umožňuje službě určit omezení tokenů, které umožňuje klientům prezentovat během ověřování. Tato konfigurace určuje, že tokeny podepsané certifikátem, jehož název subjektu je CN=STS, jsou službou přijímány.

STS zpřístupňuje jeden koncový <xref:System.ServiceModel.WS2007HttpBinding>bod pomocí standardu . Služba reaguje na požadavky klientů pro tokeny. Pokud je klient ověřen pomocí účtu systému Windows, služba vydá token, který obsahuje uživatelské jméno klienta jako deklaraci. Jako součást vytváření tokenu, STS podepisuje token pomocí soukromého klíče přidruženého k certifikátu CN = STS. Kromě toho vytvoří symetrický klíč a šifruje jej pomocí veřejného klíče přidruženého k certifikátu CN=localhost. Při vrácení tokenu klientovi STS také vrátí symetrický klíč. Klient představuje vydaný token `ICalculator` do služby a prokáže, že zná symetrický klíč podpisem zprávy s tímto klíčem.

Při spuštění ukázky je v okně konzoly STS zobrazen požadavek na token zabezpečení. Požadavky a odpovědi operace jsou zobrazeny v oknech klienta a konzoly služby. Stisknutím klávesy ENTER v libovolném systému konzoly aplikaci vypněte.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

Soubor *Setup.bat,* který je součástí této ukázky, umožňuje nakonfigurovat server a službu STS s příslušnými certifikáty pro spuštění samoobslužné aplikace. Dávkový soubor vytvoří dva certifikáty v úložišti certifikátů LocalMachine/TrustedPeople. První certifikát má název subjektu CN = STS a používá STS k podepsání tokeny zabezpečení, které vydává klientovi. Druhý certifikát má název subjektu CN = localhost a je používán STS k šifrování klíče způsobem, který služba může dešifrovat.

## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Otevřete příkazový řádek pro vývojáře pro visual studio s oprávněními správce a spusťte soubor Setup.bat a vytvořte požadované certifikáty.

 Tento dávkový soubor používá *certmgr.exe* a makecert.exe, které jsou distribuovány se sadou Windows SDK. Je však nutné spustit *Setup.bat* z příkazového řádku sady Visual Studio, aby skript tyto nástroje našel.

1. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](building-the-samples.md).

2. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](running-the-samples.md). Používáte-li systém Windows Vista, je nutné spustit program *Service.exe*, *Client.exe*a *securitytokenservice.exe* se zvýšenými oprávněními (klepněte pravým tlačítkem myši na soubory a potom klepněte na příkaz **Spustit jako správce**).

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář:
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři:
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
