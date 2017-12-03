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
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Postupy: Povolení požadavků na metadata při autorizaci
Během autorizace může být nutné povolit žádost pro metadata, aby mohl být zpracován. Následující téma vás provede kroky k ověření této žádosti.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] autorizace, najdete v části [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>K povolení požadavků na metadata při autorizaci  
  
1.  Vytvoření rozšíření <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.  
  
2.  Přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda. Vrátí metoda `true` nebo `false` v závislosti na tom, zda je povolen autorizace. Informace o aktuální procedury je najít v <xref:System.ServiceModel.OperationContext> jako parametr předaný metodě.  
  
3.  V přepsání zkontrolujte název kontraktu, obor názvů a akce, jak je znázorněno v následujícím příkladu. Pokud podmínky jsou platné, bude vrácen`true.`  
  
4.  Použijte bod rozšiřitelnost využívat třídy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: vytvoření vlastního Správce autorizací pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
