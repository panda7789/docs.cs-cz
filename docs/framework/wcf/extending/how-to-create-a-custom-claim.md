---
title: 'Postupy: vytvoření vlastních deklarací identity'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 3ee707ae4e2a7dafeb7cb42d6d56eeece8f23306
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804856"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="e7dce-102">Postupy: vytvoření vlastních deklarací identity</span><span class="sxs-lookup"><span data-stu-id="e7dce-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="e7dce-103">Infrastruktura modelu Identity ve Windows Communication Foundation (WCF) poskytuje sadu předdefinovaných typy a práva s podpůrné funkce pro vytváření <xref:System.IdentityModel.Claims.Claim> instancí s těmito typy a práva.</span><span class="sxs-lookup"><span data-stu-id="e7dce-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="e7dce-104">Tyto integrované deklarace jsou navrženy pro informace o modelu nacházejí v přihlašovacích údajů typů klientů, které podporuje WCF ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e7dce-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="e7dce-105">V mnoha případech jsou předdefinované deklarace identity dostatečná; Některé aplikace ale můžou vyžadovat vlastní deklarace.</span><span class="sxs-lookup"><span data-stu-id="e7dce-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="e7dce-106">Deklarace identity se skládá z typ deklarace identity, prostředků, pro kterou platí deklarace identity k a práv, která jsou uplatňovaná přes tento prostředek.</span><span class="sxs-lookup"><span data-stu-id="e7dce-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="e7dce-107">Toto téma popisuje postup vytvoření vlastních deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e7dce-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="e7dce-108">K vytvoření vlastních deklarací identity, která je založená na primitivní datový typ</span><span class="sxs-lookup"><span data-stu-id="e7dce-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1.  <span data-ttu-id="e7dce-109">Vytvoření vlastních deklarací identity pomocí předání typu deklarace, hodnota prostředků a právo <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e7dce-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="e7dce-110">Rozhodněte o jedinečnou hodnotu pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e7dce-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="e7dce-111">Typ deklarace identity je řetězec jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="e7dce-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="e7dce-112">Je zodpovědností Návrháře vlastních deklarací identity k zajištění, že je jedinečný identifikátor řetězec, který se používá pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e7dce-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="e7dce-113">Seznam typů deklarací identity, které jsou definovány WCF najdete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třídy.</span><span class="sxs-lookup"><span data-stu-id="e7dce-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="e7dce-114">Zvolte primitivní datový typ a hodnotu pro daný prostředek.</span><span class="sxs-lookup"><span data-stu-id="e7dce-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="e7dce-115">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="e7dce-115">A resource is an object.</span></span> <span data-ttu-id="e7dce-116">Typ CLR prostředek může být primitivní, jako například <xref:System.String> nebo <xref:System.Int32>, nebo kterýkoli typ serializable.</span><span class="sxs-lookup"><span data-stu-id="e7dce-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="e7dce-117">Typ CLR prostředku musí být serializovatelný, vzhledem k tomu, že deklarace identity jsou serializovat v různých fázích WCF.</span><span class="sxs-lookup"><span data-stu-id="e7dce-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="e7dce-118">Primitivní typy jsou serializable.</span><span class="sxs-lookup"><span data-stu-id="e7dce-118">Primitive types are serializable.</span></span>  
  
    3.  <span data-ttu-id="e7dce-119">Zvolte vpravo, která jsou definována ve WCF nebo jedinečnou hodnotu pro vlastní práva.</span><span class="sxs-lookup"><span data-stu-id="e7dce-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="e7dce-120">Pravém je identifikátor jedinečného řetězce.</span><span class="sxs-lookup"><span data-stu-id="e7dce-120">A right is a unique string identifier.</span></span> <span data-ttu-id="e7dce-121">Práva, které jsou definovány WCF jsou definovány v <xref:System.IdentityModel.Claims.Rights> třídy.</span><span class="sxs-lookup"><span data-stu-id="e7dce-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="e7dce-122">Je odpovědností Návrháře vlastních deklarací identity zajistit, že je jedinečný identifikátor řetězec, který se používá pro vpravo.</span><span class="sxs-lookup"><span data-stu-id="e7dce-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="e7dce-123">Následující příklad kódu vytvoří vlastních deklarací identity s typem deklarace identity `http://example.org/claims/simplecustomclaim`, pro prostředek s názvem `Driver's License`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> správné.</span><span class="sxs-lookup"><span data-stu-id="e7dce-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="e7dce-124">K vytvoření vlastních deklarací identity, která je založená na jiný primitivní datový typ</span><span class="sxs-lookup"><span data-stu-id="e7dce-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1.  <span data-ttu-id="e7dce-125">Vytvoření vlastních deklarací identity pomocí předání typu deklarace, hodnota prostředků a právo <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e7dce-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="e7dce-126">Rozhodněte o jedinečnou hodnotu pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e7dce-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="e7dce-127">Typ deklarace identity je řetězec jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="e7dce-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="e7dce-128">Je zodpovědností Návrháře vlastních deklarací identity k zajištění, že je jedinečný identifikátor řetězec, který se používá pro typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e7dce-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="e7dce-129">Seznam typů deklarací identity, které jsou definovány WCF najdete v tématu <xref:System.IdentityModel.Claims.ClaimTypes> třídy.</span><span class="sxs-lookup"><span data-stu-id="e7dce-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="e7dce-130">Zvolte nebo definovat serializovatelný není primitivní typ prostředku.</span><span class="sxs-lookup"><span data-stu-id="e7dce-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="e7dce-131">Prostředek je objekt.</span><span class="sxs-lookup"><span data-stu-id="e7dce-131">A resource is an object.</span></span> <span data-ttu-id="e7dce-132">Typ CLR prostředku musí být serializovatelný, vzhledem k tomu, že deklarace identity jsou serializovat v různých fázích WCF.</span><span class="sxs-lookup"><span data-stu-id="e7dce-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="e7dce-133">Primitivní typy jsou již serializable.</span><span class="sxs-lookup"><span data-stu-id="e7dce-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="e7dce-134">Pokud je nový typ definované, použít <xref:System.Runtime.Serialization.DataContractAttribute> k třídě.</span><span class="sxs-lookup"><span data-stu-id="e7dce-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="e7dce-135">Platí také <xref:System.Runtime.Serialization.DataMemberAttribute> atribut všichni členové nový typ, který je potřeba serializovat v rámci deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e7dce-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="e7dce-136">Následující příklad kódu definuje vlastní typ prostředku s názvem `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="e7dce-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  <span data-ttu-id="e7dce-137">Zvolte vpravo, která jsou definována ve WCF nebo jedinečnou hodnotu pro vlastní práva.</span><span class="sxs-lookup"><span data-stu-id="e7dce-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="e7dce-138">Pravém je identifikátor jedinečného řetězce.</span><span class="sxs-lookup"><span data-stu-id="e7dce-138">A right is a unique string identifier.</span></span> <span data-ttu-id="e7dce-139">Práva, které jsou definovány WCF jsou definovány v <xref:System.IdentityModel.Claims.Rights> třídy.</span><span class="sxs-lookup"><span data-stu-id="e7dce-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="e7dce-140">Je odpovědností Návrháře vlastních deklarací identity zajistit, že je jedinečný identifikátor řetězec, který se používá pro vpravo.</span><span class="sxs-lookup"><span data-stu-id="e7dce-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="e7dce-141">Následující příklad kódu vytvoří vlastních deklarací identity s typem deklarace identity `http://example.org/claims/complexcustomclaim`, typ vlastní prostředek `MyResourceType`a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> správné.</span><span class="sxs-lookup"><span data-stu-id="e7dce-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="e7dce-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7dce-142">Example</span></span>  
 <span data-ttu-id="e7dce-143">Následující příklad kódu ukazuje, jak vytvořit vlastní deklarace identity s typem primitivní prostředku a vlastních deklarací identity s typem prostředku není primitivní.</span><span class="sxs-lookup"><span data-stu-id="e7dce-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="e7dce-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7dce-144">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="e7dce-145">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="e7dce-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="e7dce-146">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="e7dce-146">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
