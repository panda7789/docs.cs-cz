---
title: 'Postupy: Vytvoření zabezpečené relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 80973a31050cf1ede03d4a3919066c62625ae590
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593409"
---
# <a name="how-to-create-a-secure-session"></a>Postupy: Vytvoření zabezpečené relace
S výjimkou [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) vazby poskytují systémy vazby v Windows Communication Foundation (WCF) automaticky zabezpečené relace, pokud je zapnuté zabezpečení zpráv.  
  
 Ve výchozím nastavení zabezpečené relace neobsahují webový server, který se recykluje. Po navázání zabezpečené relace klient a služba uloží klíč, který je přidružený k zabezpečené relaci. Při výměně zpráv je vyměněn pouze identifikátor pro klíč uložený v mezipaměti. Pokud dojde k recyklení webového serveru, mezipaměť je také recyklována, což znamená, že webový server nemůže načíst klíč uložený v mezipaměti pro identifikátor. Pokud k tomu dojde, je vrácena výjimka klientovi. Zabezpečené relace, které používají token kontextového kontextu zabezpečení (SCT), mohou zachovány recyklaci webového serveru. Další informace o používání stavového SCTu v zabezpečené relaci naleznete v tématu [How to: Create a Security Context token for the Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Určení, že služba používá zabezpečené relace pomocí jedné z vazeb poskytovaných systémem  
  
- Nakonfigurujte službu tak, aby používala vazbu poskytovanou systémem, která podporuje zabezpečení zpráv.  
  
     S výjimkou [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) vazby platí, že pokud jsou zadané systémové vazby nakonfigurovány na používání zabezpečení zpráv, WCF automaticky používá zabezpečené relace. V následující tabulce jsou uvedené systémové vazby, které podporují zabezpečení zpráv a zda jsou zabezpečení zpráv výchozím mechanismem zabezpečení.  
  
    |Vazba poskytnutá systémem|Element konfigurace|Zabezpečení zprávy je ve výchozím nastavení zapnuté.|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|No|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|Ne|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|Ne|  
  
     Následující příklad kódu používá konfiguraci k určení vazby s názvem, `wsHttpBinding_Calculator` která používá [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) zabezpečení, zabezpečení zprávy a zabezpečené relace.  
  
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
  
     Následující příklad kódu určuje, zda se [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) k zabezpečení služby používá zabezpečení, zabezpečení zpráv a zabezpečené relace `secureCalculator` .  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > Zabezpečené relace lze pro rozhraní vypnout [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) nastavením `establishSecurityContext` atributu na `false` . U ostatních vazeb poskytovaných systémem můžete zabezpečené relace vypnout jenom vytvořením vlastní vazby.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Určení, že služba používá zabezpečené relace pomocí vlastní vazby  
  
- Vytvořte vlastní vazbu, která určuje, zda jsou zprávy protokolu SOAP chráněny zabezpečenou relací.  
  
     Další informace o vytvoření vlastní vazby naleznete v tématu [How to: Customizing a System-dodaná vazba](../extending/how-to-customize-a-system-provided-binding.md).  
  
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
  
     Následující příklad kódu vytvoří vlastní vazbu, která <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> pro spuštění zabezpečené relace používá režim ověřování.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Přehled vazeb WCF](../bindings-overview.md)
