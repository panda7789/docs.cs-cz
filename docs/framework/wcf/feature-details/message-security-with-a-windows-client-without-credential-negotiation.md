---
title: Zabezpečení zpráv u klienta Windows bez vyjednávání pověření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 05ffe731a578f8b8d2cdbdf5e3c9229e2b03821c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Zabezpečení zpráv u klienta Windows bez vyjednávání pověření
Následující příklad ukazuje klienta Windows Communication Foundation (WCF) a služby zabezpečené pomocí protokolu Kerberos.  
  
 Službu a klienta jsou ve stejné doméně nebo důvěryhodné domény.  
  
> [!NOTE]
>  Rozdíl mezi tento scénář a [zabezpečení zpráv s klientem Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) je, že tento scénář není vyjednávání přihlašovací údaje služby ve službě před odesláním zprávy aplikace. Navíc vzhledem k tomu, že to vyžaduje protokol Kerberos, tento scénář vyžaduje prostředí domény systému Windows.  
  
 ![Zpráva zabezpečení bez vyjednávání pověření](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|Vlastnosti|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení.|Zpráva|  
|Interoperabilita|Ano, WS-zabezpečení s klienty kompatibilní profil token protokolu Kerberos|  
|Ověřování (Server)|Vzájemné ověřování klienta a serveru|  
|Ověřování (klient)|Vzájemné ověřování klienta a serveru|  
|Integrita|Ano|  
|Důvěrnost|Ano|  
|Přenos|HTTP|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určená ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvořte samostatnou službu pomocí kódu žádnou konfiguraci.  
  
-   Vytvoření služby pomocí zadaných konfigurací, ale nejsou definovány žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód vytvoří koncový bod služby, který používá zabezpečení zpráv. Kód zakáže vyjednávání pověření služby a zřízení tokenu kontextu zabezpečení (SCT).  
  
> [!NOTE]
>  Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, uživatelský účet služby musí mít přístup k hlavní název služby (SPN) registrované domény služby Active Directory. Můžete provést dvěma způsoby:  
  
1.  Použití `NetworkService` nebo `LocalSystem` účet ke spuštění služby. Vzhledem k tomu, že tyto účty přístupu k počítači hlavní název služby, který je vytvořen, když je počítač připojen k doméně služby Active Directory, WCF správné element SPN uvnitř koncový bod služby automaticky vygeneruje v metadatech služby (Web Services Description Jazyk nebo WSDL).  
  
2.  Použijte libovolný účet domény služby Active Directory ke spuštění služby. V takovém případě musíte vytvořit název SPN pro příslušný účet domény. Jeden způsob, jak to provést, je pomocí nástroje Setspn.exe nástroj. Po vytvoření názvu SPN pro účet služby nakonfigurujte WCF publikovat tento hlavní název služby klientům služby prostřednictvím jeho metadata (WSDL). To se provádí nastavením identitu koncového bodu pro zveřejněné koncový bod, buď když konfiguračního souboru aplikace nebo kódu. Následující příklad publikuje identitu prostřednictvím kódu programu.  
  
 Další informace o SPN, protokol Kerberos a služby Active Directory, naleznete v části [Kerberos technické Supplement pro Windows](http://go.microsoft.com/fwlink/?LinkId=88330). Další informace o identitách koncový bod, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující konfigurace můžete použít místo kód.  
  
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
 Následující kód a konfigurace jsou určená ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
-   Vytvořte samostatnou klienta pomocí kódu (a kód klienta).  
  
-   Vytvoření klienta, které nejsou definovány žádné adresy koncových bodů. Místo toho použijte konstruktor klienta, který přijímá jako argument Název konfigurace. Příklad:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kód  
 Následující kód konfiguruje klienta. Režim zabezpečení je nastaven na zprávu, a typu pověření klienta je nastaven na hodnotu Windows. Všimněte si, že <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnosti jsou nastaveny na `false`.  
  
> [!NOTE]
>  Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, musí být klient nakonfigurované účtu služby SPN před zahájením komunikace se službou. Klient použije SPN se získat token protokolu Kerberos k ověřování a k zabezpečení komunikace se službou. Následující příklad ukazuje, jak nakonfigurovat klienta služby SPN. Pokud používáte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klienta, názvu služby SPN se automaticky rozšíří do klienta z metadat služby (WSDL), pokud obsahuje metadata služby Tyto informace. Další informace o tom, jak nakonfigurovat službu, kterou chcete zahrnout jeho SPN služby metadata najdete v části "Služba" dál v tomto tématu.  
>   
>  Další informace o SPN, protokolu Kerberos a služby Active Directory najdete v tématu [Kerberos technické Supplement pro Windows](http://go.microsoft.com/fwlink/?LinkId=88330). Další informace o identitách koncový bod, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) tématu.  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Konfigurace  
 Následující kód konfiguruje klienta. Všimněte si, že [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element musí být nastaven tak, aby odpovídaly SPN služby as registrované pro účet služby v doméně služby Active Directory.  
  
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
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
