---
title: Porovnání transakcí u modelů COM+ a ServiceModel
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 4a47fe1686dff2e705b06b001d7d5e4ea6e8c5f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857867"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Porovnání transakcí u modelů COM+ a ServiceModel
Toto téma popisuje, jak simulovat transakcí služby COM + s použitím atributů Windows Communication Foundation (WCF) <xref:System.ServiceModel> obor názvů poskytuje.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Emulace pomocí atributy ServiceModel modelu COM +  
 Následující tabulka porovnává <xref:System.EnterpriseServices.TransactionOption> použitý k vytvoření výčtu `EnterpriseServices` transakce a způsob jejich korelaci atributů WCF <xref:System.ServiceModel> obor názvů poskytuje.  
  
|Atribut modelu COM +|Atributy WCF|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> je nastavena na <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je `true`.<br /><br /> `TransactionFlow` Je atribut v elementu vazby `false`.|  
|Požadováno|<xref:System.ServiceModel.TransactionFlowAttribute> je nastavena na <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je `true`.<br /><br /> `TransactionFlow` Je atribut v elementu vazby `true`.|  
|Podporováno|Neexistuje žádný přímý ekvivalent. Obecně platí, by měl přijmout chování určené pro `Required` místo.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> je `false`.<br /><br /> `TransactionFlow` Je atribut v elementu vazby `false`.|  
|Zakázáno|Neexistuje žádný přímý ekvivalent. Obecně platí, by měl přijmout chování určené pro `NotSupported` místo.|
