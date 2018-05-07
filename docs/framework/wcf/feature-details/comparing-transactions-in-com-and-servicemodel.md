---
title: Porovnání transakcí u modelů COM+ a ServiceModel
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 4a47fe1686dff2e705b06b001d7d5e4ea6e8c5f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Porovnání transakcí u modelů COM+ a ServiceModel
Toto téma popisuje, jak k simulaci chování transakční služby COM + s použitím atributů Windows Communication Foundation (WCF) <xref:System.ServiceModel> poskytuje obor názvů.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Emulace modelu COM + pomocí atributy ServiceModel  
 Následující tabulka porovnává <xref:System.EnterpriseServices.TransactionOption> použít k vytvoření výčtu `EnterpriseServices` transakce a jak se korelovat atributů WCF <xref:System.ServiceModel> poskytuje obor názvů.  
  
|Atribut modelu COM +|Atributy WCF|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> je nastavena na <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je `true`.<br /><br /> `TransactionFlow` Atribut v prvku vazby je `false`.|  
|Požadováno|<xref:System.ServiceModel.TransactionFlowAttribute> je nastavena na <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je `true`.<br /><br /> `TransactionFlow` Atribut v prvku vazby je `true`.|  
|Podporováno|Neexistuje žádný ekvivalent. Obecně platí, musí přijmout nastavení chování `Required` místo.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je `false`.<br /><br /> `TransactionFlow` Atribut v prvku vazby je `false`.|  
|zakázáno|Neexistuje žádný ekvivalent. Obecně platí, musí přijmout nastavení chování `NotSupported` místo.|
