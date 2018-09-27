---
title: Zabezpečení přenosu se základním ověřováním
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
author: BrucePerlerMS
ms.openlocfilehash: 4a6ad2746bea9dfea1999e272796d44f0341e64d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235569"
---
# <a name="transport-security-with-basic-authentication"></a>Zabezpečení přenosu se základním ověřováním
Následující obrázek znázorňuje klienta a služby Windows Communication Foundation (WCF). Server potřebuje platný certifikát X.509, který lze použít pro vrstvy SSL (Secure Sockets) a klienti musí důvěřovat certifikátu serveru. Dále webová služba již má implementace protokolu SSL, který lze použít. Další informace o povolení základního ověřování v Internetové informační služby (IIS) najdete v tématu [ https://go.microsoft.com/fwlink/?LinkId=83822 ](https://go.microsoft.com/fwlink/?LinkId=83822).  
  
 ![Zabezpečení se základním ověřováním přenosu](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")  
  
|Vlastnost|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Přenos|  
|Interoperabilita|Stávající klienty webové služby a služby|  
|Ověření (Server)<br /><br /> Ověření (klient)|Ano (pomocí protokolu HTTPS)<br /><br /> Ano (prostřednictvím uživatelské jméno a heslo)|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|HTTPS|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace mají běžet nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvoření samostatné služby pomocí kódu bez konfigurace.  
  
-   Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá Windows doména uživatelské jméno a heslo pro zabezpečení přenosu. Všimněte si, že služba vyžaduje, aby certifikát X.509 k ověření klienta. Další informace najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Konfigurace  
 Následující konfiguruje službu pomocí základního ověřování zabezpečení transportní vrstvy:  
  
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
 Následující kód ukazuje kód klienta, která obsahuje uživatelské jméno a heslo. Všimněte si, že uživatel musí zadat platné Windows uživatelské jméno a heslo. Zde není zobrazen kód vrátí uživatelské jméno a heslo. Použijte dialogové okno nebo jiné rozhraní k dotazování uživatele.  
  
> [!NOTE]
>  Uživatelské jméno a heslo lze nastavit pouze pomocí kódu.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód ukazuje konfiguraci klienta.  
  
> [!NOTE]
>  Konfiguraci nelze použít k nastavení uživatelského jména a hesla. Konfigurace je vidět tady musí rozšířit pomocí kódu pro nastavení uživatelského jména a hesla.  
  
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
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [\<třídu clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
 [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
