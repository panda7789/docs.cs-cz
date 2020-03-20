---
title: 'Postupy: Vytvoření vlastní deklarace identity'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: e78f577e0fd3473575fab998e55616936212ebb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185607"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="18573-102">Postupy: Vytvoření vlastní deklarace identity</span><span class="sxs-lookup"><span data-stu-id="18573-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="18573-103">Infrastruktura modelu identity v nadaci WCF (Windows Communication Foundation) poskytuje sadu předdefinovaných <xref:System.IdentityModel.Claims.Claim> typů deklarací identit a práv s pomocnými funkcemi pro vytváření instancí s těmito typy a právy.</span><span class="sxs-lookup"><span data-stu-id="18573-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="18573-104">Tyto předdefinované deklarace identity jsou navrženy tak, aby model informace nalezené v typech pověření klienta, které wcf podporuje ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="18573-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="18573-105">V mnoha případech jsou vestavěné nároky dostatečné; Některé aplikace však mohou vyžadovat vlastní deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="18573-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="18573-106">Deklarace se skládá z typu deklarace, zdroje, pro který se deklarace vztahuje, a práva, které je uplatněno nad tímto zdrojem.</span><span class="sxs-lookup"><span data-stu-id="18573-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="18573-107">Toto téma popisuje, jak vytvořit vlastní deklaraci.</span><span class="sxs-lookup"><span data-stu-id="18573-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="18573-108">Vytvoření vlastní deklarace, která je založena na primitivním datovém typu</span><span class="sxs-lookup"><span data-stu-id="18573-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="18573-109">Vytvořte vlastní deklaraci předáním typu deklarace, <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> hodnoty prostředku a práva konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="18573-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="18573-110">Rozhodněte o jedinečné hodnotě pro typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="18573-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="18573-111">Typ deklarace identity je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="18573-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="18573-112">Je vlastní deklarace návrháře odpovědnost zajistit, že identifikátor řetězce, který se používá pro typ deklarace identity je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="18573-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="18573-113">Seznam typů deklarací, které jsou definovány <xref:System.IdentityModel.Claims.ClaimTypes> WCF, naleznete v části třída.</span><span class="sxs-lookup"><span data-stu-id="18573-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="18573-114">Zvolte primitivní datový typ a hodnotu prostředku.</span><span class="sxs-lookup"><span data-stu-id="18573-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="18573-115">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="18573-115">A resource is an object.</span></span> <span data-ttu-id="18573-116">Typ CLR prostředku může být primitivní, <xref:System.String> například nebo <xref:System.Int32>, nebo jakýkoli serializovatelný typ.</span><span class="sxs-lookup"><span data-stu-id="18573-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="18573-117">Clr typ prostředku musí být serializovatelný, protože deklarace jsou serializovány na různých místech WCF.</span><span class="sxs-lookup"><span data-stu-id="18573-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="18573-118">Primitivní typy jsou serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="18573-118">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="18573-119">Vyberte právo, které je definováno WCF nebo jedinečnou hodnotu pro vlastní právo.</span><span class="sxs-lookup"><span data-stu-id="18573-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="18573-120">Pravé je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="18573-120">A right is a unique string identifier.</span></span> <span data-ttu-id="18573-121">Práva, které jsou definovány WCF <xref:System.IdentityModel.Claims.Rights> jsou definovány ve třídě.</span><span class="sxs-lookup"><span data-stu-id="18573-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="18573-122">Je vlastní deklarace návrháře odpovědnost zajistit, že identifikátor řetězce, který se používá pro právo je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="18573-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="18573-123">Následující příklad kódu vytvoří vlastní deklaraci `http://example.org/claims/simplecustomclaim`s typem `Driver's License`deklarace , <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> pro prostředek s názvem a s právem.</span><span class="sxs-lookup"><span data-stu-id="18573-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="18573-124">Vytvoření vlastní deklarace, která je založena na neprimitivním datovém typu</span><span class="sxs-lookup"><span data-stu-id="18573-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="18573-125">Vytvořte vlastní deklaraci předáním typu deklarace, <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> hodnoty prostředku a práva konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="18573-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="18573-126">Rozhodněte o jedinečné hodnotě pro typ deklarace.</span><span class="sxs-lookup"><span data-stu-id="18573-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="18573-127">Typ deklarace identity je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="18573-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="18573-128">Je vlastní deklarace návrháře odpovědnost zajistit, že identifikátor řetězce, který se používá pro typ deklarace identity je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="18573-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="18573-129">Seznam typů deklarací, které jsou definovány <xref:System.IdentityModel.Claims.ClaimTypes> WCF, naleznete v části třída.</span><span class="sxs-lookup"><span data-stu-id="18573-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="18573-130">Zvolte nebo definujte serializovatelný neprimitivní typ pro prostředek.</span><span class="sxs-lookup"><span data-stu-id="18573-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="18573-131">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="18573-131">A resource is an object.</span></span> <span data-ttu-id="18573-132">Clr typ prostředku musí být serializovatelný, protože deklarace jsou serializovány na různých místech WCF.</span><span class="sxs-lookup"><span data-stu-id="18573-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="18573-133">Primitivní typy jsou již serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="18573-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="18573-134">Když je definován nový typ, použijte <xref:System.Runtime.Serialization.DataContractAttribute> pro třídu.</span><span class="sxs-lookup"><span data-stu-id="18573-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="18573-135">Také použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut pro všechny členy nového typu, které je třeba serializovat jako součást deklarace.</span><span class="sxs-lookup"><span data-stu-id="18573-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="18573-136">Následující příklad kódu definuje vlastní typ `MyResourceType`prostředku s názvem .</span><span class="sxs-lookup"><span data-stu-id="18573-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="18573-137">Vyberte právo, které je definováno WCF nebo jedinečnou hodnotu pro vlastní právo.</span><span class="sxs-lookup"><span data-stu-id="18573-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="18573-138">Pravé je jedinečný identifikátor řetězce.</span><span class="sxs-lookup"><span data-stu-id="18573-138">A right is a unique string identifier.</span></span> <span data-ttu-id="18573-139">Práva, které jsou definovány WCF <xref:System.IdentityModel.Claims.Rights> jsou definovány ve třídě.</span><span class="sxs-lookup"><span data-stu-id="18573-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="18573-140">Je vlastní deklarace návrháře odpovědnost zajistit, že identifikátor řetězce, který se používá pro právo je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="18573-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="18573-141">Následující příklad kódu vytvoří vlastní deklaraci `http://example.org/claims/complexcustomclaim`s typem deklarace , vlastní typ prostředku `MyResourceType`a s právem. <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A></span><span class="sxs-lookup"><span data-stu-id="18573-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="18573-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="18573-142">Example</span></span>  
 <span data-ttu-id="18573-143">Následující příklad kódu ukazuje, jak vytvořit vlastní deklaraci s primitivním typem prostředku a vlastní deklarací s neprimitivním typem prostředku.</span><span class="sxs-lookup"><span data-stu-id="18573-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="18573-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="18573-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="18573-145">Správa deklarací a autorizace s modelem identity</span><span class="sxs-lookup"><span data-stu-id="18573-145">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
