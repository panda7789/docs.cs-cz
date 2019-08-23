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
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate a UriTemplateTable
Vývojáři webu vyžadují možnost popsat tvar a rozložení identifikátorů URI, na které jejich služby reagují. Windows Communication Foundation (WCF) přidal dvě nové třídy, které vývojářům poskytují kontrolu nad svými identifikátory URI. <xref:System.UriTemplate>a <xref:System.UriTemplateTable> tvoří základ odesílajícího stroje založeného na identifikátoru URI ve službě WCF. Tyto třídy lze také použít na vlastní, což vývojářům umožňuje využít výhod šablon a mechanismu mapování identifikátorů URI bez implementace služby WCF.  
  
## <a name="templates"></a>Šablony  
 Šablona je způsob, jak popsat sadu relativních identifikátorů URI. Sada šablon identifikátorů URI v následující tabulce ukazuje, jak je možné definovat systém, který načte různé typy informací o počasí.  
  
|Data|Šablona|  
|----------|--------------|  
|Národní prognóza|počasí/národní|  
|Prognóza stavu|počasí/{State}|  
|Prognóza města|počasí/{State}/{City}|  
|Prognóza aktivity|počasí/{State}/{City}/{Activity}|  
  
 Tato tabulka popisuje sadu strukturně podobných identifikátorů URI. Každá položka je šablonou identifikátoru URI. Segmenty ve složených závorkách popisují proměnné. Segmenty, které nejsou ve složených závorkách, popisují řetězce literálů. Třídy šablon WCF umožňují vývojářům převzít příchozí identifikátor URI, například "/Weather/WA/Seattle/Cycling", a odpovídat na šablonu, která ji popisuje, "/Weather/{State}/{City}/{Activity}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate>je třída, která zapouzdřuje šablonu identifikátoru URI. Konstruktor přebírá řetězcový parametr definující šablonu. Tento řetězec obsahuje šablonu ve formátu popsaném v následující části. <xref:System.UriTemplate> Třída poskytuje metody, které umožňují odpovídat příchozímu identifikátoru URI šabloně, vygenerovat identifikátor URI ze šablony, načíst kolekci názvů proměnných použitých v šabloně, zjistit, zda jsou dvě šablony ekvivalentní, a vrátí šablonu. řetezce.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>převezme základní adresu a kandidáta URI a pokusí se najít identifikátor URI pro šablonu. Je- <xref:System.UriTemplateMatch> li shoda úspěšná, je vrácena instance. Objekt obsahuje základní identifikátor URI, kandidát identifikátor URI, kolekci název/hodnota parametrů dotazu, pole segmentů relativních cest, kolekci název/hodnota proměnných, které byly spárovány <xref:System.UriTemplate> , instanci použitou k provedení shody. <xref:System.UriTemplateMatch> , řetězec, který obsahuje libovolnou neshodnou část kandidátu identifikátoru URI (používá se, když šablona obsahuje zástupný znak) a objekt, který je spojen se šablonou.  
  
> [!NOTE]
> <xref:System.UriTemplate> Třída ignoruje schéma a číslo portu při porovnání kandidátu identifikátoru URI se šablonou.  
  
 Existují dvě metody, které umožňují vygenerovat identifikátor URI ze šablony <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> a. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>převezme základní adresu a kolekci název/hodnota parametrů. Tyto parametry jsou nahrazeny pro proměnné, pokud je šablona svázána. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>převezme páry název/hodnota a nahradí je zprava doleva.  
  
 <xref:System.UriTemplate.ToString>Vrátí řetězec šablony.  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A> Vlastnost obsahuje kolekci názvů proměnných používaných v rámci segmentů cesty v řetězci šablony.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>přebírá <xref:System.UriTemplate> jako parametr a vrací logickou hodnotu, která určuje, zda jsou dvě šablony ekvivalentní. Další informace najdete v části věnované rovnosti šablon dále v tomto tématu.  
  
 <xref:System.UriTemplate>je navržený tak, aby fungoval s jakýmkoli schématem URI, které vyhovuje gramatice URI protokolu HTTP. Následují příklady podporovaných schémat identifikátorů URI.  
  
- http://  
  
- https://  
  
- net.tcp://  
  
- net.pipe://  
  
- sb://  
  
 Schémata jako file://a urn://nejsou v souladu s gramatikou identifikátoru URI HTTP a způsobují nepředvídatelné výsledky při použití se šablonami identifikátorů URI.  
  
### <a name="template-string-syntax"></a>Syntaxe řetězce šablony  
 Šablona má tři části: cestu, volitelný dotaz a volitelný fragment. Příklad naleznete v následující šabloně:  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 Cesta se skládá z "/Weather/{State}/{City}", dotaz se skládá z "? předpověď = {Length}" a fragment se skládá z "#frag1".  
  
 Úvodní a koncové lomítko jsou volitelné ve výrazu Path. Výrazy dotazu i fragmenty mohou být zcela vynechány. Cesta se skládá z řady segmentů oddělených znakem "/", každý segment může mít literálovou hodnotu, název proměnné (napsaný ve složených závorkách}) nebo zástupný znak (napsaný jako\*). V předchozí šabloně je "\weather\ segmentem" hodnota literálu, zatímco "{State}" a "{City}" jsou proměnné. Proměnné přebírají svůj název od obsahu jejich složených závorek a mohou být později nahrazeny konkrétní hodnotou pro vytvoření *zavřeného identifikátoru URI*. Zástupný znak je nepovinný, ale může se vyskytovat jenom na konci identifikátoru URI, kde logicky odpovídá "zbytek cesty".  
  
 Výraz dotazu, pokud je k dispozici, určuje řadu neuspořádaných párů název/hodnota oddělený ' & '. Prvky výrazu dotazu mohou být buď páry literálů (x = 2), nebo dvojice proměnných (x = {var}). Výraz proměnné může mít pouze pravá strana dotazu. ({nějakých} = {someValue} není povolený. Nespárované hodnoty (? x) nejsou povolené. Neexistuje žádný rozdíl mezi prázdným výrazem dotazu a výrazem dotazu, který se skládá jenom z jednoho "?". (znamená libovolný dotaz).  
  
 Výraz fragmentu může sestávat z hodnoty literálu, nejsou povoleny žádné proměnné.  
  
 Všechny názvy proměnných šablony v řetězci šablony musí být jedinečné. V názvech proměnných šablony se nerozlišují malá a velká písmena.  
  
 Příklady platných řetězců šablon:  
  
- ""  
  
- "/shoe"  
  
- "/Shoe/\*"  
  
- {bot}/Boat  
  
- {bot}/{Boat}/Bed/{Quilt}  
  
- "bot/{člun}"  
  
- "bot/{člun}/\*"  
  
- "bot/člun? x = 2"  
  
- "bot/{člun}? x = {postel}"  
  
- "shoe/{boat}?x={bed}&y=band"  
  
- "?x={shoe}"  
  
- "bot? x = 3 & y = {var}  
  
 Příklady neplatných řetězců šablon:  
  
- {bot}/{SHOE}/x = 2 – duplicitní názvy proměnných  
  
- {bot}/Boat/? postel = {bot} – duplicitní názvy proměnných  
  
- "? x = 2 & x = 3" – páry název/hodnota v řetězci dotazu musí být jedinečné, a to i v případě, že se jedná o literály.  
  
- "? x = 2 &" – řetězec dotazu je poškozen.  
  
- "? 2 & x = {bot}" – řetězec dotazu musí být dvojice název/hodnota.  
  
- "? y = 2 & & X = 3" – řetězec dotazu musí být páry hodnoty názvu, nesmí názvy začínat znakem "&".  
  
### <a name="compound-path-segments"></a>Složené segmenty cesty  
 Složené segmenty cesty umožňují, aby jeden segment cesty URI obsahoval více proměnných, a také proměnné kombinované s literály. Níže jsou uvedeny příklady platných segmentů složených cest.  
  
- /filename.{ext}/  
  
- /{filename}.jpg/  
  
- Bitmap. {EXT}/  
  
- určitého. {b} someLiteral {c} ({d})/  
  
 Následují příklady neplatných segmentů cesty.  
  
- Proměnné{} /-musí být pojmenovány.  
  
- /{Shoe}{Boat}-proměnné musí být odděleny literálem.  
  
### <a name="matching-and-compound-path-segments"></a>Párové a složené segmenty cesty  
 Složené segmenty cesty umožňují definovat šablony UriTemplate, které mají více proměnných v rámci jednoho segmentu cesty. Například v následujícím řetězci šablony: Adresa/{State}. {City}: dvě proměnné (State a City) se definují v rámci stejného segmentu. Tato šablona by odpovídala adrese URL, `http://example.com/Washington.Redmond` jako je například, ale také se shoduje `http://example.com/Washington.Redmond.Microsoft`s adresou URL, jako je. V druhém případě bude proměnná stavu obsahovat "Washington" a proměnná City bude obsahovat "Redmond. Microsoft". V tomto případě bude libovolný text (s výjimkou '/') odpovídat proměnné {City}. Pokud chcete šablonu, která se neshoduje s textem "extra", umístěte proměnnou do samostatného segmentu šablony, například: Adresa/{State}/{City}.  
  
### <a name="named-wildcard-segments"></a>Pojmenované segmenty se zástupnými znaky  
 Pojmenovaný segment se zástupným znakem je libovolný segment proměnné cesty, jejíž název proměnné začíná\*zástupným znakem. Následující řetězec šablony obsahuje pojmenovaný zástupný segment s názvem bot.  
  
```  
"literal/{*shoe}"  
```  
  
 Segmenty se zástupnými znaky musí splňovat následující pravidla:  
  
- Pro každý řetězec šablony může existovat maximálně jeden pojmenovaný zástupný segment.  
  
- Pojmenovaný segment se zástupnými znaky musí být v cestě v segmentu napravo vpravo.  
  
- Pojmenovaný segment se zástupnými znaky nemůže koexistovat s anonymním segmentem zástupného znaku v rámci stejného řetězce šablony.  
  
- Název pojmenovaného zástupného segmentu musí být jedinečný.  
  
- Pojmenované segmenty se zástupnými znaky nemůžou mít výchozí hodnoty.  
  
- Pojmenované segmenty se zástupnými znaky nemohou končit znakem "/".  
  
### <a name="default-variable-values"></a>Výchozí hodnoty proměnných  
 Výchozí proměnné hodnoty umožňují zadat výchozí hodnoty pro proměnné v rámci šablony. Výchozí proměnné lze zadat pomocí složených závorek, které deklarují proměnnou nebo jako kolekci předanou konstruktoru UriTemplate. Následující šablona ukazuje dva způsoby, jak zadat <xref:System.UriTemplate> proměnné s výchozími hodnotami.  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Tato šablona deklaruje `a` proměnnou s názvem s výchozí `1` hodnotou a proměnnou s názvem `b` s výchozí hodnotou `5`.  
  
> [!NOTE]
> Pouze proměnné segmentu cesty mají povoleny výchozí hodnoty. Proměnné řetězce dotazu, proměnné složeného segmentu a pojmenované zástupné znaky nejsou povoleny výchozí hodnoty.  
  
 Následující kód ukazuje, jak jsou zpracovávány výchozí hodnoty proměnných při porovnání s kandidátem identifikátoru URI.  
  
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
> Identifikátor URI `http://localhost:8000///` , jako je například, neodpovídá šabloně uvedené v předchozím kódu, ale identifikátor URI `http://localhost:8000/` , jako je například.  
  
 Následující kód ukazuje, jak se při vytváření identifikátoru URI se šablonou zpracovávají výchozí hodnoty proměnných.  
  
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
  
Pokud je předána výchozí hodnota `null` proměnné, existují další omezení. Proměnná může mít výchozí hodnotu, `null` Pokud je proměnná obsažena v pravém segmentu segmentu řetězce šablony nebo pokud všechny segmenty napravo od segmentu mají výchozí `null`hodnoty. Níže jsou platné řetězce šablon s výchozími hodnotami `null`:  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 Níže jsou neplatné řetězce šablon s výchozími hodnotami `null`:  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a>Výchozí hodnoty a spárování  
 Při porovnání kandidátu URI se šablonou, která má výchozí hodnoty, jsou výchozí hodnoty umístěny do <xref:System.UriTemplateMatch.BoundVariables%2A> kolekce, pokud nejsou zadány hodnoty v kandidátu identifikátoru URI.  
  
### <a name="template-equivalence"></a>Rovnocennost šablon  
 Dvě šablony jsou označeny jako *strukturální ekvivalenty* , pokud všechny literály šablony odpovídají a mají proměnné ve stejných segmentech. Například následující šablony jsou strukturně rovnocenné:  
  
- /a/{var1}/b b/{var2}? x = 1 & y = 2  
  
- a/{x}/b%20b/{var1}?y=2&x=1  
  
- a/{y}/B% c/{z}/? y = 2 & x = 1  
  
 Několik věcí, které je potřeba si všimnout:  
  
- Obsahuje-li šablona úvodní lomítka, bude ignorována pouze první z nich.  
  
- Při porovnávání řetězců šablon pro strukturální ekvivalenci je případ ignorován u názvů proměnných a segmentů cesty, řetězce dotazů rozlišují malá a velká písmena.  
  
- Řetězce dotazů jsou neseřazené.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 Třída představuje asociativní <xref:System.UriTemplate> tabulku objektů svázaných s objektem výběru vývojáře. <xref:System.UriTemplateTable> Musí obsahovat alespoň jeden <xref:System.UriTemplate> před voláním <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. <xref:System.UriTemplateTable> Obsah a <xref:System.UriTemplateTable> lze změnit, dokud <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> není voláno. Ověřování se provádí při <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> volání metody. Typ provedeného ověřování závisí na hodnotě `allowMultiple` parametru na <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>hodnotu.  
  
 V <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> případě `false`, že je voláno <xref:System.UriTemplateTable> předání, zkontroluje, že v tabulce nejsou žádné šablony. Pokud najde všechny strukturální rovnocenné šablony, vyvolá výjimku. Používá se ve spojení s <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> tím, kdy chcete zajistit, aby pouze jedna šablona odpovídala příchozímu identifikátoru URI.  
  
 Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána metoda `true`předávání, <xref:System.UriTemplateTable> umožňuje, aby bylo v rámci <xref:System.UriTemplateTable>obsaženo více strukturně ekvivalentních šablon.  
  
 Pokud sada <xref:System.UriTemplate> objektů přidaných <xref:System.UriTemplateTable> do obsahující řetězce dotazu nesmí být dvojznačná. Jsou povoleny identické řetězce dotazů.  
  
> [!NOTE]
> I když <xref:System.UriTemplateTable> umožňuje základní adresy, které používají jiné než http systémy, schéma a číslo portu se ignorují, pokud se shodují odpovídající identifikátory URI kandidátů na šablony.  
  
### <a name="query-string-ambiguity"></a>Nejednoznačnost řetězce dotazu  
 Šablony, které sdílejí stejnou cestu, obsahují dvojznačné řetězce dotazu, pokud existuje identifikátor URI, který se shoduje s více než jednou šablonou.  
  
 Následující sady řetězců dotazů jsou v rámci sebe jednoznačné:  
  
- ? x = 1  
  
- ? x = 2  
  
- ? x = 3  
  
- ? x = 1 & y = {var}  
  
- ? x = 2 & z = {var}  
  
- ? x = 3  
  
- ? x = 1  
  
- ?  
  
- ? x = {var}  
  
- ?  
  
- ?m=get&c=rss  
  
- ? m = vložení & c = RSS  
  
- ?m=get&c=atom  
  
- ? m = Put & c = Atom  
  
 Následující sady šablon řetězce dotazu jsou v rámci sebe dvojznačné:  
  
- ? x = 1  
  
- ? x = {var}  
  
 "x = 1" – odpovídá oběma šablonám.  
  
- ? x = 1  
  
- ? y = 2  
  
 "x = 1 & y = 2" odpovídají oběma šablonám. Důvodem je to, že řetězec dotazu může obsahovat více proměnných řetězce dotazu, a to tak, aby šablona odpovídala.  
  
- ? x = 1  
  
- ? x = 1 & y = {var}  
  
 "x = 1 & y = 3" odpovídají oběma šablonám.  
  
- ? x = 3 & y = 4  
  
- ? x = 3 & z = 5  
  
> [!NOTE]
> Znaky "a" jsou považovány za jiné znaky, pokud jsou zobrazeny jako součást cesty identifikátoru URI nebo <xref:System.UriTemplate> literálu segmentu cesty (ale znaky a a a jsou považovány za stejné). Znaky "a" jsou považovány za stejné znaky, pokud se zobrazují jako součást <xref:System.UriTemplate> proměnné {Variable} nebo řetězce dotazu (a a a a a a jsou také považovány za stejné znaky).  
  
## <a name="see-also"></a>Viz také:

- [Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [Programovací objektový model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [Tabulka UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [Dispečer tabulky UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
