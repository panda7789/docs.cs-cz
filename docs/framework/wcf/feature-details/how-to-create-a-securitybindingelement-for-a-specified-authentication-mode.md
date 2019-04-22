---
title: 'Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: e35df9a5dacc5f281af48cec292a09b291312119
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124511"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="73dff-102">Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování</span><span class="sxs-lookup"><span data-stu-id="73dff-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
<span data-ttu-id="73dff-103">Windows Communication Foundation (WCF) poskytuje několik režimů, které služby a klienti ověřování mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="73dff-103">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="73dff-104">Můžete vytvořit bezpečnostní prvky vazeb pro tyto režimy ověřování pomocí statické metody na <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy nebo prostřednictvím konfigurace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="73dff-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="73dff-105">Další informace o režimech ověřování 18 najdete v tématu [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="73dff-105">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73dff-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="73dff-106">Example</span></span>  
 <span data-ttu-id="73dff-107">Následující příklad kódu ukazuje metody pro vytváření vazeb v různých režimech ověřování.</span><span class="sxs-lookup"><span data-stu-id="73dff-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73dff-108">Jednou instancí <xref:System.ServiceModel.Channels.SecurityBindingElement> je vytvořen objekt, jsou neměnné, jako například počet vlastností <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> a <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="73dff-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="73dff-109">Volání `set` k takovým vlastnostem není je změnit.</span><span class="sxs-lookup"><span data-stu-id="73dff-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="73dff-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73dff-110">See also</span></span>

- [<span data-ttu-id="73dff-111">Režimy ověřování SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="73dff-111">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
- [<span data-ttu-id="73dff-112">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="73dff-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
