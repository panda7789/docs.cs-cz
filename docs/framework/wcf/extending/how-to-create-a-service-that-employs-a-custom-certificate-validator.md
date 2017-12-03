---
title: "Postupy: vytvoření služby, který využívá validátor vlastní certifikát"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb38d8310d22b8128c76ed77f06a49c9576db33d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="deed4-102">Postupy: vytvoření služby, který využívá validátor vlastní certifikát</span><span class="sxs-lookup"><span data-stu-id="deed4-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="deed4-103">Toto téma ukazuje, jak implementovat vlastní certifikát ověření a postup konfigurace klienta služby Windows nebo pověření nahradit logiku ověření certifikátu výchozí validátor vlastní certifikát.</span><span class="sxs-lookup"><span data-stu-id="deed4-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="deed4-104">Pokud certifikát X.509 slouží k ověření klienta a služby, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve výchozím nastavení používá úložiště certifikátů systému Windows a rozhraní API pro šifrování a ověřit certifikát a ujistěte se, zda je důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="deed4-104">If the X.509 certificate is used to authenticate a client or service, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="deed4-105">Někdy funkce integrované certifikát ověření nestačí a je třeba změnit.</span><span class="sxs-lookup"><span data-stu-id="deed4-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="deed4-106">poskytuje snadný způsob, jak změnit logiku ověření tím, že se uživatelům přidat validátor vlastní certifikát.</span><span class="sxs-lookup"><span data-stu-id="deed4-106"> provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="deed4-107">Pokud validátor vlastní certifikát není zadaný, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nepoužívá logiku ověření integrované certifikátu ale spoléhá na vlastní validátor místo.</span><span class="sxs-lookup"><span data-stu-id="deed4-107">If a custom certificate validator is specified, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="deed4-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="deed4-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="deed4-109">Chcete-li vytvořit vlastní certifikát ověření</span><span class="sxs-lookup"><span data-stu-id="deed4-109">To create a custom certificate validator</span></span>  
  
1.  <span data-ttu-id="deed4-110">Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="deed4-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2.  <span data-ttu-id="deed4-111">Implementaci abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="deed4-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="deed4-112">Certifikát, který musí být ověřené je jako argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="deed4-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="deed4-113">Pokud předaný certifikátu není platný podle logiku ověření, tato metoda vyvolá <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span><span class="sxs-lookup"><span data-stu-id="deed4-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="deed4-114">Pokud je certifikát platný, vrátí metoda volajícímu.</span><span class="sxs-lookup"><span data-stu-id="deed4-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="deed4-115">Pokud chcete vrátit zpátky chybám při ověřování klienta, throw <xref:System.ServiceModel.FaultException> v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="deed4-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="deed4-116">Pokud chcete zadat validátor vlastní certifikát do konfigurace služby</span><span class="sxs-lookup"><span data-stu-id="deed4-116">To specify a custom certificate validator in service configuration</span></span>  
  
1.  <span data-ttu-id="deed4-117">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu a [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span><span class="sxs-lookup"><span data-stu-id="deed4-117">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="deed4-118">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="deed4-118">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="deed4-119">Přidat [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) k `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="deed4-119">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4.  <span data-ttu-id="deed4-120">Přidat `<clientCertificate>` elementu, který chcete `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="deed4-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5.  <span data-ttu-id="deed4-121">Přidat [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) k `<clientCertificate>` elementu.</span><span class="sxs-lookup"><span data-stu-id="deed4-121">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6.  <span data-ttu-id="deed4-122">Nastavte `customCertificateValidatorType` atribut Typ validátoru.</span><span class="sxs-lookup"><span data-stu-id="deed4-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="deed4-123">Následující příklad nastaví atribut pro obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="deed4-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7.  <span data-ttu-id="deed4-124">Nastavte `certificateValidationMode` atribut `Custom`.</span><span class="sxs-lookup"><span data-stu-id="deed4-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="deed4-125">Chcete-li určit validátor vlastní certifikát pomocí konfigurace na straně klienta</span><span class="sxs-lookup"><span data-stu-id="deed4-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1.  <span data-ttu-id="deed4-126">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu a [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span><span class="sxs-lookup"><span data-stu-id="deed4-126">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="deed4-127">Přidat [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="deed4-127">Add an [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3.  <span data-ttu-id="deed4-128">Přidat `<behavior>` elementu a sadu `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="deed4-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="deed4-129">Přidat [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span><span class="sxs-lookup"><span data-stu-id="deed4-129">Add a [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5.  <span data-ttu-id="deed4-130">Přidat [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="deed4-130">Add a [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6.  <span data-ttu-id="deed4-131">Přidat [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="deed4-131">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7.  <span data-ttu-id="deed4-132">Nastavte `customCertificateValidatorType` atribut Typ validátoru.</span><span class="sxs-lookup"><span data-stu-id="deed4-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8.  <span data-ttu-id="deed4-133">Nastavte `certificateValidationMode` atribut `Custom`.</span><span class="sxs-lookup"><span data-stu-id="deed4-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="deed4-134">Následující příklad nastaví atribut pro obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="deed4-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="deed4-135">Chcete-li určit validátor vlastní certifikát pomocí kódu služby</span><span class="sxs-lookup"><span data-stu-id="deed4-135">To specify a custom certificate validator using code on the service</span></span>  
  
1.  <span data-ttu-id="deed4-136">Zadejte vlastní certifikát validátor na <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="deed4-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="deed4-137">Dostanete přihlašovací údaje služby pomocí <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="deed4-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2.  <span data-ttu-id="deed4-138">Nastavte <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="deed4-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="deed4-139">Chcete-li určit validátor vlastní certifikát pomocí kódu na straně klienta</span><span class="sxs-lookup"><span data-stu-id="deed4-139">To specify a custom certificate validator using code on the client</span></span>  
  
1.  <span data-ttu-id="deed4-140">Zadejte vlastní certifikát validátor pomocí <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="deed4-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="deed4-141">Můžete získat přístup k pověření klienta pomocí <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="deed4-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="deed4-142">(Vygenerované třídy klienta [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vždy je odvozena z <xref:System.ServiceModel.ClientBase%601> třídy.)</span><span class="sxs-lookup"><span data-stu-id="deed4-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2.  <span data-ttu-id="deed4-143">Nastavte <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="deed4-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="deed4-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="deed4-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="deed4-145">Popis</span><span class="sxs-lookup"><span data-stu-id="deed4-145">Description</span></span>  
 <span data-ttu-id="deed4-146">Následující příklad ukazuje implementaci validátoru vlastního certifikátu a jeho použití na službu.</span><span class="sxs-lookup"><span data-stu-id="deed4-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="deed4-147">Kód</span><span class="sxs-lookup"><span data-stu-id="deed4-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="deed4-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="deed4-148">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>
