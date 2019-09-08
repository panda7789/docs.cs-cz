---
title: 'Postupy: Vytvoření vlastní zásady autorizace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 5d5268cd2171bdccc3885cd599fdc8c277e61aa4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795712"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="6c6ab-102">Postupy: Vytvoření vlastní zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="6c6ab-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="6c6ab-103">Infrastruktura modelu identity ve službě Windows Communication Foundation (WCF) podporuje autorizační model založený na deklaracích identity.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="6c6ab-104">Deklarace identity se extrahují z tokenů, volitelně se zpracovávají pomocí vlastních zásad autorizace, a <xref:System.IdentityModel.Policy.AuthorizationContext> pak se umístí do služby, která se pak dá prozkoumat, aby se mohla ověřit autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="6c6ab-105">Vlastní zásady se dají použít k transformaci deklarací z příchozích tokenů na deklarace identity, které aplikace očekává.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="6c6ab-106">Tímto způsobem lze vrstvu aplikace izolované z podrobností o rozdílných deklaracích, které jsou obsluhovány různými typy tokenů, které WCF podporuje.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="6c6ab-107">V tomto tématu se dozvíte, jak implementovat vlastní zásady autorizace a jak tyto zásady přidat do kolekce zásad používané službou.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="6c6ab-108">Implementace vlastních zásad autorizace</span><span class="sxs-lookup"><span data-stu-id="6c6ab-108">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="6c6ab-109">Definujte novou třídu, která je odvozena <xref:System.IdentityModel.Policy.IAuthorizationPolicy>z.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="6c6ab-110">Implementujte vlastnost jen <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> pro čtení vygenerováním jedinečného řetězce v konstruktoru pro třídu a vrácením tohoto řetězce vždy, když je přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="6c6ab-111">Implementujte vlastnost <xref:System.IdentityModel.Claims.ClaimSet> , která <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> je jen pro čtení, vrácením reprezentujícího vystavitele zásady.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="6c6ab-112">Může to být `ClaimSet` , který představuje aplikaci nebo `ClaimSet` integrovanou `ClaimSet` (například vrácená statickou <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="6c6ab-113">Implementujte <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metodu, jak je popsáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="6c6ab-114">Implementace metody Evaluate</span><span class="sxs-lookup"><span data-stu-id="6c6ab-114">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="6c6ab-115">Do této metody jsou předány dva parametry: instance <xref:System.IdentityModel.Policy.EvaluationContext> třídy a odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="6c6ab-116">Pokud vlastní zásady autorizace přidávají <xref:System.IdentityModel.Claims.ClaimSet> instance bez ohledu na aktuální obsah rozhraní <xref:System.IdentityModel.Policy.EvaluationContext>, pak je <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> přidejte `ClaimSet` voláním metody a návratem `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="6c6ab-117">Při `true` návratu se znamená, že autorizační infrastruktura vykonala svoji práci a není nutné ji volat znovu.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="6c6ab-118">Pokud vlastní zásady autorizace přidávají sady deklarací identity jenom v případě `EvaluationContext`, že některé deklarace identity už v portálu existují, pak tyto deklarace `ClaimSet` vyhledáte kontrolou instancí <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> vrácených vlastností.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="6c6ab-119">Pokud jsou deklarace identity k dispozici, přidejte nové sady deklarací voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metody a, pokud žádné další sady deklarací nechcete přidat, vraťte `true`se, což znamená, že autorizační infrastruktura dokončila svoji práci.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="6c6ab-120">Pokud nejsou deklarace identity k dispozici, `false`vraťte se, aby se zásady autorizace znovu vyvolaly, pokud jiné zásady autorizace přidají `EvaluationContext`do. další sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="6c6ab-121">V složitějších scénářích zpracování se druhý parametr <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody používá k uložení proměnné stavu, která se během každého následného volání <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody vrátí do metody pro určité vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="6c6ab-122">Určení vlastních zásad autorizace prostřednictvím konfigurace</span><span class="sxs-lookup"><span data-stu-id="6c6ab-122">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="6c6ab-123">Zadejte typ vlastní zásady autorizace `policyType` v atributu `add` v `authorizationPolicies` `serviceAuthorization` elementu elementu v elementu.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="6c6ab-124">Určení vlastních zásad autorizace prostřednictvím kódu</span><span class="sxs-lookup"><span data-stu-id="6c6ab-124">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="6c6ab-125"><xref:System.Collections.Generic.List%601> Vytvořte .<xref:System.IdentityModel.Policy.IAuthorizationPolicy></span><span class="sxs-lookup"><span data-stu-id="6c6ab-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="6c6ab-126">Vytvořte instanci vlastních zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-126">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="6c6ab-127">Přidejte do seznamu instanci zásady autorizace.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-127">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="6c6ab-128">Opakujte kroky 2 a 3 pro každou vlastní zásadu autorizace.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="6c6ab-129">Přiřaďte k <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> vlastnosti verzi seznamu určenou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="6c6ab-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c6ab-130">Example</span></span>  
 <span data-ttu-id="6c6ab-131">Následující příklad ukazuje kompletní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementaci.</span><span class="sxs-lookup"><span data-stu-id="6c6ab-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6c6ab-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c6ab-132">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="6c6ab-133">Postupy: Porovnat deklarace identity</span><span class="sxs-lookup"><span data-stu-id="6c6ab-133">How to: Compare Claims</span></span>](how-to-compare-claims.md)
- [<span data-ttu-id="6c6ab-134">Postupy: Vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="6c6ab-134">How to: Create a Custom Authorization Manager for a Service</span></span>](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="6c6ab-135">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="6c6ab-135">Authorization Policy</span></span>](../samples/authorization-policy.md)
