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
ms.openlocfilehash: 29254bd661e72b926b21695ccb646480c53b5475
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797098"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="3ab9f-102">Postupy: Porovnání deklarací</span><span class="sxs-lookup"><span data-stu-id="3ab9f-102">How to: Compare Claims</span></span>

<span data-ttu-id="3ab9f-103">K provedení kontroly autorizace se používá infrastruktura modelu identity v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ab9f-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="3ab9f-104">Běžným úkolem je například porovnat deklarace identity v kontextu autorizace s deklaracemi, které jsou potřeba k provedení požadované akce, nebo získat přístup k požadovanému prostředku.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="3ab9f-105">Toto téma popisuje, jak porovnat deklarace identity, včetně předdefinovaných a vlastních typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="3ab9f-106">Další informace o infrastruktuře modelu identity najdete v tématu [Správa deklarací identity a autorizace pomocí modelu identity](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="3ab9f-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="3ab9f-107">Porovnání deklarací identity zahrnuje porovnání tří částí deklarace identity (typu, práva a prostředku) se stejnými částmi v jiné deklaraci identity, aby bylo možné zjistit, zda jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="3ab9f-108">Podívejte se na téma v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-108">See the following example.</span></span>

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

<span data-ttu-id="3ab9f-109">Obě deklarace mají typ <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>deklarace, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a prostředek řetězce "někdo".</span><span class="sxs-lookup"><span data-stu-id="3ab9f-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="3ab9f-110">Jelikož jsou všechny tři části deklarace identity stejné, samotné deklarace identity jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>

<span data-ttu-id="3ab9f-111">Předdefinované typy deklarací se porovnávají pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="3ab9f-112">V případě potřeby se používá kód porovnání specifický pro deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="3ab9f-113">Například s ohledem na následující dvě deklarace hlavního názvu uživatele (UPN):</span><span class="sxs-lookup"><span data-stu-id="3ab9f-113">For example, given the following two user principal name (UPN) claims:</span></span>

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

<span data-ttu-id="3ab9f-114">kód porovnání v <xref:System.IdentityModel.Claims.Claim.Equals%2A> metodě vrátí `true`za předpokladu `example\someone` , že identifikuje stejného uživatele domény jakosomeone@example.com"".</span><span class="sxs-lookup"><span data-stu-id="3ab9f-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>

<span data-ttu-id="3ab9f-115">Vlastní typy deklarací lze také porovnat pomocí <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="3ab9f-116">V případech, kdy typ <xref:System.IdentityModel.Claims.Claim.Resource%2A> vrácený vlastností deklarace je jiný než primitivní typ <xref:System.IdentityModel.Claims.Claim.Equals%2A> , vrátí funkce `true` pouze v případě, že hodnoty vracené `Resource` vlastnostmi se rovnají podle <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="3ab9f-117">V případech, kdy to není vhodné, vlastní typ vrácený `Resource` vlastností by měl <xref:System.IdentityModel.Claims.Claim.Equals%2A> přepsat metody a <xref:System.Object.GetHashCode%2A> , aby bylo možné provést jakékoli vlastní zpracování.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>

## <a name="comparing-built-in-claims"></a><span data-ttu-id="3ab9f-118">Porovnání předdefinovaných deklarací identity</span><span class="sxs-lookup"><span data-stu-id="3ab9f-118">Comparing built-in claims</span></span>

1. <span data-ttu-id="3ab9f-119">V případě, že jsou <xref:System.IdentityModel.Claims.Claim> zadány dvě instance <xref:System.IdentityModel.Claims.Claim.Equals%2A> třídy, použijte k provedení porovnání, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="3ab9f-120">Porovnání vlastních deklarací s primitivními typy prostředků</span><span class="sxs-lookup"><span data-stu-id="3ab9f-120">Comparing custom claims with primitive resource types</span></span>

1. <span data-ttu-id="3ab9f-121">Pro vlastní deklarace identity s primitivními typy prostředků je možné porovnání provést jako pro předdefinované deklarace, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. <span data-ttu-id="3ab9f-122">Pro vlastní deklarace identity s typy prostředků na základě struktury nebo třídy by měl typ prostředku přepsat <xref:System.IdentityModel.Claims.Claim.Equals%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>

3. <span data-ttu-id="3ab9f-123">Nejprve ověřte, zda `obj` je `null`parametr, a pokud ano, vraťte `false`.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. <span data-ttu-id="3ab9f-124">Další volání <xref:System.Object.ReferenceEquals%2A> a předejte `obj` `this` a jako parametry.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="3ab9f-125">Pokud se vrátí `true`, `true`vrátí.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-125">If it returns `true`, then return `true`.</span></span>

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. <span data-ttu-id="3ab9f-126">Při dalším pokusu `obj` o přiřazení k místní proměnné typu třídy.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="3ab9f-127">Pokud se to nepovede, odkaz `null`je.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="3ab9f-128">V takových případech vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-128">In such cases, return `false`.</span></span>

6. <span data-ttu-id="3ab9f-129">Proveďte vlastní porovnání potřebné ke správnému porovnání aktuální deklarace identity s poskytnutou deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>

## <a name="example"></a><span data-ttu-id="3ab9f-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ab9f-130">Example</span></span>

<span data-ttu-id="3ab9f-131">Následující příklad ukazuje porovnání vlastních deklarací identity, u kterých je prostředek deklarace identity neprimitivního typu.</span><span class="sxs-lookup"><span data-stu-id="3ab9f-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a><span data-ttu-id="3ab9f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ab9f-132">See also</span></span>

- [<span data-ttu-id="3ab9f-133">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="3ab9f-133">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="3ab9f-134">Postupy: Vytvoření vlastní deklarace identity</span><span class="sxs-lookup"><span data-stu-id="3ab9f-134">How to: Create a Custom Claim</span></span>](how-to-create-a-custom-claim.md)
