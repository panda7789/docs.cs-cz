---
title: UriTemplate a UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: f51d6fa5c78d97cf11a3c0005be7656013b30e90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955284"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="33515-102">UriTemplate a UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="33515-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="33515-103">Vývojáři webu vyžadují možnost popsat tvar a rozložení identifikátorů URI, na které jejich služby reagují.</span><span class="sxs-lookup"><span data-stu-id="33515-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="33515-104">Windows Communication Foundation (WCF) přidal dvě nové třídy, které vývojářům poskytují kontrolu nad svými identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="33515-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="33515-105"><xref:System.UriTemplate>a <xref:System.UriTemplateTable> tvoří základ odesílajícího stroje založeného na identifikátoru URI ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="33515-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="33515-106">Tyto třídy lze také použít na vlastní, což vývojářům umožňuje využít výhod šablon a mechanismu mapování identifikátorů URI bez implementace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="33515-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="33515-107">Šablony</span><span class="sxs-lookup"><span data-stu-id="33515-107">Templates</span></span>  
 <span data-ttu-id="33515-108">Šablona je způsob, jak popsat sadu relativních identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="33515-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="33515-109">Sada šablon identifikátorů URI v následující tabulce ukazuje, jak je možné definovat systém, který načte různé typy informací o počasí.</span><span class="sxs-lookup"><span data-stu-id="33515-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="33515-110">Data</span><span class="sxs-lookup"><span data-stu-id="33515-110">Data</span></span>|<span data-ttu-id="33515-111">Šablona</span><span class="sxs-lookup"><span data-stu-id="33515-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="33515-112">Národní prognóza</span><span class="sxs-lookup"><span data-stu-id="33515-112">National Forecast</span></span>|<span data-ttu-id="33515-113">počasí/národní</span><span class="sxs-lookup"><span data-stu-id="33515-113">weather/national</span></span>|  
|<span data-ttu-id="33515-114">Prognóza stavu</span><span class="sxs-lookup"><span data-stu-id="33515-114">State Forecast</span></span>|<span data-ttu-id="33515-115">počasí/{State}</span><span class="sxs-lookup"><span data-stu-id="33515-115">weather/{state}</span></span>|  
|<span data-ttu-id="33515-116">Prognóza města</span><span class="sxs-lookup"><span data-stu-id="33515-116">City Forecast</span></span>|<span data-ttu-id="33515-117">počasí/{State}/{City}</span><span class="sxs-lookup"><span data-stu-id="33515-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="33515-118">Prognóza aktivity</span><span class="sxs-lookup"><span data-stu-id="33515-118">Activity Forecast</span></span>|<span data-ttu-id="33515-119">počasí/{State}/{City}/{Activity}</span><span class="sxs-lookup"><span data-stu-id="33515-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="33515-120">Tato tabulka popisuje sadu strukturně podobných identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="33515-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="33515-121">Každá položka je šablonou identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="33515-121">Each entry is a URI template.</span></span> <span data-ttu-id="33515-122">Segmenty ve složených závorkách popisují proměnné.</span><span class="sxs-lookup"><span data-stu-id="33515-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="33515-123">Segmenty, které nejsou ve složených závorkách, popisují řetězce literálů.</span><span class="sxs-lookup"><span data-stu-id="33515-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="33515-124">Třídy šablon WCF umožňují vývojářům převzít příchozí identifikátor URI, například "/Weather/WA/Seattle/Cycling", a odpovídat na šablonu, která ji popisuje, "/Weather/{State}/{City}/{Activity}".</span><span class="sxs-lookup"><span data-stu-id="33515-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="33515-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="33515-125">UriTemplate</span></span>  
 <span data-ttu-id="33515-126"><xref:System.UriTemplate>je třída, která zapouzdřuje šablonu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="33515-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="33515-127">Konstruktor přebírá řetězcový parametr definující šablonu.</span><span class="sxs-lookup"><span data-stu-id="33515-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="33515-128">Tento řetězec obsahuje šablonu ve formátu popsaném v následující části.</span><span class="sxs-lookup"><span data-stu-id="33515-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="33515-129"><xref:System.UriTemplate> Třída poskytuje metody, které umožňují odpovídat příchozímu identifikátoru URI šabloně, vygenerovat identifikátor URI ze šablony, načíst kolekci názvů proměnných použitých v šabloně, zjistit, zda jsou dvě šablony ekvivalentní, a vrátí šablonu. řetezce.</span><span class="sxs-lookup"><span data-stu-id="33515-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="33515-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>převezme základní adresu a kandidáta URI a pokusí se najít identifikátor URI pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="33515-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="33515-131">Je- <xref:System.UriTemplateMatch> li shoda úspěšná, je vrácena instance.</span><span class="sxs-lookup"><span data-stu-id="33515-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="33515-132">Objekt obsahuje základní identifikátor URI, kandidát identifikátor URI, kolekci název/hodnota parametrů dotazu, pole segmentů relativních cest, kolekci název/hodnota proměnných, které byly spárovány <xref:System.UriTemplate> , instanci použitou k provedení shody. <xref:System.UriTemplateMatch> , řetězec, který obsahuje libovolnou neshodnou část kandidátu identifikátoru URI (používá se, když šablona obsahuje zástupný znak) a objekt, který je spojen se šablonou.</span><span class="sxs-lookup"><span data-stu-id="33515-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33515-133"><xref:System.UriTemplate> Třída ignoruje schéma a číslo portu při porovnání kandidátu identifikátoru URI se šablonou.</span><span class="sxs-lookup"><span data-stu-id="33515-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="33515-134">Existují dvě metody, které umožňují vygenerovat identifikátor URI ze šablony <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> a. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29></span><span class="sxs-lookup"><span data-stu-id="33515-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="33515-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>převezme základní adresu a kolekci název/hodnota parametrů.</span><span class="sxs-lookup"><span data-stu-id="33515-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="33515-136">Tyto parametry jsou nahrazeny pro proměnné, pokud je šablona svázána.</span><span class="sxs-lookup"><span data-stu-id="33515-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="33515-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>převezme páry název/hodnota a nahradí je zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="33515-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="33515-138"><xref:System.UriTemplate.ToString>Vrátí řetězec šablony.</span><span class="sxs-lookup"><span data-stu-id="33515-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="33515-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> Vlastnost obsahuje kolekci názvů proměnných používaných v rámci segmentů cesty v řetězci šablony.</span><span class="sxs-lookup"><span data-stu-id="33515-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="33515-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>přebírá <xref:System.UriTemplate> jako parametr a vrací logickou hodnotu, která určuje, zda jsou dvě šablony ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="33515-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="33515-141">Další informace najdete v části věnované rovnosti šablon dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="33515-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="33515-142"><xref:System.UriTemplate>je navržený tak, aby fungoval s jakýmkoli schématem URI, které vyhovuje gramatice URI protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="33515-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="33515-143">Následují příklady podporovaných schémat identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="33515-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="33515-144">http://</span><span class="sxs-lookup"><span data-stu-id="33515-144">http://</span></span>  
  
- <span data-ttu-id="33515-145">https://</span><span class="sxs-lookup"><span data-stu-id="33515-145">https://</span></span>  
  
- <span data-ttu-id="33515-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="33515-146">net.tcp://</span></span>  
  
- <span data-ttu-id="33515-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="33515-147">net.pipe://</span></span>  
  
- <span data-ttu-id="33515-148">sb://</span><span class="sxs-lookup"><span data-stu-id="33515-148">sb://</span></span>  
  
 <span data-ttu-id="33515-149">Schémata jako file://a urn://nejsou v souladu s gramatikou identifikátoru URI HTTP a způsobují nepředvídatelné výsledky při použití se šablonami identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="33515-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="33515-150">Syntaxe řetězce šablony</span><span class="sxs-lookup"><span data-stu-id="33515-150">Template String Syntax</span></span>  
 <span data-ttu-id="33515-151">Šablona má tři části: cestu, volitelný dotaz a volitelný fragment.</span><span class="sxs-lookup"><span data-stu-id="33515-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="33515-152">Příklad naleznete v následující šabloně:</span><span class="sxs-lookup"><span data-stu-id="33515-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="33515-153">Cesta se skládá z "/Weather/{State}/{City}", dotaz se skládá z "? předpověď = {Length}" a fragment se skládá z "#frag1".</span><span class="sxs-lookup"><span data-stu-id="33515-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="33515-154">Úvodní a koncové lomítko jsou volitelné ve výrazu Path.</span><span class="sxs-lookup"><span data-stu-id="33515-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="33515-155">Výrazy dotazu i fragmenty mohou být zcela vynechány.</span><span class="sxs-lookup"><span data-stu-id="33515-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="33515-156">Cesta se skládá z řady segmentů oddělených znakem "/", každý segment může mít literálovou hodnotu, název proměnné (napsaný ve složených závorkách}) nebo zástupný znak (napsaný jako\*).</span><span class="sxs-lookup"><span data-stu-id="33515-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="33515-157">V předchozí šabloně je "\weather\ segmentem" hodnota literálu, zatímco "{State}" a "{City}" jsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="33515-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="33515-158">Proměnné přebírají svůj název od obsahu jejich složených závorek a mohou být později nahrazeny konkrétní hodnotou pro vytvoření *zavřeného identifikátoru URI*.</span><span class="sxs-lookup"><span data-stu-id="33515-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="33515-159">Zástupný znak je nepovinný, ale může se vyskytovat jenom na konci identifikátoru URI, kde logicky odpovídá "zbytek cesty".</span><span class="sxs-lookup"><span data-stu-id="33515-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="33515-160">Výraz dotazu, pokud je k dispozici, určuje řadu neuspořádaných párů název/hodnota oddělený ' & '.</span><span class="sxs-lookup"><span data-stu-id="33515-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="33515-161">Prvky výrazu dotazu mohou být buď páry literálů (x = 2), nebo dvojice proměnných (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="33515-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="33515-162">Výraz proměnné může mít pouze pravá strana dotazu.</span><span class="sxs-lookup"><span data-stu-id="33515-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="33515-163">({nějakých} = {someValue} není povolený.</span><span class="sxs-lookup"><span data-stu-id="33515-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="33515-164">Nespárované hodnoty (? x) nejsou povolené.</span><span class="sxs-lookup"><span data-stu-id="33515-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="33515-165">Neexistuje žádný rozdíl mezi prázdným výrazem dotazu a výrazem dotazu, který se skládá jenom z jednoho "?". (znamená libovolný dotaz).</span><span class="sxs-lookup"><span data-stu-id="33515-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="33515-166">Výraz fragmentu může sestávat z hodnoty literálu, nejsou povoleny žádné proměnné.</span><span class="sxs-lookup"><span data-stu-id="33515-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="33515-167">Všechny názvy proměnných šablony v řetězci šablony musí být jedinečné.</span><span class="sxs-lookup"><span data-stu-id="33515-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="33515-168">V názvech proměnných šablony se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="33515-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="33515-169">Příklady platných řetězců šablon:</span><span class="sxs-lookup"><span data-stu-id="33515-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="33515-170">""</span><span class="sxs-lookup"><span data-stu-id="33515-170">""</span></span>  
  
- <span data-ttu-id="33515-171">"/shoe"</span><span class="sxs-lookup"><span data-stu-id="33515-171">"/shoe"</span></span>  
  
- <span data-ttu-id="33515-172">"/Shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="33515-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="33515-173">{bot}/Boat</span><span class="sxs-lookup"><span data-stu-id="33515-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="33515-174">{bot}/{Boat}/Bed/{Quilt}</span><span class="sxs-lookup"><span data-stu-id="33515-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="33515-175">"bot/{člun}"</span><span class="sxs-lookup"><span data-stu-id="33515-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="33515-176">"bot/{člun}/\*"</span><span class="sxs-lookup"><span data-stu-id="33515-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="33515-177">"bot/člun? x = 2"</span><span class="sxs-lookup"><span data-stu-id="33515-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="33515-178">"bot/{člun}? x = {postel}"</span><span class="sxs-lookup"><span data-stu-id="33515-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="33515-179">"shoe/{boat}?x={bed}&y=band"</span><span class="sxs-lookup"><span data-stu-id="33515-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="33515-180">"?x={shoe}"</span><span class="sxs-lookup"><span data-stu-id="33515-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="33515-181">"bot? x = 3 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="33515-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="33515-182">Příklady neplatných řetězců šablon:</span><span class="sxs-lookup"><span data-stu-id="33515-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="33515-183">{bot}/{SHOE}/x = 2 – duplicitní názvy proměnných</span><span class="sxs-lookup"><span data-stu-id="33515-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="33515-184">{bot}/Boat/? postel = {bot} – duplicitní názvy proměnných</span><span class="sxs-lookup"><span data-stu-id="33515-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="33515-185">"? x = 2 & x = 3" – páry název/hodnota v řetězci dotazu musí být jedinečné, a to i v případě, že se jedná o literály.</span><span class="sxs-lookup"><span data-stu-id="33515-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="33515-186">"? x = 2 &" – řetězec dotazu je poškozen.</span><span class="sxs-lookup"><span data-stu-id="33515-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="33515-187">"? 2 & x = {bot}" – řetězec dotazu musí být dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="33515-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="33515-188">"? y = 2 & & X = 3" – řetězec dotazu musí být páry hodnoty názvu, nesmí názvy začínat znakem "&".</span><span class="sxs-lookup"><span data-stu-id="33515-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="33515-189">Složené segmenty cesty</span><span class="sxs-lookup"><span data-stu-id="33515-189">Compound Path Segments</span></span>  
 <span data-ttu-id="33515-190">Složené segmenty cesty umožňují, aby jeden segment cesty URI obsahoval více proměnných, a také proměnné kombinované s literály.</span><span class="sxs-lookup"><span data-stu-id="33515-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="33515-191">Níže jsou uvedeny příklady platných segmentů složených cest.</span><span class="sxs-lookup"><span data-stu-id="33515-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="33515-192">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="33515-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="33515-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="33515-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="33515-194">Bitmap. {EXT}/</span><span class="sxs-lookup"><span data-stu-id="33515-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="33515-195">určitého. {b} someLiteral {c} ({d})/</span><span class="sxs-lookup"><span data-stu-id="33515-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="33515-196">Následují příklady neplatných segmentů cesty.</span><span class="sxs-lookup"><span data-stu-id="33515-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="33515-197">Proměnné{} /-musí být pojmenovány.</span><span class="sxs-lookup"><span data-stu-id="33515-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="33515-198">/{Shoe}{Boat}-proměnné musí být odděleny literálem.</span><span class="sxs-lookup"><span data-stu-id="33515-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="33515-199">Párové a složené segmenty cesty</span><span class="sxs-lookup"><span data-stu-id="33515-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="33515-200">Složené segmenty cesty umožňují definovat šablony UriTemplate, které mají více proměnných v rámci jednoho segmentu cesty.</span><span class="sxs-lookup"><span data-stu-id="33515-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="33515-201">Například v následujícím řetězci šablony: Adresa/{State}. {City}: dvě proměnné (State a City) se definují v rámci stejného segmentu.</span><span class="sxs-lookup"><span data-stu-id="33515-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="33515-202">Tato šablona by odpovídala adrese URL, `http://example.com/Washington.Redmond` jako je například, ale také se shoduje `http://example.com/Washington.Redmond.Microsoft`s adresou URL, jako je.</span><span class="sxs-lookup"><span data-stu-id="33515-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="33515-203">V druhém případě bude proměnná stavu obsahovat "Washington" a proměnná City bude obsahovat "Redmond. Microsoft".</span><span class="sxs-lookup"><span data-stu-id="33515-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="33515-204">V tomto případě bude libovolný text (s výjimkou '/') odpovídat proměnné {City}.</span><span class="sxs-lookup"><span data-stu-id="33515-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="33515-205">Pokud chcete šablonu, která se neshoduje s textem "extra", umístěte proměnnou do samostatného segmentu šablony, například: Adresa/{State}/{City}.</span><span class="sxs-lookup"><span data-stu-id="33515-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="33515-206">Pojmenované segmenty se zástupnými znaky</span><span class="sxs-lookup"><span data-stu-id="33515-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="33515-207">Pojmenovaný segment se zástupným znakem je libovolný segment proměnné cesty, jejíž název proměnné začíná\*zástupným znakem.</span><span class="sxs-lookup"><span data-stu-id="33515-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="33515-208">Následující řetězec šablony obsahuje pojmenovaný zástupný segment s názvem bot.</span><span class="sxs-lookup"><span data-stu-id="33515-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="33515-209">Segmenty se zástupnými znaky musí splňovat následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="33515-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="33515-210">Pro každý řetězec šablony může existovat maximálně jeden pojmenovaný zástupný segment.</span><span class="sxs-lookup"><span data-stu-id="33515-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="33515-211">Pojmenovaný segment se zástupnými znaky musí být v cestě v segmentu napravo vpravo.</span><span class="sxs-lookup"><span data-stu-id="33515-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="33515-212">Pojmenovaný segment se zástupnými znaky nemůže koexistovat s anonymním segmentem zástupného znaku v rámci stejného řetězce šablony.</span><span class="sxs-lookup"><span data-stu-id="33515-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="33515-213">Název pojmenovaného zástupného segmentu musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="33515-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="33515-214">Pojmenované segmenty se zástupnými znaky nemůžou mít výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="33515-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="33515-215">Pojmenované segmenty se zástupnými znaky nemohou končit znakem "/".</span><span class="sxs-lookup"><span data-stu-id="33515-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="33515-216">Výchozí hodnoty proměnných</span><span class="sxs-lookup"><span data-stu-id="33515-216">Default Variable Values</span></span>  
 <span data-ttu-id="33515-217">Výchozí proměnné hodnoty umožňují zadat výchozí hodnoty pro proměnné v rámci šablony.</span><span class="sxs-lookup"><span data-stu-id="33515-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="33515-218">Výchozí proměnné lze zadat pomocí složených závorek, které deklarují proměnnou nebo jako kolekci předanou konstruktoru UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="33515-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="33515-219">Následující šablona ukazuje dva způsoby, jak zadat <xref:System.UriTemplate> proměnné s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="33515-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="33515-220">Tato šablona deklaruje `a` proměnnou s názvem s výchozí `1` hodnotou a proměnnou s názvem `b` s výchozí hodnotou `5`.</span><span class="sxs-lookup"><span data-stu-id="33515-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33515-221">Pouze proměnné segmentu cesty mají povoleny výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="33515-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="33515-222">Proměnné řetězce dotazu, proměnné složeného segmentu a pojmenované zástupné znaky nejsou povoleny výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="33515-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="33515-223">Následující kód ukazuje, jak jsou zpracovávány výchozí hodnoty proměnných při porovnání s kandidátem identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="33515-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> <span data-ttu-id="33515-224">Identifikátor URI `http://localhost:8000///` , jako je například, neodpovídá šabloně uvedené v předchozím kódu, ale identifikátor URI `http://localhost:8000/` , jako je například.</span><span class="sxs-lookup"><span data-stu-id="33515-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="33515-225">Následující kód ukazuje, jak se při vytváření identifikátoru URI se šablonou zpracovávají výchozí hodnoty proměnných.</span><span class="sxs-lookup"><span data-stu-id="33515-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```csharp
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
  
<span data-ttu-id="33515-226">Pokud je předána výchozí hodnota `null` proměnné, existují další omezení.</span><span class="sxs-lookup"><span data-stu-id="33515-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="33515-227">Proměnná může mít výchozí hodnotu, `null` Pokud je proměnná obsažena v pravém segmentu segmentu řetězce šablony nebo pokud všechny segmenty napravo od segmentu mají výchozí `null`hodnoty.</span><span class="sxs-lookup"><span data-stu-id="33515-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="33515-228">Níže jsou platné řetězce šablon s výchozími hodnotami `null`:</span><span class="sxs-lookup"><span data-stu-id="33515-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="33515-229">Níže jsou neplatné řetězce šablon s výchozími hodnotami `null`:</span><span class="sxs-lookup"><span data-stu-id="33515-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="33515-230">Výchozí hodnoty a spárování</span><span class="sxs-lookup"><span data-stu-id="33515-230">Default Values and Matching</span></span>  
 <span data-ttu-id="33515-231">Při porovnání kandidátu URI se šablonou, která má výchozí hodnoty, jsou výchozí hodnoty umístěny do <xref:System.UriTemplateMatch.BoundVariables%2A> kolekce, pokud nejsou zadány hodnoty v kandidátu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="33515-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="33515-232">Rovnocennost šablon</span><span class="sxs-lookup"><span data-stu-id="33515-232">Template Equivalence</span></span>  
 <span data-ttu-id="33515-233">Dvě šablony jsou označeny jako *strukturální ekvivalenty* , pokud všechny literály šablony odpovídají a mají proměnné ve stejných segmentech.</span><span class="sxs-lookup"><span data-stu-id="33515-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="33515-234">Například následující šablony jsou strukturně rovnocenné:</span><span class="sxs-lookup"><span data-stu-id="33515-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="33515-235">/a/{var1}/b b/{var2}? x = 1 & y = 2</span><span class="sxs-lookup"><span data-stu-id="33515-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="33515-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="33515-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="33515-237">a/{y}/B% c/{z}/? y = 2 & x = 1</span><span class="sxs-lookup"><span data-stu-id="33515-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="33515-238">Několik věcí, které je potřeba si všimnout:</span><span class="sxs-lookup"><span data-stu-id="33515-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="33515-239">Obsahuje-li šablona úvodní lomítka, bude ignorována pouze první z nich.</span><span class="sxs-lookup"><span data-stu-id="33515-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="33515-240">Při porovnávání řetězců šablon pro strukturální ekvivalenci je případ ignorován u názvů proměnných a segmentů cesty, řetězce dotazů rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="33515-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="33515-241">Řetězce dotazů jsou neseřazené.</span><span class="sxs-lookup"><span data-stu-id="33515-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="33515-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="33515-242">UriTemplateTable</span></span>  
 <span data-ttu-id="33515-243">Třída představuje asociativní <xref:System.UriTemplate> tabulku objektů svázaných s objektem výběru vývojáře. <xref:System.UriTemplateTable></span><span class="sxs-lookup"><span data-stu-id="33515-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="33515-244">Musí obsahovat alespoň jeden <xref:System.UriTemplate> před voláním <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. <xref:System.UriTemplateTable></span><span class="sxs-lookup"><span data-stu-id="33515-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="33515-245">Obsah a <xref:System.UriTemplateTable> lze změnit, dokud <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> není voláno.</span><span class="sxs-lookup"><span data-stu-id="33515-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="33515-246">Ověřování se provádí při <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> volání metody.</span><span class="sxs-lookup"><span data-stu-id="33515-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="33515-247">Typ provedeného ověřování závisí na hodnotě `allowMultiple` parametru na <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>hodnotu.</span><span class="sxs-lookup"><span data-stu-id="33515-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="33515-248">V <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> případě `false`, že je voláno <xref:System.UriTemplateTable> předání, zkontroluje, že v tabulce nejsou žádné šablony.</span><span class="sxs-lookup"><span data-stu-id="33515-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="33515-249">Pokud najde všechny strukturální rovnocenné šablony, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="33515-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="33515-250">Používá se ve spojení s <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> tím, kdy chcete zajistit, aby pouze jedna šablona odpovídala příchozímu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="33515-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="33515-251">Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána metoda `true`předávání, <xref:System.UriTemplateTable> umožňuje, aby bylo v rámci <xref:System.UriTemplateTable>obsaženo více strukturně ekvivalentních šablon.</span><span class="sxs-lookup"><span data-stu-id="33515-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="33515-252">Pokud sada <xref:System.UriTemplate> objektů přidaných <xref:System.UriTemplateTable> do obsahující řetězce dotazu nesmí být dvojznačná.</span><span class="sxs-lookup"><span data-stu-id="33515-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="33515-253">Jsou povoleny identické řetězce dotazů.</span><span class="sxs-lookup"><span data-stu-id="33515-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33515-254">I když <xref:System.UriTemplateTable> umožňuje základní adresy, které používají jiné než http systémy, schéma a číslo portu se ignorují, pokud se shodují odpovídající identifikátory URI kandidátů na šablony.</span><span class="sxs-lookup"><span data-stu-id="33515-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="33515-255">Nejednoznačnost řetězce dotazu</span><span class="sxs-lookup"><span data-stu-id="33515-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="33515-256">Šablony, které sdílejí stejnou cestu, obsahují dvojznačné řetězce dotazu, pokud existuje identifikátor URI, který se shoduje s více než jednou šablonou.</span><span class="sxs-lookup"><span data-stu-id="33515-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="33515-257">Následující sady řetězců dotazů jsou v rámci sebe jednoznačné:</span><span class="sxs-lookup"><span data-stu-id="33515-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="33515-258">? x = 1</span><span class="sxs-lookup"><span data-stu-id="33515-258">?x=1</span></span>  
  
- <span data-ttu-id="33515-259">? x = 2</span><span class="sxs-lookup"><span data-stu-id="33515-259">?x=2</span></span>  
  
- <span data-ttu-id="33515-260">? x = 3</span><span class="sxs-lookup"><span data-stu-id="33515-260">?x=3</span></span>  
  
- <span data-ttu-id="33515-261">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="33515-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="33515-262">? x = 2 & z = {var}</span><span class="sxs-lookup"><span data-stu-id="33515-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="33515-263">? x = 3</span><span class="sxs-lookup"><span data-stu-id="33515-263">?x=3</span></span>  
  
- <span data-ttu-id="33515-264">? x = 1</span><span class="sxs-lookup"><span data-stu-id="33515-264">?x=1</span></span>  
  
- <span data-ttu-id="33515-265">?</span><span class="sxs-lookup"><span data-stu-id="33515-265">?</span></span>  
  
- <span data-ttu-id="33515-266">?</span><span class="sxs-lookup"><span data-stu-id="33515-266">?</span></span> <span data-ttu-id="33515-267">x = {var}</span><span class="sxs-lookup"><span data-stu-id="33515-267">x={var}</span></span>  
  
- <span data-ttu-id="33515-268">?</span><span class="sxs-lookup"><span data-stu-id="33515-268">?</span></span>  
  
- <span data-ttu-id="33515-269">?m=get&c=rss</span><span class="sxs-lookup"><span data-stu-id="33515-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="33515-270">? m = vložení & c = RSS</span><span class="sxs-lookup"><span data-stu-id="33515-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="33515-271">?m=get&c=atom</span><span class="sxs-lookup"><span data-stu-id="33515-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="33515-272">? m = Put & c = Atom</span><span class="sxs-lookup"><span data-stu-id="33515-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="33515-273">Následující sady šablon řetězce dotazu jsou v rámci sebe dvojznačné:</span><span class="sxs-lookup"><span data-stu-id="33515-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="33515-274">? x = 1</span><span class="sxs-lookup"><span data-stu-id="33515-274">?x=1</span></span>  
  
- <span data-ttu-id="33515-275">? x = {var}</span><span class="sxs-lookup"><span data-stu-id="33515-275">?x={var}</span></span>  
  
 <span data-ttu-id="33515-276">"x = 1" – odpovídá oběma šablonám.</span><span class="sxs-lookup"><span data-stu-id="33515-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="33515-277">? x = 1</span><span class="sxs-lookup"><span data-stu-id="33515-277">?x=1</span></span>  
  
- <span data-ttu-id="33515-278">? y = 2</span><span class="sxs-lookup"><span data-stu-id="33515-278">?y=2</span></span>  
  
 <span data-ttu-id="33515-279">"x = 1 & y = 2" odpovídají oběma šablonám.</span><span class="sxs-lookup"><span data-stu-id="33515-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="33515-280">Důvodem je to, že řetězec dotazu může obsahovat více proměnných řetězce dotazu, a to tak, aby šablona odpovídala.</span><span class="sxs-lookup"><span data-stu-id="33515-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="33515-281">? x = 1</span><span class="sxs-lookup"><span data-stu-id="33515-281">?x=1</span></span>  
  
- <span data-ttu-id="33515-282">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="33515-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="33515-283">"x = 1 & y = 3" odpovídají oběma šablonám.</span><span class="sxs-lookup"><span data-stu-id="33515-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="33515-284">? x = 3 & y = 4</span><span class="sxs-lookup"><span data-stu-id="33515-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="33515-285">? x = 3 & z = 5</span><span class="sxs-lookup"><span data-stu-id="33515-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33515-286">Znaky "a" jsou považovány za jiné znaky, pokud jsou zobrazeny jako součást cesty identifikátoru URI nebo <xref:System.UriTemplate> literálu segmentu cesty (ale znaky a a a jsou považovány za stejné).</span><span class="sxs-lookup"><span data-stu-id="33515-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="33515-287">Znaky "a" jsou považovány za stejné znaky, pokud se zobrazují jako součást <xref:System.UriTemplate> proměnné {Variable} nebo řetězce dotazu (a a a a a a jsou také považovány za stejné znaky).</span><span class="sxs-lookup"><span data-stu-id="33515-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33515-288">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33515-288">See also</span></span>

- [<span data-ttu-id="33515-289">Přehled programovacího modelu webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="33515-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="33515-290">Programovací objektový model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="33515-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="33515-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="33515-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="33515-292">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="33515-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="33515-293">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="33515-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
