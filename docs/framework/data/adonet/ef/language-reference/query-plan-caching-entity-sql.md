---
title: Ukládání do mezipaměti plánu dotazů (entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: a0e84f40aed2cff146e4e203cca73a9110de0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149983"
---
# <a name="query-plan-caching-entity-sql"></a>Ukládání do mezipaměti plánu dotazů (entity SQL)
Při každém pokusu o spuštění dotazu, kanál dotazu vyhledá do mezipaměti plánu dotazů a zobrazí, zda je přesný dotaz již zkompilován a k dispozici. Pokud ano, použije plán uložený v mezipaměti, nikoli vytvoření nového. Pokud není nalezena shoda v mezipaměti plánu dotazu, dotaz je zkompilován a uložen do mezipaměti. Dotaz je identifikován [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jeho text a parametr kolekce (názvy a typy). Všechna porovnání textu rozlišují malá a velká písmena.  
  
## <a name="configuration"></a>Konfigurace  
 Ukládání do mezipaměti plánu dotazů lze konfigurovat pomocí aplikace <xref:System.Data.EntityClient.EntityCommand>.  
  
 Chcete-li povolit nebo zakázat ukládání do mezipaměti plánu dotazů, <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>nastavte tuto vlastnost na `true` nebo `false`. Zakázání ukládání plánu do mezipaměti pro jednotlivé dynamické dotazy, které je nepravděpodobné, že budou použity více než jednou zlepší výkon.  
  
 Ukládání do mezipaměti plánu <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>dotazů můžete povolit .  
  
## <a name="recommended-practice"></a>Doporučená praxe  
 Dynamické dotazy je třeba se vyhnout, obecně. Následující příklad dynamického dotazu je zranitelný vůči útokům injektáže SQL, protože přebírá vstup uživatele přímo bez ověření.  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 Pokud používáte dynamicky generované dotazy, zvažte zakázání ukládání do mezipaměti plánu dotazů, abyste zabránili zbytečné spotřebě paměti pro položky mezipaměti, které pravděpodobně nebudou znovu použity.  
  
 Ukládání do mezipaměti plánu dotazů na statické dotazy a parametrizované dotazy může poskytnout výhody výkonu. Následuje příklad statického dotazu:  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Pro dotazy, které mají být správně sladěny mezipaměti plánu dotazů, by měly splňovat následující požadavky:  
  
- Text dotazu by měl být konstantní vzorek, nejlépe konstantní řetězec nebo prostředek.  
  
- <xref:System.Data.EntityClient.EntityParameter>nebo <xref:System.Data.Objects.ObjectParameter> by měly být použity všude tam, kde musí být předána hodnota dodaná uživatelem.  
  
 Měli byste se vyhnout následujícím vzorům dotazů, které zbytečně spotřebovávají sloty v mezipaměti plánu dotazů:  
  
- Změny písmen v textu.  
  
- Změny prázdného místa.  
  
- Změny literálových hodnot.  
  
- Změny textu uvnitř komentářů.  
  
## <a name="see-also"></a>Viz také

- [Přehled Entity SQL](entity-sql-overview.md)
