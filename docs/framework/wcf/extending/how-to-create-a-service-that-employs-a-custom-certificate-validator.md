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
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="c2825-102">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="c2825-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="c2825-103">V tomto tématu se dozvíte, jak implementovat vlastní validátor certifikátů a jak nakonfigurovat pověření klienta nebo služby, aby se výchozí logika ověřování certifikátů nahradila vlastním validátorem certifikátů.</span><span class="sxs-lookup"><span data-stu-id="c2825-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="c2825-104">Pokud se certifikát X. 509 používá k ověření klienta nebo služby, Windows Communication Foundation (WCF) ve výchozím nastavení používá úložiště certifikátů Windows a kryptografické rozhraní API k ověření certifikátu a k zajištění jeho důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="c2825-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="c2825-105">V některých případech nejsou integrované funkce ověřování certifikátů dostatečné a je třeba je změnit.</span><span class="sxs-lookup"><span data-stu-id="c2825-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="c2825-106">Služba WCF poskytuje snadný způsob, jak změnit logiku ověřování tím, že uživatelům umožní přidat vlastní validátor certifikátů.</span><span class="sxs-lookup"><span data-stu-id="c2825-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="c2825-107">Pokud je určen vlastní validátor certifikátů, WCF nepoužívá integrovanou logiku ověřování certifikátů, ale spoléhá na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="c2825-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="c2825-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="c2825-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="c2825-109">Vytvoření vlastního validátoru certifikátů</span><span class="sxs-lookup"><span data-stu-id="c2825-109">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="c2825-110">Definujte novou třídu odvozenou z <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2825-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="c2825-111">Implementujte abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="c2825-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="c2825-112">Certifikát, který se musí ověřit, se předává jako argument metody.</span><span class="sxs-lookup"><span data-stu-id="c2825-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="c2825-113">Pokud předaný certifikát není podle logiky ověřování platný, vyvolá <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>Tato metoda.</span><span class="sxs-lookup"><span data-stu-id="c2825-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="c2825-114">Pokud je certifikát platný, metoda se vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c2825-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c2825-115">Chcete-li vrátit chyby ověřování zpět do klienta, vyvolejte <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> v metodě.</span><span class="sxs-lookup"><span data-stu-id="c2825-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="c2825-116">Určení vlastního validátoru certifikátů v konfiguraci služby</span><span class="sxs-lookup"><span data-stu-id="c2825-116">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="c2825-117">Přidejte > prvek [ chovánía>serviceBehaviorsdoprvkuSystem.ServiceModel>.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c2825-117">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="c2825-118">Přidejte > `name` chování a nastavte atribut na odpovídající hodnotu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c2825-118">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="c2825-119">Přidejte [> ServiceCredentials k elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) `<behavior>`</span><span class="sxs-lookup"><span data-stu-id="c2825-119">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="c2825-120">`<clientCertificate>` Přidejte element`<serviceCredentials>` do elementu.</span><span class="sxs-lookup"><span data-stu-id="c2825-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="c2825-121">Přidejte [> ověřování k elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) `<clientCertificate>`</span><span class="sxs-lookup"><span data-stu-id="c2825-121">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="c2825-122">`customCertificateValidatorType` Nastavte atribut na typ validátoru.</span><span class="sxs-lookup"><span data-stu-id="c2825-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="c2825-123">Následující příklad nastaví atribut na obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="c2825-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="c2825-124">Nastavte atribut na `Custom`. `certificateValidationMode`</span><span class="sxs-lookup"><span data-stu-id="c2825-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="c2825-125">Určení vlastního validátoru certifikátů pomocí konfigurace na klientovi</span><span class="sxs-lookup"><span data-stu-id="c2825-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="c2825-126">Přidejte > prvek [ chovánía>serviceBehaviorsdoprvkuSystem.ServiceModel>.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c2825-126">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="c2825-127">Přidejte prvek endpointBehaviors >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c2825-127">Add an [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="c2825-128">Přidejte element a `name` nastavte atribut na odpovídající hodnotu. `<behavior>`</span><span class="sxs-lookup"><span data-stu-id="c2825-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="c2825-129">Přidejte prvek [> ClientCredentials.\<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c2825-129">Add a [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="c2825-130">Přidejte > ServiceCertificate. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2825-130">Add a [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="c2825-131">Přidejte > ověřování, jak je znázorněno v následujícím příkladu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2825-131">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="c2825-132">`customCertificateValidatorType` Nastavte atribut na typ validátoru.</span><span class="sxs-lookup"><span data-stu-id="c2825-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="c2825-133">Nastavte atribut na `Custom`. `certificateValidationMode`</span><span class="sxs-lookup"><span data-stu-id="c2825-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="c2825-134">Následující příklad nastaví atribut na obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="c2825-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="c2825-135">Určení vlastního validátoru certifikátů pomocí kódu ve službě</span><span class="sxs-lookup"><span data-stu-id="c2825-135">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="c2825-136">Zadejte vlastní validátor certifikátu pro <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c2825-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="c2825-137">K pověřením služby můžete přistupovat pomocí <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2825-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="c2825-138">Nastavte <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="c2825-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="c2825-139">Určení vlastního validátoru certifikátů pomocí kódu na klientovi</span><span class="sxs-lookup"><span data-stu-id="c2825-139">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="c2825-140">Pomocí <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> vlastnosti zadejte vlastní validátor certifikátů.</span><span class="sxs-lookup"><span data-stu-id="c2825-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="c2825-141">Přístup k přihlašovacím údajům klienta můžete <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> získat pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2825-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="c2825-142">(Třída klienta generovaná [nástrojem ServiceModel Metadata Utility (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) je vždy odvozena od <xref:System.ServiceModel.ClientBase%601> třídy.)</span><span class="sxs-lookup"><span data-stu-id="c2825-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="c2825-143">Nastavte <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="c2825-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2825-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2825-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c2825-145">Popis</span><span class="sxs-lookup"><span data-stu-id="c2825-145">Description</span></span>  
 <span data-ttu-id="c2825-146">Následující příklad ukazuje implementaci vlastního validátoru certifikátů a jeho využití ve službě.</span><span class="sxs-lookup"><span data-stu-id="c2825-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c2825-147">Kód</span><span class="sxs-lookup"><span data-stu-id="c2825-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c2825-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2825-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
