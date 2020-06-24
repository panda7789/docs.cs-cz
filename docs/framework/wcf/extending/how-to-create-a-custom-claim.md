---
title: 'Postupy: Vytvoření vlastní deklarace identity'
description: Naučte se vytvářet vlastní deklarace identity ve službě WCF. WCF podporuje celou řadu integrovaných deklarací identity a některé aplikace můžou vyžadovat vlastní deklarace identity.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 89f2b1359b48b71720db6ff38f27883745cfe612
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247543"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="123e6-104">Postupy: Vytvoření vlastní deklarace identity</span><span class="sxs-lookup"><span data-stu-id="123e6-104">How to: Create a Custom Claim</span></span>
<span data-ttu-id="123e6-105">Infrastruktura modelu identity ve službě Windows Communication Foundation (WCF) poskytuje sadu předdefinovaných typů deklarací identity a oprávnění s podpůrnými funkcemi pro vytváření <xref:System.IdentityModel.Claims.Claim> instancí s těmito typy a právy.</span><span class="sxs-lookup"><span data-stu-id="123e6-105">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="123e6-106">Tyto předdefinované deklarace identity jsou navržené tak, aby byly v typech přihlašovacích údajů klienta, které služba WCF podporuje ve výchozím nastavení, modelované.</span><span class="sxs-lookup"><span data-stu-id="123e6-106">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="123e6-107">V mnoha případech jsou předdefinované deklarace identity dostačující; Některé aplikace ale můžou vyžadovat vlastní deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="123e6-107">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="123e6-108">Deklarace identity se skládá z typu deklarace identity, prostředku, pro který se deklarace identity vztahuje, a práva, které je na tento prostředek uplatněno.</span><span class="sxs-lookup"><span data-stu-id="123e6-108">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="123e6-109">Toto téma popisuje, jak vytvořit vlastní deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="123e6-109">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="123e6-110">Vytvoření vlastní deklarace identity, která je založena na primitivním datovém typu</span><span class="sxs-lookup"><span data-stu-id="123e6-110">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="123e6-111">Vytvořte vlastní deklaraci identity předáním typu deklarace identity, hodnoty prostředku a práva <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="123e6-111">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="123e6-112">Určete jedinečnou hodnotu pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="123e6-112">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="123e6-113">Typ deklarace identity je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="123e6-113">The claim type is a unique string identifier.</span></span> <span data-ttu-id="123e6-114">Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro typ deklarace identity, je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="123e6-114">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="123e6-115">Seznam typů deklarací, které jsou definovány službou WCF, naleznete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> Třída.</span><span class="sxs-lookup"><span data-stu-id="123e6-115">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="123e6-116">Vyberte primitivní datový typ a hodnotu pro daný prostředek.</span><span class="sxs-lookup"><span data-stu-id="123e6-116">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="123e6-117">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="123e6-117">A resource is an object.</span></span> <span data-ttu-id="123e6-118">Typ CLR prostředku může být primitivní, například <xref:System.String> nebo <xref:System.Int32> , nebo jakýkoli serializovatelný typ.</span><span class="sxs-lookup"><span data-stu-id="123e6-118">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="123e6-119">Typ CLR prostředku musí být serializovatelný, protože deklarace identity jsou v různých bodech serializovány službou WCF.</span><span class="sxs-lookup"><span data-stu-id="123e6-119">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="123e6-120">Primitivní typy jsou serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="123e6-120">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="123e6-121">Vyberte právo definované službou WCF nebo jedinečnou hodnotou pro vlastní právo.</span><span class="sxs-lookup"><span data-stu-id="123e6-121">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="123e6-122">Právo je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="123e6-122">A right is a unique string identifier.</span></span> <span data-ttu-id="123e6-123">Práva, která jsou definována v rámci služby WCF, jsou definována ve <xref:System.IdentityModel.Claims.Rights> třídě.</span><span class="sxs-lookup"><span data-stu-id="123e6-123">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="123e6-124">Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro právo, je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="123e6-124">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="123e6-125">Následující příklad kódu vytvoří vlastní deklaraci identity s typem deklarace identity `http://example.org/claims/simplecustomclaim` pro prostředek s názvem `Driver's License` a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> napravo.</span><span class="sxs-lookup"><span data-stu-id="123e6-125">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="123e6-126">Vytvoření vlastní deklarace identity, která je založena na neprimitivním datovém typu</span><span class="sxs-lookup"><span data-stu-id="123e6-126">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="123e6-127">Vytvořte vlastní deklaraci identity předáním typu deklarace identity, hodnoty prostředku a práva <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="123e6-127">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="123e6-128">Určete jedinečnou hodnotu pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="123e6-128">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="123e6-129">Typ deklarace identity je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="123e6-129">The claim type is a unique string identifier.</span></span> <span data-ttu-id="123e6-130">Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro typ deklarace identity, je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="123e6-130">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="123e6-131">Seznam typů deklarací, které jsou definovány službou WCF, naleznete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> Třída.</span><span class="sxs-lookup"><span data-stu-id="123e6-131">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="123e6-132">Vyberte nebo definujte serializovatelný neprimitivní typ prostředku.</span><span class="sxs-lookup"><span data-stu-id="123e6-132">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="123e6-133">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="123e6-133">A resource is an object.</span></span> <span data-ttu-id="123e6-134">Typ CLR prostředku musí být serializovatelný, protože deklarace identity jsou v různých bodech serializovány službou WCF.</span><span class="sxs-lookup"><span data-stu-id="123e6-134">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="123e6-135">Primitivní typy jsou již serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="123e6-135">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="123e6-136">Pokud je definován nový typ, použijte <xref:System.Runtime.Serialization.DataContractAttribute> pro třídu.</span><span class="sxs-lookup"><span data-stu-id="123e6-136">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="123e6-137">Také použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut na všechny členy nového typu, které je třeba serializovat jako součást deklarace.</span><span class="sxs-lookup"><span data-stu-id="123e6-137">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="123e6-138">Následující příklad kódu definuje vlastní typ prostředku s názvem `MyResourceType` .</span><span class="sxs-lookup"><span data-stu-id="123e6-138">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="123e6-139">Vyberte právo definované službou WCF nebo jedinečnou hodnotou pro vlastní právo.</span><span class="sxs-lookup"><span data-stu-id="123e6-139">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="123e6-140">Právo je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="123e6-140">A right is a unique string identifier.</span></span> <span data-ttu-id="123e6-141">Práva, která jsou definována v rámci služby WCF, jsou definována ve <xref:System.IdentityModel.Claims.Rights> třídě.</span><span class="sxs-lookup"><span data-stu-id="123e6-141">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="123e6-142">Je zodpovědností vlastního návrháře deklarací identity, aby se zajistilo, že identifikátor řetězce, který se používá pro právo, je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="123e6-142">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="123e6-143">Následující příklad kódu vytvoří vlastní deklaraci identity s typem deklarace identity `http://example.org/claims/complexcustomclaim` , vlastním typem prostředku `MyResourceType` a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> napravo.</span><span class="sxs-lookup"><span data-stu-id="123e6-143">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="123e6-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="123e6-144">Example</span></span>  
 <span data-ttu-id="123e6-145">Následující příklad kódu ukazuje, jak vytvořit vlastní deklaraci identity s primitivním typem prostředku a vlastní deklarací s neprimitivním typem prostředku.</span><span class="sxs-lookup"><span data-stu-id="123e6-145">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="123e6-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="123e6-146">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="123e6-147">Správa deklarací a autorizace s modelem identity</span><span class="sxs-lookup"><span data-stu-id="123e6-147">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
