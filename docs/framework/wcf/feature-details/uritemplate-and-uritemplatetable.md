---
title: UriTemplate a UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 09726af0a124723de025f29927954a2100aebcb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508815"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="459b1-102">UriTemplate a UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="459b1-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="459b1-103">Vývojáři webů potřebují k popisu tvar a rozložení identifikátory URI, který své služby reagovat na.</span><span class="sxs-lookup"><span data-stu-id="459b1-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="459b1-104">Windows Communication Foundation (WCF) přidá dva nové třídy pro umožnění vývojáři kontroly nad jejich identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="459b1-105"><xref:System.UriTemplate> a <xref:System.UriTemplateTable> tvoří základ, na základě identifikátoru URI odesílání modulu ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="459b1-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="459b1-106">Tyto třídy můžete použít taky u své vlastní, což umožňuje vývojářům umožní využít šablon a identifikátor URI mechanismus mapování bez implementace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="459b1-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="459b1-107">Šablony</span><span class="sxs-lookup"><span data-stu-id="459b1-107">Templates</span></span>  
 <span data-ttu-id="459b1-108">Šablona je způsob, jak popisuje sadu relativní identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="459b1-109">Sada šablony URI v následující tabulce ukazuje, jak může být definovaná systémem, který načte různých typů informací o počasí.</span><span class="sxs-lookup"><span data-stu-id="459b1-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="459b1-110">Data</span><span class="sxs-lookup"><span data-stu-id="459b1-110">Data</span></span>|<span data-ttu-id="459b1-111">Šablony</span><span class="sxs-lookup"><span data-stu-id="459b1-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="459b1-112">National prognózy</span><span class="sxs-lookup"><span data-stu-id="459b1-112">National Forecast</span></span>|<span data-ttu-id="459b1-113">počasí/national</span><span class="sxs-lookup"><span data-stu-id="459b1-113">weather/national</span></span>|  
|<span data-ttu-id="459b1-114">Stav prognózy</span><span class="sxs-lookup"><span data-stu-id="459b1-114">State Forecast</span></span>|<span data-ttu-id="459b1-115">počasí / {stavu}</span><span class="sxs-lookup"><span data-stu-id="459b1-115">weather/{state}</span></span>|  
|<span data-ttu-id="459b1-116">Prognóza města</span><span class="sxs-lookup"><span data-stu-id="459b1-116">City Forecast</span></span>|<span data-ttu-id="459b1-117">počasí / {stavu} / {města}</span><span class="sxs-lookup"><span data-stu-id="459b1-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="459b1-118">Aktivita prognózy</span><span class="sxs-lookup"><span data-stu-id="459b1-118">Activity Forecast</span></span>|<span data-ttu-id="459b1-119">počasí / {stavu} / {města} / {aktivity}</span><span class="sxs-lookup"><span data-stu-id="459b1-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="459b1-120">Tato tabulka popisuje sadu strukturálně podobné identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="459b1-121">Každá položka je šablona identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-121">Each entry is a URI template.</span></span> <span data-ttu-id="459b1-122">Segmenty do složených závorek popisují proměnné.</span><span class="sxs-lookup"><span data-stu-id="459b1-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="459b1-123">Segmenty není do složených závorek popisují řetězcové literály.</span><span class="sxs-lookup"><span data-stu-id="459b1-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="459b1-124">Třídy šablon WCF povolit vývojář trvat příchozí URI, například "/ počasí nebo wa/Praha/prosté", a odpovídat na šablonu, která popisuje, "/weather/ {stavu} / {města} / {aktivity}".</span><span class="sxs-lookup"><span data-stu-id="459b1-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="459b1-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="459b1-125">UriTemplate</span></span>  
 <span data-ttu-id="459b1-126"><xref:System.UriTemplate> je třída, který zapouzdřuje šablonu identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="459b1-127">Konstruktor přijímá řetězcový parametr, který definuje šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="459b1-128">Tento řetězec obsahuje šablonu ve formátu popsané v další části.</span><span class="sxs-lookup"><span data-stu-id="459b1-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="459b1-129"><xref:System.UriTemplate> Třída poskytuje metody, které vám umožňují odpovídat identifikátor URI příchozí do šablony, generovat identifikátor URI ze šablony, načte kolekci názvy proměnných, které jsou použité v šabloně, určete, jestli dvě šablony jsou ekvivalentní a vrátí šablony řetězec.</span><span class="sxs-lookup"><span data-stu-id="459b1-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="459b1-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> identifikátor URI a pokusí se porovnat identifikátor URI pro šablony trvá základní adresa a kandidátem.</span><span class="sxs-lookup"><span data-stu-id="459b1-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="459b1-131">Pokud je úspěšné, shody <xref:System.UriTemplateMatch> vrácena instance.</span><span class="sxs-lookup"><span data-stu-id="459b1-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="459b1-132"><xref:System.UriTemplateMatch> Objekt obsahuje základní identifikátor URI candidate identifikátor URI, názvu a hodnoty kolekce parametry dotazu, pole segmentů relativní cestu, kolekci názvu a hodnoty proměnných, které se shodují, <xref:System.UriTemplate> instance, používá k provádění shody , řetězec, který obsahuje všechny neodpovídající část candidate identifikátor URI (používá se při šablona má zástupný znak) a objekt, který je přidružen šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="459b1-133"><xref:System.UriTemplate> Třída ignoruje schéma a číslo portu při kontrole shody kandidátem URI do šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="459b1-134">Existují dvě metody, které vám umožní generovat identifikátor URI ze šablony, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> a <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="459b1-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="459b1-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> trvá základní adresa a kolekce názvu a hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="459b1-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="459b1-136">Tyto parametry jsou nahrazena pro proměnné, když šablona je vázána.</span><span class="sxs-lookup"><span data-stu-id="459b1-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="459b1-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> trvá dvojice název/hodnota a nahradí je zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="459b1-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="459b1-138"><xref:System.UriTemplate.ToString> Vrátí řetězec šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="459b1-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> Vlastnost obsahuje kolekci názvů proměnných používaných v rámci segmenty cesty v řetězci šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="459b1-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> přijímá <xref:System.UriTemplate> jako parametr a vrací logickou hodnotu, která určuje, zda dvě šablony jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="459b1-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="459b1-141">Další informace najdete v části šablony ekvivalenční později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="459b1-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="459b1-142"><xref:System.UriTemplate> je navržen pro práci s žádné schéma identifikátoru URI, který vyhovuje gramatika HTTP URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="459b1-143">Následují příklady podporována schémata identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-143">The following are examples of supported URI schemes.</span></span>  
  
-   <span data-ttu-id="459b1-144">http://</span><span class="sxs-lookup"><span data-stu-id="459b1-144">http://</span></span>  
  
-   <span data-ttu-id="459b1-145">https://</span><span class="sxs-lookup"><span data-stu-id="459b1-145">https://</span></span>  
  
-   <span data-ttu-id="459b1-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="459b1-146">net.tcp://</span></span>  
  
-   <span data-ttu-id="459b1-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="459b1-147">net.pipe://</span></span>  
  
-   <span data-ttu-id="459b1-148">sb://</span><span class="sxs-lookup"><span data-stu-id="459b1-148">sb://</span></span>  
  
 <span data-ttu-id="459b1-149">Schémata jako file:// a urn: / / není v souladu s gramatika HTTP URI a způsobit nepředvídatelné výsledky při použití s šablony URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="459b1-150">Syntaxe řetězec šablony</span><span class="sxs-lookup"><span data-stu-id="459b1-150">Template String Syntax</span></span>  
 <span data-ttu-id="459b1-151">Šablona má tři části: cestu, volitelné dotazu a volitelné fragment.</span><span class="sxs-lookup"><span data-stu-id="459b1-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="459b1-152">Příklad najdete v tématu následující šablony:</span><span class="sxs-lookup"><span data-stu-id="459b1-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="459b1-153">Cesta se skládá z "/weather/ {stavu} / {města}", dotaz se skládá z"? prognózy = {{délka} a fragment se skládá z"#frag1".</span><span class="sxs-lookup"><span data-stu-id="459b1-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="459b1-154">Úvodní a koncové lomítka jsou volitelné ve výrazu cestu.</span><span class="sxs-lookup"><span data-stu-id="459b1-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="459b1-155">Výrazy dotazu i fragment je zcela lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="459b1-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="459b1-156">Cesta se skládá z řady segmentů oddělená '/', každý segment může mít hodnotu literálu, název proměnné (napsané v {složené závorky}) nebo zástupný znak (zapsány jako\*').</span><span class="sxs-lookup"><span data-stu-id="459b1-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="459b1-157">V šabloně předchozí "\weather\ segment je literál, ale zadaná hodnota"{stavu}"a"{města}"jsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="459b1-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="459b1-158">Proměnné trvat jména z obsahu jejich složené závorky a lze je později nahradit s konkrétní hodnotou k vytvoření *uzavřený URI*.</span><span class="sxs-lookup"><span data-stu-id="459b1-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="459b1-159">Zástupný znak je nepovinný, ale může vyskytovat pouze na konci identifikátor URI, které logicky odpovídá "zbývající část cesty".</span><span class="sxs-lookup"><span data-stu-id="459b1-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="459b1-160">Výraz dotazu, pokud existuje, určuje řadu dvojice neuspořádaný název hodnota oddělená 'a'.</span><span class="sxs-lookup"><span data-stu-id="459b1-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="459b1-161">Elementy výrazu dotazu může být buď literálu páry (x = 2) nebo pár proměnných (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="459b1-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="459b1-162">Pravé straně dotazu může mít proměnné výraz.</span><span class="sxs-lookup"><span data-stu-id="459b1-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="459b1-163">({someName} = {someValue} není povolená.</span><span class="sxs-lookup"><span data-stu-id="459b1-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="459b1-164">Nepárové hodnoty (? x) nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="459b1-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="459b1-165">Není žádný rozdíl mezi výraz dotazu prázdný a tvořený jenom jednoho výrazu dotazu '?' (i znamená "jakýkoli dotaz").</span><span class="sxs-lookup"><span data-stu-id="459b1-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="459b1-166">Fragment výraz se může skládat z literálovou hodnotou, jsou povolené žádné proměnné.</span><span class="sxs-lookup"><span data-stu-id="459b1-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="459b1-167">Všechny názvy proměnných šablony v rámci řetězec šablony musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="459b1-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="459b1-168">Názvy proměnných šablony jsou velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="459b1-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="459b1-169">Příkladem řetězce platné šablony:</span><span class="sxs-lookup"><span data-stu-id="459b1-169">Examples of valid template strings:</span></span>  
  
-   <span data-ttu-id="459b1-170">""</span><span class="sxs-lookup"><span data-stu-id="459b1-170">""</span></span>  
  
-   <span data-ttu-id="459b1-171">"/ čelisti"</span><span class="sxs-lookup"><span data-stu-id="459b1-171">"/shoe"</span></span>  
  
-   <span data-ttu-id="459b1-172">"/ čelisti / \*"</span><span class="sxs-lookup"><span data-stu-id="459b1-172">"/shoe/\*"</span></span>  
  
-   <span data-ttu-id="459b1-173">"{čelisti} / lodních"</span><span class="sxs-lookup"><span data-stu-id="459b1-173">"{shoe}/boat"</span></span>  
  
-   <span data-ttu-id="459b1-174">"{čelisti} / {lodních} /bed/ {quilt}"</span><span class="sxs-lookup"><span data-stu-id="459b1-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
-   <span data-ttu-id="459b1-175">"čelisti / {lodních}"</span><span class="sxs-lookup"><span data-stu-id="459b1-175">"shoe/{boat}"</span></span>  
  
-   <span data-ttu-id="459b1-176">"čelisti / {lodních} / \*"</span><span class="sxs-lookup"><span data-stu-id="459b1-176">"shoe/{boat}/\*"</span></span>  
  
-   <span data-ttu-id="459b1-177">"čelisti nebo člun? x = 2"</span><span class="sxs-lookup"><span data-stu-id="459b1-177">"shoe/boat?x=2"</span></span>  
  
-   <span data-ttu-id="459b1-178">"čelisti / {lodních}? x = {DNA}"</span><span class="sxs-lookup"><span data-stu-id="459b1-178">"shoe/{boat}?x={bed}"</span></span>  
  
-   <span data-ttu-id="459b1-179">"čelisti / {lodních}? x = {DNA} & y = vzdálené"</span><span class="sxs-lookup"><span data-stu-id="459b1-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
-   <span data-ttu-id="459b1-180">"? x = {čelisti}"</span><span class="sxs-lookup"><span data-stu-id="459b1-180">"?x={shoe}"</span></span>  
  
-   <span data-ttu-id="459b1-181">"čelisti? x = 3 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="459b1-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="459b1-182">Příkladem řetězce neplatný šablon:</span><span class="sxs-lookup"><span data-stu-id="459b1-182">Examples of invalid template strings:</span></span>  
  
-   <span data-ttu-id="459b1-183">"{čelisti} / {ČELISTI} / x = 2" – duplicitní názvy proměnných.</span><span class="sxs-lookup"><span data-stu-id="459b1-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
-   <span data-ttu-id="459b1-184">"{čelisti} /boat/? DNA = {čelisti}" – duplicitní názvy proměnných.</span><span class="sxs-lookup"><span data-stu-id="459b1-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
-   <span data-ttu-id="459b1-185">"? x = 2 & x = 3" – dvojice název/hodnota v rámci řetězec dotazu musí být jedinečné, i když jsou literály.</span><span class="sxs-lookup"><span data-stu-id="459b1-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
-   <span data-ttu-id="459b1-186">"? x = 2 &" – řetězec dotazu je poškozený.</span><span class="sxs-lookup"><span data-stu-id="459b1-186">"?x=2&" – Query string is malformed.</span></span>  
  
-   <span data-ttu-id="459b1-187">"? 2 & x = {čelisti}" – řetězec dotazu musí být dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="459b1-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
-   <span data-ttu-id="459b1-188">"? y = 2 & & X = 3" – řetězec dotazu musí být dvojice názvů a hodnot, nemůže začínat názvy 'a'.</span><span class="sxs-lookup"><span data-stu-id="459b1-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="459b1-189">Složené segmenty cesty</span><span class="sxs-lookup"><span data-stu-id="459b1-189">Compound Path Segments</span></span>  
 <span data-ttu-id="459b1-190">Segmenty cesty složené Povolí jeden segment cesty identifikátoru URI tak, aby obsahovala více proměnných a také v kombinaci s literály proměnné.</span><span class="sxs-lookup"><span data-stu-id="459b1-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="459b1-191">Následují příklady segmentů složené platnou cestu.</span><span class="sxs-lookup"><span data-stu-id="459b1-191">The following are examples of valid compound path segments.</span></span>  
  
-   <span data-ttu-id="459b1-192">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="459b1-192">/filename.{ext}/</span></span>  
  
-   <span data-ttu-id="459b1-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="459b1-193">/{filename}.jpg/</span></span>  
  
-   <span data-ttu-id="459b1-194">/ {filename}. {ext} /</span><span class="sxs-lookup"><span data-stu-id="459b1-194">/{filename}.{ext}/</span></span>  
  
-   <span data-ttu-id="459b1-195">/ {a}. {b}someLiteral{c}({d}) /</span><span class="sxs-lookup"><span data-stu-id="459b1-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="459b1-196">Následují příklady segmentů platná cesta UNC.</span><span class="sxs-lookup"><span data-stu-id="459b1-196">The following are examples of invalid path segments.</span></span>  
  
-   <span data-ttu-id="459b1-197">/{} -Musí mít název proměnné.</span><span class="sxs-lookup"><span data-stu-id="459b1-197">/{} - Variables must be named.</span></span>  
  
-   <span data-ttu-id="459b1-198">/ {čelisti} {člun} - proměnných musí být odděleny literál.</span><span class="sxs-lookup"><span data-stu-id="459b1-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="459b1-199">Odpovídající a složené segmenty cesty</span><span class="sxs-lookup"><span data-stu-id="459b1-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="459b1-200">Segmenty cesty složené umožňují definovat UriTemplate, který má více proměnných v rámci segmentu, jednu cestu.</span><span class="sxs-lookup"><span data-stu-id="459b1-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="459b1-201">Například v následující řetězec šablony: "adresy / {stavu}. {města} "dvě proměnné (státu a města) jsou definovány v rámci stejné segmentu.</span><span class="sxs-lookup"><span data-stu-id="459b1-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="459b1-202">Tato šablona by odpovídat adresu URL, jako "http://example.com/Washington.Redmond", ale bude se taky shodovat adresu URL jako"http://example.com/Washington.Redmond.Microsoft".</span><span class="sxs-lookup"><span data-stu-id="459b1-202">This template would match a URL such as "http://example.com/Washington.Redmond" but it will also match an URL like "http://example.com/Washington.Redmond.Microsoft".</span></span> <span data-ttu-id="459b1-203">V takovém případě proměnné stavu bude obsahovat "Washington" a proměnnou města bude obsahovat "Redmond.Microsoft".</span><span class="sxs-lookup"><span data-stu-id="459b1-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="459b1-204">V tomto případě jakýkoli text (s výjimkou '/') bude shodovat s proměnnou {města}.</span><span class="sxs-lookup"><span data-stu-id="459b1-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="459b1-205">Pokud chcete šablonu, která nebude odpovídat "výběr" text, umístěte proměnnou v samostatných šablony segmentu, například: "adresy / {stavu} / {města}.</span><span class="sxs-lookup"><span data-stu-id="459b1-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="459b1-206">Segmenty pojmenované zástupný znak</span><span class="sxs-lookup"><span data-stu-id="459b1-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="459b1-207">Segment s názvem zástupný znak je všechny proměnné segment cesty jejichž proměnné název začíná se zástupným znakem ' \*'.</span><span class="sxs-lookup"><span data-stu-id="459b1-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="459b1-208">Následující řetězec šablony obsahuje segment s názvem zástupné s názvem "čelisti".</span><span class="sxs-lookup"><span data-stu-id="459b1-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="459b1-209">Zástupný znak segmenty musí postupujte podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="459b1-209">Wildcard segments must follow the following rules:</span></span>  
  
-   <span data-ttu-id="459b1-210">Může být maximálně jeden segment s názvem zástupných znaků pro každý řetězec šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
-   <span data-ttu-id="459b1-211">Segment s názvem zástupný znak musí být uvedena v segmentu nejvíce vpravo v cestě.</span><span class="sxs-lookup"><span data-stu-id="459b1-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
-   <span data-ttu-id="459b1-212">Segment s názvem zástupné nemohou být nainstalovány s segment anonymní zástupný znak v rámci stejné řetězec šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
-   <span data-ttu-id="459b1-213">Název objektu segment s názvem zástupný znak musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="459b1-213">The name of a named wildcard segment must be unique.</span></span>  
  
-   <span data-ttu-id="459b1-214">S názvem zástupný znak nelze segmenty mají výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="459b1-214">Named wildcard segments cannot have default values.</span></span>  
  
-   <span data-ttu-id="459b1-215">Nemůže končit segmenty pojmenované zástupný znak "/".</span><span class="sxs-lookup"><span data-stu-id="459b1-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="459b1-216">Výchozí hodnoty proměnné</span><span class="sxs-lookup"><span data-stu-id="459b1-216">Default Variable Values</span></span>  
 <span data-ttu-id="459b1-217">Výchozí hodnoty proměnné umožňují zadat výchozí hodnoty pro proměnné v rámci šablon.</span><span class="sxs-lookup"><span data-stu-id="459b1-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="459b1-218">Výchozí proměnné mohou být zadané s složené závorky, které deklarovat proměnnou nebo jako kolekce předaný konstruktoru UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="459b1-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="459b1-219">Následující šablony ukazuje dva způsoby, jak určit <xref:System.UriTemplate> k proměnným s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="459b1-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```  
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="459b1-220">Tato šablona deklaruje proměnné s názvem `a` s výchozí hodnotou `1` a proměnné s názvem `b` s výchozí hodnotou `5`.</span><span class="sxs-lookup"><span data-stu-id="459b1-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="459b1-221">Do mají výchozí hodnoty jsou povoleny pouze proměnné segmentu cesty.</span><span class="sxs-lookup"><span data-stu-id="459b1-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="459b1-222">Výchozí hodnoty nejsou povoleny proměnné řetězce dotazu, složené segment proměnné a proměnné s názvem zástupný znak.</span><span class="sxs-lookup"><span data-stu-id="459b1-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="459b1-223">Následující kód ukazuje, jak výchozí hodnoty proměnné jsou zpracovávány při kontrole shody kandidátem identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```  
Uri baseAddress = new Uri("http://localhost:800   
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);0");  
UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);  
Uri candidate = new Uri("http://localhost:8000/OR");  
  
UriTemplateMatch m1 = t.Match(baseAddress, candidate);  
  
// Display contents of BoundVariables  
foreach (string key in m1.BoundVariables.AllKeys)  
{  
    Console.WriteLine("\t\t{0}={1}", key, m1.BoundVariables[key]);  
}  
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/  
// Candidate URI: http://localhost:8000/OR  
// BoundVariables:  
//      STATE=OR  
//       CITY=Redmond  
```  
  
> [!NOTE]
>  <span data-ttu-id="459b1-224">Identifikátor URI, jako http://localhost:8000/// neodpovídá šabloně uvedené v předchozí kód, ale identifikátor URI, jako http://localhost:8000/ nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="459b1-224">A URI such as http://localhost:8000/// does not match the template listed in the preceding code, however a URI such as http://localhost:8000/ does.</span></span>  
  
 <span data-ttu-id="459b1-225">Následující kód ukazuje, jak výchozí hodnoty proměnných jsou zpracovávány při vytváření identifikátorů URI pomocí šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
 <span data-ttu-id="459b1-226">Když proměnné je zadána výchozí hodnota je `null` existují některé další omezení.</span><span class="sxs-lookup"><span data-stu-id="459b1-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="459b1-227">Proměnná může mít výchozí hodnotu `null` Pokud proměnnou je obsažena v pravém většina segment řetězec šablony nebo pokud všechny segmenty napravo od segmentu mají výchozí hodnoty `null`.</span><span class="sxs-lookup"><span data-stu-id="459b1-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="459b1-228">Následují platné šablony řetězce s hodnotami výchozí `null`:</span><span class="sxs-lookup"><span data-stu-id="459b1-228">The following are valid template strings with default values of `null`:</span></span>  
  
-   ```  
    UriTemplate t = new UriTemplate("shoe/{boat=null}");  
    ```  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");  
    ```  
 <span data-ttu-id="459b1-229">Toto jsou neplatná šablony řetězce s hodnotami výchozí `null`:</span><span class="sxs-lookup"><span data-stu-id="459b1-229">The following are invalid template strings with  default values of `null`:</span></span>  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value  
    ```  
### <a name="default-values-and-matching"></a><span data-ttu-id="459b1-230">Výchozí hodnoty a odpovídající</span><span class="sxs-lookup"><span data-stu-id="459b1-230">Default Values and Matching</span></span>  
 <span data-ttu-id="459b1-231">Při porovnání kandidátem URI pomocí šablony, která má výchozí hodnoty, výchozí hodnoty jsou umístěny v <xref:System.UriTemplateMatch.BoundVariables%2A> kolekci, pokud nejsou zadané hodnoty v candidate identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="459b1-232">Ekvivalence šablony</span><span class="sxs-lookup"><span data-stu-id="459b1-232">Template Equivalence</span></span>  
 <span data-ttu-id="459b1-233">Dvě šablony jsou označeny jako *strukturálně ekvivalentní* při všechny tyto šablony literálů odpovídající a mají proměnné v stejné segmenty.</span><span class="sxs-lookup"><span data-stu-id="459b1-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="459b1-234">Například jsou strukturálně ekvivalentní následujících šablon:</span><span class="sxs-lookup"><span data-stu-id="459b1-234">For example the following templates are structurally equivalent:</span></span>  
  
-   <span data-ttu-id="459b1-235">b /b /a/ {var1} / {var2}? x = 1 & y = 2</span><span class="sxs-lookup"><span data-stu-id="459b1-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
-   <span data-ttu-id="459b1-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="459b1-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
-   <span data-ttu-id="459b1-237">a/{y}/B%20B/{z}/?y=2 & x = 1</span><span class="sxs-lookup"><span data-stu-id="459b1-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="459b1-238">Pár věcí Všimněte:</span><span class="sxs-lookup"><span data-stu-id="459b1-238">A few things to notice:</span></span>  
  
-   <span data-ttu-id="459b1-239">Pokud šablonu obsahuje úvodní lomítka, pouze první z nich se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="459b1-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
-   <span data-ttu-id="459b1-240">Při porovnávání řetězců šablony pro strukturální ekvivalenční, se ignoruje velikost písmen pro názvy proměnných a segmenty cesty, řetězce dotazu se velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="459b1-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
-   <span data-ttu-id="459b1-241">Řetězce dotazu neuspořádaného.</span><span class="sxs-lookup"><span data-stu-id="459b1-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="459b1-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="459b1-242">UriTemplateTable</span></span>  
 <span data-ttu-id="459b1-243"><xref:System.UriTemplateTable> Třída reprezentuje asociativní tabulky <xref:System.UriTemplate> objekty vázána na objekt vývojář je výběr.</span><span class="sxs-lookup"><span data-stu-id="459b1-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="459b1-244">A <xref:System.UriTemplateTable> musí obsahovat alespoň jeden <xref:System.UriTemplate> před voláním <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="459b1-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="459b1-245">Obsah <xref:System.UriTemplateTable> lze změnit až <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána.</span><span class="sxs-lookup"><span data-stu-id="459b1-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="459b1-246">Ověření se provádí při <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána.</span><span class="sxs-lookup"><span data-stu-id="459b1-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="459b1-247">Typ ověření provést, závisí na hodnotu `allowMultiple` parametru <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="459b1-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="459b1-248">Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> nazývá předávání v `false`, <xref:System.UriTemplateTable> kontroluje, zajistěte, aby v tabulce nejsou žádné šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="459b1-249">Pokud najde všechny strukturálně ekvivalentní šablony, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="459b1-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="459b1-250">To se používá ve spojení s <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> Pokud chcete zajistit jenom jedna šablona odpovídá příchozí identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="459b1-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="459b1-251">Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> nazývá předávání v `true`, <xref:System.UriTemplateTable> umožňuje víc strukturálně ekvivalentní šablony vešel do jednoho <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="459b1-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="459b1-252">Pokud sada <xref:System.UriTemplate> objektů přidaných do <xref:System.UriTemplateTable> obsahují řetězce dotazu se nesmí být nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="459b1-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="459b1-253">Jsou povoleny řetězce dotazu identické.</span><span class="sxs-lookup"><span data-stu-id="459b1-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="459b1-254">Když <xref:System.UriTemplateTable> umožňuje základní adresy tohoto použijte schémata než HTTP, schéma a číslo portu jsou ignorovány, při kontrole shody candidate identifikátory URI šablon.</span><span class="sxs-lookup"><span data-stu-id="459b1-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="459b1-255">Nejednoznačnosti řetězec dotazu</span><span class="sxs-lookup"><span data-stu-id="459b1-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="459b1-256">Šablony, které ekvivalentní cestu ke sdílené složce obsahují řetězce nejednoznačný dotazu, pokud je identifikátor URI, který odpovídá více než jednu šablonu.</span><span class="sxs-lookup"><span data-stu-id="459b1-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="459b1-257">Následující sady řetězce dotazu jsou jednoznačné v rámci sami:</span><span class="sxs-lookup"><span data-stu-id="459b1-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
-   <span data-ttu-id="459b1-258">? x = 1</span><span class="sxs-lookup"><span data-stu-id="459b1-258">?x=1</span></span>  
  
-   <span data-ttu-id="459b1-259">? x = 2</span><span class="sxs-lookup"><span data-stu-id="459b1-259">?x=2</span></span>  
  
-   <span data-ttu-id="459b1-260">? x = 3</span><span class="sxs-lookup"><span data-stu-id="459b1-260">?x=3</span></span>  
  
-   <span data-ttu-id="459b1-261">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="459b1-261">?x=1&y={var}</span></span>  
  
-   <span data-ttu-id="459b1-262">? x = 2 & z = {var}</span><span class="sxs-lookup"><span data-stu-id="459b1-262">?x=2&z={var}</span></span>  
  
-   <span data-ttu-id="459b1-263">? x = 3</span><span class="sxs-lookup"><span data-stu-id="459b1-263">?x=3</span></span>  
  
-   <span data-ttu-id="459b1-264">? x = 1</span><span class="sxs-lookup"><span data-stu-id="459b1-264">?x=1</span></span>  
  
-   <span data-ttu-id="459b1-265">?</span><span class="sxs-lookup"><span data-stu-id="459b1-265">?</span></span>  
  
-   <span data-ttu-id="459b1-266">?</span><span class="sxs-lookup"><span data-stu-id="459b1-266">?</span></span> <span data-ttu-id="459b1-267">x = {var}</span><span class="sxs-lookup"><span data-stu-id="459b1-267">x={var}</span></span>  
  
-   <span data-ttu-id="459b1-268">?</span><span class="sxs-lookup"><span data-stu-id="459b1-268">?</span></span>  
  
-   <span data-ttu-id="459b1-269">? m = get & c = rss</span><span class="sxs-lookup"><span data-stu-id="459b1-269">?m=get&c=rss</span></span>  
  
-   <span data-ttu-id="459b1-270">? m = put & c = rss</span><span class="sxs-lookup"><span data-stu-id="459b1-270">?m=put&c=rss</span></span>  
  
-   <span data-ttu-id="459b1-271">? m = get & c = atom</span><span class="sxs-lookup"><span data-stu-id="459b1-271">?m=get&c=atom</span></span>  
  
-   <span data-ttu-id="459b1-272">? m = put & c = atom</span><span class="sxs-lookup"><span data-stu-id="459b1-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="459b1-273">Následující sady šablon řetězec dotazu jsou nejednoznačné v rámci sami:</span><span class="sxs-lookup"><span data-stu-id="459b1-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
-   <span data-ttu-id="459b1-274">? x = 1</span><span class="sxs-lookup"><span data-stu-id="459b1-274">?x=1</span></span>  
  
-   <span data-ttu-id="459b1-275">? x = {var}</span><span class="sxs-lookup"><span data-stu-id="459b1-275">?x={var}</span></span>  
  
 <span data-ttu-id="459b1-276">"x = 1"-odpovídá obě šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-276">"x=1" - Matches both templates.</span></span>  
  
-   <span data-ttu-id="459b1-277">? x = 1</span><span class="sxs-lookup"><span data-stu-id="459b1-277">?x=1</span></span>  
  
-   <span data-ttu-id="459b1-278">? y = 2</span><span class="sxs-lookup"><span data-stu-id="459b1-278">?y=2</span></span>  
  
 <span data-ttu-id="459b1-279">"x = 1 & y = 2" odpovídá obě šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="459b1-280">Je to proto, že řetězec dotazu může obsahovat další proměnné řetězce dotazu, pak odpovídá šabloně.</span><span class="sxs-lookup"><span data-stu-id="459b1-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
-   <span data-ttu-id="459b1-281">? x = 1</span><span class="sxs-lookup"><span data-stu-id="459b1-281">?x=1</span></span>  
  
-   <span data-ttu-id="459b1-282">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="459b1-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="459b1-283">"x = 1 & y = 3" odpovídá obě šablony.</span><span class="sxs-lookup"><span data-stu-id="459b1-283">"x=1&y=3" matches both templates.</span></span>  
  
-   <span data-ttu-id="459b1-284">? x = 3 & y = 4</span><span class="sxs-lookup"><span data-stu-id="459b1-284">?x=3&y=4</span></span>  
  
-   <span data-ttu-id="459b1-285">? x = 3 & z = 5</span><span class="sxs-lookup"><span data-stu-id="459b1-285">?x=3&z=5</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="459b1-286">Znaky funkce a funkce se považují za různých znaků, když se zobrazí jako část cesty identifikátor URI nebo <xref:System.UriTemplate> segment cesty literálu (ale a znaky a A jsou považovány za stejnou).</span><span class="sxs-lookup"><span data-stu-id="459b1-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="459b1-287">Znaky funkce a funkce se považují za stejné znaky, když se zobrazí jako součást <xref:System.UriTemplate> {variableName} nebo řetězec dotazu (a a serverem se také považují za stejné znaky).</span><span class="sxs-lookup"><span data-stu-id="459b1-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459b1-288">Viz také</span><span class="sxs-lookup"><span data-stu-id="459b1-288">See Also</span></span>  
 [<span data-ttu-id="459b1-289">Přehled programovacího modelu webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="459b1-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [<span data-ttu-id="459b1-290">Programovací objektový model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="459b1-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [<span data-ttu-id="459b1-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="459b1-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [<span data-ttu-id="459b1-292">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="459b1-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="459b1-293">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="459b1-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
