---
title: UriTemplate a UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: b0dc3b2b747bc08da239490db7db3ba77d1e7ed8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130244"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="7e8a2-102">UriTemplate a UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="7e8a2-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="7e8a2-103">Weboví vývojáři potřebují popisují tvaru a rozložení identifikátorů URI, která odpovídají jejich služby.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="7e8a2-104">Windows Communication Foundation (WCF) přidali dvě nové třídy poskytovat vývojářům kontrolu nad jejich identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <xref:System.UriTemplate> <span data-ttu-id="7e8a2-105">a <xref:System.UriTemplateTable> představují základ pro modul na základě identifikátoru URI odeslání ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-105">and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="7e8a2-106">Tyto třídy lze také na své vlastní, umožňuje vývojářům využívat šablon a identifikátor URI mechanismu mapování bez implementace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="7e8a2-107">Šablony</span><span class="sxs-lookup"><span data-stu-id="7e8a2-107">Templates</span></span>  
 <span data-ttu-id="7e8a2-108">Šablona je způsob, jak popisují sadu relativní identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="7e8a2-109">Sadu šablon identifikátor URI v následující tabulce ukazuje, jak může být definovaná systémem, který načte různé typy informací o počasí.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="7e8a2-110">Data</span><span class="sxs-lookup"><span data-stu-id="7e8a2-110">Data</span></span>|<span data-ttu-id="7e8a2-111">Šablona</span><span class="sxs-lookup"><span data-stu-id="7e8a2-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="7e8a2-112">Národní prognózy</span><span class="sxs-lookup"><span data-stu-id="7e8a2-112">National Forecast</span></span>|<span data-ttu-id="7e8a2-113">počasí/national</span><span class="sxs-lookup"><span data-stu-id="7e8a2-113">weather/national</span></span>|  
|<span data-ttu-id="7e8a2-114">Stav prognózy</span><span class="sxs-lookup"><span data-stu-id="7e8a2-114">State Forecast</span></span>|<span data-ttu-id="7e8a2-115">počasí / {state}</span><span class="sxs-lookup"><span data-stu-id="7e8a2-115">weather/{state}</span></span>|  
|<span data-ttu-id="7e8a2-116">Předpověď Město</span><span class="sxs-lookup"><span data-stu-id="7e8a2-116">City Forecast</span></span>|<span data-ttu-id="7e8a2-117">počasí / {state} / {Město}</span><span class="sxs-lookup"><span data-stu-id="7e8a2-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="7e8a2-118">Aktivita prognózy</span><span class="sxs-lookup"><span data-stu-id="7e8a2-118">Activity Forecast</span></span>|<span data-ttu-id="7e8a2-119">počasí / {state} / {město} / {aktivitu}</span><span class="sxs-lookup"><span data-stu-id="7e8a2-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="7e8a2-120">Tato tabulka popisuje sadu strukturálně podobné identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="7e8a2-121">Každá položka je šablona identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-121">Each entry is a URI template.</span></span> <span data-ttu-id="7e8a2-122">Segmenty ve složených závorkách popisují proměnné.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="7e8a2-123">Segmenty nejsou ve složených závorkách popisují řetězcových literálů.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="7e8a2-124">Třídy šablon WCF umožňuje vývojářům příchozí identifikátor URI, například "/ počasí/wa/seattle/recyklování" a přizpůsobit šablonu, která popisuje, "/weather/ {stavu} / {město} / {aktivitu}".</span><span class="sxs-lookup"><span data-stu-id="7e8a2-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="7e8a2-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7e8a2-125">UriTemplate</span></span>  
 <xref:System.UriTemplate> <span data-ttu-id="7e8a2-126">je třída, která zapouzdřuje šablona identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-126">is a class that encapsulates a URI template.</span></span> <span data-ttu-id="7e8a2-127">Konstruktor použije parametr řetězce, který definuje šablonu.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="7e8a2-128">Tento řetězec obsahuje šablonu ve formátu popsaném v další části.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="7e8a2-129"><xref:System.UriTemplate> Třída poskytuje metody, které vám umožní odpovídá příchozí identifikátor URI pro šablony, vygenerovat identifikátor URI ze šablony, načtení kolekce názvy proměnných v šabloně použije, zjistit, jestli dvě šablony jsou ekvivalentní a nevrací šablonu. řetězec.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> <span data-ttu-id="7e8a2-130">identifikátor URI a pokusí se porovnat identifikátoru URI v šabloně použije základní adresu a kandidáta.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-130">takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="7e8a2-131">Pokud tato shoda je úspěšná, <xref:System.UriTemplateMatch> je vrácena instance.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="7e8a2-132"><xref:System.UriTemplateMatch> Objekt obsahuje základní identifikátor URI identifikátor URI kolekce názvu a hodnoty parametrů dotazu, pole segmentů relativní cesta, název/hodnota kolekce proměnných, které se shoda našla, se danému kandidátovi <xref:System.UriTemplate> instance používá k provádění porovnání , řetězec, který obsahuje všechny nespárované část Release candidate identifikátoru URI (použito, pokud šablona obsahuje zástupný znak) a objekt, který je přidružený k šabloně.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e8a2-133"><xref:System.UriTemplate> Třídy ignoruje schéma a číslo portu při porovnávání kandidát URI do šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="7e8a2-134">Existují dvě metody, které umožňují vygenerovat identifikátor URI ze šablony, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> a <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> <span data-ttu-id="7e8a2-135">používá základní adresu a název/hodnota kolekci parametrů.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-135">takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="7e8a2-136">Tyto parametry jsou nahrazeny pro proměnné, když je vytvořena vazba šablonu.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-136">These parameters are substituted for variables when the template is bound.</span></span> <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> <span data-ttu-id="7e8a2-137">vezme dvojice název/hodnota a nahradí je zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-137">takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <xref:System.UriTemplate.ToString> <span data-ttu-id="7e8a2-138">Vrátí řetězec šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-138">returns the template string.</span></span>  
  
 <span data-ttu-id="7e8a2-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> Vlastnost obsahuje kolekci názvů proměnných používaných v rámci segmenty cesty šablony řetězce.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> <span data-ttu-id="7e8a2-140">přijímá <xref:System.UriTemplate> jako parametr a vrátí logickou hodnotu, která určuje, zda dvě šablony jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-140">takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="7e8a2-141">Další informace najdete v části šablony ekvivalence dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <xref:System.UriTemplate> <span data-ttu-id="7e8a2-142">je navržena pro práci s žádné schéma identifikátoru URI, který odpovídá identifikátoru URI protokolu HTTP gramatiky.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-142">is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="7e8a2-143">Následují příklady podporovaných schémata identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="7e8a2-144">http://</span><span class="sxs-lookup"><span data-stu-id="7e8a2-144">http://</span></span>  
  
- <span data-ttu-id="7e8a2-145">https://</span><span class="sxs-lookup"><span data-stu-id="7e8a2-145">https://</span></span>  
  
- <span data-ttu-id="7e8a2-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="7e8a2-146">net.tcp://</span></span>  
  
- <span data-ttu-id="7e8a2-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="7e8a2-147">net.pipe://</span></span>  
  
- <span data-ttu-id="7e8a2-148">sb://</span><span class="sxs-lookup"><span data-stu-id="7e8a2-148">sb://</span></span>  
  
 <span data-ttu-id="7e8a2-149">Schémata, jako je file:// nebo urn: / / není odpovídat gramatice identifikátoru URI protokolu HTTP a vést k nepředvídatelným výsledkům při použití s identifikátorem URI šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="7e8a2-150">Syntaxe řetězce šablon</span><span class="sxs-lookup"><span data-stu-id="7e8a2-150">Template String Syntax</span></span>  
 <span data-ttu-id="7e8a2-151">Šablona má tři části: cesta, nepovinný dotaz a fragment volitelné.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="7e8a2-152">Příklad najdete v tématu následující šablony:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="7e8a2-153">Cesta se skládá z "/weather/ {stavu} / {Město}", dotaz se skládá z"? prognózy = {délka} a fragment se skládá z"#frag1".</span><span class="sxs-lookup"><span data-stu-id="7e8a2-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="7e8a2-154">Úvodní a koncové lomítka jsou volitelné ve výrazu cesty.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="7e8a2-155">Dotaz a fragment výrazů můžete zcela vynechat.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="7e8a2-156">Cesta se skládá z řady segmentů oddělených pomocí '/', každý segment může mít hodnotu literálu, název proměnné (napsaného v {složených závorek}) nebo zástupný znak (zapsána jako\*").</span><span class="sxs-lookup"><span data-stu-id="7e8a2-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="7e8a2-157">V šabloně předchozí "\weather\ segmentu je literál hodnotu, zatímco"{state}"a"{city}"jsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="7e8a2-158">Proměnné přijmout jejich název z obsahu jejich složených závorek a mohou být později nahrazeny s konkrétní hodnotou k vytvoření *uzavřeno URI*.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="7e8a2-159">Zástupný znak je nepovinný, ale může vyskytovat jenom na konec identifikátoru URI, které logicky odpovídá "zbývající část cesty".</span><span class="sxs-lookup"><span data-stu-id="7e8a2-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="7e8a2-160">Výraz dotazu, pokud jsou k dispozici, určuje řadu dvojice Neseřazený název hodnota oddělené 'a'.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="7e8a2-161">Prvky výrazu dotazu může být buď literál páry (x = 2) nebo dvojice proměnné (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="7e8a2-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="7e8a2-162">Výraz proměnné může mít pouze pravé straně dotazu.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="7e8a2-163">({someName} = {Nějaká_hodnota} nepovoluje.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="7e8a2-164">Nespárované hodnoty (? x) nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="7e8a2-165">Není žádný rozdíl mezi prázdný dotaz výrazem a výraz dotazu tvořené pouze jedním "?" (i znamená "jakýkoli dotaz").</span><span class="sxs-lookup"><span data-stu-id="7e8a2-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="7e8a2-166">Výraz fragmentu se může skládat z literálovou hodnotou, jsou povoleny žádné proměnné.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="7e8a2-167">Všechny názvy proměnných šablony v rámci šablony řetězce musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="7e8a2-168">Názvy proměnných šablony jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="7e8a2-169">Příklady platnou šablonu řetězců:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="7e8a2-170">""</span><span class="sxs-lookup"><span data-stu-id="7e8a2-170">""</span></span>  
  
- <span data-ttu-id="7e8a2-171">"/ bot"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-171">"/shoe"</span></span>  
  
- <span data-ttu-id="7e8a2-172">"/shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="7e8a2-173">"{bot} / lodních"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="7e8a2-174">"{bot} / {lodních} /bed/ {quilt}"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="7e8a2-175">"bot / {lodních}"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="7e8a2-176">"shoe/{boat}/\*"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="7e8a2-177">"shoe/boat?x=2"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="7e8a2-178">"shoe/{boat}?x={bed}"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="7e8a2-179">"shoe/{boat}?x={bed}&y=band"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="7e8a2-180">"?x={shoe}"</span><span class="sxs-lookup"><span data-stu-id="7e8a2-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="7e8a2-181">"bot? x = 3 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="7e8a2-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="7e8a2-182">Příkladem řetězce neplatný šablon:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="7e8a2-183">"{bot} / {bot} / x = 2" – duplicitní názvy proměnných.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="7e8a2-184">"{bot} /boat/? základnu {bot} =" – duplicitní názvy proměnných.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="7e8a2-185">"? x = 2 & x = 3" – dvojice název/hodnota v řetězci dotazu musí být jedinečné, i v případě, že jsou literály.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="7e8a2-186">"? x = 2 &" – řetězec dotazu je poškozený.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="7e8a2-187">"? 2 & x = {bot}" – řetězec dotazu musí být dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="7e8a2-188">"? y = 2 & & X = 3" – řetězec dotazu musí být páry název-hodnota, názvy nesmí začínat 'a'.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="7e8a2-189">Složené segmenty cesty</span><span class="sxs-lookup"><span data-stu-id="7e8a2-189">Compound Path Segments</span></span>  
 <span data-ttu-id="7e8a2-190">Segmenty složené cesty povolit jeden segment cesty identifikátoru URI tak, aby obsahovala více proměnných stejně jako proměnné v kombinaci s literály.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="7e8a2-191">Následují příklady segmentů platný složené cesty.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="7e8a2-192">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="7e8a2-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="7e8a2-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="7e8a2-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="7e8a2-194">/ {filename}. {ext} /</span><span class="sxs-lookup"><span data-stu-id="7e8a2-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="7e8a2-195">/ {a}. {b}someLiteral{c}({d}) /</span><span class="sxs-lookup"><span data-stu-id="7e8a2-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="7e8a2-196">Následují příklady segmentů neplatná cesta.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="7e8a2-197">/{} – Musí být název proměnné.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="7e8a2-198">/ {bot} {loď} - proměnné musí být odděleny literál.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="7e8a2-199">Odpovídající a složené segmenty cesty</span><span class="sxs-lookup"><span data-stu-id="7e8a2-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="7e8a2-200">Segmenty cesty složené umožňují definovat šablony UriTemplate, který má více proměnných v rámci segmentu jednu cestu.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="7e8a2-201">Například v následujícím řetězci šablony: "Adresy / {state}. {Město} "v rámci stejné segmentu jsou definovány dvě proměnné (státu a města).</span><span class="sxs-lookup"><span data-stu-id="7e8a2-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="7e8a2-202">Tato šablona odpovídají, jako adresa URL `http://example.com/Washington.Redmond` ale budou se také shodovat s adresu URL jako `http://example.com/Washington.Redmond.Microsoft`.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="7e8a2-203">V takovém případě proměnné stavu bude obsahovat "Washington", a proměnnou město bude obsahovat "Redmond.Microsoft".</span><span class="sxs-lookup"><span data-stu-id="7e8a2-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="7e8a2-204">V tomto případě žádný text (s výjimkou "/") bude odpovídat proměnné {město}.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="7e8a2-205">Pokud chcete šablonu, která se nebudou shodovat s textem "navíc", vložte proměnnou samostatné šablony segmentu, například: "Addresses/{state}/{city}.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="7e8a2-206">Segmenty pojmenované zástupných znaků</span><span class="sxs-lookup"><span data-stu-id="7e8a2-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="7e8a2-207">Pojmenované zástupný segment, který je segment pro proměnnou cesty, název proměnné začíná zástupný znak "\*".</span><span class="sxs-lookup"><span data-stu-id="7e8a2-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="7e8a2-208">Následující šablony řetězec obsahuje pojmenované zástupný segment s názvem "bot".</span><span class="sxs-lookup"><span data-stu-id="7e8a2-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="7e8a2-209">Zástupný znak segmenty musí postupovat podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="7e8a2-210">Může existovat maximálně jednu s názvem zástupný segment pro každý řetězec šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="7e8a2-211">Pojmenované zástupný segment se musí nacházet v úplně vpravo segment v cestě.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="7e8a2-212">Pojmenované zástupný segment nemůžou existovat současně s anonymní zástupný segment v rámci stejného řetězce šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="7e8a2-213">Název pojmenované zástupný segment musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="7e8a2-214">Zástupný znak s názvem segmenty nemůže mít výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="7e8a2-215">Segmenty pojmenované zástupný znak nemůže končit znakem "/".</span><span class="sxs-lookup"><span data-stu-id="7e8a2-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="7e8a2-216">Výchozí hodnoty proměnných</span><span class="sxs-lookup"><span data-stu-id="7e8a2-216">Default Variable Values</span></span>  
 <span data-ttu-id="7e8a2-217">Výchozí hodnoty proměnné umožňují zadat výchozí hodnoty pro proměnné v rámci šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="7e8a2-218">Výchozí proměnné lze upravit pomocí složených závorek, které deklarujete proměnnou nebo kolekci předaný konstruktoru UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="7e8a2-219">Následující šablony se zobrazí dva způsoby, jak určit <xref:System.UriTemplate> proměnné s výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="7e8a2-220">Tato šablona deklaruje proměnnou s názvem `a` s výchozí hodnotou `1` a proměnné s názvem `b` s výchozí hodnotou `5`.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e8a2-221">Výchozí hodnoty jsou povoleny pouze proměnné cesty segmentu.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="7e8a2-222">Výchozí hodnoty nejsou povoleny proměnné řetězce dotazu, složený segment proměnné a proměnné s názvem zástupný znak.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="7e8a2-223">Následující kód ukazuje způsob zpracování výchozí hodnoty proměnných při porovnávání kandidát identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
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
> <span data-ttu-id="7e8a2-224">Identifikátor URI jako `http://localhost:8000///` šablony uvedené v předchozím kódu, ale neodpovídá identifikátoru URI jako `http://localhost:8000/` nemá.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="7e8a2-225">Následující kód ukazuje způsob zpracování výchozí hodnoty proměnných při vytváření identifikátor URI s šablonou.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
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
  
<span data-ttu-id="7e8a2-226">Když je proměnné předána výchozí hodnotu `null` existují některé další omezení.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="7e8a2-227">Proměnná může mít výchozí hodnotu `null` Pokud proměnnou je obsažena v pravém většiny segment řetězec šablony nebo pokud všechny segmenty napravo od segmentu mají výchozí hodnoty `null`.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="7e8a2-228">Níže jsou řetězce platnou šablonu s výchozími hodnotami `null`:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="7e8a2-229">Neplatná šablona řetězce s výchozími hodnotami jsou následující `null`:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="7e8a2-230">Výchozí hodnoty a porovnávání</span><span class="sxs-lookup"><span data-stu-id="7e8a2-230">Default Values and Matching</span></span>  
 <span data-ttu-id="7e8a2-231">Při porovnávání kandidát URI šablonou, která má výchozí hodnoty, výchozí hodnoty jsou umístěny v <xref:System.UriTemplateMatch.BoundVariables%2A> kolekce, pokud nejsou zadané hodnoty ve Release candidate identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="7e8a2-232">Ekvivalence šablony</span><span class="sxs-lookup"><span data-stu-id="7e8a2-232">Template Equivalence</span></span>  
 <span data-ttu-id="7e8a2-233">Dvě šablony jsou označeny jako *strukturálně ekvivalentní* při všem literálů se šablony a mají proměnné stejný segmentů.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="7e8a2-234">Například následující šablony jsou strukturálně ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="7e8a2-235">b /b /a/ {var1} / {var2}? x = 1 & y = 2</span><span class="sxs-lookup"><span data-stu-id="7e8a2-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="7e8a2-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="7e8a2-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="7e8a2-237">a/{y}/B%20B/{z}/?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="7e8a2-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="7e8a2-238">Všimněte si, že několik věcí:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="7e8a2-239">Pokud šablona obsahuje úvodních lomítek, pouze první z nich se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="7e8a2-240">Při porovnávání řetězců šablony pro strukturální ekvivalenci, se ignoruje velikost písmen pro názvy proměnných a segmenty cesty, řetězce dotazu jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="7e8a2-241">Neuspořádaný řetězce dotazu.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="7e8a2-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="7e8a2-242">UriTemplateTable</span></span>  
 <span data-ttu-id="7e8a2-243"><xref:System.UriTemplateTable> Třída reprezentuje asociativní tabulku <xref:System.UriTemplate> objekty vázané na uživatele výběr objektu vývojáře.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="7e8a2-244">A <xref:System.UriTemplateTable> musí obsahovat alespoň jeden <xref:System.UriTemplate> před voláním <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="7e8a2-245">Obsah <xref:System.UriTemplateTable> můžete změnit, dokud nebude <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="7e8a2-246">Provede se ověření, když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="7e8a2-247">Typ ověřování, závisí na hodnotu `allowMultiple` parametr <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="7e8a2-248">Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána při předávání v `false`, <xref:System.UriTemplateTable> kontroluje, ujistěte se, že v tabulce nejsou žádné šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="7e8a2-249">Pokud najde všechny šablony, strukturálně ekvivalentní, dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="7e8a2-250">To se používá ve spojení s <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> kdy budete chtít zajistit pouze jedna šablona odpovídá příchozí identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="7e8a2-251">Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána při předávání v `true`, <xref:System.UriTemplateTable> umožňuje více, strukturálně ekvivalentem šablony mají být obsažena v rámci <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="7e8a2-252">Pokud sadu <xref:System.UriTemplate> objekty přidané do <xref:System.UriTemplateTable> obsahují řetězce dotazů, nesmí se jednat o nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="7e8a2-253">Jsou řetězce identické dotazu povoleny.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e8a2-254">Zatímco <xref:System.UriTemplateTable> umožňuje základní adresy tohoto použití schémata než HTTP, schéma a číslo portu jsou ignorovány při porovnávání Release candidate identifikátory URI pro šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="7e8a2-255">Nejednoznačnosti řetězec dotazu</span><span class="sxs-lookup"><span data-stu-id="7e8a2-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="7e8a2-256">Šablony, které sdílejí stejnou cestu obsahují řetězce dotazů nejednoznačný, pokud je identifikátor URI, který odpovídá více než jedna šablona.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="7e8a2-257">Následující sady řetězce dotazu jsou jednoznačné v rámci samotné:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="7e8a2-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="7e8a2-258">?x=1</span></span>  
  
- <span data-ttu-id="7e8a2-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="7e8a2-259">?x=2</span></span>  
  
- <span data-ttu-id="7e8a2-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="7e8a2-260">?x=3</span></span>  
  
- <span data-ttu-id="7e8a2-261">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="7e8a2-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="7e8a2-262">?x=2&z={var}</span><span class="sxs-lookup"><span data-stu-id="7e8a2-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="7e8a2-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="7e8a2-263">?x=3</span></span>  
  
- <span data-ttu-id="7e8a2-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="7e8a2-264">?x=1</span></span>  
  
- <span data-ttu-id="7e8a2-265">?</span><span class="sxs-lookup"><span data-stu-id="7e8a2-265">?</span></span>  
  
- <span data-ttu-id="7e8a2-266">?</span><span class="sxs-lookup"><span data-stu-id="7e8a2-266">?</span></span> <span data-ttu-id="7e8a2-267">x = {var}</span><span class="sxs-lookup"><span data-stu-id="7e8a2-267">x={var}</span></span>  
  
- <span data-ttu-id="7e8a2-268">?</span><span class="sxs-lookup"><span data-stu-id="7e8a2-268">?</span></span>  
  
- <span data-ttu-id="7e8a2-269">?m=get&c=rss</span><span class="sxs-lookup"><span data-stu-id="7e8a2-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="7e8a2-270">?m=put&c=rss</span><span class="sxs-lookup"><span data-stu-id="7e8a2-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="7e8a2-271">?m=get&c=atom</span><span class="sxs-lookup"><span data-stu-id="7e8a2-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="7e8a2-272">?m=put&c=atom</span><span class="sxs-lookup"><span data-stu-id="7e8a2-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="7e8a2-273">Následující sady šablony řetězců dotazu je nejednoznačný v rámci samotných:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="7e8a2-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="7e8a2-274">?x=1</span></span>  
  
- <span data-ttu-id="7e8a2-275">?x={var}</span><span class="sxs-lookup"><span data-stu-id="7e8a2-275">?x={var}</span></span>  
  
 <span data-ttu-id="7e8a2-276">"x = 1"-odpovídá obě šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="7e8a2-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="7e8a2-277">?x=1</span></span>  
  
- <span data-ttu-id="7e8a2-278">? y = 2</span><span class="sxs-lookup"><span data-stu-id="7e8a2-278">?y=2</span></span>  
  
 <span data-ttu-id="7e8a2-279">"x = 1 & y = 2" odpovídá obě šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="7e8a2-280">Je to proto, že řetězec dotazu může obsahovat další proměnné řetězce dotazu, pak odpovídá šabloně.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="7e8a2-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="7e8a2-281">?x=1</span></span>  
  
- <span data-ttu-id="7e8a2-282">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="7e8a2-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="7e8a2-283">"x = 1 & y = 3" odpovídá obě šablony.</span><span class="sxs-lookup"><span data-stu-id="7e8a2-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="7e8a2-284">? x = 3 & y = 4</span><span class="sxs-lookup"><span data-stu-id="7e8a2-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="7e8a2-285">? x = 3 & z = 5</span><span class="sxs-lookup"><span data-stu-id="7e8a2-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e8a2-286">Á znaků a Á považují za různých znaků, když se zobrazí jako součást cesty identifikátoru URI nebo <xref:System.UriTemplate> segment cesty literálu (ale a znaků a A jsou považovány za stejný).</span><span class="sxs-lookup"><span data-stu-id="7e8a2-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="7e8a2-287">Á znaků a Á považují za stejné znaky, pokud se zobrazují jako součást <xref:System.UriTemplate> {variableName} nebo řetězec dotazu (a a a A také považují za stejné znaky).</span><span class="sxs-lookup"><span data-stu-id="7e8a2-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e8a2-288">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e8a2-288">See also</span></span>

- [<span data-ttu-id="7e8a2-289">Přehled modelu webového programování HTTP služby WCF</span><span class="sxs-lookup"><span data-stu-id="7e8a2-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="7e8a2-290">Programovací objektový model WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="7e8a2-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="7e8a2-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7e8a2-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="7e8a2-292">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7e8a2-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="7e8a2-293">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7e8a2-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
