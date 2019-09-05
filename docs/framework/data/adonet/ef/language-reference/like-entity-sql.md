---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: fbe27f6e25c9d69f092a060fa2c3fbf0abc93318
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250502"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
Určuje, zda určitý znak `String` odpovídá zadanému vzoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Arguments  
 `match`  
 Výraz, který je vyhodnocen jako `String`. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
 `pattern`  
 Vzor, který se má shodovat se `String`zadaným.  
  
 `escape`  
 Řídicí znak.  
  
 NOT  
 Určuje, že výsledek LIKE by měl být negace.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud odpovídá vzoru, v opačném případě `false`. `string`  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]výrazy, které používají operátor LIKE jsou vyhodnocovány podobným způsobem jako výrazy, které jako kritéria filtru používají rovnost. Výrazy, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] které používají operátor LIKE, však mohou zahrnovat literály i zástupné znaky.  
  
 Následující tabulka popisuje syntaxi vzoru `string`.  
  
|Zástupný znak|Popis|Příklad|  
|------------------------|-----------------|-------------|  
|%|Jakékoli `string` nula nebo více znaků.|`title like '%computer%'`Vyhledá všechny nadpisy, `"computer"` které mají slovo kdekoli v názvu.|  
|_ (podtržítko)|Libovolný jeden znak.|`firstname like '_ean'`Vyhledá všechny čtyři písmena příjmení, které končí `"ean`na, například Dean nebo Novák.|  
|[ ]|Libovolný jeden znak v zadaném rozsahu ([a-f]) nebo set ([abcdef]).|`lastname like '[C-P]arsen'`vyhledá poslední názvy končící řetězcem "arsen" a počínaje libovolným znakem mezi C a P, jako je například Carsen nebo Larsen.|  
|[^]|Libovolný jeden znak, který není v zadaném rozsahu ([^ a-f]) nebo set ([^ abcdef]).|`lastname like 'de[^l]%'`Vyhledá všechny poslední názvy začínající písmenem "de" a neobsahují "l" jako následující písmeno.|  
  
> [!NOTE]
> Operátor LIKE a řídicí klauzuli nelze použít na `System.DateTime` hodnoty nebo `System.Guid`. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
 Podobně jako podporuje porovnávání vzorů ASCII a porovnávání vzorů znakové sady Unicode. Pokud jsou všechny parametry znaky ASCII, je proveden porovnávání vzorů ASCII. Pokud je jedním nebo více argumenty kódování Unicode, jsou všechny argumenty převedeny na porovnávání vzorů Unicode a Unicode. Pokud používáte kódování Unicode s PODOBNÝm znakem, jsou koncové mezery významné. Avšak pro jiné než Unicode není koncová mezera významná. Syntaxe řetězcového vzoru [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je stejná jako v jazyce Transact-SQL.  
  
 Vzor může obsahovat běžné znaky a zástupné znaky. Během porovnávání vzorů musí regulární znaky přesně odpovídat znakům zadaným ve znaku `string`. Zástupné znaky však mohou být porovnány s libovolnými fragmenty řetězce znaků. Pokud se používá se zástupnými znaky, operátor LIKE je flexibilnější než operátory porovnání řetězců = a! =.  
  
> [!NOTE]
> Pokud cílíte na konkrétního poskytovatele, můžete použít rozšíření specifická pro daného poskytovatele. Nicméně takové konstrukce mohou být zpracovány odlišně jinými poskytovateli, například. SqlServer podporuje vzory [First-Last] a [^ First-Last], kde předchozí odpovídá přesně jednomu znaku mezi první a poslední a druhá odpovídá přesně jednomu znaku, který není mezi první a poslední.  
  
### <a name="escape"></a>Escape  
 Pomocí klauzule ESCAPE můžete hledat řetězce znaků, které zahrnují jeden nebo více speciálních zástupných znaků popsaných v tabulce v předchozí části. Předpokládejme například, že několik dokumentů obsahuje v názvu literál "100%" a chcete vyhledat všechny tyto dokumenty. Vzhledem k tomu, že procento (%) znak je zástupným znakem, je nutné jej pomocí [!INCLUDE[esql](../../../../../../includes/esql-md.md)] řídicí klauzule pro úspěšné spuštění hledání provést. Následuje příklad tohoto filtru.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 V tomto hledaném výrazu je procentuální hodnota zástupného znaku (%) ihned po znaku vykřičníku (!) je považován za literál, nikoli jako zástupný znak. Můžete použít libovolný znak jako řídicí znak s výjimkou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zástupných znaků a čtvercových závorek (`[ ]`) znaků. V předchozím příkladu znak vykřičník (!) je řídicí znak.  
  
## <a name="example"></a>Příklad  
 Následující dva [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy používají operátory LIKE a Escape k určení, zda konkrétní řetězec znaků odpovídá zadanému vzoru. První dotaz vyhledá `Name` znak, který začíná znaky `Down_`. Tento dotaz používá možnost Escape, protože podtržítko (`_`) je zástupným znakem. Bez určení možnosti Escape dotaz vyhledá všechny `Name` hodnoty, které začínají slovem `Down` následovaným libovolným jedním znakem, který je jiný než znak podtržítka. Dotazy jsou založené na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
