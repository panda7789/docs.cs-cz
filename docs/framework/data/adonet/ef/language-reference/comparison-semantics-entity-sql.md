---
title: Porovnání sémantiku (entita SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 2184f86ee43f88b0c4cfc1b96e42e2486c17fe5f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765552"
---
# <a name="comparison-semantics-entity-sql"></a>Porovnání sémantiku (entita SQL)
Provádění některý z těchto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory zahrnuje porovnání instance typu:  
  
## <a name="explicit-comparison"></a>Explicitní porovnání  
 Operace rovnosti:  
  
-   =  
  
-   !=  
  
 Řazení operace:  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 Možnost použití hodnoty Null operace:  
  
-   MÁ HODNOTU NULL.  
  
-   NEMÁ HODNOTU NULL  
  
## <a name="explicit-distinction"></a>Explicitní rozdíl  
 Rovnost rozdíl:  
  
-   ODLIŠNÉ  
  
-   SESKUPIT PODLE  
  
 Řazení rozdíl:  
  
-   ŘADIT PODLE  
  
## <a name="implicit-distinction"></a>Implicitní rozdíl  
 Nastavit operace a predikáty (rovnosti):  
  
-   UNION  
  
-   INTERSECT  
  
-   S VÝJIMKOU  
  
-   NASTAVENÍ  
  
-   PŘEKRYTÍ.  
  
 Položka predikáty (rovnosti):  
  
-   V  
  
## <a name="supported-combinations"></a>Podporované kombinace  
 Následující tabulka uvádí podporované kombinace operátory porovnání pro jednotlivé typy typu:  
  
|**Typ**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **ODLIŠNÉ**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**MÁ HODNOTU NULL.**<br /><br /> **NEMÁ HODNOTU NULL**|  
|-|-|-|-|-|-|-|-|  
|Typ entity|REF<sup>1</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|REF<sup>1</sup>|  
|Komplexní typ|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Řádek|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Všechny vlastnosti<sup>4</sup>|Throw<sup>3</sup>|  
|primitivní typ|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|  
|Multimnožina|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|REF|Ano<sup>5</sup>|Ano<sup>5</sup>|Ano<sup>5</sup>|Ano<sup>5</sup>|Throw|Throw|Ano<sup>5</sup>|  
|Přidružení<br /><br /> – typ|Throw<sup>3</sup>|Throw|Throw|Throw|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
  
 <sup>1</sup>odkazy na danou entitu typu instancí jsou implicitně porovnání, jak je znázorněno v následujícím příkladu:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Entity instance nelze porovnat s explicitní odkaz. Pokud je tento pokus, je vyvolána výjimka. Například následující dotaz vyvolá výjimku:  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>vlastnosti komplexních typů se sloučí před odesláním do úložiště, tak, aby se stala porovnatelný z hlediska (pokud jsou jejich vlastnosti porovnatelný z hlediska). Viz také <sup>4.</sup>  
  
 <sup>3</sup>Entity Framework runtime zjistí nepodporované případ a vyvolá smysluplný výjimky bez zapojení zprostředkovatele nebo úložiště.  
  
 <sup>4</sup>je proveden pokus o porovnat všechny vlastnosti. Pokud je vlastnost, která není porovnatelný z hlediska typu, jako je text, ntext nebo image, může být vyvolána výjimka serveru.  
  
 <sup>5</sup>všechny jednotlivé elementy odkazy jsou porovnávány (to zahrnuje název sady entit a všechny vlastnosti klíče typu entity).  
  
## <a name="see-also"></a>Viz také  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
