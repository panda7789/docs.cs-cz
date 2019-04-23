---
title: 'Postupy: Vytvoření vlastní deklarace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 1892e910a86e01b7b2ee0f6a2403ad7af4688808
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295377"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="c4bdd-102">Postupy: Vytvoření vlastní deklarace</span><span class="sxs-lookup"><span data-stu-id="c4bdd-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="c4bdd-103">Infrastruktura modelu Identity ve Windows Communication Foundation (WCF) poskytuje sadu předdefinovaných deklarací typů a práva s pomocné funkce pro vytváření <xref:System.IdentityModel.Claims.Claim> instance s těmito typy a přístupových práv.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="c4bdd-104">Tyto předdefinované deklarace jsou navrženy pro informace o modelu, které jsou součástí typy přihlašovacích údajů klienta, které podporuje WCF, ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="c4bdd-105">V mnoha případech jsou dostatečné; integrované deklarací identity Některé aplikace ale můžou vyžadovat vlastní deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="c4bdd-106">Deklarace identity se skládá z typ deklarace identity, prostředek, pro kterou platí deklarace identity pro a práv, která jsou s potvrzením přes tento prostředek.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="c4bdd-107">Toto téma popisuje, jak vytvořit vlastní deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="c4bdd-108">K vytvoření vlastní deklarace identity, která je založena na primitivní datový typ</span><span class="sxs-lookup"><span data-stu-id="c4bdd-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="c4bdd-109">Vytvoření vlastních deklarací identity pomocí typu deklarace identity, hodnota prostředku a právo <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="c4bdd-110">Při rozhodování o jedinečnou hodnotu pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="c4bdd-111">Typ deklarace identity je identifikátor jedinečný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="c4bdd-112">Je Návrhář vlastních deklarací identity povinností ujistit se, že je jedinečný identifikátor řetězce, který se používá pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="c4bdd-113">Seznam typů deklarací identity, které jsou definovány službou WCF najdete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třídy.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="c4bdd-114">Zvolte primitivní datový typ a hodnotu pro prostředek.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="c4bdd-115">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-115">A resource is an object.</span></span> <span data-ttu-id="c4bdd-116">Typ CLR prostředku může být jednoduchého typu, například <xref:System.String> nebo <xref:System.Int32>, nebo libovolný typ serializovat.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="c4bdd-117">Typ CLR prostředku musí být serializovatelný, protože deklarace identity serializují v různých fázích WCF.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="c4bdd-118">Primitivní typy jsou serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-118">Primitive types are serializable.</span></span>  
  
    3.  <span data-ttu-id="c4bdd-119">Zvolte práva, která je definována WCF nebo jedinečnou hodnotu pro vlastní práva.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="c4bdd-120">Práva je identifikátor jedinečný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-120">A right is a unique string identifier.</span></span> <span data-ttu-id="c4bdd-121">Práva, které jsou definovány službou WCF, které jsou definovány v <xref:System.IdentityModel.Claims.Rights> třídy.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="c4bdd-122">Je Návrhář vlastních deklarací identity povinností ujistit se, že je jedinečný identifikátor řetězce, který slouží k pravé straně.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="c4bdd-123">Následující příklad kódu vytvoří vlastní deklarace identity s typem deklarace identity `http://example.org/claims/simplecustomclaim`, pro prostředek s názvem `Driver's License`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> vpravo.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="c4bdd-124">K vytvoření vlastní deklarace identity, který je založen na data jiného než primitivního typu</span><span class="sxs-lookup"><span data-stu-id="c4bdd-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="c4bdd-125">Vytvoření vlastních deklarací identity pomocí typu deklarace identity, hodnota prostředku a právo <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="c4bdd-126">Při rozhodování o jedinečnou hodnotu pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="c4bdd-127">Typ deklarace identity je identifikátor jedinečný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="c4bdd-128">Je Návrhář vlastních deklarací identity povinností ujistit se, že je jedinečný identifikátor řetězce, který se používá pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="c4bdd-129">Seznam typů deklarací identity, které jsou definovány službou WCF najdete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třídy.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="c4bdd-130">Vyberte nebo vytvořte serializovatelný jiného než primitivního typu prostředku.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="c4bdd-131">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-131">A resource is an object.</span></span> <span data-ttu-id="c4bdd-132">Typ CLR prostředku musí být serializovatelný, protože deklarace identity serializují v různých fázích WCF.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="c4bdd-133">Primitivní typy jsou již serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="c4bdd-134">Když je nový typ definován, použije <xref:System.Runtime.Serialization.DataContractAttribute> do třídy.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="c4bdd-135">Platí také <xref:System.Runtime.Serialization.DataMemberAttribute> všem členům, které potřebujete k serializaci jako součást deklarace nového typu atributu.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="c4bdd-136">Následující příklad kódu definuje vlastní typ prostředku s názvem `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  <span data-ttu-id="c4bdd-137">Zvolte práva, která je definována WCF nebo jedinečnou hodnotu pro vlastní práva.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="c4bdd-138">Práva je identifikátor jedinečný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-138">A right is a unique string identifier.</span></span> <span data-ttu-id="c4bdd-139">Práva, které jsou definovány službou WCF, které jsou definovány v <xref:System.IdentityModel.Claims.Rights> třídy.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="c4bdd-140">Je Návrhář vlastních deklarací identity povinností ujistit se, že je jedinečný identifikátor řetězce, který slouží k pravé straně.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="c4bdd-141">Následující příklad kódu vytvoří vlastní deklarace identity s typem deklarace identity `http://example.org/claims/complexcustomclaim`, vlastní prostředek typu `MyResourceType`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> vpravo.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="c4bdd-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4bdd-142">Example</span></span>  
 <span data-ttu-id="c4bdd-143">Následující příklad kódu ukazuje, jak vytvořit vlastní deklarace identity s typem primitivní prostředku a vlastní deklarace identity s typem neprimitivní prostředku.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="c4bdd-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4bdd-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="c4bdd-145">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="c4bdd-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
