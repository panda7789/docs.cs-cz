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
ms.openlocfilehash: 5229c872c4843df916cf538b7f2e88e451dc6b9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
