---
title: <claimTypeRequirements> – element
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 236ae880fff24f7ccbf5d6c9c03c0208d446688f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704398"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="a9761-102">\<claimTypeRequirements> element</span><span class="sxs-lookup"><span data-stu-id="a9761-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="a9761-103">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="a9761-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="a9761-104">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="a9761-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a9761-105">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="a9761-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a9761-106">Každý podřízený prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="a9761-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="a9761-107">Požadovaný typ deklarace identity se skládá z identifikátoru URI typu deklarace identity požadovaný v vydaný token spolu s, která určuje, zda deklarací identity v vydaný token se vyžaduje typ nebo je volitelný parametr logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a9761-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9761-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9761-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a9761-109">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="a9761-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a9761-110">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a9761-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a9761-111">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="a9761-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a9761-112">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a9761-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a9761-113">\<add></span><span class="sxs-lookup"><span data-stu-id="a9761-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)
- [<span data-ttu-id="a9761-114">Vazby</span><span class="sxs-lookup"><span data-stu-id="a9761-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a9761-115">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="a9761-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a9761-116">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a9761-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a9761-117">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a9761-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="a9761-118">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a9761-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="a9761-119">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="a9761-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
