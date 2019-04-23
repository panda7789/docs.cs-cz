---
title: 'Postupy: Vytvoření vlastní zásady autorizace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 05130e809356369ee2b43d9af86acf69fe527e9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295416"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="ae1ae-102">Postupy: Vytvoření vlastní zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="ae1ae-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="ae1ae-103">Infrastruktura modelu Identity ve Windows Communication Foundation (WCF) podporuje model založený na deklaraci identity autorizace.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="ae1ae-104">Extrahuje z tokenů, volitelně zpracovává vlastní zásady autorizace a pak umístit do deklarace identity <xref:System.IdentityModel.Policy.AuthorizationContext> , pak se dají prozkoumat pro autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="ae1ae-105">Vlastní zásady je možné získat deklarace identity z příchozí tokeny deklarací, aplikací.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="ae1ae-106">Tímto způsobem může být izolované aplikační vrstvu z podrobností na různé deklarace obsluhuje různé typy tokenů, které podporuje WCF.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="ae1ae-107">Toto téma ukazuje, jak implementovat vlastní zásady autorizace a tom, jak přidat tuto zásadu do kolekce zásady používané službou.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="ae1ae-108">Chcete-li implementovat vlastní zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="ae1ae-108">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="ae1ae-109">Definovat novou třídu, která je odvozena z <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="ae1ae-110">Implementovat jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> vlastnost generování jedinečného řetězce v konstruktoru pro třídu a vrácení tohoto řetězce při každém přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="ae1ae-111">Implementovat jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> vlastnost tak, že vrací <xref:System.IdentityModel.Claims.ClaimSet> , která představuje zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="ae1ae-112">Může se jednat `ClaimSet` integrovaná nebo aplikace, která představuje `ClaimSet` (například `ClaimSet` vrácené statickou <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="ae1ae-113">Implementace <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> způsob, jak je popsáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="ae1ae-114">Chcete-li implementovat metodu vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="ae1ae-114">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="ae1ae-115">Dva parametry jsou předány do této metody: instance <xref:System.IdentityModel.Policy.EvaluationContext> třídy a odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="ae1ae-116">Pokud přidá vlastní zásady autorizace <xref:System.IdentityModel.Claims.ClaimSet> instance bez ohledu na aktuální obsah <xref:System.IdentityModel.Policy.EvaluationContext>, pak přidejte `ClaimSet` voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metodu a vrátí `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="ae1ae-117">Vrací `true` označuje infrastruktury autorizace, zásady autorizace se provádí svou práci a není potřeba ji vyvolat znovu.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="ae1ae-118">Pokud zásady autorizace pro vlastní přidá sady deklarací jenom v případě, že jsou již přítomny v určité deklarace identity `EvaluationContext`, vyhledejte tyto deklarace identit tím, že kontroluje `ClaimSet` instancí vrácených <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="ae1ae-119">Pokud deklarace identity jsou k dispozici, přidejte novou deklaraci nastaví voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metoda a, pokud žádné další deklarace identity sady mají být přidána, návratový `true`, označující infrastrukturu ověření, že zásady autorizace dokončí svou práci.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="ae1ae-120">Pokud deklarace identity nejsou k dispozici, vrátí `false`, označující, že by měla být zásady autorizace volána znovu Pokud jiné zásady autorizace přidat další deklarace identity, které mají `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="ae1ae-121">Ve složitějších scénářích zpracování, druhý parametr <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda se používá k uložení proměnné stavu, který infrastruktury autorizace předá zpět při každé následné volání <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metodu pro konkrétní hodnocení.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="ae1ae-122">Chcete-li určit vlastní zásady autorizace prostřednictvím konfigurace</span><span class="sxs-lookup"><span data-stu-id="ae1ae-122">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="ae1ae-123">Zadejte typ zásad autorizace v `policyType` atribut `add` element v `authorizationPolicies` prvek v `serviceAuthorization` elementu.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
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
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="ae1ae-124">Chcete-li určit vlastní zásady autorizace prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-124">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="ae1ae-125">Vytvoření <xref:System.Collections.Generic.List%601> z <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="ae1ae-126">Vytvoření instance zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-126">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="ae1ae-127">Přidejte do seznamu instance zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-127">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="ae1ae-128">Zopakujte kroky 2 a 3 pro každou zásadu autorizace.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="ae1ae-129">Přiřadit verze jen pro čtení seznamu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="ae1ae-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae1ae-130">Example</span></span>  
 <span data-ttu-id="ae1ae-131">Následující příklad ukazuje kompletní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementace.</span><span class="sxs-lookup"><span data-stu-id="ae1ae-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ae1ae-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae1ae-132">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="ae1ae-133">Postupy: Porovnání deklarací</span><span class="sxs-lookup"><span data-stu-id="ae1ae-133">How to: Compare Claims</span></span>](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [<span data-ttu-id="ae1ae-134">Postupy: Vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="ae1ae-134">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="ae1ae-135">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="ae1ae-135">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
