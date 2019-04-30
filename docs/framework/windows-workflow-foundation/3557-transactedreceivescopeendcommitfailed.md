---
title: 3557 – TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774449"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a>3557 – TransactedReceiveScopeEndCommitFailed
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3557|  
|klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že volání metody endcommit na CommittableTransaction vygenerovalo výjimku TransactionException.  
  
## <a name="message"></a>Zpráva  
 Volání metody EndCommit na třídě CommittableTransaction s id = '%1' vygenerovalo výjimku TransactionException s touto zprávou: '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|TransactionId|xs:string|Id třídy CommittableTransaction.|  
|Výjimka|xs:string|Podrobnosti o výjimce pro výjimku|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
