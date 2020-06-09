---
title: 'Postupy: Povolení požadavků na metadata při autorizaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 6d172f9b659804179d23fb382376f83f4898edc5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601306"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="92244-102">Postupy: Povolení požadavků na metadata při autorizaci</span><span class="sxs-lookup"><span data-stu-id="92244-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="92244-103">Při vlastní autorizaci může být nutné, aby bylo možné zpracovat žádost o metadata.</span><span class="sxs-lookup"><span data-stu-id="92244-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="92244-104">Následující téma vás provede jednotlivými kroky pro ověření takové žádosti.</span><span class="sxs-lookup"><span data-stu-id="92244-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="92244-105">Další informace o autorizaci Windows Communication Foundation (WCF) najdete v tématu [authorization](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="92244-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="92244-106">Povolení požadavků na metadata při autorizaci</span><span class="sxs-lookup"><span data-stu-id="92244-106">To allow metadata requests during authorization</span></span>  
  
1. <span data-ttu-id="92244-107">Vytvořte rozšíření <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="92244-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2. <span data-ttu-id="92244-108">Přepsat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="92244-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="92244-109">Metoda vrátí `true` nebo `false` v závislosti na tom, jestli je povolená autorizace.</span><span class="sxs-lookup"><span data-stu-id="92244-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="92244-110">Informace o aktuálním postupu najdete v části <xref:System.ServiceModel.OperationContext> předané jako parametr metodě.</span><span class="sxs-lookup"><span data-stu-id="92244-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3. <span data-ttu-id="92244-111">V přepsání ověřte název kontraktu, obor názvů a akci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="92244-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="92244-112">Pokud jsou podmínky platné, pak se vrátí`true.`</span><span class="sxs-lookup"><span data-stu-id="92244-112">If the conditions are valid, then return `true.`</span></span>  
  
4. <span data-ttu-id="92244-113">Použijte bod rozšiřitelnosti k využití třídy.</span><span class="sxs-lookup"><span data-stu-id="92244-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="92244-114">Další informace najdete v tématu [Postup: Vytvoření vlastního Správce autorizací pro službu](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="92244-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92244-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="92244-115">Example</span></span>  
 <span data-ttu-id="92244-116">Následující příklad ukazuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="92244-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="92244-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="92244-117">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="92244-118">Autorizace</span><span class="sxs-lookup"><span data-stu-id="92244-118">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="92244-119">Správa deklarací a autorizace s modelem identity</span><span class="sxs-lookup"><span data-stu-id="92244-119">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
