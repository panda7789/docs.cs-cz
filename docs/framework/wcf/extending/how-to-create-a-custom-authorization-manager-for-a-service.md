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
ms.openlocfilehash: e3d0143cd68bc94c6ff07e65ca5a3c8971b45f23
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337835"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="cba8d-102">Postupy: Vytvoření vlastního správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="cba8d-102">How to: Create a Custom Authorization Manager for a Service</span></span>
<span data-ttu-id="cba8d-103">Infrastruktura modelu identit ve Windows Communication Foundation (WCF) podporuje model extensible autorizace na základě rolí.</span><span class="sxs-lookup"><span data-stu-id="cba8d-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="cba8d-104">Extrahuje z tokenů a volitelně zpracování pomocí zásad autorizace a pak umístit do deklarace identity <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="cba8d-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="cba8d-105">Správce autorizací prozkoumá deklarace identity v <xref:System.IdentityModel.Policy.AuthorizationContext> pro autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="cba8d-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>  
  
 <span data-ttu-id="cba8d-106">Ve výchozím nastavení, jsou prováděny rozhodování o autorizaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídy, ale tato rozhodnutí lze přepsat tak, že vytvoříte vlastní autorizace správce.</span><span class="sxs-lookup"><span data-stu-id="cba8d-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="cba8d-107">Chcete-li vytvořit vlastní autorizace správce, vytvořit třídu, která je odvozena z <xref:System.ServiceModel.ServiceAuthorizationManager> a implementovat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cba8d-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="cba8d-108">Rozhodování o autorizaci se provádí v <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodu, která vrací `true` když se udělí přístup k a `false` kdy byl odepřen přístup.</span><span class="sxs-lookup"><span data-stu-id="cba8d-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>  
  
 <span data-ttu-id="cba8d-109">Pokud je rozhodnutí o autorizaci závisí na obsahu těla zprávy, použijte <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cba8d-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>  
  
 <span data-ttu-id="cba8d-110">Kvůli problémům s výkonem Pokud je to možné byste měli přepracovat vaší aplikace tak, aby rozhodnutí o autorizaci nevyžaduje přístup k textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="cba8d-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>  
  
 <span data-ttu-id="cba8d-111">V kódu nebo konfigurace lze provést registraci Správce autorizace pro službu.</span><span class="sxs-lookup"><span data-stu-id="cba8d-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>  
  
### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="cba8d-112">Chcete-li vytvořit vlastní autorizace správce</span><span class="sxs-lookup"><span data-stu-id="cba8d-112">To create a custom authorization manager</span></span>  
  
1. <span data-ttu-id="cba8d-113">Odvodit třídu z <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="cba8d-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2. <span data-ttu-id="cba8d-114">Přepsat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metody.</span><span class="sxs-lookup"><span data-stu-id="cba8d-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>  
  
     <span data-ttu-id="cba8d-115">Použití <xref:System.ServiceModel.OperationContext> , který je předán <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metodu pro autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="cba8d-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>  
  
     <span data-ttu-id="cba8d-116">Následující příklad kódu používá <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> metody k vyhledání vlastních deklarací identity `http://www.contoso.com/claims/allowedoperation` provádět rozhodnutí o autorizaci.</span><span class="sxs-lookup"><span data-stu-id="cba8d-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="cba8d-117">Zaregistrovat vlastní autorizace Manageru pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="cba8d-117">To register a custom authorization manager using code</span></span>  
  
1. <span data-ttu-id="cba8d-118">Vytvoření instance vlastní autorizace správce a přiřaďte ho k <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cba8d-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>  
  
     <span data-ttu-id="cba8d-119"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Lze přistupovat pomocí <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cba8d-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>  
  
     <span data-ttu-id="cba8d-120">Následující kód například registrů `MyServiceAuthorizationManager` Správce autorizace.</span><span class="sxs-lookup"><span data-stu-id="cba8d-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="cba8d-121">Zaregistrovat vlastní autorizace Manageru pomocí konfigurace</span><span class="sxs-lookup"><span data-stu-id="cba8d-121">To register a custom authorization manager using configuration</span></span>  
  
1. <span data-ttu-id="cba8d-122">Otevřete konfigurační soubor služby.</span><span class="sxs-lookup"><span data-stu-id="cba8d-122">Open the configuration file for the service.</span></span>  
  
2. <span data-ttu-id="cba8d-123">Přidat [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="cba8d-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span></span>  
  
     <span data-ttu-id="cba8d-124">K [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), přidejte `serviceAuthorizationManagerType` atribut a nastavte její hodnotu na typ, který představuje správce autorizace.</span><span class="sxs-lookup"><span data-stu-id="cba8d-124">To the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>  
  
3. <span data-ttu-id="cba8d-125">Přidáte vazbu, která zajišťuje zabezpečení komunikace mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="cba8d-125">Add a binding that secures the communication between the client and service.</span></span>  
  
     <span data-ttu-id="cba8d-126">Vazby, který je vybrán pro tuto komunikaci určuje deklarace identity, které jsou přidány do <xref:System.IdentityModel.Policy.AuthorizationContext>, který používá správce autorizace pro autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="cba8d-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="cba8d-127">Další podrobnosti o vazeb poskytovaných systémem najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="cba8d-127">For more details about the system-provided bindings, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
4. <span data-ttu-id="cba8d-128">Přidružit chování koncového bodu služby, tak, že přidáte [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element a nastavte hodnotu `behaviorConfiguration` atributu na hodnotu atributu název [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="cba8d-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
     <span data-ttu-id="cba8d-129">Další informace o konfiguraci koncového bodu služby, najdete v části [jak: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="cba8d-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
     <span data-ttu-id="cba8d-130">Následující ukázkový kód registruje Správce autorizace `Samples.MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="cba8d-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>  
  
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
    >  <span data-ttu-id="cba8d-131">Všimněte si, že při zadání Třída serviceAuthorizationManagerType řetězec musí obsahovat plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="cba8d-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="cba8d-132">čárku a název sestavení, ve kterém je typ definován.</span><span class="sxs-lookup"><span data-stu-id="cba8d-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="cba8d-133">Pokud vynecháte název sestavení, se pokusí načíst typ z System.ServiceModel.dll WCF.</span><span class="sxs-lookup"><span data-stu-id="cba8d-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cba8d-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="cba8d-134">Example</span></span>  
 <span data-ttu-id="cba8d-135">Následující příklad kódu ukazuje základní implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídu, která zahrnuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cba8d-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="cba8d-136">Příklad kódu zkontroluje <xref:System.IdentityModel.Policy.AuthorizationContext> vlastní deklarace identity a vrátí `true` při prostředků pro tuto vlastní deklarace identity odpovídá hodnotě akce z <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="cba8d-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="cba8d-137">Pro více úplnou implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> najdete v tématu [zásad autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="cba8d-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cba8d-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cba8d-138">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="cba8d-139">Zásada autorizace</span><span class="sxs-lookup"><span data-stu-id="cba8d-139">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
