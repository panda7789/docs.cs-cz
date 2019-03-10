---
title: Transakce aktivity ve službě pracovního postupu
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: 7ffd64abdc6edf45174d4b756833d65ec0ef747c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714772"
---
# <a name="transaction-activities-in-wf"></a>Transakce aktivity ve službě pracovního postupu
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Má několik poskytované systémem aktivity pro modelování zrušení, transakce a kompenzace. Těchto programovacích modelů povolit pracovní postup, pokračujte k dalšímu postupu v případě změny v obchodní logiku a zpracování chyb. Další informace o zrušení, transakce a kompenzace najdete v tématu [transakce](workflow-transactions.md), [kompenzace](compensation.md), a [zrušení](modeling-cancellation-behavior-in-workflows.md).  
  
## <a name="transaction-activities"></a>Transakce aktivity  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|Přidruží zrušení logiky ve formuláři aktivity, hlavní cesta provádění, také vyjádřena jako aktivita.|  
|<xref:System.Activities.Statements.CompensableActivity>|Podporuje kompenzaci jeho podřízených aktivit.|  
|<xref:System.Activities.Statements.Compensate>|Explicitně vyvolá obslužnou rutinu <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.Confirm>|Explicitně vyvolá obslužnou rutinu potvrzení <xref:System.Activities.Statements.CompensableActivity>.|  
|<xref:System.Activities.Statements.TransactionScope>|Vymezuje hranice transakce pásma.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|Obory životnost transakce, která inicializuje přijaté zprávy. Transakce mohou byly převedeny do pracovního postupu na zahajující zprávu nebo vytvořené dispečer při doručení zprávy. **Poznámka:**  <xref:System.ServiceModel.Activities.TransactedReceiveScope> Se nachází v **zasílání zpráv** část **nástrojů**.|
