---
title: Transakce aktivity v WF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6132f1d9cbeef3ed7af5d2b711d04e8bd5755bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-activities-in-wf"></a>Transakce aktivity v WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Má několik poskytované systémem aktivity pro modelování transakce, kompenzace a zrušení. Těchto programovacích modelů povolit v pracovním postupu pokračovat k dalšímu postupu v případě změny v obchodní logiku a zpracování chyb. [!INCLUDE[crabout](../../../includes/crabout-md.md)]transakce, kompenzace a zrušení, najdete v části [transakce](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md), [kompenzace](../../../docs/framework/windows-workflow-foundation/compensation.md), a [zrušení](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>Transakce aktivity  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|Zrušení logiku ve formě aktivity, přidruží hlavní cesta provádění také vyjádřený jako aktivita.|  
|<xref:System.Activities.Statements.CompensableActivity>|Podporuje kompenzace jeho podřízené aktivity.|  
|<xref:System.Activities.Statements.Compensate>|Explicitně volá obslužnou rutinu kompenzace z <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.Confirm>|Explicitně volá obslužnou rutinu potvrzení z <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.TransactionScope>|Vymezuje pásma hranici transakce.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Obory životnost transakci, která se spouští pomocí přijaté zprávy. Transakce může plynoucích do pracovního postupu na inicializace zprávu nebo vytvoří dispečera, když doručení zprávy. **Poznámka:** <xref:System.ServiceModel.Activities.TransactedReceiveScope> se nachází v **zasílání zpráv** části **sada nástrojů**.|
