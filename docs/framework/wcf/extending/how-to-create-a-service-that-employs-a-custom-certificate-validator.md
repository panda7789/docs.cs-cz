---
title: 'Postupy: Vytvoření služby, která používá vlastní validátor certifikátů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: b7e8e4a750aadd8a84a57cdf22c01f6b91e6256c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767731"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Postupy: Vytvoření služby, která používá vlastní validátor certifikátů
Toto téma ukazuje, jak implementovat vlastní validátor certifikátů a jak nakonfigurovat přihlašovací údaje klienta nebo služby nahradit výchozí logiku ověření certifikátu vlastní validátor certifikátů.  
  
 Pokud certifikát X.509 se používá k ověření klienta nebo služby, Windows Communication Foundation (WCF) ve výchozím nastavení používá úložiště certifikátů Windows a rozhraní Crypto API pro ověření certifikátu a ujistěte se, že je důvěryhodný. Někdy funkci ověření integrované certifikátu není dostatečně a musí se změnit. WCF poskytuje snadný způsob, jak změnit tím, že uživatelům přidávat vlastní validátor certifikátů logiku ověřování. Pokud je zadán vlastní validátor certifikátů, WCF nepoužívá logiku ověření integrované certifikát, ale místo toho spoléhá na vlastní validátor.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Chcete-li vytvořit vlastní validátor certifikátů  
  
1. Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
2. Implementovat abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metody. Certifikát, který musí být ověřené je předán jako argument do metody. Pokud předaná certifikát není platný podle logiku ověřování, tato metoda vyvolá <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Pokud je certifikát platný, metoda vrátí volajícímu.  
  
    > [!NOTE]
    >  Pokud chcete vrátit chyby s ověřováním zpátky do klienta, throw <xref:System.ServiceModel.FaultException> v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Pokud chcete zadat vlastní validátor certifikátů do konfigurace služby  
  
1. Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu a [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.  
  
2. Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavit `name` atribut na odpovídající hodnotu.  
  
3. Přidat [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) k `<behavior>` elementu.  
  
4. Přidat `<clientCertificate>` elementu `<serviceCredentials>` elementu.  
  
5. Přidat [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) k `<clientCertificate>` elementu.  
  
6. Nastavte `customCertificateValidatorType` atribut na typ validátoru. Následující příklad nastaví atribut oboru názvů a název typu.  
  
7. Nastavte `certificateValidationMode` atribut `Custom`.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>Chcete-li určit vlastní validátor certifikátů pomocí konfigurace na straně klienta  
  
1. Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu a [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.  
  
2. Přidat [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) elementu.  
  
3. Přidat `<behavior>` elementu a nastavte `name` atribut na odpovídající hodnotu.  
  
4. Přidat [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.  
  
5. Přidat [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
6. Přidat [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak je znázorněno v následujícím příkladu.  
  
7. Nastavte `customCertificateValidatorType` atribut na typ validátoru.  
  
8. Nastavte `certificateValidationMode` atribut `Custom`. Následující příklad nastaví atribut oboru názvů a název typu.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Chcete-li určit vlastní validátor certifikátů pomocí kódu ve službě  
  
1. Zadejte vlastní validátor certifikátů na <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> vlastnost. Můžete přistupovat pomocí pověření služby <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost.  
  
2. Nastavte <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Chcete-li určit vlastní validátor certifikátů pomocí kódu na straně klienta  
  
1. Zadejte vlastní validátor certifikátů pomocí <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> vlastnost. Můžete přistupovat pomocí pověření klienta <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost. (Vygenerované třídy klienta [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vždy je odvozen od <xref:System.ServiceModel.ClientBase%601> třídy.)  
  
2. Nastavte <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje implementaci vlastní validátor certifikátů a jeho použití ve službě.  
  
### <a name="code"></a>Kód  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
