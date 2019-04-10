---
title: Důvěryhodný subsystém
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: a0f845ad0d8ca461f8ab0b3188a72e87c589add2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319362"
---
# <a name="trusted-subsystem"></a>Důvěryhodný subsystém
Klient přistupuje k jedné nebo více webových služeb, které jsou distribuovány napříč sítí. Webové služby jsou navržené tak, aby tento přístup k dalším prostředkům (například databáze nebo jiné webové služby), je zapouzdřena v obchodní logice webové služby. Tyto prostředky musí být chráněný před neoprávněným přístupem. Následující obrázek znázorňuje proces důvěryhodný subsystém.  
  
 ![Důvěryhodný subsystém](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")  
  
 Následující kroky popisují proces důvěryhodný subsystém, jak je znázorněno:  
  
1. Klient odešle požadavek na důvěryhodný subsystém spolu s přihlašovací údaje.  
  
2. Důvěryhodný subsystém ověřuje a autorizuje uživatele.  
  
3. Důvěryhodný subsystém odešle zprávu požadavku vzdáleného prostředku. Této žádosti je přiložený přihlašovací údaje pro důvěryhodného subsystém (nebo účet služby, pod kterým je prováděný procesem důvěryhodný subsystém).  
  
4. Prostředek back-end se ověřuje a autorizuje důvěryhodný subsystém. Poté zpracuje požadavek a vydá odpověď na důvěryhodný subsystém.  
  
5. Důvěryhodný subsystém zpracuje odpověď a problémy s vlastním odpověď klientovi.  
  
|Vlastnost|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Zpráva|  
|Interoperabilita|Windows Communication Foundation (WCF) pouze.|  
|Ověřování (služba)|Služba tokenů zabezpečení ověřuje a autorizuje klientů.|  
|Ověření (klient)|Důvěryhodný subsystém ověřuje klienta a prostředku ověřuje službě důvěryhodný subsystém.|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|HTTP mezi klientem a službou důvěryhodný subsystém.<br /><br /> SÍŤ. TCP mezi důvěryhodný subsystém služeb a prostředků (služba back-end).|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|  
  
## <a name="resource-back-end-service"></a>Prostředků (služba Back-End)  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby pro prostředek, který používá zabezpečení přenosu přenosový protokol TCP.  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurace nastaví stejný koncový bod pomocí konfigurace.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a>Důvěryhodný subsystém  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby pro důvěryhodného podsystému, který používá zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověřování.  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 Následující kód ukazuje služby v důvěryhodný subsystém, který komunikuje s back-end služby pomocí zabezpečení přenosu přenosový protokol TCP.  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurace nastaví stejný koncový bod pomocí konfigurace. Všimněte si dvě vazby: Jeden zabezpečuje službu hostovanou v důvěryhodný subsystém a druhý zajišťuje komunikaci mezi důvěryhodný subsystém a back-end služby.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""   
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit klienta, který komunikuje s důvěryhodný subsystém pomocí zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověření.  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód konfiguruje klienta pro ověřování pomocí zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo. Uživatelské jméno a heslo lze zadat pouze pomocí kódu (není konfigurovatelné).  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""   
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
