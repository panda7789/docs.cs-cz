---
title: Zabezpečení zpráv u klienta Windows bez vyjednávání pověření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: 699ea45d67658ab9c768bf938d5336be7a5427c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955354"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Zabezpečení zpráv u klienta Windows bez vyjednávání pověření
V následujícím scénáři vidíte klienta služby a službu Windows Communication Foundation (WCF) zabezpečený protokolem Kerberos.  
  
 Služba i klient jsou ve stejné doméně nebo důvěryhodných doménách.  
  
> [!NOTE]
> Rozdíl mezi tímto scénářem a [zabezpečením zprávy pomocí klienta Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) je v tom, že tento scénář nevyjednává pověření služby se službou před odesláním zprávy aplikace. Navíc vzhledem k tomu, že tento scénář vyžaduje protokol Kerberos, vyžaduje prostředí domény systému Windows.  
  
 ![Zabezpečení zpráv bez vyjednávání přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|Charakteristiku|Popis|  
|--------------------|-----------------|  
|Režim zabezpečení|Message|  
|Interoperabilita|Ano, WS-Security s kompatibilními klienty profilování Kerberos|  
|Ověřování (Server)|Vzájemné ověřování serveru a klienta|  
|Ověřování (klient)|Vzájemné ověřování serveru a klienta|  
|Způsobilost|Ano|  
|Chovávat|Ano|  
|Přepravu|HTTP|  
|Vazba|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Služba  
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
- Vytvořte samostatnou službu pomocí kódu bez konfigurace.  
  
- Vytvořte službu pomocí zadané konfigurace, ale nedefinujte žádné koncové body.  
  
### <a name="code"></a>Kód  
 Následující kód vytvoří koncový bod služby, který používá zabezpečení zprávy. Kód zakazuje vyjednávání pověření služby a nakládání s tokenem kontextu zabezpečení (SCT).  
  
> [!NOTE]
> Chcete-li použít typ přihlašovacích údajů systému Windows bez vyjednávání, musí mít uživatelský účet služby přístup k hlavnímu názvu služby (SPN), který je zaregistrován v doméně služby Active Directory. Můžete to provést dvěma způsoby:  
  
1. Použijte účet `LocalSystem` nebo ke spuštění služby. `NetworkService` Vzhledem k tomu, že tyto účty mají přístup k hlavnímu názvu služby počítače, který se vytvoří, když se počítač připojí k doméně služby Active Directory, WCF automaticky vygeneruje správný element SPN v rámci koncového bodu služby v metadatech služby (popis webových služeb Jazyk nebo WSDL).  
  
2. Ke spuštění služby použijte libovolný účet domény služby Active Directory. V takovém případě musíte pro tento doménový účet vytvořit hlavní název služby (SPN). Jedním ze způsobů, jak to provést, je použít nástroj Setspn. exe Utility. Po vytvoření hlavního názvu služby (SPN) pro účet služby nakonfigurujte WCF pro publikování tohoto hlavního názvu služby do klientů služby prostřednictvím metadat (WSDL). To se provádí nastavením identity koncového bodu pro vystavený koncový bod, a to buď pomocí konfiguračního souboru aplikace, nebo kódu. Následující příklad publikuje identitu programově.  
  
 Další informace o SPN, protokolu Kerberos a službě Active Directory najdete v tématu [Kerberos Technical dodatk pro Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Další informace o identitách koncových bodů najdete v tématu [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>Konfiguraci  
 Místo kódu lze použít následující konfiguraci.  
  
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
 Následující kód a konfigurace jsou určeny ke spuštění nezávisle. Proveďte jednu z těchto akcí:  
  
- Vytvořte samostatného klienta pomocí kódu (a kódu klienta).  
  
- Vytvořte klienta, který nedefinuje žádné adresy koncových bodů. Místo toho použijte konstruktor klienta, který převezme název konfigurace jako argument. Příklad:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kód  
 Následující kód nakonfiguruje klienta. Režim zabezpečení je nastaven na hodnotu zpráva a typ přihlašovacích údajů klienta je nastaven na hodnotu Windows. Všimněte si, <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> že <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnosti a jsou nastaveny `false`na.  
  
> [!NOTE]
> Chcete-li použít typ přihlašovacích údajů systému Windows bez vyjednávání, musí být klient nakonfigurován pomocí SPN účtu služby před zahájením komunikace se službou. Klient používá hlavní název služby (SPN) k získání tokenu protokolu Kerberos k ověření a zabezpečení komunikace se službou. Následující příklad ukazuje, jak nakonfigurovat klienta nástroje pomocí hlavního názvu služby (SPN). Pokud k vygenerování klienta používáte [Nástroj pro metadata ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , hlavní název služby (SPN) se automaticky rozšíří na klienta z metadat služby (WSDL), pokud metadata služby obsahují tyto informace. Další informace o tom, jak nakonfigurovat službu tak, aby obsahovala hlavní název služby (SPN) v metadatech služby, najdete v části služba dále v tomto tématu.  
>   
>  Další informace o hlavních názvových názvech, protokolech Kerberos a službě Active Directory najdete v tématu [Kerberos Technical dodatk pro Windows](https://go.microsoft.com/fwlink/?LinkId=88330). Další informace o identitách koncových bodů najdete v tématu [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) .  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Konfiguraci  
 Následující kód nakonfiguruje klienta. Všimněte si, že [ \<element servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) musí být nastaven tak, aby odpovídal názvu SPN služby, jak je zaregistrován pro účet služby v doméně služby Active Directory.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
