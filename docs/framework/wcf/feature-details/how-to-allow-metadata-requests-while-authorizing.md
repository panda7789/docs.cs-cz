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
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Postupy: Povolení požadavků na metadata při autorizaci
Během autorizace může být nutné povolit žádost pro metadata, aby mohl být zpracován. Následující téma vás provede kroky k ověření této žádosti.  
  
 Další informace o autorizaci Windows Communication Foundation (WCF) najdete v tématu [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>K povolení požadavků na metadata při autorizaci  
  
1.  Vytvoření rozšíření <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.  
  
2.  Přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda. Vrátí metoda `true` nebo `false` v závislosti na tom, zda je povolen autorizace. Informace o aktuální procedury je najít v <xref:System.ServiceModel.OperationContext> jako parametr předaný metodě.  
  
3.  V přepsání zkontrolujte název kontraktu, obor názvů a akce, jak je znázorněno v následujícím příkladu. Pokud podmínky jsou platné, bude vrácen `true.`  
  
4.  Použijte bod rozšiřitelnost využívat třídy. Další informace najdete v tématu [postupy: vytvoření vlastního Správce autorizací pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
