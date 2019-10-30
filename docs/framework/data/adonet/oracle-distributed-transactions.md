---
title: Distribuované transakce Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: edd06b94ce4157e90d334ee7feac2a449f7ee74b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040483"
---
# <a name="oracle-distributed-transactions"></a>Distribuované transakce Oracle
Objekt <xref:System.Data.OracleClient.OracleConnection> automaticky zařadí do existující distribuované transakce, pokud zjistí, že je transakce aktivní. K automatickému zařazení transakce dochází, když je připojení otevřeno nebo načteno z fondu připojení. Automatické zařazení v existujících transakcích můžete zakázat zadáním  
  
```csharp  
Enlist=false  
```  
  
 jako parametr připojovacího řetězce pro <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Viz také:

- [Oracle a ADO.NET](oracle-and-adonet.md)
- [Přehled ADO.NET](ado-net-overview.md)
