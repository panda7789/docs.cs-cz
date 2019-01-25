---
title: Stejně jako (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 406e660efcc351df3fd2720a5d13d8398d1a8216
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536968"
---
# <a name="like-entity-sql"></a>Stejně jako (Entity SQL)
Určuje, zda konkrétní znak `String` odpovídá zadanému vzoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Arguments  
 `match`  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Výraz, který se vyhodnotí `String`.  
  
 `pattern`  
 Vzor odpovídá zadanému `String`.  
  
 `escape`  
 Řídicí znak.  
  
 NOT  
 Určuje, že bude výsledek jako negovat.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `string` shoduje se vzorem; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazy, které používají operátor LIKE se vyhodnocují prakticky stejně jako výrazy, které používají rovnosti jako kritéria filtru. Ale [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazů, které používají operátor LIKE může zahrnovat literály a zástupné znaky.  
  
 Následující tabulka popisuje syntaxi vzor `string`.  
  
|Zástupný znak|Popis|Příklad|  
|------------------------|-----------------|-------------|  
|%|Žádné `string` nula nebo více znaků.|`title like '%computer%'` Vyhledá všechny Tituly s slovo `"computer"` kdekoliv v názvu.|  
|_ (podtržítko)|Libovolný znak.|`firstname like '_ean'` Vyhledá všechny čtyřpísmenný křestní jména, které končí `"ean`, "například Dean nebo pracovníka.|  
|[ ]|Kterýkoli jednotlivý znak v zadaném rozsahu ([-f]), nebo nastavte ([abcdef]).|`lastname like '[C-P]arsen'` Najde poslední názvy končící na "arsen" a počínaje mezi jazyky C a P, jako je například Carsen nebo Larsen jednoho libovolného znaku.|  
|[^]|Jeden libovolný znak není v zadaném rozsahu ([^-f]), nebo nastavte ([^ abcdef]).|`lastname like 'de[^l]%'` Vyhledá všechny poslední názvy, které začínají řetězcem "de" a nemusí obsahovat písmeno "l".|  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Jako operátor a ODCHODOVOU klauzuli nelze použít pro `System.DateTime` nebo `System.Guid` hodnoty.  
  
 NAPŘÍKLAD porovnávání aplikace podporuje ASCII a Unicode porovnávání vzorů. Všechny parametry jsou znaky ASCII, provádí ASCII porovnávání vzorů. Pokud jeden nebo více argumentů Unicode, jsou všechny argumenty převést do kódování Unicode a porovnávání vzorů Unicode se provádí. Při použití kódování Unicode s podobné koncové mezery jsou významné. ale pro kódování Unicode, koncové mezery nejsou důležité. Syntaxe řetězce vzor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je stejné jako u [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
 Vzorek může obsahovat regulární znaky a zástupné znaky. Při porovnávání vzorů, pravidelné znaky se musí přesně shodovat znaků určených v znak `string`. Zástupné znaky, ale mohou odpovídat fragmenty libovolného řetězce znaků. Při použití se zástupnými znaky, je flexibilnější, než = operátor LIKE a! = operátory porovnání řetězců.  
  
> [!NOTE]
>  Pokud je cílem konkrétního zprostředkovatele můžete použít rozšíření specifické pro zprostředkovatele. Ale tyto konstrukce může považovat za odlišně podle jiných poskytovatelů, třeba. Systému SQL Server podporuje [první poslední] a [^ první poslední] vzory, kde dřívější odpovídá přesně jeden znak mezi první a poslední a druhá možnost odpovídá přesně jeden znak, který není mezi první a poslední.  
  
### <a name="escape"></a>Escape  
 Pomocí řídicí klauzule můžete hledat řetězce znaků, které zahrnují jeden nebo více speciální zástupné znaky jsou popsané v tabulce v předchozí části. Předpokládejme například, několik dokumentů obsahují literál "100 %" v názvu a chcete hledat ve všech těchto dokumentů. Protože znak procent (%) je zástupný znak, musíte před něj pomocí [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ODCHODOVOU klauzuli úspěšně provést hledání. Následuje příklad tohoto filtru.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 V tomto výrazu vyhledávání procenta zástupný znak (%) hned za znak vykřičník (!) je považován za literál, místo jako zástupný znak. Můžete použít libovolný znak jako řídicí znak s výjimkou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zástupné znaky a druhou mocninu závorka (`[ ]`) znaků. V předchozím příkladu znak vykřičník (!) je řídicí znak.  
  
## <a name="example"></a>Příklad  
 Následující dva [!INCLUDE[esql](../../../../../../includes/esql-md.md)] použít podobné dotazy a řídicí operátory k určení, zda řetězec konkrétní znak odpovídá zadanému vzoru. Vyhledá první dotaz `Name` , které začíná znaky `Down_`. Tento dotaz používá možnost řídicí, protože podtržítko (`_`) je zástupný znak. Bez zadání možnosti řídicí, dotaz bude vyhledávat libovolné `Name` hodnoty, které začínají slovem `Down` za nímž následuje jakémukoli jednomu znaku jiného než podtržítko. Dotazy jsou založeny na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
