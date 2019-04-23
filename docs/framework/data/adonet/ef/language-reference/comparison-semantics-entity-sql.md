---
title: Sémantika porovnání (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 6b4c4177ebd6c45e00a1ac7774e40a43e0c14a74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083332"
---
# <a name="comparison-semantics-entity-sql"></a>Sémantika porovnání (Entity SQL)
Provádění kterékoli z následujících [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje operátory porovnání instance typu:  
  
## <a name="explicit-comparison"></a>Explicitní porovnání  
 Operace rovnosti:  
  
-   =  
  
-   !=  
  
 Pořadí operací:  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 Možnost použití hodnoty Null operace:  
  
-   MÁ HODNOTU NULL.  
  
-   NENÍ ROVNO HODNOTĚ NULL  
  
## <a name="explicit-distinction"></a>Explicitní rozlišení  
 Rovnost rozdíl:  
  
-   DISTINCT  
  
-   GROUP BY  
  
 Řazení rozdíl:  
  
-   ŘADIT PODLE  
  
## <a name="implicit-distinction"></a>Implicitní rozlišení  
 Operace a predikáty (rovnost) nastavte:  
  
-   UNION  
  
-   INTERSECT  
  
-   EXCEPT  
  
-   SET  
  
-   OVERLAPS  
  
 Predikáty položky (rovnost):  
  
-   IN  
  
## <a name="supported-combinations"></a>Podporované kombinace  
 V následující tabulce jsou uvedeny podporované kombinace operátory porovnání pro každý druh typu:  
  
|**Typ**|**=**<br /><br /> **\!=**|**GROUP BY**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**IS NULL**<br /><br /> **NENÍ ROVNO HODNOTĚ NULL**|  
|-|-|-|-|-|-|-|-|  
|Typ entity|REF<sup>1</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|REF<sup>1</sup>|  
|komplexní typ|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|  
|Řádek|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Všechny vlastnosti<sup>4</sup>|Vyvolat<sup>3</sup>|  
|primitivní typ|Specifické pro zprostředkovatele|Specifické pro zprostředkovatele|Specifické pro zprostředkovatele|Specifické pro zprostředkovatele|Specifické pro zprostředkovatele|Specifické pro zprostředkovatele|Specifické pro zprostředkovatele|  
|Multiset|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|  
|REF|Ano<sup>5</sup>|Ano<sup>5</sup>|Ano<sup>5</sup>|Ano<sup>5</sup>|vyvolání výjimky|vyvolání výjimky|Ano<sup>5</sup>|  
|Přidružení<br /><br />  – typ|Vyvolat<sup>3</sup>|vyvolání výjimky|vyvolání výjimky|vyvolání výjimky|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|Vyvolat<sup>3</sup>|  
  
 <sup>1</sup>odkazy na danou entitu typu instance jsou implicitně porovnání, jak je znázorněno v následujícím příkladu:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Na explicitní odkaz nelze porovnat instanci entity. Pokud se pokus o, je vyvolána výjimka. Například následující dotaz vyvolá výjimku:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>komplexní typy vlastností se sloučí před odesláním do úložiště, takže budou srovnatelné (za předpokladu, jejich vlastnosti jsou srovnatelné). Viz také <sup>4.</sup>  
  
 <sup>3</sup>modul runtime rozhraní Entity Framework detekuje nepodporované případ a vyvolá výjimky na smysluplný bez zapojení zprostředkovatele nebo úložiště.  
  
 <sup>4</sup>je proveden pokus o porovnání všech vlastností. Pokud je vlastnost, která není porovnatelný z hlediska typu, jako je například text, ntext nebo image, může být vyvolána výjimka serveru.  
  
 <sup>5</sup>z odkazů na všechny jednotlivé prvky jsou porovnány (to zahrnuje název sady entit a všechny vlastnosti klíče typu entity).  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
