---
title: "Porovnání transakcí u modelů COM+ a ServiceModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e3df31060a9c71e0b2868aa34373bca221fa79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Porovnání transakcí u modelů COM+ a ServiceModel
Toto téma popisuje, jak k simulaci chování transakcí modelu COM + službu pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] atributy <xref:System.ServiceModel> poskytuje obor názvů.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Emulace modelu COM + pomocí atributy ServiceModel  
 Následující tabulka porovnává <xref:System.EnterpriseServices.TransactionOption> použít k vytvoření výčtu `EnterpriseServices` transakce a jak se korelaci do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] atributy <xref:System.ServiceModel> poskytuje obor názvů.  
  
|Atribut modelu COM +|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]atributy|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute>je nastavena na <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>je `true`.<br /><br /> `TransactionFlow` Atribut v prvku vazby je `false`.|  
|Požadováno|<xref:System.ServiceModel.TransactionFlowAttribute>je nastavena na <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>je `true`.<br /><br /> `TransactionFlow` Atribut v prvku vazby je `true`.|  
|Podporováno|Neexistuje žádný ekvivalent. Obecně platí, musí přijmout nastavení chování `Required` místo.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>je `false`.<br /><br /> `TransactionFlow` Atribut v prvku vazby je `false`.|  
|zakázáno|Neexistuje žádný ekvivalent. Obecně platí, musí přijmout nastavení chování `NotSupported` místo.|
