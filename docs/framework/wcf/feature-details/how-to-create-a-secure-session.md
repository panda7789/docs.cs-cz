---
title: 'Postupy: Vytvoření zabezpečené relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: bdb0f89b950d086e04cbb9d6da161bd315fc64b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934382"
---
# <a name="how-to-create-a-secure-session"></a>Postupy: Vytvoření zabezpečené relace
S výjimkou [ \<> vazby](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , jsou vazby poskytnuté systémem v Windows Communication Foundation (WCF) automaticky používat zabezpečené relace, pokud je zapnuté zabezpečení zpráv.  
  
 Ve výchozím nastavení zabezpečené relace neobsahují webový server, který se recykluje. Po navázání zabezpečené relace klient a služba uloží klíč, který je přidružený k zabezpečené relaci. Při výměně zpráv je vyměněn pouze identifikátor pro klíč uložený v mezipaměti. Pokud dojde k recyklení webového serveru, mezipaměť je také recyklována, což znamená, že webový server nemůže načíst klíč uložený v mezipaměti pro identifikátor. Pokud k tomu dojde, je vrácena výjimka klientovi. Zabezpečené relace, které používají token kontextového kontextu zabezpečení (SCT), mohou zachovány recyklaci webového serveru. Další informace o používání stavového SCTu v zabezpečené relaci najdete v tématu [How to: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Určení, že služba používá zabezpečené relace pomocí jedné z vazeb poskytovaných systémem  
  
- Nakonfigurujte službu tak, aby používala vazbu poskytovanou systémem, která podporuje zabezpečení zpráv.  
  
     S výjimkou [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, pokud jsou zadané systémové vazby nakonfigurovány na používání zabezpečení zpráv, WCF automaticky používá zabezpečené relace. V následující tabulce jsou uvedené systémové vazby, které podporují zabezpečení zpráv a zda jsou zabezpečení zpráv výchozím mechanismem zabezpečení.  
  
    |Vazba poskytnutá systémem|Element konfigurace|Zabezpečení zprávy je ve výchozím nastavení zapnuté.|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Ne|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Ne|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Ne|  
  
     Následující příklad kódu používá konfiguraci k určení vazby s názvem `wsHttpBinding_Calculator` , která [ \<používá WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpečení zpráv a zabezpečené relace.  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     Následující příklad kódu určuje, že `secureCalculator` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)se k zabezpečení služby používá WSHttpBinding >, zabezpečení zpráv a zabezpečené relace.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > Zabezpečené relace je možné vypnout pro `establishSecurityContext` [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nastavením atributu na. `false` U ostatních vazeb poskytovaných systémem můžete zabezpečené relace vypnout jenom vytvořením vlastní vazby.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Určení, že služba používá zabezpečené relace pomocí vlastní vazby  
  
- Vytvořte vlastní vazbu, která určuje, zda jsou zprávy protokolu SOAP chráněny zabezpečenou relací.  
  
     Další informace o vytvoření vlastní vazby naleznete v tématu [How to: Přizpůsobení vazby](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)poskytnuté systémem.  
  
     Následující příklad kódu používá konfiguraci k určení vlastní vazby pro zprávy pomocí zabezpečené relace.  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     Následující příklad kódu vytvoří vlastní vazbu, která pro spuštění zabezpečené <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> relace používá režim ověřování.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled vazeb WCF](../../../../docs/framework/wcf/bindings-overview.md)
