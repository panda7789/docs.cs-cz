---
title: Zabezpečení přenosu se základním ověřováním
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 65d076a9fef716fca4fe87df6bc5c7773e2dda0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="transport-security-with-basic-authentication"></a>Zabezpečení přenosu se základním ověřováním
Následující obrázek znázorňuje klienta a služby Windows Communication Foundation (WCF). Server vyžaduje platný certifikát X.509, který lze použít pro vrstvy SSL (Secure Sockets) a klienti musí důvěřovat certifikátu serveru. Navíc webová služba již má implementaci protokolu SSL, který lze použít. Další informace o povolení základní ověřování v Internetové informační služby (IIS) najdete v tématu [ http://go.microsoft.com/fwlink/?LinkId=83822 ](http://go.microsoft.com/fwlink/?LinkId=83822).  
  
 ![Přenosu zabezpečení se základním ověřováním](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")  
  
|Vlastnosti|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení.|Přenos|  
|Interoperabilita|S existující klienty webové služby a služby|  
|Ověřování (Server)<br /><br /> Ověřování (klient)|Ano (pomocí protokolu HTTPS)<br /><br /> Ano (prostřednictvím uživatelské jméno a heslo)|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|HTTPS|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určená ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.  
  
-   Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód ukazuje, jak vytvořit koncový bod služby, který používá Windows domény uživatelské jméno a heslo pro zabezpečení přenosu. Všimněte si, že služba vyžaduje, aby certifikátu X.509. certifikát k ověření klienta. Další informace najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) a [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Konfigurace  
 Následující konfiguruje službu používat základní ověřování s zabezpečení na úrovni přenosu:  
  
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
 Následující kód ukazuje kód klienta, která obsahuje uživatelské jméno a heslo. Všimněte si, že uživatel musí poskytnout platné uživatelské jméno systému Windows a heslo. Kód, který vrátí uživatelské jméno a heslo není zobrazeny zde. Použijte dialogové okno nebo jiných rozhraní k dotazování uživatelské informace.  
  
> [!NOTE]
>  Uživatelské jméno a heslo lze nastavit pouze pomocí kódu.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód ukazuje konfigurace klienta.  
  
> [!NOTE]
>  Konfigurace nelze použít k nastavení uživatelské jméno a heslo. Konfigurace znázorněné v tomto poli musí rozšířit pomocí kódu nastavit uživatelské jméno a heslo.  
  
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
 [\<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
