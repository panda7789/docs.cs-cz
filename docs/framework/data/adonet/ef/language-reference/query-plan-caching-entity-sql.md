---
title: Plán dotazu ukládání do mezipaměti (entita SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 0e00d7f9382fca2af630a8e1d50a5cde5178da05
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="query-plan-caching-entity-sql"></a>Plán dotazu ukládání do mezipaměti (entita SQL)
Vždy, když je proveden pokus o provedení dotazu, kanálu dotaz vyhledává své mezipaměti plánu dotazu zda přesný dotazu je již kompilované a k dispozici. Pokud ano, je opětovně používá plánu v mezipaměti místo vytváření nové. Pokud není nalezena shoda v mezipaměti plánu dotazu, dotaz kompiluje a uloží do mezipaměti. Dotaz je určený podle jeho [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kolekce textu a parametr (názvy a typy). Všechny text porovnávání rozlišuje velká a malá písmena.  
  
## <a name="configuration"></a>Konfigurace  
 Ukládání do mezipaměti plánu dotazu je možné konfigurovat pomocí <xref:System.Data.EntityClient.EntityCommand>.  
  
 K povolení nebo zakázání dotazu plán ukládání do mezipaměti prostřednictvím <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, nastavte tuto vlastnost `true` nebo `false`. Zakázání plánu ukládání do mezipaměti pro jednotlivé dynamických dotazů, které pravděpodobně k použít více než jednou zvyšuje výkon.  
  
 Můžete povolit dotazu plán ukládání do mezipaměti prostřednictvím <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.  
  
## <a name="recommended-practice"></a>Doporučený postup  
 Dynamické dotazy je nutno, obecně. Následující příklad dynamické dotazu je bude zranitelný vůči útoku prostřednictvím injektáže SQL, protože trvá vstup uživatele přímo bez jakéhokoli ověřování.  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 Pokud používáte dynamicky generovaném dotazy, zvažte zákaz dotazu plán ukládání do mezipaměti předejdete spotřeby nepotřebné paměti pro položky mezipaměti, které pravděpodobně znovu použít.  
  
 Plán dotazu ukládání do mezipaměti na statické dotazy a parametrizovaných dotazů můžou poskytovat výhody výkonu. Následuje příklad statické dotazu:  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Pro dotazy lze porovnat správně mezipamětí plán dotazu by měly splňovat následující požadavky:  
  
-   Text dotazu musí být konstantní vzor, pokud možno konstantní řetězec nebo prostředku.  
  
-   <xref:System.Data.EntityClient.EntityParameter> nebo <xref:System.Data.Objects.ObjectParameter> slouží bez ohledu na hodnotu zadanou uživatelem, musí být předán.  
  
 Neměli byste následující typy dotazů, které zbytečně spotřebovávat sloty v mezipaměti plánu dotazu:  
  
-   Změny textu v takovém případě písmeno.  
  
-   Změny mezer.  
  
-   Změny na skutečné hodnoty.  
  
-   Změny text v rámci komentáře.  
  
## <a name="see-also"></a>Viz také  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
