---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: c2fb32c4c693cbfc487ce89b36f013398cbdb703
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
