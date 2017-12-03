---
title: "Výjimky transakce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5896f1f7e15fa7ed86f80bbd7c06ae77faded90
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-exceptions"></a>Výjimky transakce
Toto téma uvádí všechny výjimky generované [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] transakce.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|Informace o zásadách importovaných z metadat určuje různé hodnoty pro TransactionProtocol mezi operace. Je podporován pouze jeden TransactionProtocol pro každý koncový bod.|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|Vlastnost TransactionAutoComplete nemůže mít hodnotu false, není-li režim InstanceContextMode služby PerSession. Na implementaci zadaný kontraktu a operace byla nalezena chyba.|  
|SFxTransactionInvalidSetTransactionComplete|OperationContext.SetTransactionComplete lze volat v operaci jenom v případě, že je vlastnost TransactionAutoComplete nastaven na hodnotu false a vlastností TransactionScopeRequired nastavena na hodnotu true. Jedná se o neplatný scénář a aktuální transakce byla ukončena.|  
|TransactionFlowRequiredIssuedTokens|Tok transakcí, předávaných vystavené tokeny musí také podporovat.|  
|TrustDriverVersionDoesNotSupportIssuedTokens|Nakonfigurované verze důvěryhodnosti nepodporuje vystavené tokeny. Použijte WSTrustFeb2005 nebo vyšší.|
