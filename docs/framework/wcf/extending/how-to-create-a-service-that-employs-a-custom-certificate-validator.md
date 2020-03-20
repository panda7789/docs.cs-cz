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
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="05e38-102">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="05e38-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="05e38-103">Toto téma ukazuje, jak implementovat vlastní validátor certifikátu a jak nakonfigurovat pověření klienta nebo služby tak, aby nahradila výchozí logiku ověření certifikátu vlastním validátorem certifikátu.</span><span class="sxs-lookup"><span data-stu-id="05e38-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="05e38-104">Pokud je certifikát X.509 použit k ověření klienta nebo služby, windows communication foundation (WCF) ve výchozím nastavení používá úložiště certifikátů systému Windows a crypto API k ověření certifikátu a k zajištění jeho důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="05e38-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="05e38-105">V některých proto není dostatečná vestavěná funkce ověření certifikátu, která musí být změněna.</span><span class="sxs-lookup"><span data-stu-id="05e38-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="05e38-106">WCF poskytuje snadný způsob, jak změnit logiku ověřování tím, že umožňuje uživatelům přidat vlastní validátor certifikátu.</span><span class="sxs-lookup"><span data-stu-id="05e38-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="05e38-107">Pokud je zadán vlastní validátor certifikátu, WCF nepoužívá předdefinovanou logiku ověření certifikátu, ale místo toho spoléhá na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="05e38-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="05e38-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="05e38-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="05e38-109">Vytvoření vlastního validátoru certifikátu</span><span class="sxs-lookup"><span data-stu-id="05e38-109">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="05e38-110">Definujte novou třídu <xref:System.IdentityModel.Selectors.X509CertificateValidator>odvozenou z .</span><span class="sxs-lookup"><span data-stu-id="05e38-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="05e38-111">Implementujte <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> abstraktní metodu.</span><span class="sxs-lookup"><span data-stu-id="05e38-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="05e38-112">Certifikát, který musí být ověřen, je předán jako argument metodě.</span><span class="sxs-lookup"><span data-stu-id="05e38-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="05e38-113">Pokud předaný certifikát není platný podle logiky ověřování, tato metoda vyvolá <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span><span class="sxs-lookup"><span data-stu-id="05e38-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="05e38-114">Pokud je certifikát platný, metoda se vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="05e38-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="05e38-115">Chcete-li vrátit chyby ověřování <xref:System.ServiceModel.FaultException> zpět <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> klientovi, vyhoďte metodu.</span><span class="sxs-lookup"><span data-stu-id="05e38-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="05e38-116">Určení vlastního validátoru certifikátu v konfiguraci služby</span><span class="sxs-lookup"><span data-stu-id="05e38-116">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="05e38-117">Přidejte [ \<chování>](../../configure-apps/file-schema/wcf/behaviors.md) element a [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do elementu [ \<system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="05e38-117">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="05e38-118">Přidejte [ \<>chování](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) `name` a nastavte atribut na příslušnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="05e38-118">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="05e38-119">Přidejte [ \<>serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md) do `<behavior>` prvku.</span><span class="sxs-lookup"><span data-stu-id="05e38-119">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="05e38-120">Přidejte `<clientCertificate>` prvek `<serviceCredentials>` do prvku.</span><span class="sxs-lookup"><span data-stu-id="05e38-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="05e38-121">Přidejte [ \<>ověřování](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) do `<clientCertificate>` prvku.</span><span class="sxs-lookup"><span data-stu-id="05e38-121">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="05e38-122">Nastavte `customCertificateValidatorType` atribut na typ validátoru.</span><span class="sxs-lookup"><span data-stu-id="05e38-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="05e38-123">Následující příklad nastaví atribut na obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="05e38-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="05e38-124">Nastavte `certificateValidationMode` atribut `Custom`na .</span><span class="sxs-lookup"><span data-stu-id="05e38-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="05e38-125">Určení vlastního validátoru certifikátu pomocí konfigurace v klientovi</span><span class="sxs-lookup"><span data-stu-id="05e38-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="05e38-126">Přidejte [ \<chování>](../../configure-apps/file-schema/wcf/behaviors.md) element a [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do elementu [ \<system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="05e38-126">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="05e38-127">Přidejte [ \<prvek>koncového boduChování.](../../configure-apps/file-schema/wcf/endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="05e38-127">Add an [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="05e38-128">Přidejte `<behavior>` prvek a `name` nastavte atribut na příslušnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="05e38-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="05e38-129">Přidejte [ \<prvek>clientCredentials.](../../configure-apps/file-schema/wcf/clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="05e38-129">Add a [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="05e38-130">Přidejte [ \<službuCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="05e38-130">Add a [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="05e38-131">Přidejte [ \<ověřovací>,](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="05e38-131">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="05e38-132">Nastavte `customCertificateValidatorType` atribut na typ validátoru.</span><span class="sxs-lookup"><span data-stu-id="05e38-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="05e38-133">Nastavte `certificateValidationMode` atribut `Custom`na .</span><span class="sxs-lookup"><span data-stu-id="05e38-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="05e38-134">Následující příklad nastaví atribut na obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="05e38-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="05e38-135">Určení vlastního validátoru certifikátu pomocí kódu ve službě</span><span class="sxs-lookup"><span data-stu-id="05e38-135">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="05e38-136">Zadejte vlastní validátor certifikátu ve vlastnosti. <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A></span><span class="sxs-lookup"><span data-stu-id="05e38-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="05e38-137">Můžete přistupovat k pověření <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> služby pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="05e38-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="05e38-138">Nastavte <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>na .</span><span class="sxs-lookup"><span data-stu-id="05e38-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="05e38-139">Určení vlastního validátoru certifikátu pomocí kódu na straně klienta</span><span class="sxs-lookup"><span data-stu-id="05e38-139">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="05e38-140">Zadejte vlastní validátor certifikátu pomocí vlastnosti. <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A></span><span class="sxs-lookup"><span data-stu-id="05e38-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="05e38-141">Můžete přistupovat k pověření <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> klienta pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="05e38-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="05e38-142">(Třída klienta generovaná [nástrojem ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) je vždy odvozena <xref:System.ServiceModel.ClientBase%601> od třídy.)</span><span class="sxs-lookup"><span data-stu-id="05e38-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="05e38-143">Nastavte <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>na .</span><span class="sxs-lookup"><span data-stu-id="05e38-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05e38-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="05e38-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="05e38-145">Popis</span><span class="sxs-lookup"><span data-stu-id="05e38-145">Description</span></span>  
 <span data-ttu-id="05e38-146">Následující ukázka ukazuje implementaci vlastní validátor certifikátu a jeho použití ve službě.</span><span class="sxs-lookup"><span data-stu-id="05e38-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="05e38-147">kód</span><span class="sxs-lookup"><span data-stu-id="05e38-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="05e38-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="05e38-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
