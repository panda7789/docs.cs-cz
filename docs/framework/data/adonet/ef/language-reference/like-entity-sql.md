---
title: JAKO (entita SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: f2d06b364c577b581bb64af0436c133ca830bb2b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="like-entity-sql"></a>JAKO (entita SQL)
Určuje, zda konkrétní znak `String` odpovídá zadanému vzoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Arguments  
 `match`  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Výraz, který se vyhodnocuje `String`.  
  
 `pattern`  
 Vzor tak, aby odpovídala na zadaný `String`.  
  
 `escape`  
 Řídicí znak.  
  
 NENÍ  
 Určuje, že se Negované výsledek jako.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `string` odpovídá vzorku, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazy, které používají operátor LIKE se vyhodnocují prakticky stejně jako výrazy, které používají rovnosti jako kritéria filtru. Ale [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazy, které používají operátor LIKE může zahrnovat literály a zástupné znaky.  
  
 Následující tabulka popisuje syntaxe vzoru `string`.  
  
|Zástupný znak|Popis|Příklad|  
|------------------------|-----------------|-------------|  
|%|Všechny `string` nula nebo více znaků.|`title like '%computer%'` Vyhledá všechny Tituly s slovo `"computer"` kdekoli v názvu.|  
|_ (podtržítko)|Jednoho libovolného znaku.|`firstname like '_ean'` Vyhledá všechny názvy první čtyři písmeno, které končí `"ean`, "například Dean nebo pracovníka.|  
|[ ]|Všechny jeden znak v zadaném rozsahu ([-f]) nebo nastavte ([abcdef]).|`lastname like '[C-P]arsen'` Najde poslední názvy konče "arsen" a počínaje mezi C a P, jako je například Carsen nebo Lomikar jednoho libovolného znaku.|  
|[^]|Libovolný znak není v zadaném rozsahu ([^-f]), nebo nastavte ([^ abcdef]).|`lastname like 'de[^l]%'` Vyhledá všechny poslední názvy, které začínají řetězcem "de" a "l" jako písmeno nezahrnují.|  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Jako operátor a klauzule řídicí nelze použít pro `System.DateTime` nebo `System.Guid` hodnoty.  
  
 JAKO porovnávání vzorů podporuje ASCII a Unicode porovnávání vzorů. Všechny parametry jsou znaky ASCII, provádí porovnávání vzorů ASCII. Pokud jeden nebo více parametrů je kódování Unicode, všechny argumenty se převede na kódování Unicode a porovnávání vzorů Unicode se provádí. Použijete-li se jako Unicode, koncové mezery jsou důležitá; ale pro kódování Unicode, koncové mezery nejsou důležité. Syntaxe řetězec vzor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je stejný jako u [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
 Vzor může obsahovat regulární znaky a zástupné znaky. Při porovnávání vzorů regulární znaků se musí přesně shodovat zadané v znak znaky `string`. Zástupné znaky je však možné přidružit k libovolné fragmenty řetězcem znaků. Pokud se používá se zástupnými znaky, je flexibilnější než = operátor LIKE a! = operátory porovnání řetězce.  
  
> [!NOTE]
>  Pokud cílíte konkrétního poskytovatele, můžete použít rozšíření specifický pro zprostředkovatele. Však takové konstrukce může být zpracovávat odděleně podle jiných poskytovatelů, třeba. SQL Server podporuje [první last] a [^ první poslední] vzory kde bývalé odpovídá přesně jeden znak mezi první a poslední a pozdější odpovídá přesně jeden znak, který není mezi první a poslední.  
  
### <a name="escape"></a>Escape  
 Pomocí klauzule řídicí můžete vyhledat znakové řetězce, které obsahují jeden nebo více speciální zástupné znaky popsané v tabulce v předchozí části. Předpokládejme například, několik dokumentů zahrnout literálu "100 %" v názvu a chcete hledat u všech těchto dokumentů. Protože znak procenta (%) je zástupný znak, musí se vyhnuli, pomocí [!INCLUDE[esql](../../../../../../includes/esql-md.md)] řídicí klauzule úspěšně provést hledání. Následuje příklad tento filtr.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 V tomto výrazu vyhledávání procenta zástupného znaku (%), hned za znak vykřičníkem (!) je považována za literál, místo jako zástupný znak. Můžete použít libovolný znak jako řídicí znak s výjimkou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zástupné znaky a druhou mocninu závorka (`[ ]`) znaků. V předchozím příkladu znak vykřičníkem (!) je řídicí znak.  
  
## <a name="example"></a>Příklad  
 Následující dva [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy pomocí LIKE a operátory řídicí k určení, zda řetězec znaků konkrétní odpovídá zadanému vzoru. První dotaz vyhledává `Name` , které začíná znaky `Down_`. Tento dotaz používá možnost řídicí, protože podtržítko (`_`) je zástupný znak. Bez zadání možnosti řídicí, dotaz by vyhledávat libovolné `Name` hodnoty, které začínat slovem `Down` následuje libovolný znak než znak podtržítka. Dotazy jsou založené na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
