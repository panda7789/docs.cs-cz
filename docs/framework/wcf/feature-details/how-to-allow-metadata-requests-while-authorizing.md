---
title: "Postupy: Povolení požadavků na metadata při autorizaci"
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
helpviewer_keywords: allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b388a7517dbab8d30df51bfffac0058ded04bda
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="4fce9-102">Postupy: Povolení požadavků na metadata při autorizaci</span><span class="sxs-lookup"><span data-stu-id="4fce9-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="4fce9-103">Během autorizace může být nutné povolit žádost pro metadata, aby mohl být zpracován.</span><span class="sxs-lookup"><span data-stu-id="4fce9-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="4fce9-104">Následující téma vás provede kroky k ověření této žádosti.</span><span class="sxs-lookup"><span data-stu-id="4fce9-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4fce9-105">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] autorizace, najdete v části [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="4fce9-105"> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="4fce9-106">K povolení požadavků na metadata při autorizaci</span><span class="sxs-lookup"><span data-stu-id="4fce9-106">To allow metadata requests during authorization</span></span>  
  
1.  <span data-ttu-id="4fce9-107">Vytvoření rozšíření <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="4fce9-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2.  <span data-ttu-id="4fce9-108">Přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4fce9-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="4fce9-109">Vrátí metoda `true` nebo `false` v závislosti na tom, zda je povolen autorizace.</span><span class="sxs-lookup"><span data-stu-id="4fce9-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="4fce9-110">Informace o aktuální procedury je najít v <xref:System.ServiceModel.OperationContext> jako parametr předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="4fce9-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3.  <span data-ttu-id="4fce9-111">V přepsání zkontrolujte název kontraktu, obor názvů a akce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4fce9-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="4fce9-112">Pokud podmínky jsou platné, bude vrácen`true.`</span><span class="sxs-lookup"><span data-stu-id="4fce9-112">If the conditions are valid, then return `true.`</span></span>  
  
4.  <span data-ttu-id="4fce9-113">Použijte bod rozšiřitelnost využívat třídy.</span><span class="sxs-lookup"><span data-stu-id="4fce9-113">Use the extensibility point to employ the class.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="4fce9-114">[Postupy: vytvoření vlastního Správce autorizací pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="4fce9-114"> [How to: Create a Custom Authorization Manager for a Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fce9-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fce9-115">Example</span></span>  
 <span data-ttu-id="4fce9-116">Následující příklad ukazuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4fce9-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4fce9-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fce9-117">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="4fce9-118">Autorizace</span><span class="sxs-lookup"><span data-stu-id="4fce9-118">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="4fce9-119">Správa deklarací a autorizace s modelem Identity</span><span class="sxs-lookup"><span data-stu-id="4fce9-119">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
