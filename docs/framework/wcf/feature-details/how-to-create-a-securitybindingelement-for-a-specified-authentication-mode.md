---
title: "Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 29cbe3c10ac68d508dc22781e46a6041f2d7eab7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="ba379-102">Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování</span><span class="sxs-lookup"><span data-stu-id="ba379-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="ba379-103">poskytuje několik režimy, které služby a klienti ověřování jednu na druhou.</span><span class="sxs-lookup"><span data-stu-id="ba379-103"> provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="ba379-104">Můžete vytvořit bezpečnostní prvky vazeb pro tyto režimy ověřování pomocí statické metody na <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy nebo prostřednictvím konfigurace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ba379-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ba379-105">režimy 18 ověřování, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="ba379-105"> the 18 authentication modes, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba379-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba379-106">Example</span></span>  
 <span data-ttu-id="ba379-107">Následující příklad kódu ukazuje metody pro vytvoření vazby v různých režimech ověřování.</span><span class="sxs-lookup"><span data-stu-id="ba379-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba379-108">Jednou instance <xref:System.ServiceModel.Channels.SecurityBindingElement> je vytvořen objekt, jsou neměnné, například počet vlastností <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> a <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="ba379-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="ba379-109">Volání metody `set` na tyto vlastnosti nejsou změněny.</span><span class="sxs-lookup"><span data-stu-id="ba379-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ba379-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba379-110">See Also</span></span>  
 [<span data-ttu-id="ba379-111">Režimy ověřování SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ba379-111">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [<span data-ttu-id="ba379-112">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ba379-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
