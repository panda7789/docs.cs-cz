---
title: <claimTypeRequirements> – element
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: b4d8479dd9a24774afbd0549caf9e261f55fa147
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926148"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="84d3e-102">\<claimTypeRequirements – element ></span><span class="sxs-lookup"><span data-stu-id="84d3e-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="84d3e-103">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="84d3e-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="84d3e-104">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="84d3e-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="84d3e-105">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="84d3e-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="84d3e-106">Každý podřízený element v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="84d3e-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="84d3e-107">Požadavek typu deklarace identity se skládá z identifikátoru URI typu deklarace, který je požadován v vystaveném tokenu, spolu s parametrem Boolean, který označuje, zda je daný typ deklarace identity požadován v vystaveném tokenu, nebo je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="84d3e-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d3e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84d3e-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="84d3e-109">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="84d3e-109">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="84d3e-110">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="84d3e-110">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="84d3e-111">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="84d3e-111">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="84d3e-112">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="84d3e-112">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="84d3e-113">\<add></span><span class="sxs-lookup"><span data-stu-id="84d3e-113">\<add></span></span>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="84d3e-114">Vazby</span><span class="sxs-lookup"><span data-stu-id="84d3e-114">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="84d3e-115">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="84d3e-115">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="84d3e-116">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="84d3e-116">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="84d3e-117">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="84d3e-117">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="84d3e-118">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="84d3e-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="84d3e-119">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="84d3e-119">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
