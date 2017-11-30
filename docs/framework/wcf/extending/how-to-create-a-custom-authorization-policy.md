---
title: "Postupy: Vytvoření vlastní zásady autorizace"
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
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8a4a458d49e7ec3db3e80202e53e3a1f264d207b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="f79ca-102">Postupy: Vytvoření vlastní zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="f79ca-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="f79ca-103">Infrastruktura Identity modelu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporuje model na základě deklarace autorizace.</span><span class="sxs-lookup"><span data-stu-id="f79ca-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a claim-based authorization model.</span></span> <span data-ttu-id="f79ca-104">Deklarace identity jsou extrahovány z tokenů, volitelně zpracovává vlastní zásady autorizace a pak umístit do <xref:System.IdentityModel.Policy.AuthorizationContext> , pak může být prověřen pro autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="f79ca-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="f79ca-105">Vlastní zásadu lze použít na transformaci deklarací od příchozí tokeny do očekávaného aplikaci deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="f79ca-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="f79ca-106">Tímto způsobem může být aplikační vrstvu izolované od podrobnosti o různé deklarace obsloužených token různé typy, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje.</span><span class="sxs-lookup"><span data-stu-id="f79ca-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports.</span></span> <span data-ttu-id="f79ca-107">Toto téma ukazuje, jak implementovat vlastní zásady autorizace a postup přidání ke kolekci zásady, které používá služba pro tuto zásadu.</span><span class="sxs-lookup"><span data-stu-id="f79ca-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="f79ca-108">Chcete-li implementovat vlastní zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="f79ca-108">To implement a custom authorization policy</span></span>  
  
1.  <span data-ttu-id="f79ca-109">Zadejte novou třídu odvozenou od <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="f79ca-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2.  <span data-ttu-id="f79ca-110">Implementace jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> vlastnost generování jedinečného řetězce v konstruktoru pro třídu a vrácení tento řetězec je o přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f79ca-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3.  <span data-ttu-id="f79ca-111">Implementace jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> vlastnost vrácením <xref:System.IdentityModel.Claims.ClaimSet> představující vystavitele zásad.</span><span class="sxs-lookup"><span data-stu-id="f79ca-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="f79ca-112">To může být `ClaimSet` nebo integrované aplikace, která představuje `ClaimSet` (například `ClaimSet` vrácený statických <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f79ca-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4.  <span data-ttu-id="f79ca-113">Implementace <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda, jak je popsáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="f79ca-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="f79ca-114">Chcete-li implementovat metodu hodnocení</span><span class="sxs-lookup"><span data-stu-id="f79ca-114">To implement the Evaluate method</span></span>  
  
1.  <span data-ttu-id="f79ca-115">Jsou dva parametry předané této metodě: instance <xref:System.IdentityModel.Policy.EvaluationContext> třídy a odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="f79ca-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2.  <span data-ttu-id="f79ca-116">Pokud zásady autorizace pro vlastní přidá <xref:System.IdentityModel.Claims.ClaimSet> instance bez ohledu na aktuální obsah <xref:System.IdentityModel.Policy.EvaluationContext>, poté přidat každý `ClaimSet` voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metoda a vraťte se `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f79ca-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="f79ca-117">Vrácení `true` označuje infrastruktury autorizace, že zásady autorizace byla provedena svou práci a nemusí být volán znovu.</span><span class="sxs-lookup"><span data-stu-id="f79ca-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3.  <span data-ttu-id="f79ca-118">Pokud zásady autorizace pro vlastní přidá sad deklarací identit jenom v případě, že jsou již přítomny v určité deklarace identity `EvaluationContext`, vyhledejte těchto deklarací identity tak, že prověří `ClaimSet` instancí vrácených funkcí <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f79ca-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="f79ca-119">Pokud jsou v něm deklarace identity, přidejte novou deklaraci nastaví voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metoda a, pokud žádné další deklarace identity sady mají být přidána, návratový `true`, naznačuje infrastruktury autorizace, zásady autorizace byla dokončena svou práci.</span><span class="sxs-lookup"><span data-stu-id="f79ca-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="f79ca-120">Pokud deklarace identity nejsou, vrátí `false`, indikující, že zásady autorizace by se měla volat znovu Pokud jiné zásady autorizace přidat více deklarací identity, které mají `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="f79ca-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4.  <span data-ttu-id="f79ca-121">Ve složitějších scénářích zpracování, druhý parametr <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda se používá k ukládání stavu proměnné, která infrastruktury autorizace předá zpět při každém následných volání <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda konkrétní zkušební verze.</span><span class="sxs-lookup"><span data-stu-id="f79ca-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="f79ca-122">Chcete-li určit vlastní zásady autorizace prostřednictvím konfigurace</span><span class="sxs-lookup"><span data-stu-id="f79ca-122">To specify a custom authorization policy through configuration</span></span>  
  
1.  <span data-ttu-id="f79ca-123">Zadejte typ zásad autorizace v `policyType` atribut `add` element v `authorizationPolicies` element v `serviceAuthorization` elementu.</span><span class="sxs-lookup"><span data-stu-id="f79ca-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>         
            <add policyType="Samples.MyAuthorizationPolicy"  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="f79ca-124">Chcete-li určit vlastní zásady autorizace prostřednictvím kódu</span><span class="sxs-lookup"><span data-stu-id="f79ca-124">To specify a custom authorization policy through code</span></span>  
  
1.  <span data-ttu-id="f79ca-125">Vytvoření <xref:System.Collections.Generic.List%601> z <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="f79ca-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2.  <span data-ttu-id="f79ca-126">Vytvoření instance zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="f79ca-126">Create an instance of the custom authorization policy.</span></span>  
  
3.  <span data-ttu-id="f79ca-127">Přidejte do seznamu instance zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="f79ca-127">Add the authorization policy instance to the list.</span></span>  
  
4.  <span data-ttu-id="f79ca-128">Opakujte kroky 2 a 3 pro každý vlastní zásady autorizace.</span><span class="sxs-lookup"><span data-stu-id="f79ca-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5.  <span data-ttu-id="f79ca-129">Přiřadit pouze ke čtení verzi v seznamu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f79ca-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="f79ca-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="f79ca-130">Example</span></span>  
 <span data-ttu-id="f79ca-131">Následující příklad ukazuje úplná <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementace.</span><span class="sxs-lookup"><span data-stu-id="f79ca-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f79ca-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f79ca-132">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="f79ca-133">Postupy: porovnávání deklarací</span><span class="sxs-lookup"><span data-stu-id="f79ca-133">How to: Compare Claims</span></span>](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [<span data-ttu-id="f79ca-134">Postupy: vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="f79ca-134">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="f79ca-135">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="f79ca-135">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
