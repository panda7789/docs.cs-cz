---
title: "Postupy: použití více tokeny zabezpečení stejného typu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 0e43a140a583550880a4263f431bc983285075d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="7247a-102">Postupy: použití více tokeny zabezpečení stejného typu</span><span class="sxs-lookup"><span data-stu-id="7247a-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="7247a-103">V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, klienta zprávy pouze obsahují jeden token daného typu.</span><span class="sxs-lookup"><span data-stu-id="7247a-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="7247a-104">Nyní zprávy klienta může obsahovat více tokeny typu.</span><span class="sxs-lookup"><span data-stu-id="7247a-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="7247a-105">Toto téma ukazuje, jak chcete zahrnout do zpráv klienta více tokeny stejného typu.</span><span class="sxs-lookup"><span data-stu-id="7247a-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="7247a-106">Všimněte si, že nemůžete nakonfigurovat službu tímto způsobem: služby může obsahovat jenom jeden token podpory.</span><span class="sxs-lookup"><span data-stu-id="7247a-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="7247a-107">Použití více tokeny zabezpečení stejného typu</span><span class="sxs-lookup"><span data-stu-id="7247a-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="7247a-108">Vytvořte kolekci elementů vazby prázdný vyplnit.</span><span class="sxs-lookup"><span data-stu-id="7247a-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="7247a-109">Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> voláním <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="7247a-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="7247a-110">Vytvoření <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> kolekce.</span><span class="sxs-lookup"><span data-stu-id="7247a-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="7247a-111">Tokeny SAML přidáte do kolekce.</span><span class="sxs-lookup"><span data-stu-id="7247a-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="7247a-112">Přidání do kolekce <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7247a-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="7247a-113">Prvky vazeb přidáte do kolekce elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="7247a-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="7247a-114">Vrátí novou vlastní vazby vytvořené z kolekce elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="7247a-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="7247a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="7247a-115">Example</span></span>  
 <span data-ttu-id="7247a-116">Níže je celý metody popsané předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="7247a-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="7247a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7247a-117">See Also</span></span>  
 [<span data-ttu-id="7247a-118">Architektura zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7247a-118">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
