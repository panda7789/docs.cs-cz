---
title: Porovnání sémantiky (entita SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150451"
---
# <a name="comparison-semantics-entity-sql"></a>Porovnání sémantiky (entita SQL)
Provedení některého z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujících operátorů zahrnuje porovnání instance typu:  
  
## <a name="explicit-comparison"></a>Explicitní porovnání  
 Operace rovnosti:  
  
- =  
  
- !=  
  
 Objednávání operací:  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 Operace s nulovou hodnotou:  
  
- JE NULL  
  
- NENÍ NULL  
  
## <a name="explicit-distinction"></a>Explicitní rozlišení  
 Rozlišení rovnosti:  
  
- DISTINCT  
  
- GROUP BY  
  
 Rozlišování objednávek:  
  
- ORDER BY  
  
## <a name="implicit-distinction"></a>Implicitní rozlišení  
 Nastavení operací a predikátů (rovnost):  
  
- UNION  
  
- INTERSECT  
  
- EXCEPT  
  
- SET  
  
- OVERLAPS  
  
 Predikáty položek (rovnost):  
  
- IN  
  
## <a name="supported-combinations"></a>Podporované kombinace  
 V následující tabulce jsou uvedeny všechny podporované kombinace operátorů porovnání pro každý typ:  
  
|**Typ**|**=**<br /><br /> **!=**|**SKUPINA PODLE**<br /><br /> **Odlišné**|**Unie**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **Nastavit**<br /><br /> **OVERLAPS**|**In**|**< <=**<br /><br /> **> >=**|**ORDER BY**|**JE NULL**<br /><br /> **NENÍ NULL**|  
|-|-|-|-|-|-|-|-|  
|Typ entity|Ref<sup>1</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Všechny vlastnosti<sup>2</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Ref<sup>1</sup>|  
|Komplexní typ|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|  
|Řádek|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Všechny vlastnosti<sup>4</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Všechny vlastnosti<sup>4</sup>|Hod<sup>3</sup>|  
|Primitivní typ|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|Specifické pro poskytovatele|  
|Vícesetový soubor|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|  
|Ref|Ano<sup>5</sup>|Ano<sup>5</sup>|Ano<sup>5</sup>|Ano<sup>5</sup>|Throw|Throw|Ano<sup>5</sup>|  
|Přidružení<br /><br /> type|Hod<sup>3</sup>|Throw|Throw|Throw|Hod<sup>3</sup>|Hod<sup>3</sup>|Hod<sup>3</sup>|  
  
 <sup>1.</sup> Odkazy na dané instance typu entity jsou implicitně porovnány, jak je znázorněno v následujícím příkladu:  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Instanci entity nelze porovnat s explicitním odkazem. Pokud se o to pokusí, je vyvolána výjimka. Například následující dotaz vyvolá výjimku:  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <sup>2.</sup> Vlastnosti komplexních typů jsou před odesláním do obchodu srovnány se slouhány, takže se stanou srovnatelnými (pokud jsou všechny jejich vlastnosti srovnatelné). Viz také <sup>4.</sup>  
  
 <sup>3.</sup> Modul runtime Entity Framework detekuje nepodporovaný případ a vyvolá smysluplnou výjimku bez zapojení zprostředkovatele nebo úložiště.  
  
 <sup>4.</sup> Je proveden pokus o porovnání všech vlastností. Pokud je vlastnost, která je nesrovnatelného typu, jako je například text, ntext nebo obrázek, může být vyvolána výjimka serveru.  
  
 <sup>5.</sup> Porovnávají se všechny jednotlivé prvky odkazů (to zahrnuje název sady entit a všechny klíčové vlastnosti typu entity).  
  
## <a name="see-also"></a>Viz také

- [Přehled Entity SQL](entity-sql-overview.md)
