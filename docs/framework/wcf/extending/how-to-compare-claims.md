---
title: "Postupy: Porovnávání deklarací"
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
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf7a621a7aa457b2993c761caa2ad576d216638b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="ea942-102">Postupy: Porovnávání deklarací</span><span class="sxs-lookup"><span data-stu-id="ea942-102">How to: Compare Claims</span></span>
<span data-ttu-id="ea942-103">Infrastruktura Identity modelu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] se používá k provádění kontroly autorizace.</span><span class="sxs-lookup"><span data-stu-id="ea942-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used to perform authorization checking.</span></span> <span data-ttu-id="ea942-104">Běžné úlohy jako takový je k porovnání deklarací identity v kontextu autorizace deklarací potřeba provést požadovanou akci nebo přístupu k požadovanému zdroji.</span><span class="sxs-lookup"><span data-stu-id="ea942-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="ea942-105">Toto téma popisuje, jak má být porovnán nároky, včetně typů předdefinované a vlastní deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="ea942-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ea942-106">infrastruktury modelu Identity, najdete v části [správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="ea942-106"> the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="ea942-107">Porovnání deklarace identity spočívá v porovnání tři části deklarace (typ práva a prostředků) proti stejné části v jiné deklarace identity, pokud chcete zobrazit, pokud jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="ea942-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="ea942-108">Podívejte se na téma v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ea942-108">See the following example.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 <span data-ttu-id="ea942-109">Typ deklarace identity mají obě deklarace identity <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a prostředek řetězce "uživatel".</span><span class="sxs-lookup"><span data-stu-id="ea942-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="ea942-110">Všechny tři části deklarace identity jsou stejné, sami deklarace identity jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="ea942-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>  
  
 <span data-ttu-id="ea942-111">Typy deklarací identity předdefinované jsou porovnávány pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ea942-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="ea942-112">Porovnání deklarace identity specifické kód používá tam, kde je to nezbytné.</span><span class="sxs-lookup"><span data-stu-id="ea942-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="ea942-113">Například uděleno následující dva uživatele deklarace hlavní název (UPN):</span><span class="sxs-lookup"><span data-stu-id="ea942-113">For example, given the following two user principal name (UPN) claims:</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 <span data-ttu-id="ea942-114">porovnání kód <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda vrátí `true`, v případě `example\someone` identifikuje stejného uživatele domény, který "someone@example.com".</span><span class="sxs-lookup"><span data-stu-id="ea942-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>  
  
 <span data-ttu-id="ea942-115">Typy vlastních deklarací identity také je možné porovnávat pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ea942-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="ea942-116">Však v případech, kde typ vrácený <xref:System.IdentityModel.Claims.Claim.Resource%2A> vlastnost deklarace identity je něco jiného než primitivní typ, <xref:System.IdentityModel.Claims.Claim.Equals%2A> vrátí `true` pouze v případě, že hodnoty vrácené `Resource` vlastnosti jsou stejné podle <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ea942-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="ea942-117">V případech, kde to není vhodná, vlastní typ vrácený `Resource` by měly přepsat vlastnost <xref:System.IdentityModel.Claims.Claim.Equals%2A> a <xref:System.Object.GetHashCode%2A> metody pro jakoukoli vlastní zpracování je nezbytné provést.</span><span class="sxs-lookup"><span data-stu-id="ea942-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>  
  
### <a name="comparing-built-in-claims"></a><span data-ttu-id="ea942-118">Porovnání předdefinované deklarace identity</span><span class="sxs-lookup"><span data-stu-id="ea942-118">Comparing built-in claims</span></span>  
  
1.  <span data-ttu-id="ea942-119">Zadána dvě instance <xref:System.IdentityModel.Claims.Claim> třídy, použijte <xref:System.IdentityModel.Claims.Claim.Equals%2A> pro porovnání, ujistěte se, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ea942-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="ea942-120">Porovnání vlastní deklarace s typy primitivní prostředků</span><span class="sxs-lookup"><span data-stu-id="ea942-120">Comparing custom claims with primitive resource types</span></span>  
  
1.  <span data-ttu-id="ea942-121">Pro vlastní deklarace s typy primitivní prostředků porovnání můžete provést jako integrované deklarace identity, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ea942-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  <span data-ttu-id="ea942-122">Pro vlastní deklarace s struktura nebo typy na základě těchto prostředků, typ prostředku by měly přepsat <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ea942-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>  
  
3.  <span data-ttu-id="ea942-123">Nejdřív zkontrolujte, zda `obj` parametr `null`a pokud ano, vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="ea942-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  <span data-ttu-id="ea942-124">Další volání <xref:System.Object.ReferenceEquals%2A> a předejte `this` a `obj` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="ea942-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="ea942-125">Vrátí-li `true`, pak vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="ea942-125">If it returns `true`, then return `true`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  <span data-ttu-id="ea942-126">Další pokus o přiřazení `obj` místní proměnné typu třídy.</span><span class="sxs-lookup"><span data-stu-id="ea942-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="ea942-127">Pokud se to nezdaří, je odkaz `null`.</span><span class="sxs-lookup"><span data-stu-id="ea942-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="ea942-128">V takových případech vrátit `false`.</span><span class="sxs-lookup"><span data-stu-id="ea942-128">In such cases, return `false`.</span></span>  
  
6.  <span data-ttu-id="ea942-129">Proveďte vlastní porovnání nezbytné správně porovnat aktuální deklarace identity do zadané deklarací.</span><span class="sxs-lookup"><span data-stu-id="ea942-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea942-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea942-130">Example</span></span>  
 <span data-ttu-id="ea942-131">Následující příklad ukazuje porovnání vlastní deklarace, kde prostředků deklarace identity představuje není primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="ea942-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="ea942-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea942-132">See Also</span></span>  
 [<span data-ttu-id="ea942-133">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="ea942-133">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="ea942-134">Postupy: Vytvoření vlastní deklarace identity</span><span class="sxs-lookup"><span data-stu-id="ea942-134">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
