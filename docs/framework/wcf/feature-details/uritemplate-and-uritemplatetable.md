---
title: UriTemplate a UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: b0dc3b2b747bc08da239490db7db3ba77d1e7ed8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130244"
---
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate a UriTemplateTable
Weboví vývojáři potřebují popisují tvaru a rozložení identifikátorů URI, která odpovídají jejich služby. Windows Communication Foundation (WCF) přidali dvě nové třídy poskytovat vývojářům kontrolu nad jejich identifikátorů URI. <xref:System.UriTemplate> a <xref:System.UriTemplateTable> představují základ pro modul na základě identifikátoru URI odeslání ve službě WCF. Tyto třídy lze také na své vlastní, umožňuje vývojářům využívat šablon a identifikátor URI mechanismu mapování bez implementace služby WCF.  
  
## <a name="templates"></a>Šablony  
 Šablona je způsob, jak popisují sadu relativní identifikátory URI. Sadu šablon identifikátor URI v následující tabulce ukazuje, jak může být definovaná systémem, který načte různé typy informací o počasí.  
  
|Data|Šablona|  
|----------|--------------|  
|Národní prognózy|počasí/national|  
|Stav prognózy|počasí / {state}|  
|Předpověď Město|počasí / {state} / {Město}|  
|Aktivita prognózy|počasí / {state} / {město} / {aktivitu}|  
  
 Tato tabulka popisuje sadu strukturálně podobné identifikátorů URI. Každá položka je šablona identifikátoru URI. Segmenty ve složených závorkách popisují proměnné. Segmenty nejsou ve složených závorkách popisují řetězcových literálů. Třídy šablon WCF umožňuje vývojářům příchozí identifikátor URI, například "/ počasí/wa/seattle/recyklování" a přizpůsobit šablonu, která popisuje, "/weather/ {stavu} / {město} / {aktivitu}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> je třída, která zapouzdřuje šablona identifikátoru URI. Konstruktor použije parametr řetězce, který definuje šablonu. Tento řetězec obsahuje šablonu ve formátu popsaném v další části. <xref:System.UriTemplate> Třída poskytuje metody, které vám umožní odpovídá příchozí identifikátor URI pro šablony, vygenerovat identifikátor URI ze šablony, načtení kolekce názvy proměnných v šabloně použije, zjistit, jestli dvě šablony jsou ekvivalentní a nevrací šablonu. řetězec.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> identifikátor URI a pokusí se porovnat identifikátoru URI v šabloně použije základní adresu a kandidáta. Pokud tato shoda je úspěšná, <xref:System.UriTemplateMatch> je vrácena instance. <xref:System.UriTemplateMatch> Objekt obsahuje základní identifikátor URI identifikátor URI kolekce názvu a hodnoty parametrů dotazu, pole segmentů relativní cesta, název/hodnota kolekce proměnných, které se shoda našla, se danému kandidátovi <xref:System.UriTemplate> instance používá k provádění porovnání , řetězec, který obsahuje všechny nespárované část Release candidate identifikátoru URI (použito, pokud šablona obsahuje zástupný znak) a objekt, který je přidružený k šabloně.  
  
> [!NOTE]
>  <xref:System.UriTemplate> Třídy ignoruje schéma a číslo portu při porovnávání kandidát URI do šablony.  
  
 Existují dvě metody, které umožňují vygenerovat identifikátor URI ze šablony, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> a <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>. <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> používá základní adresu a název/hodnota kolekci parametrů. Tyto parametry jsou nahrazeny pro proměnné, když je vytvořena vazba šablonu. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> vezme dvojice název/hodnota a nahradí je zleva doprava.  
  
 <xref:System.UriTemplate.ToString> Vrátí řetězec šablony.  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A> Vlastnost obsahuje kolekci názvů proměnných používaných v rámci segmenty cesty šablony řetězce.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> přijímá <xref:System.UriTemplate> jako parametr a vrátí logickou hodnotu, která určuje, zda dvě šablony jsou ekvivalentní. Další informace najdete v části šablony ekvivalence dále v tomto tématu.  
  
 <xref:System.UriTemplate> je navržena pro práci s žádné schéma identifikátoru URI, který odpovídá identifikátoru URI protokolu HTTP gramatiky. Následují příklady podporovaných schémata identifikátoru URI.  
  
- http://  
  
- https://  
  
- net.tcp://  
  
- net.pipe://  
  
- sb://  
  
 Schémata, jako je file:// nebo urn: / / není odpovídat gramatice identifikátoru URI protokolu HTTP a vést k nepředvídatelným výsledkům při použití s identifikátorem URI šablony.  
  
### <a name="template-string-syntax"></a>Syntaxe řetězce šablon  
 Šablona má tři části: cesta, nepovinný dotaz a fragment volitelné. Příklad najdete v tématu následující šablony:  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 Cesta se skládá z "/weather/ {stavu} / {Město}", dotaz se skládá z"? prognózy = {délka} a fragment se skládá z"#frag1".  
  
 Úvodní a koncové lomítka jsou volitelné ve výrazu cesty. Dotaz a fragment výrazů můžete zcela vynechat. Cesta se skládá z řady segmentů oddělených pomocí '/', každý segment může mít hodnotu literálu, název proměnné (napsaného v {složených závorek}) nebo zástupný znak (zapsána jako\*"). V šabloně předchozí "\weather\ segmentu je literál hodnotu, zatímco"{state}"a"{city}"jsou proměnné. Proměnné přijmout jejich název z obsahu jejich složených závorek a mohou být později nahrazeny s konkrétní hodnotou k vytvoření *uzavřeno URI*. Zástupný znak je nepovinný, ale může vyskytovat jenom na konec identifikátoru URI, které logicky odpovídá "zbývající část cesty".  
  
 Výraz dotazu, pokud jsou k dispozici, určuje řadu dvojice Neseřazený název hodnota oddělené 'a'. Prvky výrazu dotazu může být buď literál páry (x = 2) nebo dvojice proměnné (x = {var}). Výraz proměnné může mít pouze pravé straně dotazu. ({someName} = {Nějaká_hodnota} nepovoluje. Nespárované hodnoty (? x) nejsou povoleny. Není žádný rozdíl mezi prázdný dotaz výrazem a výraz dotazu tvořené pouze jedním "?" (i znamená "jakýkoli dotaz").  
  
 Výraz fragmentu se může skládat z literálovou hodnotou, jsou povoleny žádné proměnné.  
  
 Všechny názvy proměnných šablony v rámci šablony řetězce musí být jedinečný. Názvy proměnných šablony jsou malá a velká písmena.  
  
 Příklady platnou šablonu řetězců:  
  
- ""  
  
- "/ bot"  
  
- "/shoe/\*"  
  
- "{bot} / lodních"  
  
- "{bot} / {lodních} /bed/ {quilt}"  
  
- "bot / {lodních}"  
  
- "shoe/{boat}/\*"  
  
- "shoe/boat?x=2"  
  
- "shoe/{boat}?x={bed}"  
  
- "shoe/{boat}?x={bed}&y=band"  
  
- "?x={shoe}"  
  
- "bot? x = 3 & y = {var}  
  
 Příkladem řetězce neplatný šablon:  
  
- "{bot} / {bot} / x = 2" – duplicitní názvy proměnných.  
  
- "{bot} /boat/? základnu {bot} =" – duplicitní názvy proměnných.  
  
- "? x = 2 & x = 3" – dvojice název/hodnota v řetězci dotazu musí být jedinečné, i v případě, že jsou literály.  
  
- "? x = 2 &" – řetězec dotazu je poškozený.  
  
- "? 2 & x = {bot}" – řetězec dotazu musí být dvojice název/hodnota.  
  
- "? y = 2 & & X = 3" – řetězec dotazu musí být páry název-hodnota, názvy nesmí začínat 'a'.  
  
### <a name="compound-path-segments"></a>Složené segmenty cesty  
 Segmenty složené cesty povolit jeden segment cesty identifikátoru URI tak, aby obsahovala více proměnných stejně jako proměnné v kombinaci s literály. Následují příklady segmentů platný složené cesty.  
  
- /filename.{ext}/  
  
- /{filename}.jpg/  
  
- / {filename}. {ext} /  
  
- / {a}. {b}someLiteral{c}({d}) /  
  
 Následují příklady segmentů neplatná cesta.  
  
- /{} – Musí být název proměnné.  
  
- / {bot} {loď} - proměnné musí být odděleny literál.  
  
### <a name="matching-and-compound-path-segments"></a>Odpovídající a složené segmenty cesty  
 Segmenty cesty složené umožňují definovat šablony UriTemplate, který má více proměnných v rámci segmentu jednu cestu. Například v následujícím řetězci šablony: "Adresy / {state}. {Město} "v rámci stejné segmentu jsou definovány dvě proměnné (státu a města). Tato šablona odpovídají, jako adresa URL `http://example.com/Washington.Redmond` ale budou se také shodovat s adresu URL jako `http://example.com/Washington.Redmond.Microsoft`. V takovém případě proměnné stavu bude obsahovat "Washington", a proměnnou město bude obsahovat "Redmond.Microsoft". V tomto případě žádný text (s výjimkou "/") bude odpovídat proměnné {město}. Pokud chcete šablonu, která se nebudou shodovat s textem "navíc", vložte proměnnou samostatné šablony segmentu, například: "Addresses/{state}/{city}.  
  
### <a name="named-wildcard-segments"></a>Segmenty pojmenované zástupných znaků  
 Pojmenované zástupný segment, který je segment pro proměnnou cesty, název proměnné začíná zástupný znak "\*". Následující šablony řetězec obsahuje pojmenované zástupný segment s názvem "bot".  
  
```  
"literal/{*shoe}"  
```  
  
 Zástupný znak segmenty musí postupovat podle následujících pravidel:  
  
- Může existovat maximálně jednu s názvem zástupný segment pro každý řetězec šablony.  
  
- Pojmenované zástupný segment se musí nacházet v úplně vpravo segment v cestě.  
  
- Pojmenované zástupný segment nemůžou existovat současně s anonymní zástupný segment v rámci stejného řetězce šablony.  
  
- Název pojmenované zástupný segment musí být jedinečný.  
  
- Zástupný znak s názvem segmenty nemůže mít výchozí hodnoty.  
  
- Segmenty pojmenované zástupný znak nemůže končit znakem "/".  
  
### <a name="default-variable-values"></a>Výchozí hodnoty proměnných  
 Výchozí hodnoty proměnné umožňují zadat výchozí hodnoty pro proměnné v rámci šablony. Výchozí proměnné lze upravit pomocí složených závorek, které deklarujete proměnnou nebo kolekci předaný konstruktoru UriTemplate. Následující šablony se zobrazí dva způsoby, jak určit <xref:System.UriTemplate> proměnné s výchozími hodnotami.  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Tato šablona deklaruje proměnnou s názvem `a` s výchozí hodnotou `1` a proměnné s názvem `b` s výchozí hodnotou `5`.  
  
> [!NOTE]
>  Výchozí hodnoty jsou povoleny pouze proměnné cesty segmentu. Výchozí hodnoty nejsou povoleny proměnné řetězce dotazu, složený segment proměnné a proměnné s názvem zástupný znak.  
  
 Následující kód ukazuje způsob zpracování výchozí hodnoty proměnných při porovnávání kandidát identifikátoru URI.  
  
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
> Identifikátor URI jako `http://localhost:8000///` šablony uvedené v předchozím kódu, ale neodpovídá identifikátoru URI jako `http://localhost:8000/` nemá.  
  
 Následující kód ukazuje způsob zpracování výchozí hodnoty proměnných při vytváření identifikátor URI s šablonou.  
  
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
  
Když je proměnné předána výchozí hodnotu `null` existují některé další omezení. Proměnná může mít výchozí hodnotu `null` Pokud proměnnou je obsažena v pravém většiny segment řetězec šablony nebo pokud všechny segmenty napravo od segmentu mají výchozí hodnoty `null`. Níže jsou řetězce platnou šablonu s výchozími hodnotami `null`:  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 Neplatná šablona řetězce s výchozími hodnotami jsou následující `null`:  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a>Výchozí hodnoty a porovnávání  
 Při porovnávání kandidát URI šablonou, která má výchozí hodnoty, výchozí hodnoty jsou umístěny v <xref:System.UriTemplateMatch.BoundVariables%2A> kolekce, pokud nejsou zadané hodnoty ve Release candidate identifikátoru URI.  
  
### <a name="template-equivalence"></a>Ekvivalence šablony  
 Dvě šablony jsou označeny jako *strukturálně ekvivalentní* při všem literálů se šablony a mají proměnné stejný segmentů. Například následující šablony jsou strukturálně ekvivalentní:  
  
- b /b /a/ {var1} / {var2}? x = 1 & y = 2  
  
- a/{x}/b%20b/{var1}?y=2&x=1  
  
- a/{y}/B%20B/{z}/?y=2&x=1  
  
 Všimněte si, že několik věcí:  
  
- Pokud šablona obsahuje úvodních lomítek, pouze první z nich se ignoruje.  
  
- Při porovnávání řetězců šablony pro strukturální ekvivalenci, se ignoruje velikost písmen pro názvy proměnných a segmenty cesty, řetězce dotazu jsou malá a velká písmena.  
  
- Neuspořádaný řetězce dotazu.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Třída reprezentuje asociativní tabulku <xref:System.UriTemplate> objekty vázané na uživatele výběr objektu vývojáře. A <xref:System.UriTemplateTable> musí obsahovat alespoň jeden <xref:System.UriTemplate> před voláním <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. Obsah <xref:System.UriTemplateTable> můžete změnit, dokud nebude <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána. Provede se ověření, když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána. Typ ověřování, závisí na hodnotu `allowMultiple` parametr <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.  
  
 Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána při předávání v `false`, <xref:System.UriTemplateTable> kontroluje, ujistěte se, že v tabulce nejsou žádné šablony. Pokud najde všechny šablony, strukturálně ekvivalentní, dojde k výjimce. To se používá ve spojení s <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> kdy budete chtít zajistit pouze jedna šablona odpovídá příchozí identifikátor URI.  
  
 Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána při předávání v `true`, <xref:System.UriTemplateTable> umožňuje více, strukturálně ekvivalentem šablony mají být obsažena v rámci <xref:System.UriTemplateTable>.  
  
 Pokud sadu <xref:System.UriTemplate> objekty přidané do <xref:System.UriTemplateTable> obsahují řetězce dotazů, nesmí se jednat o nejednoznačný. Jsou řetězce identické dotazu povoleny.  
  
> [!NOTE]
>  Zatímco <xref:System.UriTemplateTable> umožňuje základní adresy tohoto použití schémata než HTTP, schéma a číslo portu jsou ignorovány při porovnávání Release candidate identifikátory URI pro šablony.  
  
### <a name="query-string-ambiguity"></a>Nejednoznačnosti řetězec dotazu  
 Šablony, které sdílejí stejnou cestu obsahují řetězce dotazů nejednoznačný, pokud je identifikátor URI, který odpovídá více než jedna šablona.  
  
 Následující sady řetězce dotazu jsou jednoznačné v rámci samotné:  
  
- ?x=1  
  
- ?x=2  
  
- ?x=3  
  
- ? x = 1 & y = {var}  
  
- ?x=2&z={var}  
  
- ?x=3  
  
- ?x=1  
  
- ?  
  
- ? x = {var}  
  
- ?  
  
- ?m=get&c=rss  
  
- ?m=put&c=rss  
  
- ?m=get&c=atom  
  
- ?m=put&c=atom  
  
 Následující sady šablony řetězců dotazu je nejednoznačný v rámci samotných:  
  
- ?x=1  
  
- ?x={var}  
  
 "x = 1"-odpovídá obě šablony.  
  
- ?x=1  
  
- ? y = 2  
  
 "x = 1 & y = 2" odpovídá obě šablony. Je to proto, že řetězec dotazu může obsahovat další proměnné řetězce dotazu, pak odpovídá šabloně.  
  
- ?x=1  
  
- ? x = 1 & y = {var}  
  
 "x = 1 & y = 3" odpovídá obě šablony.  
  
- ? x = 3 & y = 4  
  
- ? x = 3 & z = 5  
  
> [!NOTE]
> Á znaků a Á považují za různých znaků, když se zobrazí jako součást cesty identifikátoru URI nebo <xref:System.UriTemplate> segment cesty literálu (ale a znaků a A jsou považovány za stejný). Á znaků a Á považují za stejné znaky, pokud se zobrazují jako součást <xref:System.UriTemplate> {variableName} nebo řetězec dotazu (a a a A také považují za stejné znaky).  
  
## <a name="see-also"></a>Viz také:

- [Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [Programovací objektový model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [Tabulka UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [Dispečer tabulky UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
