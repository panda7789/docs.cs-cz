---
title: "Postupy: vytvoření služby, který využívá validátor vlastní certifikát"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e0a48801b1d4674b81a0e4b54a80b69d026ce2af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Postupy: vytvoření služby, který využívá validátor vlastní certifikát
Toto téma ukazuje, jak implementovat vlastní certifikát ověření a postup konfigurace klienta služby Windows nebo pověření nahradit logiku ověření certifikátu výchozí validátor vlastní certifikát.  
  
 Pokud certifikát X.509 slouží k ověření klienta a služby, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve výchozím nastavení používá úložiště certifikátů systému Windows a rozhraní API pro šifrování a ověřit certifikát a ujistěte se, zda je důvěryhodný. Někdy funkce integrované certifikát ověření nestačí a je třeba změnit. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje snadný způsob, jak změnit logiku ověření tím, že se uživatelům přidat validátor vlastní certifikát. Pokud validátor vlastní certifikát není zadaný, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nepoužívá logiku ověření integrované certifikátu ale spoléhá na vlastní validátor místo.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Chcete-li vytvořit vlastní certifikát ověření  
  
1.  Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
2.  Implementaci abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metoda. Certifikát, který musí být ověřené je jako argument předaný metodě. Pokud předaný certifikátu není platný podle logiku ověření, tato metoda vyvolá <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Pokud je certifikát platný, vrátí metoda volajícímu.  
  
    > [!NOTE]
    >  Pokud chcete vrátit zpátky chybám při ověřování klienta, throw <xref:System.ServiceModel.FaultException> v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Pokud chcete zadat validátor vlastní certifikát do konfigurace služby  
  
1.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu a [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.  
  
2.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavte `name` atribut na odpovídající hodnotu.  
  
3.  Přidat [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) k `<behavior>` elementu.  
  
4.  Přidat `<clientCertificate>` elementu, který chcete `<serviceCredentials>` elementu.  
  
5.  Přidat [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) k `<clientCertificate>` elementu.  
  
6.  Nastavte `customCertificateValidatorType` atribut Typ validátoru. Následující příklad nastaví atribut pro obor názvů a název typu.  
  
7.  Nastavte `certificateValidationMode` atribut `Custom`.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>Chcete-li určit validátor vlastní certifikát pomocí konfigurace na straně klienta  
  
1.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu a [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.  
  
2.  Přidat [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element.  
  
3.  Přidat `<behavior>` elementu a sadu `name` atribut na odpovídající hodnotu.  
  
4.  Přidat [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.  
  
5.  Přidat [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
6.  Přidat [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak je znázorněno v následujícím příkladu.  
  
7.  Nastavte `customCertificateValidatorType` atribut Typ validátoru.  
  
8.  Nastavte `certificateValidationMode` atribut `Custom`. Následující příklad nastaví atribut pro obor názvů a název typu.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"   
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Chcete-li určit validátor vlastní certifikát pomocí kódu služby  
  
1.  Zadejte vlastní certifikát validátor na <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> vlastnost. Dostanete přihlašovací údaje služby pomocí <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost.  
  
2.  Nastavte <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Chcete-li určit validátor vlastní certifikát pomocí kódu na straně klienta  
  
1.  Zadejte vlastní certifikát validátor pomocí <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> vlastnost. Můžete získat přístup k pověření klienta pomocí <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost. (Vygenerované třídy klienta [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vždy je odvozena z <xref:System.ServiceModel.ClientBase%601> třídy.)  
  
2.  Nastavte <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje implementaci validátoru vlastního certifikátu a jeho použití na službu.  
  
### <a name="code"></a>Kód  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>
