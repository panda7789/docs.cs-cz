---
title: Stránkování (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 25d52734c30e087629be9923a43e720f94c96d04
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249577"
---
# <a name="paging-entity-sql"></a>Stránkování (Entity SQL)
Fyzické stránkování lze provést pomocí dílčích klauzulí [Skip](skip-entity-sql.md) a [limit](limit-entity-sql.md) v klauzuli [ORDER by](order-by-entity-sql.md) . Chcete-li provést fyzické stránkování v deterministickém případě, použijte příkaz přeskočit a omezit. Pokud chcete omezit počet řádků v důsledku nedeterministického způsobu, měli byste použít [Top](top-entity-sql.md). Klauzule TOP a SKIP a LIMIT se vzájemně vylučují.  
  
## <a name="top-overview"></a>HLAVNÍ přehled  
 Klauzule SELECT může mít volitelnou klauzuli TOP sub podle volitelného modifikátoru ALL/DISTINCT. Dílčí klauzule TOP určuje, že z výsledku dotazu bude vrácena pouze první sada řádků. Další informace najdete v [části Top](top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Přehled pro PŘESKOČENí a omezení  
 Klauzule SKIP a LIMIT jsou součástí klauzule ORDER BY. Pokud je v klauzuli ORDER BY přítomna dílčí klauzule SKIP Expression, výsledky se seřadí podle specifikace řazení a sada výsledků bude obsahovat řádky začínající od dalšího řádku hned za výrazem SKIP. Například PŘESKOČENí 5 přeskočí prvních pět řádků a vrátí se z šestého řádku předá. Pokud je dílčí klauzule výrazu omezení přítomna v klauzuli ORDER BY, dotaz se seřadí podle specifikace řazení a výsledný počet řádků bude omezen výrazem LIMIT. Například omezení 5 omezí výsledek sady na pět instancí nebo řádků. VYNECHÁNí a omezení není nutné používat společně; můžete použít pouze přeskočit nebo pouze omezit pomocí klauzule ORDER BY. Další informace naleznete v následujících tématech:  
  
- [SKIP](skip-entity-sql.md)  
  
- [LIMIT](limit-entity-sql.md)  
  
- [ORDER BY](order-by-entity-sql.md)  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)
- [Postupy: Stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
