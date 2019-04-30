---
title: Výjimky transakce
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936973"
---
# <a name="transaction-exceptions"></a>Výjimky transakce
Toto téma uvádí všechny výjimky generovaných transakcí Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Informace o zásadách importované z metadat určuje jiné hodnoty pro třídu TransactionProtocol mezi operace. Je podporován pouze jednu třídu TransactionProtocol pro každý koncový bod.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Vlastnost TransactionAutoComplete nemůže být hodnota false, pokud je režim InstanceContextMode služby na hodnotu PerSession. V implementaci zadaný kontrakt a operace byla nalezena chyba.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete může být volána v operaci pouze v případě, že vlastnost TransactionAutoComplete nastavena na hodnotu false a vlastností TransactionScopeRequired je nastavena na hodnotu true. Toto je neplatný scénář a aktuální transakce byla ukončena.|  
|TransactionFlowRequiredIssuedTokens|Tok transakcí, tok vydané tokeny musí podporovat také.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|Nakonfigurovaná verze Trust nepodporuje vydané tokeny. Použijte verzi WSTrustFeb2005 nebo novější.|
