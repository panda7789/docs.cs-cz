---
title: 'Postupy: Vytvoření vlastní deklarace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 399aba1a6ad70ae37355f529a291ab2f604af03f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797085"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="0e7b1-102">Postupy: Vytvoření vlastní deklarace</span><span class="sxs-lookup"><span data-stu-id="0e7b1-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="0e7b1-103">Infrastruktura modelu identity ve službě Windows Communication Foundation (WCF) poskytuje sadu předdefinovaných typů deklarací identity a oprávnění s podpůrnými funkcemi pro vytváření <xref:System.IdentityModel.Claims.Claim> instancí s těmito typy a právy.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="0e7b1-104">Tyto předdefinované deklarace identity jsou navržené tak, aby byly v typech přihlašovacích údajů klienta, které služba WCF podporuje ve výchozím nastavení, modelované.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="0e7b1-105">V mnoha případech jsou předdefinované deklarace identity dostačující; Některé aplikace ale můžou vyžadovat vlastní deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="0e7b1-106">Deklarace identity se skládá z typu deklarace identity, prostředku, pro který se deklarace identity vztahuje, a práva, které je na tento prostředek uplatněno.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="0e7b1-107">Toto téma popisuje, jak vytvořit vlastní deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="0e7b1-108">Vytvoření vlastní deklarace identity, která je založena na primitivním datovém typu</span><span class="sxs-lookup"><span data-stu-id="0e7b1-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="0e7b1-109">Vytvořte vlastní deklaraci identity předáním typu deklarace identity, hodnoty prostředku a práva <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="0e7b1-110">Určete jedinečnou hodnotu pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="0e7b1-111">Typ deklarace identity je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="0e7b1-112">Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro typ deklarace identity, je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="0e7b1-113">Seznam typů deklarací, které jsou definovány službou WCF, naleznete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třída.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="0e7b1-114">Vyberte primitivní datový typ a hodnotu pro daný prostředek.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="0e7b1-115">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-115">A resource is an object.</span></span> <span data-ttu-id="0e7b1-116">Typ CLR prostředku může být primitivní, například <xref:System.String> nebo <xref:System.Int32>, nebo jakýkoli serializovatelný typ.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="0e7b1-117">Typ CLR prostředku musí být serializovatelný, protože deklarace identity jsou v různých bodech serializovány službou WCF.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="0e7b1-118">Primitivní typy jsou serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-118">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="0e7b1-119">Vyberte právo definované službou WCF nebo jedinečnou hodnotou pro vlastní právo.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="0e7b1-120">Právo je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-120">A right is a unique string identifier.</span></span> <span data-ttu-id="0e7b1-121">Práva, která jsou definována v rámci <xref:System.IdentityModel.Claims.Rights> služby WCF, jsou definována ve třídě.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="0e7b1-122">Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro právo, je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="0e7b1-123">Následující příklad kódu vytvoří vlastní deklaraci identity s typem `http://example.org/claims/simplecustomclaim`deklarace identity pro prostředek s názvem `Driver's License`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> napravo.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="0e7b1-124">Vytvoření vlastní deklarace identity, která je založena na neprimitivním datovém typu</span><span class="sxs-lookup"><span data-stu-id="0e7b1-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="0e7b1-125">Vytvořte vlastní deklaraci identity předáním typu deklarace identity, hodnoty prostředku a práva <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="0e7b1-126">Určete jedinečnou hodnotu pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="0e7b1-127">Typ deklarace identity je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="0e7b1-128">Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro typ deklarace identity, je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="0e7b1-129">Seznam typů deklarací, které jsou definovány službou WCF, naleznete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třída.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="0e7b1-130">Vyberte nebo definujte serializovatelný neprimitivní typ prostředku.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="0e7b1-131">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-131">A resource is an object.</span></span> <span data-ttu-id="0e7b1-132">Typ CLR prostředku musí být serializovatelný, protože deklarace identity jsou v různých bodech serializovány službou WCF.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="0e7b1-133">Primitivní typy jsou již serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="0e7b1-134">Pokud je definován nový typ, použijte <xref:System.Runtime.Serialization.DataContractAttribute> pro třídu.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="0e7b1-135">Také použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut na všechny členy nového typu, které je třeba serializovat jako součást deklarace.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="0e7b1-136">Následující příklad kódu definuje vlastní typ prostředku s názvem `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3. <span data-ttu-id="0e7b1-137">Vyberte právo definované službou WCF nebo jedinečnou hodnotou pro vlastní právo.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="0e7b1-138">Právo je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-138">A right is a unique string identifier.</span></span> <span data-ttu-id="0e7b1-139">Práva, která jsou definována v rámci <xref:System.IdentityModel.Claims.Rights> služby WCF, jsou definována ve třídě.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="0e7b1-140">Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro právo, je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="0e7b1-141">Následující příklad kódu vytvoří vlastní deklaraci identity s typem `http://example.org/claims/complexcustomclaim`deklarace identity, vlastním `MyResourceType`typem prostředku a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> napravo.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="0e7b1-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e7b1-142">Example</span></span>  
 <span data-ttu-id="0e7b1-143">Následující příklad kódu ukazuje, jak vytvořit vlastní deklaraci identity s primitivním typem prostředku a vlastní deklarací s neprimitivním typem prostředku.</span><span class="sxs-lookup"><span data-stu-id="0e7b1-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="0e7b1-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e7b1-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="0e7b1-145">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="0e7b1-145">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
