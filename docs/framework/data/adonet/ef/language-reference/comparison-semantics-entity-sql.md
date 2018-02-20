---
title: "Porovnání sémantiku (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e20d47e0ae97067d2dcafcf929f717598d4e3e80
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2018
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
  
-   DISTINCT  
  
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
  
|Typ|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|MÁ HODNOTU NULL.<br /><br /> NEMÁ HODNOTU NULL|  
|-|-|-|-|-|-|-|-|  
|Typ entity|Ref<sup>1</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Ref<sup>1</sup>|  
|Komplexní typ|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Řádek|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Všechny vlastnosti<sup>4</sup>|Throw<sup>3</sup>|  
|primitivní typ|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|Specifický pro zprostředkovatele|  
|Multiset|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
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
