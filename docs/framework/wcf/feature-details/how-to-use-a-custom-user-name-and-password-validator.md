---
title: 'Postupy: Použití validátoru vlastního uživatelského jména a hesla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 5ada34ca2d0d757ea333fed60aef179d6578356c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601176"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="01d76-102">Postupy: Použití validátoru vlastního uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="01d76-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="01d76-103">Ve výchozím nastavení platí, že když se pro ověřování používá uživatelské jméno a heslo, Windows Communication Foundation (WCF) použije Windows k ověření uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="01d76-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="01d76-104">WCF však umožňuje vlastní uživatelské jméno a ověřovací schémata hesla, označované také jako *validátory*.</span><span class="sxs-lookup"><span data-stu-id="01d76-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="01d76-105">Chcete-li začlenit vlastní validátor uživatelského jména a hesla, vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a poté ji nakonfigurujte.</span><span class="sxs-lookup"><span data-stu-id="01d76-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="01d76-106">Ukázkovou aplikaci najdete v tématu [validátor hesla uživatelského jména](../samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="01d76-106">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="01d76-107">Vytvoření vlastního validátoru uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="01d76-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="01d76-108">Vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .</span><span class="sxs-lookup"><span data-stu-id="01d76-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="01d76-109">Implementujte vlastní schéma ověřování přepsáním <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="01d76-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="01d76-110">Nepoužívejte kód v následujícím příkladu, který Přepisuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="01d76-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="01d76-111">Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.</span><span class="sxs-lookup"><span data-stu-id="01d76-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="01d76-112">Chcete-li vrátit chyby ověřování zpět do klienta, vyvolejte <xref:System.ServiceModel.FaultException> v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="01d76-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="01d76-113">Konfigurace služby tak, aby používala vlastní validátor uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="01d76-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="01d76-114">Nakonfigurujte vazbu, která používá zabezpečení zpráv prostřednictvím jakéhokoli přenosu nebo zabezpečení na úrovni přenosu přes HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="01d76-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="01d76-115">Pokud používáte zabezpečení zpráv, přidejte jednu z systémových vazeb, jako je například [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) nebo, [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) která podporuje zabezpečení zprávy a `UserName` typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="01d76-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="01d76-116">Pokud používáte zabezpečení na úrovni přenosu přes protokol HTTP (S), přidejte buď [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) nebo [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) , a, [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) který používá protokol HTTP, a `Basic` schéma ověřování.</span><span class="sxs-lookup"><span data-stu-id="01d76-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="01d76-117">Při použití .NET Framework 3,5 nebo novějších verzí můžete používat vlastní validátor uživatelského jména a hesla se zabezpečením zpráv a přenosů.</span><span class="sxs-lookup"><span data-stu-id="01d76-117">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="01d76-118">Pomocí WinFX se vlastní validátor uživatelského jména a hesla dá použít jenom se zabezpečením zpráv.</span><span class="sxs-lookup"><span data-stu-id="01d76-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="01d76-119">Další informace o použití \<netTcpBinding> v tomto kontextu naleznete v tématu [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="01d76-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="01d76-120">V konfiguračním souboru, pod [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) prvkem, přidejte [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span><span class="sxs-lookup"><span data-stu-id="01d76-120">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="01d76-121">Přidejte [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) element or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) do oddílu Bindings.</span><span class="sxs-lookup"><span data-stu-id="01d76-121">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="01d76-122">Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="01d76-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="01d76-123">Nastavte `mode` atribut [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) nebo [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na `Message` , `Transport` nebo `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="01d76-123">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="01d76-124">Nastavte `clientCredentialType` atribut [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) nebo [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="01d76-124">Set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="01d76-125">Pokud používáte zabezpečení zprávy, nastavte `clientCredentialType` atribut na [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) `UserName` .</span><span class="sxs-lookup"><span data-stu-id="01d76-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="01d76-126">Při použití zabezpečení na úrovni přenosu přes HTTP (S) nastavte `clientCredentialType` atribut [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) nebo [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) na `Basic` .</span><span class="sxs-lookup"><span data-stu-id="01d76-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="01d76-127">Když je služba WCF hostovaná ve službě Internetová informační služba (IIS) pomocí zabezpečení na úrovni přenosu a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> vlastnost je nastavená na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> , používá vlastní schéma ověřování podmnožinu ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="01d76-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="01d76-128">To znamená, že v tomto scénáři provede služba IIS ověřování systému Windows předtím, než WCF vyvolá vlastní ověřovatel.</span><span class="sxs-lookup"><span data-stu-id="01d76-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="01d76-129">Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="01d76-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="01d76-130">Následující příklad ukazuje konfigurační kód pro vazbu:</span><span class="sxs-lookup"><span data-stu-id="01d76-130">The following example shows the configuration code for the binding:</span></span>

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

2. <span data-ttu-id="01d76-131">Nakonfigurujte chování, které určuje, že se k ověření párů uživatelského jména a hesla pro příchozí tokeny zabezpečení používá vlastní validátor uživatelského jména a hesla <xref:System.IdentityModel.Tokens.UserNameSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="01d76-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="01d76-132">Jako podřízený [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) prvek elementu přidejte [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="01d76-132">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="01d76-133">Přidejte [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) k [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="01d76-133">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="01d76-134">Přidejte [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01d76-134">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="01d76-135">Přidejte [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) k [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="01d76-135">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="01d76-136">Přidejte [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) do [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="01d76-136">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="01d76-137">Nastavte na `userNamePasswordValidationMode` `Custom` .</span><span class="sxs-lookup"><span data-stu-id="01d76-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="01d76-138">Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF místo vlastního uživatelského jména a validátoru hesla použije ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="01d76-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="01d76-139">Nastavte na `customUserNamePasswordValidatorType` typ, který představuje vaše vlastní uživatelské jméno a Validátor hesel.</span><span class="sxs-lookup"><span data-stu-id="01d76-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="01d76-140">Následující příklad ukazuje `<serviceCredentials>` fragment do tohoto bodu:</span><span class="sxs-lookup"><span data-stu-id="01d76-140">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="01d76-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d76-141">Example</span></span>

<span data-ttu-id="01d76-142">Následující příklad kódu ukazuje, jak vytvořit vlastní validátor uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="01d76-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="01d76-143">Nepoužívejte kód, který Přepisuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="01d76-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="01d76-144">Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.</span><span class="sxs-lookup"><span data-stu-id="01d76-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="01d76-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="01d76-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="01d76-146">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="01d76-146">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="01d76-147">Authentication</span><span class="sxs-lookup"><span data-stu-id="01d76-147">Authentication</span></span>](authentication-in-wcf.md)
