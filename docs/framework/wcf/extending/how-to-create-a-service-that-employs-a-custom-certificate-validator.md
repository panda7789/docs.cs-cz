---
title: 'Postupy: Vytvoření služby, která používá vlastní validátor certifikátů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: af1bb9b2ff793f6e6854c1b253dd445a35a5076f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185580"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Postupy: Vytvoření služby, která používá vlastní validátor certifikátů
Toto téma ukazuje, jak implementovat vlastní validátor certifikátu a jak nakonfigurovat pověření klienta nebo služby tak, aby nahradila výchozí logiku ověření certifikátu vlastním validátorem certifikátu.  
  
 Pokud je certifikát X.509 použit k ověření klienta nebo služby, windows communication foundation (WCF) ve výchozím nastavení používá úložiště certifikátů systému Windows a crypto API k ověření certifikátu a k zajištění jeho důvěryhodnosti. V některých proto není dostatečná vestavěná funkce ověření certifikátu, která musí být změněna. WCF poskytuje snadný způsob, jak změnit logiku ověřování tím, že umožňuje uživatelům přidat vlastní validátor certifikátu. Pokud je zadán vlastní validátor certifikátu, WCF nepoužívá předdefinovanou logiku ověření certifikátu, ale místo toho spoléhá na vlastní validátor.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Vytvoření vlastního validátoru certifikátu  
  
1. Definujte novou třídu <xref:System.IdentityModel.Selectors.X509CertificateValidator>odvozenou z .  
  
2. Implementujte <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> abstraktní metodu. Certifikát, který musí být ověřen, je předán jako argument metodě. Pokud předaný certifikát není platný podle logiky ověřování, tato metoda vyvolá <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Pokud je certifikát platný, metoda se vrátí volajícímu.  
  
    > [!NOTE]
    > Chcete-li vrátit chyby ověřování <xref:System.ServiceModel.FaultException> zpět <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> klientovi, vyhoďte metodu.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Určení vlastního validátoru certifikátu v konfiguraci služby  
  
1. Přidejte [ \<chování>](../../configure-apps/file-schema/wcf/behaviors.md) element a [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do elementu [ \<system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Přidejte [ \<>chování](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) `name` a nastavte atribut na příslušnou hodnotu.  
  
3. Přidejte [ \<>serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md) do `<behavior>` prvku.  
  
4. Přidejte `<clientCertificate>` prvek `<serviceCredentials>` do prvku.  
  
5. Přidejte [ \<>ověřování](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) do `<clientCertificate>` prvku.  
  
6. Nastavte `customCertificateValidatorType` atribut na typ validátoru. Následující příklad nastaví atribut na obor názvů a název typu.  
  
7. Nastavte `certificateValidationMode` atribut `Custom`na .  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>Určení vlastního validátoru certifikátu pomocí konfigurace v klientovi  
  
1. Přidejte [ \<chování>](../../configure-apps/file-schema/wcf/behaviors.md) element a [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do elementu [ \<system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Přidejte [ \<prvek>koncového boduChování.](../../configure-apps/file-schema/wcf/endpointbehaviors.md)  
  
3. Přidejte `<behavior>` prvek a `name` nastavte atribut na příslušnou hodnotu.  
  
4. Přidejte [ \<prvek>clientCredentials.](../../configure-apps/file-schema/wcf/clientcredentials.md)  
  
5. Přidejte [ \<službuCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
6. Přidejte [ \<ověřovací>,](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak je znázorněno v následujícím příkladu.  
  
7. Nastavte `customCertificateValidatorType` atribut na typ validátoru.  
  
8. Nastavte `certificateValidationMode` atribut `Custom`na . Následující příklad nastaví atribut na obor názvů a název typu.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Určení vlastního validátoru certifikátu pomocí kódu ve službě  
  
1. Zadejte vlastní validátor certifikátu ve vlastnosti. <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> Můžete přistupovat k pověření <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> služby pomocí vlastnosti.  
  
2. Nastavte <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>na .  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Určení vlastního validátoru certifikátu pomocí kódu na straně klienta  
  
1. Zadejte vlastní validátor certifikátu pomocí vlastnosti. <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> Můžete přistupovat k pověření <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> klienta pomocí vlastnosti. (Třída klienta generovaná [nástrojem ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) je vždy odvozena <xref:System.ServiceModel.ClientBase%601> od třídy.)  
  
2. Nastavte <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>na .  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující ukázka ukazuje implementaci vlastní validátor certifikátu a jeho použití ve službě.  
  
### <a name="code"></a>kód  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
