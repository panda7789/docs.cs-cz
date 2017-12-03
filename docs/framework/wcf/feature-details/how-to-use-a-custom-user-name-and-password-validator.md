---
title: "Postupy: Použití validátoru vlastního uživatelského jména a hesla"
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
helpviewer_keywords: WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1ec4dc2d7f066d79b2cf54c3d474b47e769b626c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="d39ba-102">Postupy: Použití validátoru vlastního uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="d39ba-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="d39ba-103">Ve výchozím nastavení, pokud uživatelské jméno a heslo slouží k ověřování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] používá Windows k ověření uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="d39ba-103">By default, when a user name and password is used for authentication, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses Windows to validate the user name and password.</span></span> <span data-ttu-id="d39ba-104">Ale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umožňuje vlastní uživatelské jméno a heslo schémat ověřování, také známé jako *validátory*.</span><span class="sxs-lookup"><span data-stu-id="d39ba-104">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="d39ba-105">Zahrnout validátor vlastní uživatelské jméno a heslo, vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a potom jej nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="d39ba-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="d39ba-106">Ukázkovou aplikaci, najdete v části [validátor hesel pro uživatele název](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="d39ba-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="d39ba-107">Chcete-li vytvořit validátor vlastní uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="d39ba-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="d39ba-108">Vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="d39ba-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="d39ba-109">Implementace vlastního ověřování schématu přepsáním <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d39ba-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="d39ba-110">Nepoužívejte kód v následujícím příkladu, který přepíše <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="d39ba-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="d39ba-111">Nahraďte kód vaše vlastní uživatelské jméno a heslo schéma ověřování, které mohou zahrnovat načítání dvojice název a heslo uživatele z databáze.</span><span class="sxs-lookup"><span data-stu-id="d39ba-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="d39ba-112">Pokud chcete vrátit zpátky chybám při ověřování klienta, throw <xref:System.ServiceModel.FaultException> v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d39ba-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="d39ba-113">Nakonfigurujte službu používat validátor vlastní uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="d39ba-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="d39ba-114">Nakonfigurujte vazbu, která používá zabezpečení zpráv přes všechny přenos nebo zabezpečení na úrovni přenosu přes protokol HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="d39ba-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="d39ba-115">Při použití zabezpečení zpráv, přidejte jedno z vazby poskytované systémem, jako například [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), nebo [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) zabezpečení podporuje zpráv a `UserName` typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="d39ba-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="d39ba-116">Při použití zabezpečení na úrovni přenosu přes protokol HTTP (S), přidejte buď [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nebo [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) nebo [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , který používá protokol HTTP (S) a `Basic` schéma ověřování.</span><span class="sxs-lookup"><span data-stu-id="d39ba-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d39ba-117">Když [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] nebo novějším, je použít, můžete použít vlastní validátor uživatelské jméno a heslo s zabezpečení zprávy a přenos.</span><span class="sxs-lookup"><span data-stu-id="d39ba-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="d39ba-118">S [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], vlastní validátor uživatelské jméno a heslo lze použít pouze s zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="d39ba-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d39ba-119">Další informace o používání \<netTcpBinding > v tomto kontextu, najdete v části [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d39ba-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="d39ba-120">V konfiguračním souboru v části [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, přidejte [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span><span class="sxs-lookup"><span data-stu-id="d39ba-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="d39ba-121">Přidat [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nebo [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element do části vazby.</span><span class="sxs-lookup"><span data-stu-id="d39ba-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d39ba-122">vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby elementu, najdete v části [postupy: zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d39ba-122"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="d39ba-123">Nastavte `mode` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) nebo [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) k `Message`, `Transport`, `or``TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="d39ba-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, `or``TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="d39ba-124">Nastavte `clientCredentialType` atribut [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) nebo [ \<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d39ba-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="d39ba-125">Při použití zabezpečení zpráv, `clientCredentialType` atribut [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) k `UserName`.</span><span class="sxs-lookup"><span data-stu-id="d39ba-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="d39ba-126">Při použití zabezpečení na úrovni přenosu přes protokol HTTP (S), `clientCredentialType` atribut [ \<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) nebo [ \<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) k `Basic`.</span><span class="sxs-lookup"><span data-stu-id="d39ba-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="d39ba-127">Když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba je hostovaná v Internetové informační služby (IIS) pomocí zabezpečení na úrovni přenosu a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> je nastavena na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, schéma vlastní ověřování používá podmnožinu ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d39ba-127">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="d39ba-128">Důvodem je, že v tomto scénáři služba IIS provede ověřování systému Windows před [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyvolání vlastní authenticator.</span><span class="sxs-lookup"><span data-stu-id="d39ba-128">That is because in this scenario, IIS performs Windows authentication prior to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invoking the custom authenticator.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d39ba-129">vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby elementu, najdete v části [postupy: zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d39ba-129"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="d39ba-130">Následující příklad ukazuje kód konfigurace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-130">The following example shows the configuration code for the binding.</span></span>  
  
    ```xml  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="d39ba-131">Konfigurace chování, která určuje, zda validátor vlastní uživatelské jméno a heslo slouží k ověření uživatele dvojice název a heslo pro příchozí <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d39ba-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="d39ba-132">Jako podřízené [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="d39ba-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="d39ba-133">Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="d39ba-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="d39ba-134">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu a sadu `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="d39ba-135">Přidat [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="d39ba-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="d39ba-136">Přidat [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) k [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="d39ba-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="d39ba-137">Nastavte `userNamePasswordValidationMode` k `Custom`.</span><span class="sxs-lookup"><span data-stu-id="d39ba-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="d39ba-138">Pokud `userNamePasswordValidationMode` hodnota není nastavena, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá ověřování systému Windows místo validátoru vlastního uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="d39ba-138">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="d39ba-139">Nastavte `customUserNamePasswordValidatorType` typu, který představuje validátor vaše vlastní uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="d39ba-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="d39ba-140">Následující příklad ukazuje `<serviceCredentials>` fragment k tomuto bodu.</span><span class="sxs-lookup"><span data-stu-id="d39ba-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="d39ba-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="d39ba-141">Example</span></span>  
 <span data-ttu-id="d39ba-142">Následující příklad kódu ukazuje, jak vytvořit vlastní uživatelská jména a hesla validátoru.</span><span class="sxs-lookup"><span data-stu-id="d39ba-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="d39ba-143">Nepoužívejte kód, který přepíše <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="d39ba-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="d39ba-144">Nahraďte kód vaše vlastní uživatelské jméno a heslo schéma ověřování, které mohou zahrnovat načítání dvojice název a heslo uživatele z databáze.</span><span class="sxs-lookup"><span data-stu-id="d39ba-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d39ba-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="d39ba-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="d39ba-146">Postupy: použití poskytovatele členství prostředí ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d39ba-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="d39ba-147">Ověřování</span><span class="sxs-lookup"><span data-stu-id="d39ba-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
