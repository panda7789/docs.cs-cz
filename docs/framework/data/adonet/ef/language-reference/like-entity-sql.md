---
title: JAKO (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 773547b097bad80e82350b473b6e59d0d84aa6dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="like-entity-sql"></a><span data-ttu-id="d341f-102">JAKO (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="d341f-102">LIKE (Entity SQL)</span></span>
<span data-ttu-id="d341f-103">Určuje, zda konkrétní znak `String` odpovídá zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="d341f-103">Determines whether a specific character `String` matches a specified pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d341f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d341f-104">Syntax</span></span>  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d341f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d341f-105">Arguments</span></span>  
 `match`  
 <span data-ttu-id="d341f-106">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Výraz, který se vyhodnocuje `String`.</span><span class="sxs-lookup"><span data-stu-id="d341f-106">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression that evaluates to a `String`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="d341f-107">Vzor tak, aby odpovídala na zadaný `String`.</span><span class="sxs-lookup"><span data-stu-id="d341f-107">A pattern to match to the specified `String`.</span></span>  
  
 `escape`  
 <span data-ttu-id="d341f-108">Řídicí znak.</span><span class="sxs-lookup"><span data-stu-id="d341f-108">An escape character.</span></span>  
  
 <span data-ttu-id="d341f-109">NENÍ</span><span class="sxs-lookup"><span data-stu-id="d341f-109">NOT</span></span>  
 <span data-ttu-id="d341f-110">Určuje, že se Negované výsledek jako.</span><span class="sxs-lookup"><span data-stu-id="d341f-110">Specifies that the result of LIKE be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d341f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d341f-111">Return Value</span></span>  
 <span data-ttu-id="d341f-112">`true`Pokud `string` odpovídá vzorku, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="d341f-112">`true` if the `string` matches the pattern; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d341f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d341f-113">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d341f-114">výrazy, které používají operátor LIKE se vyhodnocují prakticky stejně jako výrazy, které používají rovnosti jako kritéria filtru.</span><span class="sxs-lookup"><span data-stu-id="d341f-114"> expressions that use the LIKE operator are evaluated in much the same way as expressions that use equality as the filter criteria.</span></span> <span data-ttu-id="d341f-115">Ale [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazy, které používají operátor LIKE může zahrnovat literály a zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="d341f-115">However, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator can include both literals and wildcard characters.</span></span>  
  
 <span data-ttu-id="d341f-116">Následující tabulka popisuje syntaxe vzoru `string`.</span><span class="sxs-lookup"><span data-stu-id="d341f-116">The following table describes the syntax of the pattern `string`.</span></span>  
  
|<span data-ttu-id="d341f-117">Zástupný znak</span><span class="sxs-lookup"><span data-stu-id="d341f-117">Wildcard Character</span></span>|<span data-ttu-id="d341f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d341f-118">Description</span></span>|<span data-ttu-id="d341f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="d341f-119">Example</span></span>|  
|------------------------|-----------------|-------------|  
|%|<span data-ttu-id="d341f-120">Všechny `string` nula nebo více znaků.</span><span class="sxs-lookup"><span data-stu-id="d341f-120">Any `string` of zero or more characters.</span></span>|<span data-ttu-id="d341f-121">`title like '%computer%'`Vyhledá všechny Tituly s slovo `"computer"` kdekoli v názvu.</span><span class="sxs-lookup"><span data-stu-id="d341f-121">`title like '%computer%'` finds all titles with the word `"computer"` anywhere in the title.</span></span>|  
|<span data-ttu-id="d341f-122">_ (podtržítko)</span><span class="sxs-lookup"><span data-stu-id="d341f-122">_ (underscore)</span></span>|<span data-ttu-id="d341f-123">Jednoho libovolného znaku.</span><span class="sxs-lookup"><span data-stu-id="d341f-123">Any single character.</span></span>|<span data-ttu-id="d341f-124">`firstname like '_ean'`Vyhledá všechny názvy první čtyři písmeno, které končí `"ean`, "například Dean nebo pracovníka.</span><span class="sxs-lookup"><span data-stu-id="d341f-124">`firstname like '_ean'` finds all four-letter first names that end with `"ean`," such as Dean or Sean.</span></span>|  
|<span data-ttu-id="d341f-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="d341f-125">[ ]</span></span>|<span data-ttu-id="d341f-126">Všechny jeden znak v zadaném rozsahu ([-f]) nebo nastavte ([abcdef]).</span><span class="sxs-lookup"><span data-stu-id="d341f-126">Any single character in the specified range ([a-f]) or set ([abcdef]).</span></span>|<span data-ttu-id="d341f-127">`lastname like '[C-P]arsen'`Najde poslední názvy konče "arsen" a počínaje mezi C a P, jako je například Carsen nebo Lomikar jednoho libovolného znaku.</span><span class="sxs-lookup"><span data-stu-id="d341f-127">`lastname like '[C-P]arsen'` finds last names ending with "arsen" and beginning with any single character between C and P, such as Carsen or Larsen.</span></span>|  
|<span data-ttu-id="d341f-128">[^]</span><span class="sxs-lookup"><span data-stu-id="d341f-128">[^]</span></span>|<span data-ttu-id="d341f-129">Libovolný znak není v zadaném rozsahu ([^-f]), nebo nastavte ([^ abcdef]).</span><span class="sxs-lookup"><span data-stu-id="d341f-129">Any single character not in the specified range ([^a-f]) or set ([^abcdef]).</span></span>|<span data-ttu-id="d341f-130">`lastname like 'de[^l]%'`Vyhledá všechny poslední názvy, které začínají řetězcem "de" a "l" jako písmeno nezahrnují.</span><span class="sxs-lookup"><span data-stu-id="d341f-130">`lastname like 'de[^l]%'` finds all last names that begin with "de" and do not include "l" as the following letter.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d341f-131">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Jako operátor a klauzule řídicí nelze použít pro `System.DateTime` nebo `System.Guid` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d341f-131">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE operator and ESCAPE clause cannot be applied to `System.DateTime` or `System.Guid` values.</span></span>  
  
 <span data-ttu-id="d341f-132">JAKO porovnávání vzorů podporuje ASCII a Unicode porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="d341f-132">LIKE supports ASCII pattern matching and Unicode pattern matching.</span></span> <span data-ttu-id="d341f-133">Všechny parametry jsou znaky ASCII, provádí porovnávání vzorů ASCII.</span><span class="sxs-lookup"><span data-stu-id="d341f-133">When all parameters are ASCII characters, ASCII pattern matching is performed.</span></span> <span data-ttu-id="d341f-134">Pokud jeden nebo více parametrů je kódování Unicode, všechny argumenty se převede na kódování Unicode a porovnávání vzorů Unicode se provádí.</span><span class="sxs-lookup"><span data-stu-id="d341f-134">If one or more of the arguments are Unicode, all arguments are converted to Unicode and Unicode pattern matching is performed.</span></span> <span data-ttu-id="d341f-135">Použijete-li se jako Unicode, koncové mezery jsou důležitá; ale pro kódování Unicode, koncové mezery nejsou důležité.</span><span class="sxs-lookup"><span data-stu-id="d341f-135">When you use Unicode with LIKE, trailing blanks are significant; however, for non-Unicode, trailing blanks are not significant.</span></span> <span data-ttu-id="d341f-136">Syntaxe řetězec vzor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je stejný jako u [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d341f-136">The pattern string syntax of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is the same as that of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d341f-137">Vzor může obsahovat regulární znaky a zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="d341f-137">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="d341f-138">Při porovnávání vzorů regulární znaků se musí přesně shodovat zadané v znak znaky `string`.</span><span class="sxs-lookup"><span data-stu-id="d341f-138">During pattern matching, regular characters must exactly match the characters specified in the character `string`.</span></span> <span data-ttu-id="d341f-139">Zástupné znaky je však možné přidružit k libovolné fragmenty řetězcem znaků.</span><span class="sxs-lookup"><span data-stu-id="d341f-139">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="d341f-140">Pokud se používá se zástupnými znaky, je flexibilnější než = operátor LIKE a! = operátory porovnání řetězce.</span><span class="sxs-lookup"><span data-stu-id="d341f-140">When it is used with wildcard characters, the LIKE operator is more flexible than the = and != string comparison operators.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d341f-141">Pokud cílíte konkrétního poskytovatele, můžete použít rozšíření specifický pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="d341f-141">You may use provider-specific extensions if you target a specific provider.</span></span> <span data-ttu-id="d341f-142">Však takové konstrukce může být zpracovávat odděleně podle jiných poskytovatelů, třeba.</span><span class="sxs-lookup"><span data-stu-id="d341f-142">However, such constructs may be treated differently by other providers, for example.</span></span> <span data-ttu-id="d341f-143">SQL Server podporuje [první last] a [^ první poslední] vzory kde bývalé odpovídá přesně jeden znak mezi první a poslední a pozdější odpovídá přesně jeden znak, který není mezi první a poslední.</span><span class="sxs-lookup"><span data-stu-id="d341f-143">SqlServer supports [first-last] and [^first-last] patterns where the former matches exactly one character between first and last, and the latter matches exactly one character that is not between first and last.</span></span>  
  
### <a name="escape"></a><span data-ttu-id="d341f-144">Escape</span><span class="sxs-lookup"><span data-stu-id="d341f-144">Escape</span></span>  
 <span data-ttu-id="d341f-145">Pomocí klauzule řídicí můžete vyhledat znakové řetězce, které obsahují jeden nebo více speciální zástupné znaky popsané v tabulce v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="d341f-145">By using the ESCAPE clause, you can search for character strings that include one or more of the special wildcard characters described in the table in the previous section.</span></span> <span data-ttu-id="d341f-146">Předpokládejme například, několik dokumentů zahrnout literálu "100 %" v názvu a chcete hledat u všech těchto dokumentů.</span><span class="sxs-lookup"><span data-stu-id="d341f-146">For example, assume several documents include the literal "100%" in the title and you want to search for all of those documents.</span></span> <span data-ttu-id="d341f-147">Protože znak procenta (%) je zástupný znak, musí se vyhnuli, pomocí [!INCLUDE[esql](../../../../../../includes/esql-md.md)] řídicí klauzule úspěšně provést hledání.</span><span class="sxs-lookup"><span data-stu-id="d341f-147">Because the percent (%) character is a wildcard character, you must escape it using the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE clause to successfully execute the search.</span></span> <span data-ttu-id="d341f-148">Následuje příklad tento filtr.</span><span class="sxs-lookup"><span data-stu-id="d341f-148">The following is an example of this filter.</span></span>  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 <span data-ttu-id="d341f-149">V tomto výrazu vyhledávání procenta zástupného znaku (%), hned za znak vykřičníkem (!) je považována za literál, místo jako zástupný znak.</span><span class="sxs-lookup"><span data-stu-id="d341f-149">In this search expression, the percent wildcard character (%) immediately following the exclamation point character (!) is treated as a literal, instead of as a wildcard character.</span></span> <span data-ttu-id="d341f-150">Můžete použít libovolný znak jako řídicí znak s výjimkou [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zástupné znaky a druhou mocninu závorka (`[ ]`) znaků.</span><span class="sxs-lookup"><span data-stu-id="d341f-150">You can use any character as an escape character except for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wildcard characters and the square bracket (`[ ]`) characters.</span></span> <span data-ttu-id="d341f-151">V předchozím příkladu znak vykřičníkem (!) je řídicí znak.</span><span class="sxs-lookup"><span data-stu-id="d341f-151">In the previous example, the exclamation point (!) character is the escape character.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d341f-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="d341f-152">Example</span></span>  
 <span data-ttu-id="d341f-153">Následující dva [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy pomocí LIKE a operátory řídicí k určení, zda řetězec znaků konkrétní odpovídá zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="d341f-153">The following two [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries use the LIKE and ESCAPE operators to determine whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="d341f-154">První dotaz vyhledává `Name` , které začíná znaky `Down_`.</span><span class="sxs-lookup"><span data-stu-id="d341f-154">The first query searches for the `Name` that starts with the characters `Down_`.</span></span> <span data-ttu-id="d341f-155">Tento dotaz používá možnost řídicí, protože podtržítko (`_`) je zástupný znak.</span><span class="sxs-lookup"><span data-stu-id="d341f-155">This query uses the ESCAPE option because the underscore (`_`) is a wildcard character.</span></span> <span data-ttu-id="d341f-156">Bez zadání možnosti řídicí, dotaz by vyhledávat libovolné `Name` hodnoty, které začínat slovem `Down` následuje libovolný znak než znak podtržítka.</span><span class="sxs-lookup"><span data-stu-id="d341f-156">Without specifying the ESCAPE option, the query would search for any `Name` values that start with the word `Down` followed by any single character other than the underscore character.</span></span> <span data-ttu-id="d341f-157">Dotazy jsou založené na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d341f-157">The queries are based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d341f-158">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="d341f-158">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d341f-159">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d341f-159">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="d341f-160">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="d341f-160">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a><span data-ttu-id="d341f-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="d341f-161">See Also</span></span>  
 [<span data-ttu-id="d341f-162">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="d341f-162">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
