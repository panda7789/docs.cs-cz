---
title: 'Postupy: Vytvoření zabezpečené relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: c0e5281d227d343d8734809b27b57d8a2bead627
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147590"
---
# <a name="how-to-create-a-secure-session"></a>Postupy: Vytvoření zabezpečené relace
S výjimkou produktů [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, vazeb poskytovaných systémem Windows Communication Foundation (WCF) automaticky pomocí zabezpečených relací, pokud je povoleno zabezpečení zpráv.  
  
 Ve výchozím nastavení zabezpečených relací nepřežije webový server, který se recykluje. Po vytvoření zabezpečené relace, klient a služba mezipaměti klíč, který je přidružený k zabezpečené relace. Jak se vyměňují zprávy, se vyměňují pouze identifikátor pro klíč uložený v mezipaměti. Pokud se recykluje webový server, mezipaměť je také recyklovat, tak, aby webový server nemůže načíst uložené v mezipaměti klíče pro identifikátor. Pokud k tomu dojde, výjimka je vyvolána zpět do klienta. Zabezpečené relace, které používají token kontextu zabezpečení stavové (SCT) přežijí neumožňovala recyklaci, webový server. Další informace o používání stavové SCT v zabezpečené relaci v tématu [jak: Vytvoření kontextu zabezpečení pro zabezpečenou relaci Token](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Chcete-li určit, že služba používá zabezpečených relací pomocí jedné z vazeb poskytovaných systémem  
  
-   Konfigurace vazeb poskytovaných systémem, který podporuje zabezpečení zpráv pomocí ve službě.  
  
     S výjimkou produktů [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, když jsou vazeb poskytovaných systémem nakonfigurovány pro použití zabezpečení zpráv WCF automaticky používá zabezpečených relací. V následující tabulce jsou uvedeny vazeb poskytovaných systémem, které podporují zabezpečení zpráv a zda je zabezpečení zpráv výchozího mechanismu zabezpečení.  
  
    |Vazeb poskytovaných systémem|Element konfigurace|Zabezpečení zpráv na ve výchozím nastavení|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Ne|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Ne|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Ne|  
  
     Následující příklad kódu používá k určení vazeb s názvem konfigurace `wsHttpBinding_Calculator` , která používá [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)zabezpečení zpráv a zabezpečené relace.  
  
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
  
     Následující příklad kódu určuje, že [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)zabezpečení zpráv a zabezpečené relace se používají k zabezpečení `secureCalculator` služby.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  Zabezpečené relace lze vypnout pro [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nastavením `establishSecurityContext` atribut `false`. Pro jiných vazeb poskytovaných systémem zabezpečených relací můžete vypnout jenom tak, že vytvoříte vlastní vazby.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Chcete-li určit, že služba používá zabezpečených relací s použitím vlastní vazby  
  
-   Vytvoření vlastní vazby, která určuje, že zprávy protokolu SOAP jsou chráněny zabezpečenou relaci.  
  
     Další informace o vytvoření vlastní vazby, naleznete v tématu [jak: Přizpůsobení vazeb poskytovaných systémem](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
     Následující příklad kódu používá konfigurace k určení vlastních vazeb této zprávy pomocí zabezpečenou relaci.  
  
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
  
     Následující příklad kódu vytvoří vlastní vazby, který používá <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> režim ověřování ke spuštění zabezpečenou relaci.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled vazeb WCF](../../../../docs/framework/wcf/bindings-overview.md)
