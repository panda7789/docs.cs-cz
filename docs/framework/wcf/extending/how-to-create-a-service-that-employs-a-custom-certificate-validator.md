---
title: 'Postupy: Vytvoření služby, která používá vlastní validátor certifikátů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 7c2eb820a7e087d99ebd2c463db6e10595f7c1da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119623"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="f758a-102">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="f758a-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="f758a-103">Toto téma ukazuje, jak implementovat vlastní validátor certifikátů a jak nakonfigurovat přihlašovací údaje klienta nebo služby nahradit výchozí logiku ověření certifikátu vlastní validátor certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f758a-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="f758a-104">Pokud certifikát X.509 se používá k ověření klienta nebo služby, Windows Communication Foundation (WCF) ve výchozím nastavení používá úložiště certifikátů Windows a rozhraní Crypto API pro ověření certifikátu a ujistěte se, že je důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="f758a-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="f758a-105">Někdy funkci ověření integrované certifikátu není dostatečně a musí se změnit.</span><span class="sxs-lookup"><span data-stu-id="f758a-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="f758a-106">WCF poskytuje snadný způsob, jak změnit tím, že uživatelům přidávat vlastní validátor certifikátů logiku ověřování.</span><span class="sxs-lookup"><span data-stu-id="f758a-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="f758a-107">Pokud je zadán vlastní validátor certifikátů, WCF nepoužívá logiku ověření integrované certifikát, ale místo toho spoléhá na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="f758a-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="f758a-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="f758a-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="f758a-109">Chcete-li vytvořit vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="f758a-109">To create a custom certificate validator</span></span>  
  
1.  <span data-ttu-id="f758a-110">Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="f758a-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2.  <span data-ttu-id="f758a-111">Implementovat abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f758a-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="f758a-112">Certifikát, který musí být ověřené je předán jako argument do metody.</span><span class="sxs-lookup"><span data-stu-id="f758a-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="f758a-113">Pokud předaná certifikát není platný podle logiku ověřování, tato metoda vyvolá <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span><span class="sxs-lookup"><span data-stu-id="f758a-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="f758a-114">Pokud je certifikát platný, metoda vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f758a-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f758a-115">Pokud chcete vrátit chyby s ověřováním zpátky do klienta, throw <xref:System.ServiceModel.FaultException> v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f758a-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="f758a-116">Pokud chcete zadat vlastní validátor certifikátů do konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="f758a-116">To specify a custom certificate validator in service configuration</span></span>  
  
1.  <span data-ttu-id="f758a-117">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu a [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f758a-117">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="f758a-118">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavit `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f758a-118">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="f758a-119">Přidat [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) k `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f758a-119">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4.  <span data-ttu-id="f758a-120">Přidat `<clientCertificate>` elementu `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f758a-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5.  <span data-ttu-id="f758a-121">Přidat [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) k `<clientCertificate>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f758a-121">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6.  <span data-ttu-id="f758a-122">Nastavte `customCertificateValidatorType` atribut na typ validátoru.</span><span class="sxs-lookup"><span data-stu-id="f758a-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="f758a-123">Následující příklad nastaví atribut oboru názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="f758a-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7.  <span data-ttu-id="f758a-124">Nastavte `certificateValidationMode` atribut `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f758a-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="f758a-125">Chcete-li určit vlastní validátor certifikátů pomocí konfigurace na straně klienta</span><span class="sxs-lookup"><span data-stu-id="f758a-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1.  <span data-ttu-id="f758a-126">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu a [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f758a-126">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="f758a-127">Přidat [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f758a-127">Add an [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3.  <span data-ttu-id="f758a-128">Přidat `<behavior>` elementu a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f758a-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="f758a-129">Přidat [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f758a-129">Add a [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5.  <span data-ttu-id="f758a-130">Přidat [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="f758a-130">Add a [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6.  <span data-ttu-id="f758a-131">Přidat [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f758a-131">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7.  <span data-ttu-id="f758a-132">Nastavte `customCertificateValidatorType` atribut na typ validátoru.</span><span class="sxs-lookup"><span data-stu-id="f758a-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8.  <span data-ttu-id="f758a-133">Nastavte `certificateValidationMode` atribut `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f758a-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="f758a-134">Následující příklad nastaví atribut oboru názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="f758a-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="f758a-135">Chcete-li určit vlastní validátor certifikátů pomocí kódu ve službě</span><span class="sxs-lookup"><span data-stu-id="f758a-135">To specify a custom certificate validator using code on the service</span></span>  
  
1.  <span data-ttu-id="f758a-136">Zadejte vlastní validátor certifikátů na <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f758a-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="f758a-137">Můžete přistupovat pomocí pověření služby <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f758a-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2.  <span data-ttu-id="f758a-138">Nastavte <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="f758a-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="f758a-139">Chcete-li určit vlastní validátor certifikátů pomocí kódu na straně klienta</span><span class="sxs-lookup"><span data-stu-id="f758a-139">To specify a custom certificate validator using code on the client</span></span>  
  
1.  <span data-ttu-id="f758a-140">Zadejte vlastní validátor certifikátů pomocí <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f758a-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="f758a-141">Můžete přistupovat pomocí pověření klienta <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f758a-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="f758a-142">(Vygenerované třídy klienta [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vždy je odvozen od <xref:System.ServiceModel.ClientBase%601> třídy.)</span><span class="sxs-lookup"><span data-stu-id="f758a-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2.  <span data-ttu-id="f758a-143">Nastavte <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="f758a-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f758a-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="f758a-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f758a-145">Popis</span><span class="sxs-lookup"><span data-stu-id="f758a-145">Description</span></span>  
 <span data-ttu-id="f758a-146">Následující příklad ukazuje implementaci vlastní validátor certifikátů a jeho použití ve službě.</span><span class="sxs-lookup"><span data-stu-id="f758a-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f758a-147">Kód</span><span class="sxs-lookup"><span data-stu-id="f758a-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f758a-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f758a-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
