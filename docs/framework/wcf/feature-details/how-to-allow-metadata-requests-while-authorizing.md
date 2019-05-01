---
title: 'Postupy: Povolení požadavků na metadata při autorizaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: bea4f7e90df29678697fe6708bdc6a73145522db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047799"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Postupy: Povolení požadavků na metadata při autorizaci
Během autorizace může být potřeba povolit požadavek na metadata ke zpracování. Následující téma vás provede kroky k ověření žádosti.  
  
 Další informace o povolení Windows Communication Foundation (WCF), najdete v části [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>K povolení požadavků na metadata při autorizaci  
  
1. Vytvoření rozšíření <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.  
  
2. Přepsat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody. Metoda vrátí `true` nebo `false` v závislosti na tom, zda je povoleno ověření. Informace o aktuálním postupu najdete v <xref:System.ServiceModel.OperationContext> jako parametr předán metodě.  
  
3. V přepsání zkontrolujte název smlouvy, obor názvů a akce, jak je znázorněno v následujícím příkladu. Pokud podmínky jsou platné, bude vrácen `true.`  
  
4. Můžete použít třídu bodu rozšiřitelnosti. Další informace najdete v tématu [jak: Vytvoření vlastního Správce autorizací pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
