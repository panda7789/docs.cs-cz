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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 712f8a7a153d7255275ff7ebaa647d5a624f8ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
