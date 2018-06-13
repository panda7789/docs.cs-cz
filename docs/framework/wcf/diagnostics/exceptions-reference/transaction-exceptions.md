---
title: Výjimky transakce
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474828"
---
# <a name="transaction-exceptions"></a>Výjimky transakce
Toto téma uvádí všechny výjimky generovaných transakcí Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Informace o zásadách importovaných z metadat určuje různé hodnoty pro TransactionProtocol mezi operace. Je podporován pouze jeden TransactionProtocol pro každý koncový bod.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Vlastnost TransactionAutoComplete nemůže mít hodnotu false, není-li režim InstanceContextMode služby PerSession. Na implementaci zadaný kontraktu a operace byla nalezena chyba.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete lze volat v operaci jenom v případě, že je vlastnost TransactionAutoComplete nastaven na hodnotu false a vlastností TransactionScopeRequired nastavena na hodnotu true. Jedná se o neplatný scénář a aktuální transakce byla ukončena.|  
|TransactionFlowRequiredIssuedTokens|Tok transakcí, předávaných vystavené tokeny musí také podporovat.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|Nakonfigurované verze důvěryhodnosti nepodporuje vystavené tokeny. Použijte WSTrustFeb2005 nebo vyšší.|
