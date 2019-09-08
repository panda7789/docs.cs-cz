---
title: 'Postupy: Vytvoření vlastního správce autorizací pro službu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: 9c28cb81b78f80505cfcf5f7e4dfdba083bd0793
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797110"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="532e9-102">Postupy: Vytvoření vlastního správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="532e9-102">How to: Create a Custom Authorization Manager for a Service</span></span>

<span data-ttu-id="532e9-103">Infrastruktura modelu identity ve službě Windows Communication Foundation (WCF) podporuje rozšiřitelný autorizační model založený na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="532e9-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="532e9-104">Deklarace identity se extrahují z tokenů a volitelně se zpracovávají pomocí vlastních zásad autorizace a <xref:System.IdentityModel.Policy.AuthorizationContext>pak se umístí do.</span><span class="sxs-lookup"><span data-stu-id="532e9-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="532e9-105">Správce autorizací prověřuje deklarace v <xref:System.IdentityModel.Policy.AuthorizationContext> nástroji a provede rozhodnutí o autorizaci.</span><span class="sxs-lookup"><span data-stu-id="532e9-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>

<span data-ttu-id="532e9-106">Ve výchozím nastavení se provádí <xref:System.ServiceModel.ServiceAuthorizationManager> rozhodnutí o autorizaci třídou. Tato rozhodnutí ale můžete přepsat vytvořením vlastního Správce autorizací.</span><span class="sxs-lookup"><span data-stu-id="532e9-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="532e9-107">Chcete-li vytvořit vlastního Správce autorizací, vytvořte třídu, která je <xref:System.ServiceModel.ServiceAuthorizationManager> odvozena <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> z metody a implementovat metodu.</span><span class="sxs-lookup"><span data-stu-id="532e9-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="532e9-108">Autorizační rozhodnutí se provádí v <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodě, která vrací `true` po udělení přístupu a `false` odepření přístupu.</span><span class="sxs-lookup"><span data-stu-id="532e9-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>

<span data-ttu-id="532e9-109">Pokud autorizační rozhodnutí závisí na obsahu zprávy, použijte <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="532e9-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>

<span data-ttu-id="532e9-110">Z důvodu problémů s výkonem byste měli, pokud je to možné, změnit návrh aplikace tak, aby autorizační rozhodnutí nevyžadovalo přístup k textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="532e9-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>

<span data-ttu-id="532e9-111">Registraci vlastního Správce autorizací pro službu je možné provést v kódu nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="532e9-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>

### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="532e9-112">Vytvoření vlastního Správce autorizací</span><span class="sxs-lookup"><span data-stu-id="532e9-112">To create a custom authorization manager</span></span>

1. <span data-ttu-id="532e9-113">Odvodit třídu od <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="532e9-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. <span data-ttu-id="532e9-114">Přepsat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metody.</span><span class="sxs-lookup"><span data-stu-id="532e9-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>

    <span data-ttu-id="532e9-115">K provedení autorizačních rozhodnutí použijte <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metodu ,kterájepředánametodě.<xref:System.ServiceModel.OperationContext></span><span class="sxs-lookup"><span data-stu-id="532e9-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>

    <span data-ttu-id="532e9-116">Následující příklad kódu používá <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> metodu k vyhledání vlastní deklarace identity `http://www.contoso.com/claims/allowedoperation` k rozhodnutí o autorizaci.</span><span class="sxs-lookup"><span data-stu-id="532e9-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="532e9-117">Registrace vlastního Správce autorizací pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="532e9-117">To register a custom authorization manager using code</span></span>

1. <span data-ttu-id="532e9-118">Vytvořte instanci vlastního Správce autorizací a přiřaďte ji k <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="532e9-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>

    <span data-ttu-id="532e9-119">K <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> poli lze použít <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="532e9-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>

    <span data-ttu-id="532e9-120">Následující příklad kódu registruje `MyServiceAuthorizationManager` vlastního Správce autorizací.</span><span class="sxs-lookup"><span data-stu-id="532e9-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="532e9-121">Registrace vlastního Správce autorizací pomocí konfigurace</span><span class="sxs-lookup"><span data-stu-id="532e9-121">To register a custom authorization manager using configuration</span></span>

1. <span data-ttu-id="532e9-122">Otevřete konfigurační soubor pro službu.</span><span class="sxs-lookup"><span data-stu-id="532e9-122">Open the configuration file for the service.</span></span>

2. <span data-ttu-id="532e9-123">Přidejte [> serviceAuthorization do > chování. \<](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) [ \<](../../configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="532e9-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md).</span></span>

    <span data-ttu-id="532e9-124">`serviceAuthorizationManagerType` [Do serviceAuthorization > přidejte atribut a nastavte jeho hodnotu na typ, který představuje vlastního Správce autorizací. \<](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="532e9-124">To the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>

3. <span data-ttu-id="532e9-125">Přidejte vazbu, která zabezpečuje komunikaci mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="532e9-125">Add a binding that secures the communication between the client and service.</span></span>

    <span data-ttu-id="532e9-126">Vazba, která je zvolena pro tuto komunikaci <xref:System.IdentityModel.Policy.AuthorizationContext>, určuje deklarace identity, které jsou přidány do, který vlastní Správce autorizací používá k rozhodování o autorizaci.</span><span class="sxs-lookup"><span data-stu-id="532e9-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="532e9-127">Další informace o vazbách poskytovaných systémem najdete v tématu [vazby poskytované systémem](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="532e9-127">For more details about the system-provided bindings, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

4. <span data-ttu-id="532e9-128">Přidružte chování ke koncovému bodu služby přidáním `behaviorConfiguration` [ \<prvku > služby](../../configure-apps/file-schema/wcf/service.md) a nastavte hodnotu atributu na [ \<](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) hodnotu atributu název pro > elementu behavior.</span><span class="sxs-lookup"><span data-stu-id="532e9-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    <span data-ttu-id="532e9-129">Další informace o konfiguraci koncového bodu služby najdete v [tématu How to: V konfiguraci](../feature-details/how-to-create-a-service-endpoint-in-configuration.md)vytvořte koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="532e9-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>

    <span data-ttu-id="532e9-130">Následující příklad kódu registruje vlastního správce `Samples.MyServiceAuthorizationManager`autorizací.</span><span class="sxs-lookup"><span data-stu-id="532e9-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <services>
          <service
              name="Microsoft.ServiceModel.Samples.CalculatorService"
              behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <endpoint address=""
                      binding="wsHttpBinding_Calculator"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
          </service>
        </services>
        <bindings>
          <WSHttpBinding>
           <binding name = "wsHttpBinding_Calculator">
             <security mode="Message">
               <message clientCredentialType="Windows"/>
             </security>
            </binding>
          </WSHttpBinding>
        </bindings>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />
             </behavior>
         </serviceBehaviors>
       </behaviors>
      </system.serviceModel>
    </configuration>
    ```

    > [!WARNING]
    > <span data-ttu-id="532e9-131">Všimněte si, že když zadáte serviceAuthorizationManagerType, řetězec musí obsahovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="532e9-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="532e9-132">čárka a název sestavení, ve kterém je definován typ.</span><span class="sxs-lookup"><span data-stu-id="532e9-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="532e9-133">Pokud necháte název sestavení, služba WCF se pokusí načíst typ ze souboru System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="532e9-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>

## <a name="example"></a><span data-ttu-id="532e9-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="532e9-134">Example</span></span>

<span data-ttu-id="532e9-135">Následující příklad kódu ukazuje základní implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídy, která obsahuje <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> přepsání metody.</span><span class="sxs-lookup"><span data-stu-id="532e9-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="532e9-136">Vzorový kód kontroluje vlastní deklaraci <xref:System.IdentityModel.Policy.AuthorizationContext> identity a vrátí `true` , když prostředek pro tuto vlastní deklaraci identity odpovídá hodnotě akce z <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="532e9-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="532e9-137">Úplnější implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídy najdete v tématu [zásady autorizace](../samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="532e9-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../samples/authorization-policy.md).</span></span>

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a><span data-ttu-id="532e9-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="532e9-138">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="532e9-139">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="532e9-139">Authorization Policy</span></span>](../samples/authorization-policy.md)
