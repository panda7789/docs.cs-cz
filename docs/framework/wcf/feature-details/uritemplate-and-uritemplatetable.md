---
title: UriTemplate a UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 2742217cb082f5c0354510a7e66818bafd6f1393
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144692"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="6fbb0-102">UriTemplate a UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="6fbb0-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="6fbb0-103">Vývojáři webu vyžadují možnost popsat tvar a rozložení identifikátorů URI, na které jejich služby reagují.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="6fbb0-104">Windows Communication Foundation (WCF) přidal dvě nové třídy, které vývojářům poskytují kontrolu nad svými identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="6fbb0-105"><xref:System.UriTemplate>a <xref:System.UriTemplateTable> tvoří základ odesílajícího stroje založeného na identifikátoru URI ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="6fbb0-106">Tyto třídy lze také použít na vlastní, což vývojářům umožňuje využít výhod šablon a mechanismu mapování identifikátorů URI bez implementace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="6fbb0-107">Šablony</span><span class="sxs-lookup"><span data-stu-id="6fbb0-107">Templates</span></span>  
 <span data-ttu-id="6fbb0-108">Šablona je způsob, jak popsat sadu relativních identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="6fbb0-109">Sada šablon identifikátorů URI v následující tabulce ukazuje, jak je možné definovat systém, který načte různé typy informací o počasí.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="6fbb0-110">Data</span><span class="sxs-lookup"><span data-stu-id="6fbb0-110">Data</span></span>|<span data-ttu-id="6fbb0-111">Šablona</span><span class="sxs-lookup"><span data-stu-id="6fbb0-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="6fbb0-112">Národní prognóza</span><span class="sxs-lookup"><span data-stu-id="6fbb0-112">National Forecast</span></span>|<span data-ttu-id="6fbb0-113">počasí/národní</span><span class="sxs-lookup"><span data-stu-id="6fbb0-113">weather/national</span></span>|  
|<span data-ttu-id="6fbb0-114">Prognóza stavu</span><span class="sxs-lookup"><span data-stu-id="6fbb0-114">State Forecast</span></span>|<span data-ttu-id="6fbb0-115">počasí/{State}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-115">weather/{state}</span></span>|  
|<span data-ttu-id="6fbb0-116">Prognóza města</span><span class="sxs-lookup"><span data-stu-id="6fbb0-116">City Forecast</span></span>|<span data-ttu-id="6fbb0-117">počasí/{State}/{City}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="6fbb0-118">Prognóza aktivity</span><span class="sxs-lookup"><span data-stu-id="6fbb0-118">Activity Forecast</span></span>|<span data-ttu-id="6fbb0-119">počasí/{State}/{City}/{Activity}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="6fbb0-120">Tato tabulka popisuje sadu strukturně podobných identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="6fbb0-121">Každá položka je šablonou identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-121">Each entry is a URI template.</span></span> <span data-ttu-id="6fbb0-122">Segmenty ve složených závorkách popisují proměnné.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="6fbb0-123">Segmenty, které nejsou ve složených závorkách, popisují řetězce literálů.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="6fbb0-124">Třídy šablon WCF umožňují vývojářům převzít příchozí identifikátor URI, například "/Weather/WA/Seattle/Cycling", a odpovídat na šablonu, která ji popisuje, "/Weather/{State}/{City}/{Activity}".</span><span class="sxs-lookup"><span data-stu-id="6fbb0-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="6fbb0-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="6fbb0-125">UriTemplate</span></span>  
 <span data-ttu-id="6fbb0-126"><xref:System.UriTemplate>je třída, která zapouzdřuje šablonu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="6fbb0-127">Konstruktor přebírá řetězcový parametr definující šablonu.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="6fbb0-128">Tento řetězec obsahuje šablonu ve formátu popsaném v následující části.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="6fbb0-129"><xref:System.UriTemplate>Třída poskytuje metody, které umožňují odpovídat příchozímu identifikátoru URI šabloně, vygenerovat identifikátor URI ze šablony, načíst kolekci názvů proměnných použitých v šabloně, určit, zda jsou dvě šablony ekvivalentní, a vrátí řetězec šablony.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="6fbb0-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>převezme základní adresu a kandidáta URI a pokusí se najít identifikátor URI pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="6fbb0-131">Je-li shoda úspěšná, <xref:System.UriTemplateMatch> je vrácena instance.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="6fbb0-132"><xref:System.UriTemplateMatch>Objekt obsahuje základní identifikátor URI. identifikátor URI kandidáta, kolekce název/hodnota parametrů dotazu, pole relativních segmentů cesty, kolekce název/hodnota proměnných, které byly spárovány, <xref:System.UriTemplate> instance použitá k provedení shody, řetězec, který obsahuje libovolnou neshodnou část KANDIDÁTu identifikátoru URI (používá se, když šablona obsahuje zástupný znak) a objekt, který je spojen se šablonou.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fbb0-133"><xref:System.UriTemplate>Třída ignoruje schéma a číslo portu při porovnání kandidátu identifikátoru URI se šablonou.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="6fbb0-134">Existují dvě metody, které umožňují vygenerovat identifikátor URI ze šablony <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> a <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> .</span><span class="sxs-lookup"><span data-stu-id="6fbb0-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="6fbb0-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>převezme základní adresu a kolekci název/hodnota parametrů.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="6fbb0-136">Tyto parametry jsou nahrazeny pro proměnné, pokud je šablona svázána.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="6fbb0-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>převezme páry název/hodnota a nahradí je zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="6fbb0-138"><xref:System.UriTemplate.ToString>Vrátí řetězec šablony.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="6fbb0-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A>Vlastnost obsahuje kolekci názvů proměnných používaných v rámci segmentů cesty v řetězci šablony.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="6fbb0-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>přebírá <xref:System.UriTemplate> jako parametr a vrací logickou hodnotu, která určuje, zda jsou dvě šablony ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="6fbb0-141">Další informace najdete v části věnované rovnosti šablon dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="6fbb0-142"><xref:System.UriTemplate>je navržený tak, aby fungoval s jakýmkoli schématem URI, které vyhovuje gramatice URI protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="6fbb0-143">Následují příklady podporovaných schémat identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-143">The following are examples of supported URI schemes.</span></span>  
  
- `http://`  
  
- `https://`  
  
- `net.tcp://`  
  
- `net.pipe://`  
  
- `sb://`  
  
 <span data-ttu-id="6fbb0-144">Schémata jako file://a urn://nejsou v souladu s gramatikou identifikátoru URI HTTP a způsobují nepředvídatelné výsledky při použití se šablonami identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-144">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="6fbb0-145">Syntaxe řetězce šablony</span><span class="sxs-lookup"><span data-stu-id="6fbb0-145">Template String Syntax</span></span>  
 <span data-ttu-id="6fbb0-146">Šablona má tři části: cestu, volitelný dotaz a volitelný fragment.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-146">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="6fbb0-147">Příklad naleznete v následující šabloně:</span><span class="sxs-lookup"><span data-stu-id="6fbb0-147">For an example, see the following template:</span></span>  
  
`"/weather/{state}/{city}?forecast={length)#frag1`  
  
 <span data-ttu-id="6fbb0-148">Cesta se skládá z "/Weather/{State}/{City}", dotaz se skládá z "? předpověď = {Length}" a fragment se skládá z "#frag1".</span><span class="sxs-lookup"><span data-stu-id="6fbb0-148">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="6fbb0-149">Úvodní a koncové lomítko jsou volitelné ve výrazu Path.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-149">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="6fbb0-150">Výrazy dotazu i fragmenty mohou být zcela vynechány.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-150">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="6fbb0-151">Cesta se skládá z řady segmentů oddělených znakem "/", každý segment může mít literálovou hodnotu, název proměnné (napsaný ve složených závorkách}) nebo zástupný znak (napsaný jako \* ).</span><span class="sxs-lookup"><span data-stu-id="6fbb0-151">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="6fbb0-152">V předchozí šabloně je "\weather\ segmentem" hodnota literálu, zatímco "{State}" a "{City}" jsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-152">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="6fbb0-153">Proměnné přebírají svůj název od obsahu jejich složených závorek a mohou být později nahrazeny konkrétní hodnotou pro vytvoření *zavřeného identifikátoru URI*.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-153">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="6fbb0-154">Zástupný znak je nepovinný, ale může se vyskytovat jenom na konci identifikátoru URI, kde logicky odpovídá "zbytek cesty".</span><span class="sxs-lookup"><span data-stu-id="6fbb0-154">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="6fbb0-155">Výraz dotazu, pokud je k dispozici, určuje řadu neuspořádaných párů název/hodnota oddělený ' & '.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-155">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="6fbb0-156">Prvky výrazu dotazu mohou být buď páry literálů (x = 2), nebo dvojice proměnných (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="6fbb0-156">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="6fbb0-157">Výraz proměnné může mít pouze pravá strana dotazu.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-157">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="6fbb0-158">({nějakých} = {someValue} není povolený.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-158">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="6fbb0-159">Nespárované hodnoty (? x) nejsou povolené.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-159">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="6fbb0-160">Neexistuje žádný rozdíl mezi prázdným výrazem dotazu a výrazem dotazu, který se skládá jenom z jednoho "?". (znamená libovolný dotaz).</span><span class="sxs-lookup"><span data-stu-id="6fbb0-160">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="6fbb0-161">Výraz fragmentu může sestávat z hodnoty literálu, nejsou povoleny žádné proměnné.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-161">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="6fbb0-162">Všechny názvy proměnných šablony v řetězci šablony musí být jedinečné.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-162">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="6fbb0-163">V názvech proměnných šablony se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-163">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="6fbb0-164">Příklady platných řetězců šablon:</span><span class="sxs-lookup"><span data-stu-id="6fbb0-164">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="6fbb0-165">""</span><span class="sxs-lookup"><span data-stu-id="6fbb0-165">""</span></span>  
  
- <span data-ttu-id="6fbb0-166">"/shoe"</span><span class="sxs-lookup"><span data-stu-id="6fbb0-166">"/shoe"</span></span>  
  
- <span data-ttu-id="6fbb0-167">"/Shoe/ \* "</span><span class="sxs-lookup"><span data-stu-id="6fbb0-167">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="6fbb0-168">{bot}/Boat</span><span class="sxs-lookup"><span data-stu-id="6fbb0-168">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="6fbb0-169">{bot}/{Boat}/Bed/{Quilt}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-169">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="6fbb0-170">"bot/{člun}"</span><span class="sxs-lookup"><span data-stu-id="6fbb0-170">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="6fbb0-171">"bot/{člun}/ \* "</span><span class="sxs-lookup"><span data-stu-id="6fbb0-171">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="6fbb0-172">"bot/člun? x = 2"</span><span class="sxs-lookup"><span data-stu-id="6fbb0-172">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="6fbb0-173">"bot/{člun}? x = {postel}"</span><span class="sxs-lookup"><span data-stu-id="6fbb0-173">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="6fbb0-174">"bot/{člun}? x = {postel} &y = Band"</span><span class="sxs-lookup"><span data-stu-id="6fbb0-174">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="6fbb0-175">"? x = {bot}"</span><span class="sxs-lookup"><span data-stu-id="6fbb0-175">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="6fbb0-176">"bot? x = 3&y = {var}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-176">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="6fbb0-177">Příklady neplatných řetězců šablon:</span><span class="sxs-lookup"><span data-stu-id="6fbb0-177">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="6fbb0-178">{bot}/{SHOE}/x = 2 – duplicitní názvy proměnných</span><span class="sxs-lookup"><span data-stu-id="6fbb0-178">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="6fbb0-179">{bot}/Boat/? postel = {bot} – duplicitní názvy proměnných</span><span class="sxs-lookup"><span data-stu-id="6fbb0-179">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="6fbb0-180">"? x = 2&x = 3" – páry název/hodnota v řetězci dotazu musí být jedinečné, a to i v případě, že se jedná o literály.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-180">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="6fbb0-181">"? x = 2&" – řetězec dotazu je poškozen.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-181">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="6fbb0-182">"? 2&x = {bot}" – řetězec dotazu musí být dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-182">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="6fbb0-183">"? y = 2&&X = 3" – řetězec dotazu musí být páry název hodnota, názvy nemohou začínat na "&".</span><span class="sxs-lookup"><span data-stu-id="6fbb0-183">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="6fbb0-184">Složené segmenty cesty</span><span class="sxs-lookup"><span data-stu-id="6fbb0-184">Compound Path Segments</span></span>  
 <span data-ttu-id="6fbb0-185">Složené segmenty cesty umožňují, aby jeden segment cesty URI obsahoval více proměnných, a také proměnné kombinované s literály.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-185">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="6fbb0-186">Níže jsou uvedeny příklady platných segmentů složených cest.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-186">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="6fbb0-187">Bitmap. {EXT}/</span><span class="sxs-lookup"><span data-stu-id="6fbb0-187">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="6fbb0-188">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="6fbb0-188">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="6fbb0-189">Bitmap. {EXT}/</span><span class="sxs-lookup"><span data-stu-id="6fbb0-189">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="6fbb0-190">určitého. {b} someLiteral {c} ({d})/</span><span class="sxs-lookup"><span data-stu-id="6fbb0-190">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="6fbb0-191">Následují příklady neplatných segmentů cesty.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-191">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="6fbb0-192">{}Proměnné/-musí být pojmenovány.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-192">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="6fbb0-193">/{Shoe}{Boat}-proměnné musí být odděleny literálem.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-193">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="6fbb0-194">Párové a složené segmenty cesty</span><span class="sxs-lookup"><span data-stu-id="6fbb0-194">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="6fbb0-195">Složené segmenty cesty umožňují definovat šablony UriTemplate, které mají více proměnných v rámci jednoho segmentu cesty.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-195">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="6fbb0-196">Například v následujícím řetězci šablony: "adresy/{State}". {City}: dvě proměnné (State a City) se definují v rámci stejného segmentu.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-196">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="6fbb0-197">Tato šablona by odpovídala adrese URL, jako je například, `http://example.com/Washington.Redmond` ale také se shoduje s adresou URL, jako je `http://example.com/Washington.Redmond.Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="6fbb0-197">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="6fbb0-198">V druhém případě bude proměnná stavu obsahovat "Washington" a proměnná City bude obsahovat "Redmond. Microsoft".</span><span class="sxs-lookup"><span data-stu-id="6fbb0-198">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="6fbb0-199">V tomto případě bude libovolný text (s výjimkou '/') odpovídat proměnné {City}.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-199">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="6fbb0-200">Pokud chcete šablonu, která se neshoduje s textem "extra", umístěte proměnnou do samostatného segmentu šablony, například: addresss/{State}/{City}.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-200">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="6fbb0-201">Pojmenované segmenty se zástupnými znaky</span><span class="sxs-lookup"><span data-stu-id="6fbb0-201">Named Wildcard Segments</span></span>  
 <span data-ttu-id="6fbb0-202">Pojmenovaný segment se zástupným znakem je libovolný segment proměnné cesty, jejíž název proměnné začíná zástupným znakem \* .</span><span class="sxs-lookup"><span data-stu-id="6fbb0-202">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="6fbb0-203">Následující řetězec šablony obsahuje pojmenovaný zástupný segment s názvem bot.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-203">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
`"literal/{*shoe}"`  
  
 <span data-ttu-id="6fbb0-204">Segmenty se zástupnými znaky musí splňovat následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="6fbb0-204">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="6fbb0-205">Pro každý řetězec šablony může existovat maximálně jeden pojmenovaný zástupný segment.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-205">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="6fbb0-206">Pojmenovaný segment se zástupnými znaky musí být v cestě v segmentu napravo vpravo.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-206">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="6fbb0-207">Pojmenovaný segment se zástupnými znaky nemůže koexistovat s anonymním segmentem zástupného znaku v rámci stejného řetězce šablony.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-207">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="6fbb0-208">Název pojmenovaného zástupného segmentu musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-208">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="6fbb0-209">Pojmenované segmenty se zástupnými znaky nemůžou mít výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-209">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="6fbb0-210">Pojmenované segmenty se zástupnými znaky nemohou končit znakem "/".</span><span class="sxs-lookup"><span data-stu-id="6fbb0-210">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="6fbb0-211">Výchozí hodnoty proměnných</span><span class="sxs-lookup"><span data-stu-id="6fbb0-211">Default Variable Values</span></span>  
 <span data-ttu-id="6fbb0-212">Výchozí proměnné hodnoty umožňují zadat výchozí hodnoty pro proměnné v rámci šablony.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-212">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="6fbb0-213">Výchozí proměnné lze zadat pomocí složených závorek, které deklarují proměnnou nebo jako kolekci předanou konstruktoru UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-213">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="6fbb0-214">Následující šablona ukazuje dva způsoby, jak zadat <xref:System.UriTemplate> proměnné s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-214">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="6fbb0-215">Tato šablona deklaruje proměnnou s názvem `a` s výchozí hodnotou `1` a proměnnou s názvem `b` s výchozí hodnotou `5` .</span><span class="sxs-lookup"><span data-stu-id="6fbb0-215">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fbb0-216">Pouze proměnné segmentu cesty mají povoleny výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-216">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="6fbb0-217">Proměnné řetězce dotazu, proměnné složeného segmentu a pojmenované zástupné znaky nejsou povoleny výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-217">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="6fbb0-218">Následující kód ukazuje, jak jsou zpracovávány výchozí hodnoty proměnných při porovnání s kandidátem identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-218">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
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
> <span data-ttu-id="6fbb0-219">Identifikátor URI, jako je například `http://localhost:8000///` , neodpovídá šabloně uvedené v předchozím kódu, ale identifikátor URI, jako je například `http://localhost:8000/` .</span><span class="sxs-lookup"><span data-stu-id="6fbb0-219">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="6fbb0-220">Následující kód ukazuje, jak se při vytváření identifikátoru URI se šablonou zpracovávají výchozí hodnoty proměnných.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-220">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
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
  
<span data-ttu-id="6fbb0-221">Pokud je předána výchozí hodnota proměnné, `null` existují další omezení.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-221">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="6fbb0-222">Proměnná může mít výchozí hodnotu, `null` Pokud je proměnná obsažena v pravém segmentu segmentu řetězce šablony nebo pokud všechny segmenty napravo od segmentu mají výchozí hodnoty `null` .</span><span class="sxs-lookup"><span data-stu-id="6fbb0-222">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="6fbb0-223">Níže jsou platné řetězce šablon s výchozími hodnotami `null` :</span><span class="sxs-lookup"><span data-stu-id="6fbb0-223">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="6fbb0-224">Níže jsou neplatné řetězce šablon s výchozími hodnotami `null` :</span><span class="sxs-lookup"><span data-stu-id="6fbb0-224">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="6fbb0-225">Výchozí hodnoty a spárování</span><span class="sxs-lookup"><span data-stu-id="6fbb0-225">Default Values and Matching</span></span>  
 <span data-ttu-id="6fbb0-226">Při porovnání kandidátu URI se šablonou, která má výchozí hodnoty, jsou výchozí hodnoty umístěny do <xref:System.UriTemplateMatch.BoundVariables%2A> kolekce, pokud nejsou zadány hodnoty v kandidátu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-226">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="6fbb0-227">Rovnocennost šablon</span><span class="sxs-lookup"><span data-stu-id="6fbb0-227">Template Equivalence</span></span>  
 <span data-ttu-id="6fbb0-228">Dvě šablony jsou označeny jako *strukturální ekvivalenty* , pokud všechny literály šablony odpovídají a mají proměnné ve stejných segmentech.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-228">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="6fbb0-229">Například následující šablony jsou strukturně rovnocenné:</span><span class="sxs-lookup"><span data-stu-id="6fbb0-229">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="6fbb0-230">/a/{var1}/b b/{var2}? x = 1&y = 2</span><span class="sxs-lookup"><span data-stu-id="6fbb0-230">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="6fbb0-231">a/{x}/b% c/{var1}? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="6fbb0-231">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="6fbb0-232">a/{y}/B% c/{z}/? y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="6fbb0-232">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="6fbb0-233">Několik věcí, které je potřeba si všimnout:</span><span class="sxs-lookup"><span data-stu-id="6fbb0-233">A few things to notice:</span></span>  
  
- <span data-ttu-id="6fbb0-234">Obsahuje-li šablona úvodní lomítka, bude ignorována pouze první z nich.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-234">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="6fbb0-235">Při porovnávání řetězců šablon pro strukturální ekvivalenci je případ ignorován u názvů proměnných a segmentů cesty, řetězce dotazů rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-235">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="6fbb0-236">Řetězce dotazů jsou neseřazené.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-236">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="6fbb0-237">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="6fbb0-237">UriTemplateTable</span></span>  
 <span data-ttu-id="6fbb0-238"><xref:System.UriTemplateTable>Třída představuje asociativní tabulku <xref:System.UriTemplate> objektů svázaných s objektem výběru vývojáře.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-238">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="6fbb0-239"><xref:System.UriTemplateTable>Musí obsahovat alespoň jeden <xref:System.UriTemplate> před voláním <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="6fbb0-239">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="6fbb0-240">Obsah a <xref:System.UriTemplateTable> lze změnit, dokud <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> není voláno.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-240">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="6fbb0-241">Ověřování se provádí při <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> volání metody.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-241">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="6fbb0-242">Typ provedeného ověřování závisí na hodnotě `allowMultiple` parametru na hodnotu <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .</span><span class="sxs-lookup"><span data-stu-id="6fbb0-242">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="6fbb0-243">V případě <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> , že je voláno předání `false` , <xref:System.UriTemplateTable> zkontroluje, že v tabulce nejsou žádné šablony.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-243">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="6fbb0-244">Pokud najde všechny strukturální rovnocenné šablony, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-244">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="6fbb0-245">Používá se ve spojení s tím, <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> kdy chcete zajistit, aby pouze jedna šablona odpovídala příchozímu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-245">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="6fbb0-246">Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána metoda předávání `true` , <xref:System.UriTemplateTable> umožňuje, aby bylo v rámci obsaženo více strukturně ekvivalentních šablon <xref:System.UriTemplateTable> .</span><span class="sxs-lookup"><span data-stu-id="6fbb0-246">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="6fbb0-247">Pokud sada <xref:System.UriTemplate> objektů přidaných do <xref:System.UriTemplateTable> obsahující řetězce dotazu nesmí být dvojznačná.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-247">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="6fbb0-248">Jsou povoleny identické řetězce dotazů.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-248">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fbb0-249">I když <xref:System.UriTemplateTable> umožňuje základní adresy, které používají jiné než http systémy, schéma a číslo portu se ignorují, pokud se shodují odpovídající identifikátory URI kandidátů na šablony.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-249">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="6fbb0-250">Nejednoznačnost řetězce dotazu</span><span class="sxs-lookup"><span data-stu-id="6fbb0-250">Query String Ambiguity</span></span>  
 <span data-ttu-id="6fbb0-251">Šablony, které sdílejí stejnou cestu, obsahují dvojznačné řetězce dotazu, pokud existuje identifikátor URI, který se shoduje s více než jednou šablonou.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-251">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="6fbb0-252">Následující sady řetězců dotazů jsou v rámci sebe jednoznačné:</span><span class="sxs-lookup"><span data-stu-id="6fbb0-252">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="6fbb0-253">? x = 1</span><span class="sxs-lookup"><span data-stu-id="6fbb0-253">?x=1</span></span>  
  
- <span data-ttu-id="6fbb0-254">? x = 2</span><span class="sxs-lookup"><span data-stu-id="6fbb0-254">?x=2</span></span>  
  
- <span data-ttu-id="6fbb0-255">? x = 3</span><span class="sxs-lookup"><span data-stu-id="6fbb0-255">?x=3</span></span>  
  
- <span data-ttu-id="6fbb0-256">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-256">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="6fbb0-257">? x = 2&z = {var}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-257">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="6fbb0-258">? x = 3</span><span class="sxs-lookup"><span data-stu-id="6fbb0-258">?x=3</span></span>  
  
- <span data-ttu-id="6fbb0-259">? x = 1</span><span class="sxs-lookup"><span data-stu-id="6fbb0-259">?x=1</span></span>  
  
- <span data-ttu-id="6fbb0-260">?</span><span class="sxs-lookup"><span data-stu-id="6fbb0-260">?</span></span>  
  
- <span data-ttu-id="6fbb0-261">?</span><span class="sxs-lookup"><span data-stu-id="6fbb0-261">?</span></span> <span data-ttu-id="6fbb0-262">x = {var}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-262">x={var}</span></span>  
  
- <span data-ttu-id="6fbb0-263">?</span><span class="sxs-lookup"><span data-stu-id="6fbb0-263">?</span></span>  
  
- <span data-ttu-id="6fbb0-264">? m = získat&c = RSS</span><span class="sxs-lookup"><span data-stu-id="6fbb0-264">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="6fbb0-265">? m = vložení&c = RSS</span><span class="sxs-lookup"><span data-stu-id="6fbb0-265">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="6fbb0-266">? m = získat&c = Atom</span><span class="sxs-lookup"><span data-stu-id="6fbb0-266">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="6fbb0-267">? m = Put&c = Atom</span><span class="sxs-lookup"><span data-stu-id="6fbb0-267">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="6fbb0-268">Následující sady šablon řetězce dotazu jsou v rámci sebe dvojznačné:</span><span class="sxs-lookup"><span data-stu-id="6fbb0-268">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="6fbb0-269">? x = 1</span><span class="sxs-lookup"><span data-stu-id="6fbb0-269">?x=1</span></span>  
  
- <span data-ttu-id="6fbb0-270">? x = {var}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-270">?x={var}</span></span>  
  
 <span data-ttu-id="6fbb0-271">"x = 1" – odpovídá oběma šablonám.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-271">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="6fbb0-272">? x = 1</span><span class="sxs-lookup"><span data-stu-id="6fbb0-272">?x=1</span></span>  
  
- <span data-ttu-id="6fbb0-273">? y = 2</span><span class="sxs-lookup"><span data-stu-id="6fbb0-273">?y=2</span></span>  
  
 <span data-ttu-id="6fbb0-274">"x = 1&y = 2" odpovídají oběma šablonám.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-274">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="6fbb0-275">Důvodem je to, že řetězec dotazu může obsahovat více proměnných řetězce dotazu, a to tak, aby šablona odpovídala.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-275">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="6fbb0-276">? x = 1</span><span class="sxs-lookup"><span data-stu-id="6fbb0-276">?x=1</span></span>  
  
- <span data-ttu-id="6fbb0-277">? x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="6fbb0-277">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="6fbb0-278">"x = 1&y = 3" odpovídají oběma šablonám.</span><span class="sxs-lookup"><span data-stu-id="6fbb0-278">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="6fbb0-279">? x = 3&y = 4</span><span class="sxs-lookup"><span data-stu-id="6fbb0-279">?x=3&y=4</span></span>  
  
- <span data-ttu-id="6fbb0-280">? x = 3&z = 5</span><span class="sxs-lookup"><span data-stu-id="6fbb0-280">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fbb0-281">Znaky "a" jsou považovány za jiné znaky, pokud jsou zobrazeny jako součást cesty identifikátoru URI nebo <xref:System.UriTemplate> literálu segmentu cesty (ale znaky a a a jsou považovány za stejné).</span><span class="sxs-lookup"><span data-stu-id="6fbb0-281">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="6fbb0-282">Znaky "a" jsou považovány za stejné znaky, pokud se zobrazují jako součást <xref:System.UriTemplate> proměnné {Variable} nebo řetězce dotazu (a a a a a a jsou také považovány za stejné znaky).</span><span class="sxs-lookup"><span data-stu-id="6fbb0-282">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fbb0-283">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fbb0-283">See also</span></span>

- [<span data-ttu-id="6fbb0-284">Přehled programovacího modelu webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="6fbb0-284">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="6fbb0-285">Programovací objektový model WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="6fbb0-285">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="6fbb0-286">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="6fbb0-286">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="6fbb0-287">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="6fbb0-287">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="6fbb0-288">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="6fbb0-288">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
