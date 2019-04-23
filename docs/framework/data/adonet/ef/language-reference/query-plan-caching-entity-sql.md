---
title: Plán dotazu, ukládání do mezipaměti (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 9f042d46d9a601c1091e36f8d81ce8f933140b20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178175"
---
# <a name="query-plan-caching-entity-sql"></a>Plán dotazu, ukládání do mezipaměti (Entity SQL)
Pokaždé, když je proveden pokus o provedení dotazu, kanál dotaz vyhledá mezipaměti plánu dotazu, jestli přesně dotazu je již kompilované a k dispozici. Pokud ano, jeho opakované používání plánů v mezipaměti namísto vytváření nové. Pokud se najde shoda v mezipaměti plánu dotazu dotazu je zkompilován a uložili do mezipaměti. Dotaz je identifikován jeho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text a parametr kolekce (názvy a typy). Všechna porovnání textu rozlišují malá a velká písmena.  
  
## <a name="configuration"></a>Konfigurace  
 Ukládání do mezipaměti plánu dotazu se dají konfigurovat prostřednictvím <xref:System.Data.EntityClient.EntityCommand>.  
  
 K povolení nebo zakázání dotazu ukládání do mezipaměti plánu prostřednictvím <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, nastavte tuto vlastnost na `true` nebo `false`. Zakázání ukládání do mezipaměti plánu pro jednotlivé dynamických dotazů, které je nepravděpodobné, že chcete použít více než jednou zvyšuje výkon.  
  
 Můžete povolit dotazu ukládání do mezipaměti plánu prostřednictvím <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.  
  
## <a name="recommended-practice"></a>Doporučený postup  
 Mělo by se vyhnout dynamické dotazy, Obecné. Následující příklad dynamický dotaz je ohrožen útoky prostřednictvím injektáže SQL, protože ho využívá uživatelský vstup přímo bez jakéhokoli ověřování.  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 Pokud používáte dynamicky generované dotazy, vezměte v úvahu zakazuje dotaz ukládání do mezipaměti plánu, aby zbytečného spotřeby pro položky mezipaměti, které pravděpodobně znovu použít.  
  
 Plán dotazu do mezipaměti na statické dotazy a parametrizované dotazy můžete zadat přinese zlepšení výkonu. Následuje příklad statické dotazu:  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Pro dotazy se nezúčastní správně mezipaměti plánu dotazu by měly splňovat následující požadavky:  
  
-   Text dotazu by měl být konstantní vzorek, pokud možno konstanty typu řetězec nebo prostředek.  
  
-   <xref:System.Data.EntityClient.EntityParameter> nebo <xref:System.Data.Objects.ObjectParameter> by měl použít, kdykoli se musí předávat hodnotu zadanou uživatelem.  
  
 Měli byste se vyhnout následující vzory dotazů, které zbytečně spotřebovávají sloty v mezipaměti plánu dotazu:  
  
-   Změny písmena v textu.  
  
-   Změní na prázdný znak.  
  
-   Změny na literálové hodnoty.  
  
-   Změny v textu v komentářích.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
