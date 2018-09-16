---
title: Zabezpečení zpráv u klienta Windows bez vyjednávání pověření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7f46ea28fe0827e7919b62550492d66a51a125fc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676568"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Zabezpečení zpráv u klienta Windows bez vyjednávání pověření
Následující scénář ukazuje klienta Windows Communication Foundation (WCF) a služby zabezpečené pomocí protokolu Kerberos.  
  
 Službu a klienta jsou ve stejné doméně nebo důvěryhodné domény.  
  
> [!NOTE]
>  Rozdíl mezi tento scénář a [zabezpečení zpráv pomocí klienta Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) je, že tento scénář není vyjednávání přihlašovacích údajů pro služby ve službě před odesláním zprávy aplikace. Navíc vzhledem k tomu, že to vyžaduje protokol Kerberos, tento scénář vyžaduje prostředí domény Windows.  
  
 ![Zabezpečení bez vyjednávání přihlašovacích údajů zpráv](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|Vlastnost|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Zpráva|  
|Interoperabilita|Ano, WS-Security s klienty kompatibilní profilu token protokolu Kerberos|  
|Ověření (Server)|Vzájemné ověřování klienta a serveru|  
|Ověření (klient)|Vzájemné ověřování klienta a serveru|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|HTTP|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace mají běžet nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvoření samostatné služby pomocí kódu bez konfigurace.  
  
-   Vytvoření služby pomocí zadaných konfigurací, ale nedefinují žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód vytvoří koncový bod služby, který používá zabezpečení zpráv. Kód zakáže vyjednávání přihlašovacích údajů služby a zřízení token kontextu zabezpečení (SCT).  
  
> [!NOTE]
>  Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, služby uživatelský účet musí mít přístup k hlavní název služby (SPN), který je zaregistrován s doménou služby Active Directory. Můžete to provést dvěma způsoby:  
  
1.  Použití `NetworkService` nebo `LocalSystem` účet ke spuštění služby. Vzhledem k tomu, že tyto účty mají přístup k počítači hlavní název služby, který je vytvořen, když je počítač připojen k doméně služby Active Directory, WCF automaticky generuje elementu řádné SPN uvnitř koncového bodu služby v metadatech služby (Web Services Description Jazyk, nebo WSDL).  
  
2.  Použijte libovolný účet domény služby Active Directory ke spuštění služby. V takovém případě potřebujete vytvořit název SPN pro příslušný účet domény. Jeden způsob, jak to je použití nástroje nástroje Setspn.exe. Po vytvoření názvu SPN pro účet služby konfigurace WCF k publikování této hlavní název služby klientům služby prostřednictvím jeho metadat (WSDL). To se provádí nastavením identitě koncového bodu vystavené koncového bodu, buď když k konfigurační soubor aplikace nebo kódu. Následující příklad publikuje identitu prostřednictvím kódu programu.  
  
 Další informace o SPN, protokol Kerberos a Active Directory, naleznete v tématu [Kerberos technické Supplement pro Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Další informace o identitách koncový bod, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurace je možné použít místo kódu.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="KerberosBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator"   
                  listenUri="net.tcp://localhost/metadata" >  
         <identity>  
            <servicePrincipalName value="service_spn_name" />  
         </identity>  
        </endpoint>  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="KerberosBinding">  
          <security>  
            <message negotiateServiceCredential="false"   
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
 Následující kód a konfigurace mají běžet nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvoření samostatného klienta pomocí kódu (a kód klienta).  
  
-   Vytvoření klienta, která nedefinuje žádné adresy koncových bodů. Místo toho použijte klienta konstruktor, který přijímá jako argument Název konfigurace. Příklad:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kód  
 Následující kód konfiguruje klienta. Režim zabezpečení je nastavena na zprávu, a typ pověření klienta je nastaven na Windows. Všimněte si, <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnosti jsou nastaveny na `false`.  
  
> [!NOTE]
>  Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, musí klient nakonfigurovaný s účtem služby SPN před zahájením komunikace se službou. Klient použije hlavní název služby se získat token protokolu Kerberos k ověření a zabezpečení komunikace se službou. Následující příklad ukazuje, jak nakonfigurovat klienta služby SPN. Pokud používáte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Pokud chcete vygenerovat klienta, název služby SPN se automaticky rozšíří do klienta z metadat služby (WSDL), pokud obsahuje metadata služby Tyto informace. Další informace o tom, jak nakonfigurovat službu zahrnout jeho hlavního názvu služby metadata služby najdete v části "Služba" dále v tomto tématu.  
>   
>  Další informace o hlavní názvy služby protokolu Kerberos a Active Directory najdete v tématu [Kerberos technické Supplement pro Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Další informace o identitách koncový bod, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) tématu.  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód konfiguruje klienta. Všimněte si, [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elementu musí být nastavena tak, aby odpovídaly služby SPN, protože registrovaný pro účet služby v doméně služby Active Directory.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Windows"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <servicePrincipalName value="service_spn_name" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
