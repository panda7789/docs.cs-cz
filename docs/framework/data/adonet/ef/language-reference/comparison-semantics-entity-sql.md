---
title: Sémantika porovnání (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 8d7868b0166f0a18824ec25e6cdf639deec665ac
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833934"
---
# <a name="comparison-semantics-entity-sql"></a>Sémantika porovnání (Entity SQL)
Provádění kterékoli z následujících operátorů [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje porovnání instancí typů:  
  
## <a name="explicit-comparison"></a>Explicitní porovnání  
 Operace rovnosti:  
  
- =  
  
- !=  
  
 Operace řazení:  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 Operace s hodnotou null:  
  
- MÁ HODNOTU NULL  
  
- NENÍ NULL  
  
## <a name="explicit-distinction"></a>Explicitní rozlišení  
 Rozlišení rovnosti:  
  
- ZNAK  
  
- GROUP BY  
  
 Rozlišení řazení:  
  
- ŘADIT PODLE  
  
## <a name="implicit-distinction"></a>Implicitní rozlišení  
 Nastavit operace a predikáty (rovnost):  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 Predikáty položky (rovnost):  
  
- IN  
  
## <a name="supported-combinations"></a>Podporované kombinace  
 V následující tabulce jsou uvedeny všechny podporované kombinace relačních operátorů pro každý druh typu:  
  
|**Textový**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **ZNAK**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**< < =**<br /><br /> **> > =**|**ORDER BY**|**MÁ HODNOTU NULL**<br /><br /> **NENÍ NULL**|  
|-|-|-|-|-|-|-|-|  
|Typ entity|Odkaz<sup>1</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Odkaz<sup>1</sup>|  
|komplexní typ|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|řadě|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Všechny vlastnosti<sup>4</sup>|Throw<sup>3</sup>|  
|Primitivní typ|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|  
|Multiset|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|odkazů|Ano<sup>5</sup>|Ano<sup>5</sup>|Ano<sup>5</sup>|Ano<sup>5</sup>|Throw|Throw|Ano<sup>5</sup>|  
|řídí<br /><br /> – typ|Throw<sup>3</sup>|Throw|Throw|Throw|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
  
 <sup>1</sup> Odkazy na dané instance typů entit jsou implicitně porovnány, jak je znázorněno v následujícím příkladu:  
  
```sql  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Instanci entity nelze porovnat s explicitním odkazem. Pokud se to pokusí, je vyvolána výjimka. Například následující dotaz vyvolá výjimku:  
  
```sql  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup> . Vlastnosti komplexních typů jsou před odesláním do úložiště shrnuty, takže se stanou srovnatelnými (pokud jsou všechny jejich vlastnosti srovnatelné). Podívejte se také na <sup>4.</sup>  
  
 <sup>3</sup> . Modul runtime Entity Framework detekuje nepodporovaný případ a vyvolá smysluplnou výjimku bez zásahu poskytovatele nebo úložiště.  
  
 <sup>4</sup> . Byl proveden pokus o porovnání všech vlastností. Pokud existuje vlastnost, která má nesrovnatelný typ, jako je například text, ntext nebo Image, může být vyvolána výjimka serveru.  
  
 <sup>5</sup> . Všechny jednotlivé prvky odkazů jsou porovnávány (to zahrnuje název sady entit a všechny klíčové vlastnosti typu entity).  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
