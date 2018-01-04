---
title: UriTemplate a UriTemplateTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac77fe2c83828d2cc9473417d2b29b2d2e540923
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate a UriTemplateTable
Vývojáři webů potřebují k popisu tvar a rozložení identifikátory URI, který své služby reagovat na. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Přidá dva nové třídy pro umožnění vývojáři kontroly nad jejich identifikátory URI. <xref:System.UriTemplate>a <xref:System.UriTemplateTable> tvoří základ, na základě identifikátoru URI odesílání stroje v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Tyto třídy lze také na své vlastní, povolení vývojáři využít šablon a mechanismus mapování URI bez implementace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
## <a name="templates"></a>Šablony  
 Šablona je způsob, jak popisuje sadu relativní identifikátory URI. Sada šablony URI v následující tabulce ukazuje, jak může být definovaná systémem, který načte různých typů informací o počasí.  
  
|Data|Šablony|  
|----------|--------------|  
|National prognózy|počasí/national|  
|Stav prognózy|počasí / {stavu}|  
|Prognóza města|počasí / {stavu} / {města}|  
|Aktivita prognózy|počasí / {stavu} / {města} / {aktivity}|  
  
 Tato tabulka popisuje sadu strukturálně podobné identifikátory URI. Každá položka je šablona identifikátor URI. Segmenty do složených závorek popisují proměnné. Segmenty není do složených závorek popisují řetězcové literály. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Tříd šablon povolit vývojář trvat příchozí URI, například "/ počasí nebo wa/Praha/prosté", a odpovídat na šablonu, která popisuje, "/weather/ {stavu} / {města} / {aktivity}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate>je třída, který zapouzdřuje šablonu identifikátor URI. Konstruktor přijímá řetězcový parametr, který definuje šablony. Tento řetězec obsahuje šablonu ve formátu popsané v další části. <xref:System.UriTemplate> Třída poskytuje metody, které vám umožňují odpovídat identifikátor URI příchozí do šablony, generovat identifikátor URI ze šablony, načte kolekci názvy proměnných, které jsou použité v šabloně, určete, jestli dvě šablony jsou ekvivalentní a vrátí šablony řetězec.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>identifikátor URI a pokusí se porovnat identifikátor URI pro šablony trvá základní adresa a kandidátem. Pokud je úspěšné, shody <xref:System.UriTemplateMatch> vrácena instance. <xref:System.UriTemplateMatch> Objekt obsahuje základní identifikátor URI candidate identifikátor URI, názvu a hodnoty kolekce parametry dotazu, pole segmentů relativní cestu, kolekci názvu a hodnoty proměnných, které se shodují, <xref:System.UriTemplate> instance, používá k provádění shody , řetězec, který obsahuje všechny neodpovídající část candidate identifikátor URI (používá se při šablona má zástupný znak) a objekt, který je přidružen šablony.  
  
> [!NOTE]
>  <xref:System.UriTemplate> Třída ignoruje schéma a číslo portu při kontrole shody kandidátem URI do šablony.  
  
 Existují dvě metody, které vám umožní generovat identifikátor URI ze šablony, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> a <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>. <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>trvá základní adresa a kolekce názvu a hodnoty parametrů. Tyto parametry jsou nahrazena pro proměnné, když šablona je vázána. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>trvá dvojice název/hodnota a nahradí je zprava doleva.  
  
 <xref:System.UriTemplate.ToString>Vrátí řetězec šablony.  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A> Vlastnost obsahuje kolekci názvů proměnných používaných v rámci segmenty cesty v řetězci šablony.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>přijímá <xref:System.UriTemplate> jako parametr a vrací logickou hodnotu, která určuje, zda dvě šablony jsou ekvivalentní. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]část šablony ekvivalenční později v tomto tématu.  
  
 <xref:System.UriTemplate>je navržen pro práci s žádné schéma identifikátoru URI, který vyhovuje gramatika HTTP URI. Následují příklady podporována schémata identifikátoru URI.  
  
-   http://  
  
-   https://  
  
-   NET.TCP://  
  
-   NET.pipe://  
  
-   SB: / /  
  
 Schémata jako file:// a urn: / / není v souladu s gramatika HTTP URI a způsobit nepředvídatelné výsledky při použití s šablony URI.  
  
### <a name="template-string-syntax"></a>Syntaxe řetězec šablony  
 Šablona má tři části: cestu, volitelné dotazu a volitelné fragment. Příklad najdete v tématu následující šablony:  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 Cesta se skládá z "/weather/ {stavu} / {města}", dotaz se skládá z"? prognózy = {{délka} a fragment se skládá z"#frag1".  
  
 Úvodní a koncové lomítka jsou volitelné ve výrazu cestu. Výrazy dotazu i fragment je zcela lze vynechat. Cesta se skládá z řady segmentů oddělená '/', každý segment může mít hodnotu literálu, název proměnné (napsané v {složené závorky}) nebo zástupný znak (zapsány jako\*'). V šabloně předchozí "\weather\ segment je literál, ale zadaná hodnota"{stavu}"a"{města}"jsou proměnné. Proměnné trvat jména z obsahu jejich složené závorky a lze je později nahradit s konkrétní hodnotou k vytvoření *uzavřený URI*. Zástupný znak je nepovinný, ale může vyskytovat pouze na konci identifikátor URI, které logicky odpovídá "zbývající část cesty".  
  
 Výraz dotazu, pokud existuje, určuje řadu dvojice neuspořádaný název hodnota oddělená 'a'. Elementy výrazu dotazu může být buď literálu páry (x = 2) nebo pár proměnných (x = {var}). Pravé straně dotazu může mít proměnné výraz. ({someName} = {someValue} není povolená. Nepárové hodnoty (? x) nejsou povoleny. Není žádný rozdíl mezi výraz dotazu prázdný a tvořený jenom jednoho výrazu dotazu '?' (i znamená "jakýkoli dotaz").  
  
 Fragment výraz se může skládat z literálovou hodnotou, jsou povolené žádné proměnné.  
  
 Všechny názvy proměnných šablony v rámci řetězec šablony musí být jedinečný. Názvy proměnných šablony jsou velká a malá písmena.  
  
 Příkladem řetězce platné šablony:  
  
-   ""  
  
-   "/ čelisti"  
  
-   "/ čelisti / *"  
  
-   "{čelisti} / lodních"  
  
-   "{čelisti} / {lodních} /bed/ {quilt}"  
  
-   "čelisti / {lodních}"  
  
-   "čelisti / {lodních} / *"  
  
-   "čelisti nebo člun? x = 2"  
  
-   "čelisti / {lodních}? x = {DNA}"  
  
-   "čelisti / {lodních}? x = {DNA} & y = vzdálené"  
  
-   "? x = {čelisti}"  
  
-   "čelisti? x = 3 & y = {var}  
  
 Příkladem řetězce neplatný šablon:  
  
-   "{čelisti} / {ČELISTI} / x = 2" – duplicitní názvy proměnných.  
  
-   "{čelisti} /boat/? DNA = {čelisti}" – duplicitní názvy proměnných.  
  
-   "? x = 2 & x = 3" – dvojice název/hodnota v rámci řetězec dotazu musí být jedinečné, i když jsou literály.  
  
-   "? x = 2 &" – řetězec dotazu je poškozený.  
  
-   "? 2 & x = {čelisti}" – řetězec dotazu musí být dvojice název/hodnota.  
  
-   "? y = 2 & & X = 3" – řetězec dotazu musí být dvojice názvů a hodnot, nemůže začínat názvy 'a'.  
  
### <a name="compound-path-segments"></a>Složené segmenty cesty  
 Segmenty cesty složené Povolí jeden segment cesty identifikátoru URI tak, aby obsahovala více proměnných a také v kombinaci s literály proměnné. Následují příklady segmentů složené platnou cestu.  
  
-   argument/FILENAME. {ext} /  
  
-   /{filename}.jpg/  
  
-   / {filename}. {ext} /  
  
-   / {a}. {b}someLiteral{c}({d}) /  
  
 Následují příklady segmentů platná cesta UNC.  
  
-   /{} - Musí mít název proměnné.  
  
-   / {čelisti} {člun} - proměnných musí být odděleny literál.  
  
### <a name="matching-and-compound-path-segments"></a>Odpovídající a složené segmenty cesty  
 Segmenty cesty složené umožňují definovat UriTemplate, který má více proměnných v rámci segmentu, jednu cestu. Například v následující řetězec šablony: "adresy / {stavu}. {města} "dvě proměnné (státu a města) jsou definovány v rámci stejné segmentu. Tato šablona by odpovídat adresy URL, například "http://example.com/Washington.Redmond", ale bude se taky shodovat adresu URL jako "http://example.com/Washington.Redmond.Microsoft". V takovém případě proměnné stavu bude obsahovat "Washington" a proměnnou města bude obsahovat "Redmond.Microsoft". V tomto případě jakýkoli text (s výjimkou '/') bude shodovat s proměnnou {města}. Pokud chcete šablonu, která nebude odpovídat "výběr" text, umístěte proměnnou v samostatných šablony segmentu, například: "adresy / {stavu} / {města}.  
  
### <a name="named-wildcard-segments"></a>Segmenty pojmenované zástupný znak  
 Segment s názvem zástupný znak je všechny proměnné segment cesty jejichž proměnné název začíná se zástupným znakem ' *'. Následující řetězec šablony obsahuje segment s názvem zástupné s názvem "čelisti".  
  
```  
"literal/{*shoe}"  
```  
  
 Zástupný znak segmenty musí postupujte podle následujících pravidel:  
  
-   Může být maximálně jeden segment s názvem zástupných znaků pro každý řetězec šablony.  
  
-   Segment s názvem zástupný znak musí být uvedena v segmentu nejvíce vpravo v cestě.  
  
-   Segment s názvem zástupné nemohou být nainstalovány s segment anonymní zástupný znak v rámci stejné řetězec šablony.  
  
-   Název objektu segment s názvem zástupný znak musí být jedinečný.  
  
-   S názvem zástupný znak nelze segmenty mají výchozí hodnoty.  
  
-   Nemůže končit segmenty pojmenované zástupný znak "/".  
  
### <a name="default-variable-values"></a>Výchozí hodnoty proměnné  
 Výchozí hodnoty proměnné umožňují zadat výchozí hodnoty pro proměnné v rámci šablon. Výchozí proměnné mohou být zadané s složené závorky, které deklarovat proměnnou nebo jako kolekce předaný konstruktoru UriTemplate. Následující šablony ukazuje dva způsoby, jak určit <xref:System.UriTemplate> k proměnným s výchozími hodnotami.  
  
```  
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Tato šablona deklaruje proměnné s názvem `a` s výchozí hodnotou `1` a proměnné s názvem `b` s výchozí hodnotou `5`.  
  
> [!NOTE]
>  Do mají výchozí hodnoty jsou povoleny pouze proměnné segmentu cesty. Výchozí hodnoty nejsou povoleny proměnné řetězce dotazu, složené segment proměnné a proměnné s názvem zástupný znak.  
  
 Následující kód ukazuje, jak výchozí hodnoty proměnné jsou zpracovávány při kontrole shody kandidátem identifikátor URI.  
  
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
>  Identifikátor URI, jako je například http://localhost: 8000 / / / neodpovídá šabloně uvedené v předchozí kód, ale identifikátor URI, jako je například http://localhost: 8000 / nemá.  
  
 Následující kód ukazuje, jak výchozí hodnoty proměnných jsou zpracovávány při vytváření identifikátorů URI pomocí šablony.  
  
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
  
 Když proměnné je zadána výchozí hodnota je `null` existují některé další omezení. Proměnná může mít výchozí hodnotu `null` Pokud proměnnou je obsažena v pravém většina segment řetězec šablony nebo pokud všechny segmenty napravo od segmentu mají výchozí hodnoty `null`. Následují platné šablony řetězce s hodnotami výchozí `null`:  
  
-   ```  
    UriTemplate t = new UriTemplate("shoe/{boat=null}");  
    ```  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");  
    ```  
 Toto jsou neplatná šablony řetězce s hodnotami výchozí `null`:  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value  
    ```  
### <a name="default-values-and-matching"></a>Výchozí hodnoty a odpovídající  
 Při porovnání kandidátem URI pomocí šablony, která má výchozí hodnoty, výchozí hodnoty jsou umístěny v <xref:System.UriTemplateMatch.BoundVariables%2A> kolekci, pokud nejsou zadané hodnoty v candidate identifikátor URI.  
  
### <a name="template-equivalence"></a>Ekvivalence šablony  
 Dvě šablony jsou označeny jako *strukturálně ekvivalentní* při všechny tyto šablony literálů odpovídající a mají proměnné v stejné segmenty. Například jsou strukturálně ekvivalentní následujících šablon:  
  
-   b /b /a/ {var1} / {var2}? x = 1 & y = 2  
  
-   a/{x}/b%20b/{var1}?y=2 & x = 1  
  
-   a/{y}/B%20B/{z}/?y=2 & x = 1  
  
 Pár věcí Všimněte:  
  
-   Pokud šablonu obsahuje úvodní lomítka, pouze první z nich se ignoruje.  
  
-   Při porovnávání řetězců šablony pro strukturální ekvivalenční, se ignoruje velikost písmen pro názvy proměnných a segmenty cesty, řetězce dotazu se velká a malá písmena.  
  
-   Řetězce dotazu neuspořádaného.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Třída reprezentuje asociativní tabulky <xref:System.UriTemplate> objekty vázána na objekt vývojář je výběr. A <xref:System.UriTemplateTable> musí obsahovat alespoň jeden <xref:System.UriTemplate> před voláním <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. Obsah <xref:System.UriTemplateTable> lze změnit až <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána. Ověření se provádí při <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> je volána. Typ ověření provést, závisí na hodnotu `allowMultiple` parametru <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.  
  
 Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> nazývá předávání v `false`, <xref:System.UriTemplateTable> kontroluje, zajistěte, aby v tabulce nejsou žádné šablony. Pokud najde všechny strukturálně ekvivalentní šablony, vyvolá výjimku. To se používá ve spojení s <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> Pokud chcete zajistit jenom jedna šablona odpovídá příchozí identifikátor URI.  
  
 Když <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> nazývá předávání v `true`, <xref:System.UriTemplateTable> umožňuje víc strukturálně ekvivalentní šablony vešel do jednoho <xref:System.UriTemplateTable>.  
  
 Pokud sada <xref:System.UriTemplate> objektů přidaných do <xref:System.UriTemplateTable> obsahují řetězce dotazu se nesmí být nejednoznačný. Jsou povoleny řetězce dotazu identické.  
  
> [!NOTE]
>  Když <xref:System.UriTemplateTable> umožňuje základní adresy tohoto použijte schémata než HTTP, schéma a číslo portu jsou ignorovány, při kontrole shody candidate identifikátory URI šablon.  
  
### <a name="query-string-ambiguity"></a>Nejednoznačnosti řetězec dotazu  
 Šablony, které ekvivalentní cestu ke sdílené složce obsahují řetězce nejednoznačný dotazu, pokud je identifikátor URI, který odpovídá více než jednu šablonu.  
  
 Následující sady řetězce dotazu jsou jednoznačné v rámci sami:  
  
-   ? x = 1  
  
-   ? x = 2  
  
-   ? x = 3  
  
-   ? x = 1 & y = {var}  
  
-   ? x = 2 & z = {var}  
  
-   ? x = 3  
  
-   ? x = 1  
  
-   ?  
  
-   ? x = {var}  
  
-   ?  
  
-   ? m = get & c = rss  
  
-   ? m = put & c = rss  
  
-   ? m = get & c = atom  
  
-   ? m = put & c = atom  
  
 Následující sady šablon řetězec dotazu jsou nejednoznačné v rámci sami:  
  
-   ? x = 1  
  
-   ? x = {var}  
  
 "x = 1"-odpovídá obě šablony.  
  
-   ? x = 1  
  
-   ? y = 2  
  
 "x = 1 & y = 2" odpovídá obě šablony. Je to proto, že řetězec dotazu může obsahovat další proměnné řetězce dotazu, pak odpovídá šabloně.  
  
-   ? x = 1  
  
-   ? x = 1 & y = {var}  
  
 "x = 1 & y = 3" odpovídá obě šablony.  
  
-   ? x = 3 & y = 4  
  
-   ? x = 3 & z = 5  
  
> [!NOTE]
>  Znaky funkce a funkce se považují za různých znaků, když se zobrazí jako část cesty identifikátor URI nebo <xref:System.UriTemplate> segment cesty literálu (ale a znaky a A jsou považovány za stejnou). Znaky funkce a funkce se považují za stejné znaky, když se zobrazí jako součást <xref:System.UriTemplate> {variableName} nebo řetězec dotazu (a a serverem se také považují za stejné znaky).  
  
## <a name="see-also"></a>Viz také  
 [Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [Programovací objektový model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [Tabulka UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [Dispečer tabulky UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
