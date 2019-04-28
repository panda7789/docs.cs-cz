---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641681"
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třídy TransactionFlowBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídy TransactionFlowBindingElement má následující vlastnosti:  
  
### <a name="issuedtokens"></a>IssuedTokens  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Určuje požadavek pro hlavičku tokeny vydané zabezpečení (IssuedTokens z WS-Trust).  
  
### <a name="transactionprotocol"></a>transactionProtocol  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Protokol transakce použitý službou pro tok transakcí.  
  
### <a name="transactions"></a>Transakce  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Označuje, zda je příchozí transakce.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
