---
title: 'Postupy: Použití víc tokenů zabezpečení stejného typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 84009eacca113fcd83a0e4908c7d6eb0c82db7d5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928764"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="38fa7-102">Postupy: Použití víc tokenů zabezpečení stejného typu</span><span class="sxs-lookup"><span data-stu-id="38fa7-102">How to: Use Multiple Security Tokens of the Same Type</span></span>

- <span data-ttu-id="38fa7-103">V .NET Framework 3,0 zpráva klienta obsahovala pouze jeden token daného typu.</span><span class="sxs-lookup"><span data-stu-id="38fa7-103">In .NET Framework 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="38fa7-104">Nyní mohou klientské zprávy obsahovat více tokenů typu.</span><span class="sxs-lookup"><span data-stu-id="38fa7-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="38fa7-105">V tomto tématu se dozvíte, jak do zprávy klienta zahrnout více tokenů stejného typu.</span><span class="sxs-lookup"><span data-stu-id="38fa7-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="38fa7-106">Upozorňujeme, že nemůžete nakonfigurovat službu tímto způsobem: služba může obsahovat jenom jeden podpůrný token.</span><span class="sxs-lookup"><span data-stu-id="38fa7-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="38fa7-107">Použití více tokenů zabezpečení stejného typu</span><span class="sxs-lookup"><span data-stu-id="38fa7-107">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="38fa7-108">Vytvořte prázdnou kolekci elementů vazby, která se má naplnit.</span><span class="sxs-lookup"><span data-stu-id="38fa7-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="38fa7-109"><xref:System.ServiceModel.Channels.SecurityBindingElement> Vytvořte voláním. <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A></span><span class="sxs-lookup"><span data-stu-id="38fa7-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="38fa7-110"><xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> Vytvořte kolekci.</span><span class="sxs-lookup"><span data-stu-id="38fa7-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="38fa7-111">Přidejte do kolekce tokeny SAML.</span><span class="sxs-lookup"><span data-stu-id="38fa7-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="38fa7-112">Přidejte kolekci do <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="38fa7-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="38fa7-113">Přidejte prvky vazby do kolekce elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="38fa7-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="38fa7-114">Vrátí novou vlastní vazbu vytvořenou z kolekce elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="38fa7-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="38fa7-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="38fa7-115">Example</span></span>  
 <span data-ttu-id="38fa7-116">Následuje celá metoda, kterou popisuje předchozí postup.</span><span class="sxs-lookup"><span data-stu-id="38fa7-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
