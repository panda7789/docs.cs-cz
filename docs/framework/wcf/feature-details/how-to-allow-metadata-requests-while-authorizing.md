---
title: 'Postupy: Povolení požadavků na metadata při autorizaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 2f855080cf3ba4cee08470af77c52945e47a2ec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489632"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="58570-102">Postupy: Povolení požadavků na metadata při autorizaci</span><span class="sxs-lookup"><span data-stu-id="58570-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="58570-103">Během autorizace může být nutné povolit žádost pro metadata, aby mohl být zpracován.</span><span class="sxs-lookup"><span data-stu-id="58570-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="58570-104">Následující téma vás provede kroky k ověření této žádosti.</span><span class="sxs-lookup"><span data-stu-id="58570-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="58570-105">Další informace o autorizaci Windows Communication Foundation (WCF) najdete v tématu [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="58570-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="58570-106">K povolení požadavků na metadata při autorizaci</span><span class="sxs-lookup"><span data-stu-id="58570-106">To allow metadata requests during authorization</span></span>  
  
1.  <span data-ttu-id="58570-107">Vytvoření rozšíření <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="58570-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2.  <span data-ttu-id="58570-108">Přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="58570-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="58570-109">Vrátí metoda `true` nebo `false` v závislosti na tom, zda je povolen autorizace.</span><span class="sxs-lookup"><span data-stu-id="58570-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="58570-110">Informace o aktuální procedury je najít v <xref:System.ServiceModel.OperationContext> jako parametr předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="58570-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3.  <span data-ttu-id="58570-111">V přepsání zkontrolujte název kontraktu, obor názvů a akce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="58570-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="58570-112">Pokud podmínky jsou platné, bude vrácen `true.`</span><span class="sxs-lookup"><span data-stu-id="58570-112">If the conditions are valid, then return `true.`</span></span>  
  
4.  <span data-ttu-id="58570-113">Použijte bod rozšiřitelnost využívat třídy.</span><span class="sxs-lookup"><span data-stu-id="58570-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="58570-114">Další informace najdete v tématu [postupy: vytvoření vlastního Správce autorizací pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="58570-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58570-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="58570-115">Example</span></span>  
 <span data-ttu-id="58570-116">Následující příklad ukazuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="58570-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="58570-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="58570-117">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="58570-118">Autorizace</span><span class="sxs-lookup"><span data-stu-id="58570-118">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="58570-119">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="58570-119">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
