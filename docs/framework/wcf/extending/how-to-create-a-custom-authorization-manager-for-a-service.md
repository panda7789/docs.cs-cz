---
title: "Postupy: Vytvoření vlastního správce autorizací pro službu"
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
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cba64767aaac4092f3c6103f7417a9d707b9a380
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="da1f9-102">Postupy: Vytvoření vlastního správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="da1f9-102">How to: Create a Custom Authorization Manager for a Service</span></span>
<span data-ttu-id="da1f9-103">Infrastruktura Identity modelu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporuje model extensible autorizace založené na deklaracích identity.</span><span class="sxs-lookup"><span data-stu-id="da1f9-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="da1f9-104">Deklarace identity jsou extrahovány z tokenů a volitelně zpracovává zásady autorizace a pak umístit do <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="da1f9-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="da1f9-105">Správce autorizací prozkoumá deklarací identity ve <xref:System.IdentityModel.Policy.AuthorizationContext> pro autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="da1f9-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>  
  
 <span data-ttu-id="da1f9-106">Ve výchozím nastavení, jsou provedené rozhodnutí o autorizaci <xref:System.ServiceModel.ServiceAuthorizationManager> třída; ale tato rozhodnutí mohou být přepsány vytvoření vlastní ověření správce.</span><span class="sxs-lookup"><span data-stu-id="da1f9-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="da1f9-107">Vytvořit vlastní autorizace správci, vytvořte třídu, která je odvozena z <xref:System.ServiceModel.ServiceAuthorizationManager> a implementovat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="da1f9-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="da1f9-108">Rozhodnutí o autorizaci, které jsou vytvářeny v <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda, která vrátí `true` když je přístup povolen a `false` když byl odepřen přístup.</span><span class="sxs-lookup"><span data-stu-id="da1f9-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>  
  
 <span data-ttu-id="da1f9-109">Pokud rozhodnutí o autorizaci závisí na obsahu textu zprávy, použijte <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="da1f9-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>  
  
 <span data-ttu-id="da1f9-110">Kvůli problémům s výkonem Pokud je to možné jste měli změnit návrh aplikace tak, aby rozhodnutí o autorizaci nevyžaduje přístup k tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="da1f9-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>  
  
 <span data-ttu-id="da1f9-111">Registrace Správce autorizace pro službu lze provést v kódu nebo konfigurace.</span><span class="sxs-lookup"><span data-stu-id="da1f9-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>  
  
### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="da1f9-112">Chcete-li vytvořit vlastní autorizace manager</span><span class="sxs-lookup"><span data-stu-id="da1f9-112">To create a custom authorization manager</span></span>  
  
1.  <span data-ttu-id="da1f9-113">Odvození třídy z <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="da1f9-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  <span data-ttu-id="da1f9-114">Přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="da1f9-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>  
  
     <span data-ttu-id="da1f9-115">Použití <xref:System.ServiceModel.OperationContext> předá do <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metoda pro autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="da1f9-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>  
  
     <span data-ttu-id="da1f9-116">Následující příklad kódu používá <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> metody k vyhledání vlastních deklarací identity `http://www.contoso.com/claims/allowedoperation` aby rozhodnutí o autorizaci.</span><span class="sxs-lookup"><span data-stu-id="da1f9-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="da1f9-117">K registraci manažera autorizace pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="da1f9-117">To register a custom authorization manager using code</span></span>  
  
1.  <span data-ttu-id="da1f9-118">Vytvořte instanci vlastní autorizace správce a přiřaďte ho do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="da1f9-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>  
  
     <span data-ttu-id="da1f9-119"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Lze přistupovat pomocí <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="da1f9-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>  
  
     <span data-ttu-id="da1f9-120">Následující kód například registrů `MyServiceAuthorizationManager` správce vlastní ověřování.</span><span class="sxs-lookup"><span data-stu-id="da1f9-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="da1f9-121">K registraci manažera autorizace pomocí konfigurace</span><span class="sxs-lookup"><span data-stu-id="da1f9-121">To register a custom authorization manager using configuration</span></span>  
  
1.  <span data-ttu-id="da1f9-122">Otevření konfiguračního souboru pro službu.</span><span class="sxs-lookup"><span data-stu-id="da1f9-122">Open the configuration file for the service.</span></span>  
  
2.  <span data-ttu-id="da1f9-123">Přidat [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="da1f9-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span></span>  
  
     <span data-ttu-id="da1f9-124">K [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), přidejte `serviceAuthorizationManagerType` atribut a jeho hodnotu nastavte typ, který představuje správce autorizace.</span><span class="sxs-lookup"><span data-stu-id="da1f9-124">To the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>  
  
3.  <span data-ttu-id="da1f9-125">Přidejte vazbu, které slouží k zabezpečení komunikace mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="da1f9-125">Add a binding that secures the communication between the client and service.</span></span>  
  
     <span data-ttu-id="da1f9-126">Vazba, která je zvolen pro tuto komunikaci určuje deklarace identity, které jsou přidány do <xref:System.IdentityModel.Policy.AuthorizationContext>, který vlastní autorizace manager používá pro autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="da1f9-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="da1f9-127">Další podrobnosti o vazby poskytované systémem najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="da1f9-127">For more details about the system-provided bindings, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
4.  <span data-ttu-id="da1f9-128">Přidružení chování pro koncový bod služby přidáním [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu a nastavte hodnotu `behaviorConfiguration` hodnota název atributu pro atribut [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="da1f9-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
     <span data-ttu-id="da1f9-129">Další informace o konfiguraci koncového bodu služby najdete v tématu [postupy: vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="da1f9-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
     <span data-ttu-id="da1f9-130">Následující ukázkový kód registruje Správce autorizace `Samples.MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="da1f9-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>  
  
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
    >  <span data-ttu-id="da1f9-131">Všimněte si, že pokud zadáte Třída serviceAuthorizationManagerType, řetězec musí obsahovat plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="da1f9-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="da1f9-132">čárku a název sestavení, ve kterém je definovaný typ.</span><span class="sxs-lookup"><span data-stu-id="da1f9-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="da1f9-133">Pokud se název sestavení, se pokusí načíst typ z System.ServiceModel.dll WCF.</span><span class="sxs-lookup"><span data-stu-id="da1f9-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da1f9-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="da1f9-134">Example</span></span>  
 <span data-ttu-id="da1f9-135">Následující příklad kódu ukazuje základní implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídu, která zahrnuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="da1f9-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="da1f9-136">Prozkoumá ukázkový kód <xref:System.IdentityModel.Policy.AuthorizationContext> vlastní deklarace identity a vrátí `true` když prostředek pro tuto vlastní deklarace identity odpovídá hodnotě akce z <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="da1f9-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="da1f9-137">Pro podrobnější implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídy najdete v tématu [zásad autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="da1f9-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="da1f9-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="da1f9-138">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="da1f9-139">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="da1f9-139">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [<span data-ttu-id="da1f9-140">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="da1f9-140">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
