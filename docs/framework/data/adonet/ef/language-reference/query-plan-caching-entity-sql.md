---
title: Ukládání plánu dotazu do mezipaměti (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: ca95f3aed5c092247a97bbfe5b0237a45b95ae16
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249286"
---
# <a name="query-plan-caching-entity-sql"></a>Ukládání plánu dotazu do mezipaměti (Entity SQL)
Pokaždé, když se vytvoří dotaz, kanál dotazu vyhledá svou mezipaměť plánu dotazů a zjistí, jestli je už přesný dotaz kompilovaný a dostupný. V takovém případě znovu použije plán v mezipaměti namísto sestavování nového. Pokud se shoda nenajde v mezipaměti plánu dotazů, dotaz se zkompiluje a uloží do mezipaměti. Dotaz je identifikován jeho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekcí text a parametrů (názvy a typy). U všech porovnávání textu se rozlišují velká a malá písmena.  
  
## <a name="configuration"></a>Konfiguraci  
 Mezipaměť plánu dotazů je možné nakonfigurovat prostřednictvím <xref:System.Data.EntityClient.EntityCommand>.  
  
 Pokud chcete povolit nebo zakázat ukládání do mezipaměti <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>v plánu dotazů, nastavte `true` tuto `false`vlastnost na nebo. Když se zakáže ukládání do mezipaměti pro jednotlivé dynamické dotazy, které se nepravděpodobné použití víc než po zvýšení výkonu.  
  
 Můžete povolit ukládání do mezipaměti plánu dotazů <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>prostřednictvím.  
  
## <a name="recommended-practice"></a>Doporučený postup  
 Dynamické dotazy by se měly vyhnout, obecně. Následující příklad dynamického dotazu je zranitelný vůči útokům prostřednictvím injektáže SQL, protože přebírá vstup uživatele přímo bez ověření.  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 Pokud používáte dynamicky generované dotazy, zvažte zakázání ukládání plánu dotazů do mezipaměti, aby nedocházelo k zbytečným spotřebám paměti pro položky mezipaměti, které se pravděpodobně znovu nepoužívají.  
  
 Ukládání plánu dotazů do mezipaměti pro statické dotazy a parametrizované dotazy může poskytovat výhody týkající se výkonu. Následuje příklad statického dotazu:  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Aby se dotazy správně shodovaly s mezipamětí plánu dotazů, měly by splňovat následující požadavky:  
  
- Text dotazu by měl být konstantním vzorem, nejlépe s konstantním řetězcem nebo prostředkem.  
  
- <xref:System.Data.EntityClient.EntityParameter>nebo <xref:System.Data.Objects.ObjectParameter> by se měl použít všude, kde musí být předána hodnota zadaná uživatelem.  
  
 Měli byste se vyhnout následujícím vzorům dotazů, které zbytečně využívají sloty v mezipaměti plánu dotazů:  
  
- Změní velikost písmen v textu.  
  
- Změny prázdného místa.  
  
- Změny hodnot literálů.  
  
- Změny textu v komentářích.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
