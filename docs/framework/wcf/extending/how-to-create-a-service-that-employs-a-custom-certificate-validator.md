---
title: 'Postupy: Vytvoření služby, která používá vlastní validátor certifikátů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 156d661fd5602333fae8066f3062b442a1df19af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951708"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Postupy: Vytvoření služby, která používá vlastní validátor certifikátů
V tomto tématu se dozvíte, jak implementovat vlastní validátor certifikátů a jak nakonfigurovat pověření klienta nebo služby, aby se výchozí logika ověřování certifikátů nahradila vlastním validátorem certifikátů.  
  
 Pokud se certifikát X. 509 používá k ověření klienta nebo služby, Windows Communication Foundation (WCF) ve výchozím nastavení používá úložiště certifikátů Windows a kryptografické rozhraní API k ověření certifikátu a k zajištění jeho důvěryhodnosti. V některých případech nejsou integrované funkce ověřování certifikátů dostatečné a je třeba je změnit. Služba WCF poskytuje snadný způsob, jak změnit logiku ověřování tím, že uživatelům umožní přidat vlastní validátor certifikátů. Pokud je určen vlastní validátor certifikátů, WCF nepoužívá integrovanou logiku ověřování certifikátů, ale spoléhá na vlastní validátor.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Vytvoření vlastního validátoru certifikátů  
  
1. Definujte novou třídu odvozenou z <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
2. Implementujte abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metodu. Certifikát, který se musí ověřit, se předává jako argument metody. Pokud předaný certifikát není podle logiky ověřování platný, vyvolá <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>Tato metoda. Pokud je certifikát platný, metoda se vrátí volajícímu.  
  
    > [!NOTE]
    > Chcete-li vrátit chyby ověřování zpět do klienta, vyvolejte <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> v metodě.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Určení vlastního validátoru certifikátů v konfiguraci služby  
  
1. Přidejte > prvek [ chovánía>serviceBehaviorsdoprvkuSystem.ServiceModel>.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Přidejte > `name` chování a nastavte atribut na odpovídající hodnotu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
  
3. Přidejte [> ServiceCredentials k elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) `<behavior>`  
  
4. `<clientCertificate>` Přidejte element`<serviceCredentials>` do elementu.  
  
5. Přidejte [> ověřování k elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) `<clientCertificate>`  
  
6. `customCertificateValidatorType` Nastavte atribut na typ validátoru. Následující příklad nastaví atribut na obor názvů a název typu.  
  
7. Nastavte atribut na `Custom`. `certificateValidationMode`  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>Určení vlastního validátoru certifikátů pomocí konfigurace na klientovi  
  
1. Přidejte > prvek [ chovánía>serviceBehaviorsdoprvkuSystem.ServiceModel>.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Přidejte prvek endpointBehaviors >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)  
  
3. Přidejte element a `name` nastavte atribut na odpovídající hodnotu. `<behavior>`  
  
4. Přidejte prvek [> ClientCredentials.\<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
  
5. Přidejte > ServiceCertificate. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)  
  
6. Přidejte > ověřování, jak je znázorněno v následujícím příkladu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
7. `customCertificateValidatorType` Nastavte atribut na typ validátoru.  
  
8. Nastavte atribut na `Custom`. `certificateValidationMode` Následující příklad nastaví atribut na obor názvů a název typu.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Určení vlastního validátoru certifikátů pomocí kódu ve službě  
  
1. Zadejte vlastní validátor certifikátu pro <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> vlastnost. K pověřením služby můžete přistupovat pomocí <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnosti.  
  
2. Nastavte <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Určení vlastního validátoru certifikátů pomocí kódu na klientovi  
  
1. Pomocí <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> vlastnosti zadejte vlastní validátor certifikátů. Přístup k přihlašovacím údajům klienta můžete <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> získat pomocí vlastnosti. (Třída klienta generovaná [nástrojem ServiceModel Metadata Utility (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) je vždy odvozena od <xref:System.ServiceModel.ClientBase%601> třídy.)  
  
2. Nastavte <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje implementaci vlastního validátoru certifikátů a jeho využití ve službě.  
  
### <a name="code"></a>Kód  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
