---
title: 'Postupy: vytvoření zabezpečené relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ce351a87e70b09a2f68654af817e28fa3145d79d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-secure-session"></a>Postupy: vytvoření zabezpečené relace
S výjimkou produktů [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, vazby poskytované systémem Windows Communication Foundation (WCF) automaticky použít zabezpečených relací, pokud je povolená zabezpečení zpráv.  
  
 Ve výchozím nastavení zabezpečených relací není i po webový server, který recykluje. Po vytvoření zabezpečené relace mezipaměti klienta a služby, klíč, který je přidružen zabezpečené relace. Jak se vyměňují zprávy, se vyměňují jenom identifikátor ke klíči v mezipaměti. Pokud webový server je recykluje, mezipaměti je také recykluje, tak, aby webový server nemůže načíst uložené v mezipaměti klíče pro identifikátor. V takovém případě je klientovi zpět vyvolána výjimka. Zabezpečených relací, které používají tokenu kontextu zabezpečení stavová (SCT) přežijí recyklovány webového serveru. Další informace o používání stavová SCT v zabezpečené relaci najdete v tématu [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Chcete-li určit, že služba používá zabezpečených relací pomocí jedné z vazby poskytované systémem  
  
-   Nakonfigurujte službu, která používá vazbu poskytované systémem, který podporuje zabezpečení zpráv.  
  
     S výjimkou produktů [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, pokud jsou vazby poskytované systémem nakonfigurovány pro použití zabezpečení zpráv WCF automaticky používá zabezpečených relací. Následující tabulka uvádí vazby poskytované systémem, které podporují zabezpečení zpráv a zda je zabezpečení zpráv výchozího mechanismu zabezpečení.  
  
    |Vazby poskytované systémem|Konfigurační element|Zabezpečení zpráv na ve výchozím nastavení|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Ne|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Ano|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Ne|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<– netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Ne|  
  
     Následující příklad kódu používá k určení vazbu s názvem konfigurace `wsHttpBinding_Calculator` používající [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)zabezpečení zpráv a zabezpečené relace.  
  
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
  
     Následující příklad kódu určuje, že [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)zabezpečení zpráv a zabezpečení relací se používají k zabezpečení `secureCalculator` služby.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  Může být vypnuto zabezpečených relací pro [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nastavením `establishSecurityContext` atribut `false`. Pro ostatní poskytované systémem vazby zabezpečených relací lze pouze vypnout tak, že vytvoříte vlastní vazby.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Chcete-li určit, že služba používá zabezpečených relací pomocí vlastní vazby  
  
-   Vytvoření vlastní vazby, která určuje, že protokolu SOAP zprávy jsou chráněny zabezpečené relaci.  
  
     Další informace o vytváření vlastních vazeb najdete v tématu [postupy: přizpůsobení vazbu System-Provided](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
     Následující příklad kódu používá konfiguraci určuje vlastní vazby této zprávy pomocí zabezpečené relaci.  
  
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
  
     Následující příklad kódu vytvoří vlastní vazby, který používá <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> režim ověřování bootstrap zabezpečené relaci.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled vazeb WCF](../../../../docs/framework/wcf/bindings-overview.md)
