---
title: 'Postupy: Porovnání deklarací'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: 932ad347730b35a936e040e116e5aa6af36cd3dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857756"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="c9a28-102">Postupy: Porovnání deklarací</span><span class="sxs-lookup"><span data-stu-id="c9a28-102">How to: Compare Claims</span></span>
<span data-ttu-id="c9a28-103">Infrastruktura modelu Identity ve Windows Communication Foundation (WCF) se používá k provedení kontroly autorizace.</span><span class="sxs-lookup"><span data-stu-id="c9a28-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="c9a28-104">V důsledku toho běžných úloh je porovnávání deklarací identity v kontextu autorizace deklarací identity potřebný k provedení požadované akce nebo přístup k požadovanému prostředku.</span><span class="sxs-lookup"><span data-stu-id="c9a28-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="c9a28-105">Toto téma popisuje, jak porovnat deklarace identity, včetně typů předdefinované a vlastní deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="c9a28-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="c9a28-106">Další informace o infrastruktuře identit modelu najdete v tématu [správa deklarací identity a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="c9a28-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="c9a28-107">Porovnání deklarace identity spočívá v porovnání tři části deklarace identity (typ a prostředků) proti stejné části v jiné deklarace identity, pokud chcete zobrazit, pokud jsou shodné.</span><span class="sxs-lookup"><span data-stu-id="c9a28-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="c9a28-108">Podívejte se na téma v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c9a28-108">See the following example.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 <span data-ttu-id="c9a28-109">Obě deklarace identity mají typ deklarace identity <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a prostředek řetězce "uživatel".</span><span class="sxs-lookup"><span data-stu-id="c9a28-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="c9a28-110">Protože všechny tři části deklarace identity jsou stejné, sami deklarace identity jsou si rovny.</span><span class="sxs-lookup"><span data-stu-id="c9a28-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>  
  
 <span data-ttu-id="c9a28-111">Typy integrovaných deklarace identity jsou porovnány pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c9a28-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="c9a28-112">Porovnání deklarace identity kódu se používá v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="c9a28-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="c9a28-113">Mějme například následující deklarace identity uživatele dvě hlavní název (UPN):</span><span class="sxs-lookup"><span data-stu-id="c9a28-113">For example, given the following two user principal name (UPN) claims:</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 <span data-ttu-id="c9a28-114">srovnávací kód v <xref:System.IdentityModel.Claims.Claim.Equals%2A> vrátí metoda `true`, předpokládá `example\someone` stejného uživatele domény, který identifikuje "someone@example.com".</span><span class="sxs-lookup"><span data-stu-id="c9a28-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>  
  
 <span data-ttu-id="c9a28-115">Typy vlastních deklarací identity je také možné porovnat pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c9a28-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="c9a28-116">Ale v případech, kde se typ vrácený <xref:System.IdentityModel.Claims.Claim.Resource%2A> něco jiného než primitivního typu, je vlastnost deklarace identity <xref:System.IdentityModel.Claims.Claim.Equals%2A> vrátí `true` pouze v případě, že hodnoty vrácené funkcí `Resource` vlastnosti jsou stejné podle <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c9a28-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="c9a28-117">V případech, kdy to není vhodný, vlastní typ vrácených `Resource` by měly přepsat vlastnost <xref:System.IdentityModel.Claims.Claim.Equals%2A> a <xref:System.Object.GetHashCode%2A> metody k provedení jakékoli vlastní zpracování je nezbytné.</span><span class="sxs-lookup"><span data-stu-id="c9a28-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>  
  
### <a name="comparing-built-in-claims"></a><span data-ttu-id="c9a28-118">Porovnání integrovaných deklarací identity</span><span class="sxs-lookup"><span data-stu-id="c9a28-118">Comparing built-in claims</span></span>  
  
1. <span data-ttu-id="c9a28-119">Dvě instance s ohledem <xref:System.IdentityModel.Claims.Claim> třídy, použijte <xref:System.IdentityModel.Claims.Claim.Equals%2A> k porovnání, ujistěte se, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c9a28-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="c9a28-120">Porovnání vlastní deklarace identity s prostředků primitivní typy</span><span class="sxs-lookup"><span data-stu-id="c9a28-120">Comparing custom claims with primitive resource types</span></span>  
  
1. <span data-ttu-id="c9a28-121">U vlastních deklarací identity s prostředků primitivní typy porovnání se dá udělat jako integrované deklarace identity, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c9a28-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2. <span data-ttu-id="c9a28-122">Pro vlastní deklarace identity s struktury nebo třídy, na základě typů prostředků, typ prostředku by měl přepsat <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c9a28-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>  
  
3. <span data-ttu-id="c9a28-123">Nejdřív zkontrolujte, zda `obj` parametr je `null`a pokud ano, vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="c9a28-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4. <span data-ttu-id="c9a28-124">Další volání <xref:System.Object.ReferenceEquals%2A> a předejte mu `this` a `obj` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="c9a28-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="c9a28-125">Vrátí-li `true`a pak se vrátit `true`.</span><span class="sxs-lookup"><span data-stu-id="c9a28-125">If it returns `true`, then return `true`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5. <span data-ttu-id="c9a28-126">Další pokus o přiřazení `obj` na místní proměnnou typu třídy.</span><span class="sxs-lookup"><span data-stu-id="c9a28-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="c9a28-127">Když se to nepovede, odkaz je `null`.</span><span class="sxs-lookup"><span data-stu-id="c9a28-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="c9a28-128">V takových případech vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="c9a28-128">In such cases, return `false`.</span></span>  
  
6. <span data-ttu-id="c9a28-129">Proveďte vlastní porovnání nezbytné správně porovnat aktuální deklarace identity do zadané deklarací.</span><span class="sxs-lookup"><span data-stu-id="c9a28-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9a28-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9a28-130">Example</span></span>  
 <span data-ttu-id="c9a28-131">Následující příklad ukazuje porovnání vlastní deklarace identity, kde deklarace identity prostředku je jiného než primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="c9a28-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="c9a28-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9a28-132">See also</span></span>

- [<span data-ttu-id="c9a28-133">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="c9a28-133">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="c9a28-134">Postupy: Vytvoření vlastní deklarace</span><span class="sxs-lookup"><span data-stu-id="c9a28-134">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
