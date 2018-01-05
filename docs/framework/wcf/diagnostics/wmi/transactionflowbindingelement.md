---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b073efc47ccc1708bf4c58153b1001a21eee25f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída TransactionFlowBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída TransactionFlowBindingElement má následující vlastnosti:  
  
### <a name="issuedtokens"></a>IssuedTokens  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje požadavek na hlavičku tokeny vydané zabezpečení (IssuedTokens z WS-Trust).  
  
### <a name="transactionprotocol"></a>TransactionProtocol  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Služba směrování transakcí používá protokol transakcí.  
  
### <a name="transactions"></a>Transakce  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Označuje, zda příchozí transakce.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
