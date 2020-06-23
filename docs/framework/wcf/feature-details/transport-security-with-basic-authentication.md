---
title: Zabezpečení přenosu se základním ověřováním
description: Projděte si tento scénář WCF, který ukazuje základní ověřování pro službu a klienta WCF. Služba potřebuje platný certifikát, který důvěřuje klientovi.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: f15a19feaed631a76948efd24ee225acf789cb2d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244852"
---
# <a name="transport-security-with-basic-authentication"></a>Zabezpečení přenosu se základním ověřováním
Následující ilustrace znázorňuje službu Windows Communication Foundation (WCF) a klienta. Server potřebuje platný certifikát X. 509, který se dá použít pro SSL (Secure Sockets Layer) (SSL), a klienti musí důvěřovat certifikátu serveru. Kromě toho webová služba už používá implementaci SSL, kterou je možné použít. Další informace o povolení základního ověřování na Internetová informační služba (IIS) najdete v tématu <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> .  
  
 ![Snímek obrazovky, který zobrazuje zabezpečení přenosu pomocí základního ověřování.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|Charakteristika|Description|  
|--------------------|-----------------|  
|Režim zabezpečení|Přenos|  
|Interoperabilita|S existujícími klienty a službami webové služby|  
|Ověřování (Server)<br /><br /> Ověřování (klient)|Ano (pomocí HTTPS)<br /><br /> Ano (pomocí uživatelského jména a hesla)|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|HTTPS|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z následujících akcí:  
  
- Vytvořte samostatnou službu pomocí kódu bez konfigurace.  
  
- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá uživatelské jméno a heslo domény systému Windows pro přenos zabezpečení. Všimněte si, že služba vyžaduje pro ověření klienta certifikát X. 509. Další informace najdete v tématu [práce s certifikáty](working-with-certificates.md) a [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Konfigurace  
 Následující nakonfiguruje službu tak, aby používala základní ověřování s zabezpečením na úrovni přenosu:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje kód klienta, který obsahuje uživatelské jméno a heslo. Všimněte si, že uživatel musí zadat platné uživatelské jméno a heslo systému Windows. Zde není zobrazen kód pro vrácení uživatelského jména a hesla. Použijte dialogové okno nebo jiné rozhraní k dotazování uživatele na informace.  
  
> [!NOTE]
> Uživatelské jméno a heslo lze nastavit pouze pomocí kódu.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód ukazuje konfiguraci klienta.  
  
> [!NOTE]
> Konfiguraci nelze použít k nastavení uživatelského jména a hesla. Zde uvedená konfigurace musí být rozšířena pomocí kódu pro nastavení uživatelského jména a hesla.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [Práce s certifikáty](working-with-certificates.md)
- [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
- [Přehled zabezpečení](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
