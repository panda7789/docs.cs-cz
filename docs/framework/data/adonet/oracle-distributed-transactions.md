---
title: Distribuované transakce Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 6f910f1dbbe448352c0edd5d1b80df659ac453d4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795144"
---
# <a name="oracle-distributed-transactions"></a>Distribuované transakce Oracle
<xref:System.Data.OracleClient.OracleConnection> Objekt automaticky zařadí do existující distribuované transakce, pokud zjistí, že je transakce aktivní. K automatickému zařazení transakce dochází, když je připojení otevřeno nebo načteno z fondu připojení. Automatické zařazení v existujících transakcích můžete zakázat zadáním  
  
```  
Enlist=false  
```  
  
 jako parametr připojovacího řetězce pro <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Viz také:

- [Oracle a ADO.NET](oracle-and-adonet.md)
- [Přehled ADO.NET](ado-net-overview.md)
