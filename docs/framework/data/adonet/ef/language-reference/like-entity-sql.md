---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: f9e33c78235f637e0aa0622d9d8cc30255722beb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319671"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
Určuje, zda určitý znak `String` odpovídá zadanému vzoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Argumenty  
 `match`  
 Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)], který je vyhodnocen jako `String`.  
  
 `pattern`  
 Vzor, který odpovídá určenému `String`.  
  
 `escape`  
 Řídicí znak.  
  
 NOT  
 Určuje, že výsledek LIKE by měl být negace.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, pokud `string` odpovídá vzoru; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazy, které používají operátor LIKE jsou vyhodnocovány podobným způsobem jako výrazy, které jako kritéria filtru používají rovnost. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazy, které používají operátor LIKE, však mohou zahrnovat literály i zástupné znaky.  
  
 Následující tabulka popisuje syntaxi `string`vzorů.  
  
|Zástupný znak|Popis|Příklad|  
|------------------------|-----------------|-------------|  
|%|Jakékoli `string` nula nebo více znaků.|`title like '%computer%'` vyhledá všechny nadpisy se slovem `"computer"` kdekoli v názvu.|  
|_ (podtržítko)|Libovolný jeden znak.|`firstname like '_ean'` najde názvy všech čtyř písmen, které končí `"ean`, například Dean nebo Novák.|  
|[ ]|Libovolný jeden znak v zadaném rozsahu ([a-f]) nebo set ([abcdef]).|`lastname like '[C-P]arsen'` vyhledá příjmení končící řetězcem "arsen" a počínaje jakýmkoli jedním znakem v rozsahu C až P, jako je například Carsen nebo Larsen.|  
|[^]|Libovolný jeden znak, který není v zadaném rozsahu ([^ a-f]) nebo set ([^ abcdef]).|`lastname like 'de[^l]%'` vyhledá všechny poslední názvy začínající písmenem "de" a neobsahují "l" jako následující písmeno.|  
  
> [!NOTE]
> Klauzuli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE and ESCAPE nelze použít pro hodnoty `System.DateTime` nebo `System.Guid`.  
  
 Podobně jako podporuje porovnávání vzorů ASCII a porovnávání vzorů znakové sady Unicode. Pokud jsou všechny parametry znaky ASCII, je proveden porovnávání vzorů ASCII. Pokud je jedním nebo více argumenty kódování Unicode, jsou všechny argumenty převedeny na porovnávání vzorů Unicode a Unicode. Pokud používáte kódování Unicode s PODOBNÝm znakem, jsou koncové mezery významné. Avšak pro jiné než Unicode není koncová mezera významná. Syntaxe řetězcového vzoru [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je stejná jako v jazyce Transact-SQL.  
  
 Vzor může obsahovat běžné znaky a zástupné znaky. Během porovnávání vzorů musí regulární znaky přesně odpovídat znakům zadaným ve znakovém `string`. Zástupné znaky však mohou být porovnány s libovolnými fragmenty řetězce znaků. Pokud se používá se zástupnými znaky, operátor LIKE je flexibilnější než operátory porovnání řetězců = a! =.  
  
> [!NOTE]
> Pokud cílíte na konkrétního poskytovatele, můžete použít rozšíření specifická pro daného poskytovatele. Nicméně takové konstrukce mohou být zpracovány odlišně jinými poskytovateli, například. SqlServer podporuje vzory [First-Last] a [^ First-Last], kde předchozí odpovídá přesně jednomu znaku mezi první a poslední a druhá odpovídá přesně jednomu znaku, který není mezi první a poslední.  
  
### <a name="escape"></a>Escape  
 Pomocí klauzule ESCAPE můžete hledat řetězce znaků, které zahrnují jeden nebo více speciálních zástupných znaků popsaných v tabulce v předchozí části. Předpokládejme například, že několik dokumentů obsahuje v názvu literál "100%" a chcete vyhledat všechny tyto dokumenty. Vzhledem k tomu, že procento (%) znak je zástupným znakem, je nutné ho pomocí řídicí klauzule [!INCLUDE[esql](../../../../../../includes/esql-md.md)]e úspěšně spustit. Následuje příklad tohoto filtru.  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 V tomto hledaném výrazu je procentuální hodnota zástupného znaku (%) ihned po znaku vykřičníku (!) je považován za literál, nikoli jako zástupný znak. Můžete použít libovolný znak jako řídicí znak s výjimkou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zástupných znaků a čtvercových závorek (`[ ]`) znaků. V předchozím příkladu znak vykřičník (!) je řídicí znak.  
  
## <a name="example"></a>Příklad  
 Následující dva [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy používají operátory LIKE a ESCAPE k určení, zda konkrétní řetězec znaků odpovídá zadanému vzoru. První dotaz vyhledá `Name` začínající znaky `Down_`. Tento dotaz používá možnost ESCAPE, protože podtržítko (`_`) je zástupný znak. Bez určení možnosti ESCAPE dotaz vyhledá všechny `Name` hodnoty, které začínají slovem `Down` následovaný libovolným jedním znakem, který je jiný než znak podtržítka. Dotazy jsou založené na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
