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
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Postupy: Povolení požadavků na metadata při autorizaci
Při vlastní autorizaci může být nutné, aby bylo možné zpracovat žádost o metadata. Následující téma vás provede jednotlivými kroky pro ověření takové žádosti.  
  
 Další informace o autorizaci Windows Communication Foundation (WCF) najdete v tématu [authorization](authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Povolení požadavků na metadata při autorizaci  
  
1. Vytvořte rozšíření <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.  
  
2. Přepsat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodu. Metoda vrátí `true` nebo `false` v závislosti na tom, jestli je povolená autorizace. Informace o aktuálním postupu najdete v části <xref:System.ServiceModel.OperationContext> předané jako parametr metodě.  
  
3. V přepsání ověřte název kontraktu, obor názvů a akci, jak je znázorněno v následujícím příkladu. Pokud jsou podmínky platné, pak se vrátí`true.`  
  
4. Použijte bod rozšiřitelnosti k využití třídy. Další informace najdete v tématu [Postup: Vytvoření vlastního Správce autorizací pro službu](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Autorizace](authorization-in-wcf.md)
- [Správa deklarací a autorizace s modelem identity](managing-claims-and-authorization-with-the-identity-model.md)
