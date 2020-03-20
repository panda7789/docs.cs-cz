---
title: Důvěryhodný subsystém
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: b226eed9218207cde99add61ef1f3eb64b459009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184297"
---
# <a name="trusted-subsystem"></a>Důvěryhodný subsystém
Klient přistupuje k jedné nebo více webovým službám, které jsou distribuovány v síti. Webové služby jsou navrženy tak, aby byl přístup k dalším prostředkům (například databázím nebo jiným webovým službám) zapouzdřen v obchodní logice webové služby. Tyto prostředky musí být chráněny před neoprávněným přístupem. Následující obrázek znázorňuje proces důvěryhodného subsystému.  
  
 ![Důvěryhodný subsystém](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")  
  
 Následující kroky popisují proces důvěryhodného subsystému, jak je znázorněno:  
  
1. Klient odešle požadavek do důvěryhodného subsystému spolu s pověřeními.  
  
2. Důvěryhodný subsystém ověřuje a autorizuje uživatele.  
  
3. Důvěryhodný subsystém odešle zprávu požadavku vzdálenému prostředku. Tento požadavek je doprovázen pověřeními důvěryhodného subsystému (nebo účtu služby, pod kterým je prováděn proces důvěryhodného subsystému).  
  
4. Prostředek back-end ověřuje a autorizuje důvěryhodný subsystém. Poté zpracuje požadavek a vydá odpověď na důvěryhodný subsystém.  
  
5. Důvěryhodný subsystém zpracuje odpověď a vydá vlastní odpověď klientovi.  
  
|Charakteristika|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Zpráva|  
|Vzájemná funkční spolupráce|Pouze windows communication foundation (WCF).|  
|Ověřování (služba)|Služba tokenů zabezpečení ověřuje a autorizuje klienty.|  
|Ověřování (klient)|Důvěryhodný podsystém ověří klienta a prostředek ověří důvěryhodnou službu subsystému.|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|HTTP mezi klientem a důvěryhodnou službou subsystému.<br /><br /> Čisté. Protokol TCP mezi důvěryhodnou službou subsystému a prostředkem (back-endová služba).|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding><xref:System.ServiceModel.NetTcpBinding> [a \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|  
  
## <a name="resource-back-end-service"></a>Prostředek (služba back-end)  
  
### <a name="code"></a>kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby pro prostředek, který používá zabezpečení přenosu přes přenosový protokol TCP.  
  
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
  
### <a name="code"></a>kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby pro důvěryhodný podsystém, který používá zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověřování.  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 Následující kód zobrazuje službu v důvěryhodném subsystému, který komunikuje se službou back-end pomocí zabezpečení přenosu přes přenosový protokol TCP.  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurace nastaví stejný koncový bod pomocí konfigurace. Všimněte si dvou vazeb: Jedna zabezpečuje službu hostovací v důvěryhodném subsystému a druhá komunikuje mezi důvěryhodným subsystémem a back-endovou službou.  
  
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
  
### <a name="code"></a>kód  
 Následující kód ukazuje, jak vytvořit klienta, který komunikuje s důvěryhodným subsystémem pomocí zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověřování.  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód nakonfiguruje klienta tak, aby používal zabezpečení zpráv přes protokol HTTP a uživatelské jméno a heslo pro ověřování. Uživatelské jméno a heslo lze zadat pouze pomocí kódu (nelze jej konfigurovat).  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
