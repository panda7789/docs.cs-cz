---
title: 'Postupy: Použití validátoru vlastního uživatelského jména a hesla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 7df6ec57204990066ce59700e5c2582701f2a81a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045913"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="612e6-102">Postupy: Použití validátoru vlastního uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="612e6-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="612e6-103">Ve výchozím nastavení platí, že když se pro ověřování používá uživatelské jméno a heslo, Windows Communication Foundation (WCF) použije Windows k ověření uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="612e6-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="612e6-104">WCF však umožňuje vlastní uživatelské jméno a ověřovací schémata hesla, označované také jako *validátory*.</span><span class="sxs-lookup"><span data-stu-id="612e6-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="612e6-105">Chcete-li začlenit vlastní validátor uživatelského jména a hesla, vytvořte třídu, která <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> je odvozena z a poté ji nakonfigurujte.</span><span class="sxs-lookup"><span data-stu-id="612e6-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="612e6-106">Ukázkovou aplikaci najdete v tématu [validátor hesla uživatelského jména](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="612e6-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="612e6-107">Vytvoření vlastního validátoru uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="612e6-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="612e6-108">Vytvořte třídu, která je odvozena <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>z.</span><span class="sxs-lookup"><span data-stu-id="612e6-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="612e6-109">Implementujte vlastní schéma ověřování přepsáním <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="612e6-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="612e6-110">Nepoužívejte kód v následujícím příkladu, který Přepisuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="612e6-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="612e6-111">Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.</span><span class="sxs-lookup"><span data-stu-id="612e6-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="612e6-112">Chcete-li vrátit chyby ověřování zpět do klienta, vyvolejte <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> v metodě.</span><span class="sxs-lookup"><span data-stu-id="612e6-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="612e6-113">Konfigurace služby tak, aby používala vlastní validátor uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="612e6-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="612e6-114">Nakonfigurujte vazbu, která používá zabezpečení zpráv prostřednictvím jakéhokoli přenosu nebo zabezpečení na úrovni přenosu přes HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="612e6-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="612e6-115">Pokud používáte zabezpečení zpráv, přidejte jednu z systémových vazeb, jako je [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), nebo `UserName` [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , která podporuje zabezpečení zpráv a typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="612e6-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="612e6-116">Pokud používáte zabezpečení na úrovni přenosu přes HTTP (S), přidejte buď [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nebo [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) [ \<BasicHttpBinding >, NetTcpBinding > nebo CustomBinding > ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)který používá protokol HTTP (S) a `Basic` schéma ověřování.</span><span class="sxs-lookup"><span data-stu-id="612e6-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="612e6-117">Když [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] použijete nebo později, můžete použít vlastní validátor uživatelského jména a hesla se zabezpečením zpráv a přenosů.</span><span class="sxs-lookup"><span data-stu-id="612e6-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="612e6-118">Pomocí WinFX se vlastní validátor uživatelského jména a hesla dá použít jenom se zabezpečením zpráv.</span><span class="sxs-lookup"><span data-stu-id="612e6-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="612e6-119">Další informace o použití \<> NetTcpBinding v tomto kontextu najdete v tématu [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="612e6-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>

    1. <span data-ttu-id="612e6-120">V konfiguračním souboru v rámci [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<prvku System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) přidejte vazby > elementu.</span><span class="sxs-lookup"><span data-stu-id="612e6-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="612e6-121">Do části Bindings přidejte prvek [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [> WSHttpBindingneboBasicHttpBinding.\<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="612e6-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="612e6-122">Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: Zadejte vazbu služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="612e6-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="612e6-123">`mode` Nastavte atribut `Message` [ >zabezpečenínebo\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) [> zabezpečenína,nebo.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Transport` `TransportWithMessageCredential`</span><span class="sxs-lookup"><span data-stu-id="612e6-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="612e6-124">`clientCredentialType` Nastavte atribut [ >zprávynebo>přenosu.\<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="612e6-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="612e6-125">Pokud používáte zabezpečení zprávy, nastavte `clientCredentialType` atribut [ \<> zprávy](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na. `UserName`</span><span class="sxs-lookup"><span data-stu-id="612e6-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="612e6-126">Při použití zabezpečení na úrovni přenosu přes HTTP ( `clientCredentialType` S) nastavte atribut [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) `Basic`Transport > nebo [ \<> přenosu](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="612e6-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="612e6-127">Když je služba WCF hostovaná ve službě Internetová informační služba (IIS) pomocí zabezpečení na úrovni přenosu a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> vlastnost je nastavená <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>na, používá vlastní schéma ověřování podmnožinu ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="612e6-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="612e6-128">To znamená, že v tomto scénáři provede služba IIS ověřování systému Windows předtím, než WCF vyvolá vlastní ověřovatel.</span><span class="sxs-lookup"><span data-stu-id="612e6-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="612e6-129">Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: Zadejte vazbu služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="612e6-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="612e6-130">Následující příklad ukazuje konfigurační kód pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="612e6-130">The following example shows the configuration code for the binding.</span></span>

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

2. <span data-ttu-id="612e6-131">Nakonfigurujte chování, které určuje, že se k ověření párů uživatelského jména a hesla pro příchozí <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokeny zabezpečení používá vlastní validátor uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="612e6-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="612e6-132">Jako podřízený [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) [ prvkuSystem.ServiceModel>přidejteprvek>chování.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="612e6-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="612e6-133">Do prvku [> \<chování](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) přidejte [> serviceBehaviors.\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="612e6-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="612e6-134">Přidejte >`name` prvek [chování a nastavte atribut na odpovídající hodnotu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="612e6-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="612e6-135">Přidejte [> ServiceCredentials k chování > elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="612e6-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="612e6-136">Přidejte [> UserNameAuthentication do > ServiceCredentials. \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="612e6-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="612e6-137">`userNamePasswordValidationMode` Nastavte`Custom`na.</span><span class="sxs-lookup"><span data-stu-id="612e6-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="612e6-138">`userNamePasswordValidationMode` Pokud hodnota není nastavená, WCF místo vlastního uživatelského jména a validátoru hesla použije ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="612e6-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="612e6-139">`customUserNamePasswordValidatorType` Nastavte na typ, který představuje vaše vlastní uživatelské jméno a Validátor hesel.</span><span class="sxs-lookup"><span data-stu-id="612e6-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="612e6-140">Následující příklad ukazuje `<serviceCredentials>` fragment na tento bod.</span><span class="sxs-lookup"><span data-stu-id="612e6-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="612e6-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="612e6-141">Example</span></span>

<span data-ttu-id="612e6-142">Následující příklad kódu ukazuje, jak vytvořit vlastní validátor uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="612e6-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="612e6-143">Nepoužívejte kód, který Přepisuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="612e6-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="612e6-144">Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.</span><span class="sxs-lookup"><span data-stu-id="612e6-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="612e6-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="612e6-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="612e6-146">Postupy: Použití poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="612e6-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="612e6-147">Ověřování</span><span class="sxs-lookup"><span data-stu-id="612e6-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
