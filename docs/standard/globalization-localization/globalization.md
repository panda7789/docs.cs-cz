---
title: Globalizace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
ms.assetid: 4e919934-6b19-42f2-b770-275a4fae87c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eb57aa0d6645958691c0003b07db6e8bb844fc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579571"
---
# <a name="globalization"></a>Globalizace
Globalizace zahrnuje návrh a vývoj připravených aplikaci, která podporuje lokalizované rozhraní a místní data pro uživatele ve více jazykových verzí. Před zahájením fáze návrhu, měli byste určit jazykové verze, které bude podporovat aplikace. I když aplikace cílí na jednu kulturu nebo oblasti jako jeho výchozí, můžete navrhnout a zapisuje tak, aby ho lze snadno rozšířit na uživatele ve dalších jazykové verze.  
  
 Jako vývojáři všechny máme předpoklady o uživatelská rozhraní a data, která jsou tvořeny naše jazykové verze. Například pro vývojář hovořícího anglicky ve Spojených státech amerických serializaci jako řetězec ve formátu data a času `MM/dd/yyyy hh:mm:ss` zdá se, že perfektně přiměřené. Při deserializaci tento řetězec na systém v jinou jazykovou verzi je však pravděpodobně throw <xref:System.FormatException> nepřesných dat. výjimky nebo produktu. Globalizace umožňuje nám určit tyto předpoklady specifické pro jazykovou verzi a ujistěte se, že neovlivňují návrhu vaší aplikace nebo kódu.  
  
 Následující části popisují některé významných problémech, které byste měli zvážit a osvědčené postupy, které vám pomůžou při zpracování řetězců, datum a čas hodnoty a číselné hodnoty v globalizovaná aplikace.  
  
-   [Zpracování řetězce](../../../docs/standard/globalization-localization/globalization.md#HandlingStrings)  
  
    -   [Interně pomocí kódování Unicode](../../../docs/standard/globalization-localization/globalization.md#Strings_Unicode)  
  
    -   [Použít soubory prostředků](../../../docs/standard/globalization-localization/globalization.md#Strings_Resources)  
  
    -   [Vyhledávání a porovnávání řetězců ](../../../docs/standard/globalization-localization/globalization.md#Strings_Searching)  
  
    -   [Testování rovnosti řetězce](../../../docs/standard/globalization-localization/globalization.md#Strings_Equality)  
  
    -   [Uspořádání a řazení řetězců ](../../../docs/standard/globalization-localization/globalization.md#Strings_Ordering)  
  
    -   [Vyhněte se zřetězení řetězců](../../../docs/standard/globalization-localization/globalization.md#Strings_Concat)  
  
-   [Zpracování dat a časů](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes)  
  
    -   [Zachování dat a časů](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Persist)  
  
    -   [Zobrazení dat a časů](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Display)  
  
    -   [Serializace a časové pásmo](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_TimeZones)  
  
    -   [Datum a čas aritmetické operace](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Arithmetic)  
  
-   [Zpracování číselné hodnoty.](../../../docs/standard/globalization-localization/globalization.md#Numbers)  
  
    -   [Zobrazení číselných hodnot](../../../docs/standard/globalization-localization/globalization.md#Numbers_Display)  
  
    -   [Uložením číselné hodnoty.](../../../docs/standard/globalization-localization/globalization.md#Numbers_Persist)  
  
-   [Práce s nastavením specifické pro jazykovou verzi](../../../docs/standard/globalization-localization/globalization.md#Cultures)  
  
<a name="HandlingStrings"></a>   
## <a name="handling-strings"></a>Zpracování řetězců  
 Zpracování znaky a řetězce je hlavní cíl globalizace, protože může pomocí různých znaků a znakových sad a seřadit je jinak každou jazykovou verzi nebo oblasti. Tato část obsahuje doporučení pro používání řetězců v globalizovaná aplikace.  
  
<a name="Strings_Unicode"></a>   
### <a name="use-unicode-internally"></a>Interní používání standardu Unicode  
 Ve výchozím nastavení používá rozhraní .NET Framework řetězců v kódu Unicode. Řetězec znaků Unicode se skládá z nuly, jednu nebo více <xref:System.Char> objektů, z nichž každý představuje jednotku kódu UTF-16. Není Unicode znázornění pro každý znak v každé znakovou sadu používá po celém světě.  
  
 Mnoho aplikací a operačních systémů, včetně operačního systému Windows, můžete použít také pomocí znakové stránky představují znakových sad. Znakové stránky obvykle obsahují standardní hodnoty ASCII 0x00 prostřednictvím 0x7F a namapujte dalšími znaky na zbývající hodnoty 0x80 prostřednictvím 0xFF. Výklad hodnoty z 0x80 prostřednictvím 0xFF závisí na konkrétní znaková stránka. Z tohoto důvodu byste neměli používat znakové stránky v aplikaci globalizovaná Pokud je to možné.  
  
 Následující příklad ilustruje nebezpečích interpretace data znakové stránky, pokud se liší od znakové stránky, na kterém byla uložena data výchozí znakovou stránku v systému. (K simulaci tento scénář, příklad explicitně určuje jiné znakové stránky.) Nejprve v příkladu definuje pole, které se skládá z velkých písmen řecké abecedy. Ho kóduje je do bajtového pole pomocí kódu stránky 737 (také označované jako řečtina MS-DOS) a uloží do souboru bajtové pole. Pokud se načítají souboru a jeho bajtové pole je dekódovat pomocí kódu stránky 737, se obnoví původní znaky. Ale pokud jsou načtena souboru a jeho bajtové pole je dekódovat pomocí znaková stránka 1252 (nebo Windows-1252, která představuje znaků latinku), původní znaky budou ztraceny.  
  
 [!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
 [!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]  
  
 Použití Unicode zajišťuje, že stejný kód jednotky vždy mapování na stejné znaky a že stejné znaky vždy mapování na stejné pole bajtů.  
  
<a name="Strings_Resources"></a>   
### <a name="use-resource-files"></a>Používání souborů prostředků  
 I když vyvíjíte aplikaci, která cílí na jednu kulturu nebo oblast, používejte soubory prostředků pro uložení řetězce a další prostředky, které se zobrazují v uživatelském rozhraní. Měli byste nikdy přidat je přímo do vašeho kódu. Pomocí souborů prostředků má několik výhod:  
  
-   Všechny řetězce jsou na jednom místě. Nemáte pro vyhledávání v rámci vašeho zdrojového kódu k identifikaci řetězce upravit pro konkrétní jazyk nebo jazykovou verzi.  
  
-   Není nutné duplicitní řetězce. Vývojáři, kteří nepoužívají soubory prostředků často definujte do jednoho řetězce v několika soubory zdrojového kódu. Tato duplikace zvyšuje pravděpodobnost, že jeden nebo více instancí bude přehlížen, když dojde k úpravě řetězec.  
  
-   Jiné než řetězec prostředky, například obrázky nebo binárních dat, můžete zahrnout do souboru prostředků místo ukládání v samostatné samostatný soubor, takže se dá snadno načíst.  
  
 Pomocí souborů prostředků má konkrétní výhod, pokud vytváříte lokalizované aplikace. Když nasadíte prostředky v satelitní sestavení, modul common language runtime automaticky vybere příslušnou jazykovou verzi prostředku podle uživatele aktuální jazykové verze uživatelského rozhraní podle definice <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost. Zadejte odpovídající prostředek specifické pro jazykovou verzi a správně vytváření instancí <xref:System.Resources.ResourceManager> objektu nebo použití třídy prostředků se silnými typy, modul runtime zpracovává podrobnosti o načítání s příslušnými prostředky.  
  
 Další informace o vytváření soubory prostředků najdete v tématu [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Informace o vytváření a nasazování satelitní sestavení najdete v tématu [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) a [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
<a name="Strings_Searching"></a>   
### <a name="searching-and-comparing-strings"></a>Vyhledávání a porovnávání řetězců  
 Pokud je to možné, by měla řídit řetězce jako celé řetězce místo jejich zpracování jako řadu jednotlivých znaků. To je obzvláště důležité, pokud řazení nebo vyhledejte dílčích řetězců, aby se zabránilo problémy související s analýzou kombinovaných znaků.  
  
> [!TIP]
>  Můžete použít <xref:System.Globalization.StringInfo> třídy pro práci s elementy textu, nikoli jednotlivých znaků v řetězci.  
  
 Řetězec hledání a porovnání Obvyklou chybou je považovat za kolekce znaků, z nichž každý představuje řetězec <xref:System.Char> objektu. Ve skutečnosti může být vytvořen jeden znak. jednu, dvě nebo více <xref:System.Char> objekty. Tyto znaky se nejčastěji nacházejí v řetězci jazykové verze, jejíž abeced skládat z znaků mimo Unicode základní Latinské rozsah znaků (U + 0021 až U + 007E). V následujícím příkladu se pokusí vyhledat index znaku LATIN velké písmeno A s čárkou nad vlevo (U + 00C 0) v řetězci. Však tento znak může být reprezentován dvěma různými způsoby: jako jednotka jeden kódu (U + 00C 0) nebo jako složený znak (dvě jednotky code: U + 0021 a U + 007E). V takovém případě znak je reprezentována v instanci řetězec dva <xref:System.Char> objektů, U + 0021 a U + 007E. Příklad volání kódu <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> a <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> přetížení najít pozici tento znak v instanci řetězec, ale tyto vrátí odlišné výsledky. První volání metody, které má <xref:System.Char> argument; se provádí ordinální porovnávání a proto nemůže najít odpovídající. Má druhé volání <xref:System.String> argument; ji provede porovnání zohledňující jazykovou verzi a proto najde shoda.  
  
 [!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
 [!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]  
  
 Některé z důvodu nejasností ohledně tohoto příkladu (volání dvě podobné přetížení metody vrátí odlišné výsledky) se můžete vyhnout voláním přetížení, které zahrnuje <xref:System.StringComparison> parametr, jako <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> nebo <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metoda.  
  
 Hledání jsou však není vždy zohledňující jazykovou verzi. Pokud účel hledání k rozhodnutí, zabezpečení nebo uživatelům povolit nebo zakázat přístup k některé prostředku, musí být porovnání pořadí, jak je popsáno v následující části.  
  
<a name="Strings_Equality"></a>   
### <a name="testing-strings-for-equality"></a>Testování rovnosti řetězců  
 Pokud chcete testovat dva řetězce rovnosti místo určování jejich porovnání v pořadí řazení, použijte <xref:System.String.Equals%2A?displayProperty=nameWithType> metody místo metodu porovnání řetězců, jako <xref:System.String.Compare%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.  
  
 Porovnání rovnosti se obvykle provádí některé prostředků podmíněně přístup. Můžete například provést porovnání rovnosti Chcete-li ověřit heslo nebo potvrďte, zda soubor existuje. Takové-lingvistické porovnání by měla být vždy v pořadí, nikoli zohledňující jazykovou verzi. Obecně platí, by měly volat instance <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metoda nebo statické <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metoda s hodnotou <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> pro řetězce, jako jsou hesla a hodnota <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro řetězce, jako jsou názvy souborů nebo identifikátory URI.  
  
 Porovnání rovnosti někdy zahrnují hledání nebo substring porovnání namísto volání <xref:System.String.Equals%2A?displayProperty=nameWithType> metoda. V některých případech může vyhledání substring použít k určení, zda tento dílčí řetězec rovná jiným řetězcem. Toto porovnání se používá jiný lingvistické, hledání měla by být pořadí, nikoli zohledňující jazykovou verzi.  
  
 Následující příklad ilustruje nebezpečí vyhledávání zohledňující jazykovou verzi na údaje o-jazyku. `AccessesFileSystem` Metoda je určena k zákazu přístupu k systému souborů pro identifikátory URI, které začínají dílčí řetězec "Soubor". K tomuto účelu provede porovnání zohledňující jazykovou verzi, bez rozlišování velikosti písmen na začátek identifikátor URI s řetězcem "Soubor". Protože identifikátor URI, který přistupuje k systému souborů může začínat buď "souboru:" nebo "souboru:", implicitní předpokladem je, že "i" (U + 0069) je vždy malá ekvivalentem "I" (U + 0049). Ale v turečtina a Ázerbájdžánština velká verzi "i" je "İ" (U + 0130). Z důvodu této nesrovnalosti Porovnání zohledňující jazykovou verzi umožňuje přístupu k systému souborů, když by mělo být zakázáno.  
  
 [!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
 [!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]  
  
 Je-li předejít tomuto problému, provádění porovnávání podle pořadového čísla, které ignoruje velikost písmen, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
 [!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]  
  
<a name="Strings_Ordering"></a>   
### <a name="ordering-and-sorting-strings"></a>Řazení řetězců  
 Obvykle seřazené řetězce, které se mají zobrazovat v uživatelském rozhraní by měly seřadit podle jazykové verze. Ve většině případů takové porovnání řetězců jsou zpracovávány implicitně rozhraní .NET Framework při volání metody, která seřadí řetězců, jako například <xref:System.Array.Sort%2A?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Ve výchozím nastavení jsou seřazeny řetězců pomocí konvence řazení aktuální jazykové verze. Následující příklad znázorňuje rozdíl, pokud pole řetězců je seřazen podle pomocí konvencí jazykové verze Angličtina (Spojené státy) a jazykovou verzi Švédština (Švédsko).  
  
 [!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
 [!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]  
  
 Porovnání řetězců je definována <xref:System.Globalization.CompareInfo> objekt, který je vrácen rutinou každou jazykovou verzi <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> vlastnost. Porovnání řetězců, které používají <xref:System.String.Compare%2A?displayProperty=nameWithType> přetížení metody také použít <xref:System.Globalization.CompareInfo> objektu.  
  
 Rozhraní .NET Framework používá k provedení zohledňující jazykovou verzi na řetězec dat tabulky. Obsah těchto tabulek, které obsahují údaje o váhy řazení a řetězec normalizace, je určen podle verze standardu Unicode implementované konkrétní verzi rozhraní .NET Framework. Následující tabulka uvádí verze Unicode implementované zadaná verze rozhraní .NET Framework. Všimněte si, že tento seznam podporovaných verzí Unicode se vztahují na znak porovnání a řazení pouze; nevztahuje se na klasifikaci znaky Unicode podle kategorie. Další informace najdete v části "Řetězce a ve standardu Unicode" v <xref:System.String> článku.  
  
|Verze rozhraní .NET Framework|Operační systém|Unicode verze|  
|----------------------------|----------------------|---------------------|  
|.NET Framework 2.0|Všechny operační systémy|Unicode 4.1|  
|.NET Framework 3.0|Všechny operační systémy|Unicode 4.1|  
|.NET Framework 3.5|Všechny operační systémy|Unicode 4.1|  
|.NET Framework 4|Všechny operační systémy|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win7](../../../includes/win7-md.md)]|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win8](../../../includes/win8-md.md)]|Unicode 6.0|  
  
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], porovnání a řazení řetězců závisí na operačním systému. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Systémem [!INCLUDE[win7](../../../includes/win7-md.md)] načte data ze svých tabulek, které implementují 5.0 kódování Unicode. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Systémem [!INCLUDE[win8](../../../includes/win8-md.md)] načítá data z tabulek operačního systému, které implementují 6.0 kódování Unicode. Pokud jste serializovat jazykovou seřazená data, můžete použít <xref:System.Globalization.SortVersion> třídu k určení, když serializovaná data potřebuje, který se má seřadit, aby byl konzistentní s rozhraní .NET Framework a operačního systému pořadí řazení. Příklad, naleznete v části <xref:System.Globalization.SortVersion> třída tématu.  
  
 Pokud vaše aplikace provádí rozsáhlé řazení specifické pro jazykovou verzi řetězec dat, můžete pracovat <xref:System.Globalization.SortKey> třídy pro porovnání řetězců. Klíč řazení odráží váhy řazení specifické pro jazykovou verzi, včetně abecedním, případ a diakritiky váhu konkrétní řetězec. Vzhledem k porovnání pomocí klíčů řazení jsou binární, jsou rychlejší než porovnání, které používají <xref:System.Globalization.CompareInfo> objektu implicitně nebo explicitně. Vytvořte klíč řazení specifické pro jazykovou verzi pro určitý řetězec předáním řetězec, který má <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> metoda.  
  
 V následujícím příkladu je podobně jako v předchozím příkladu. Ale namísto volání <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> metodu, která volá implicitně <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> metoda, definuje <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementace, který porovnává řazení klíčů, které se vytvoří a předá <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> metoda.  
  
 [!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
 [!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]  
  
<a name="Strings_Concat"></a>   
### <a name="avoid-string-concatenation"></a>Vyhněte se řetězení řetězců  
 Pokud je to možné Vyhněte se použití složené řetězců, které jsou vytvořené v době běhu ze spojených frází. Složené řetězce obtížně lokalizaci, protože často předpokládají gramaticky pořadí v jazyce původní aplikace, který nelze použít na jiných lokalizovaných jazycích.  
  
<a name="DatesAndTimes"></a>   
## <a name="handling-dates-and-times"></a>Zpracování hodnot data a času  
 Jak zpracovat datum a čas hodnoty závisí na tom, zda se zobrazí v uživatelském rozhraní nebo trvalé. Tento oddíl se zabývá obě použití. Také popisuje, jak může zpracovat aritmetické operace a časové pásmo rozdíly při práci s daty a časy.  
  
<a name="DatesAndTimes_Display"></a>   
### <a name="displaying-dates-and-times"></a>Zobrazení hodnot data a času  
 Obvykle, když data a časy jsou zobrazeny v uživatelském rozhraní, měli byste použít konvencí formátování jazykové verze uživatele, který je definovaný <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti a <xref:System.Globalization.DateTimeFormatInfo> objekt vrácený `CultureInfo.CurrentCulture.DateTimeFormat` vlastnost. Formátování konvence aktuální jazykové verze automaticky se použijí při formátování data pomocí některé z těchto metod:  
  
-   Bezparametrový <xref:System.DateTime.ToString?displayProperty=nameWithType> – metoda  
  
-   <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> Metodu, která obsahuje řetězec formátu  
  
-   Bezparametrový <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> – metoda  
  
-   <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, Což zahrnuje řetězec formátu  
  
-   [Složené formátování](../../../docs/standard/base-types/composite-formatting.md) funkce, pokud se používá s daty  
  
 Následující příklad zobrazí sunrise a Jahoda data dvakrát pro 11 říjen 2012. Nejprve nastaví aktuální jazykovou verzi na Chorvatština (Chorvatsko) a pak na angličtinu (Velká Británie). V každém případě data a časy jsou zobrazeny ve formátu, který je vhodný pro danou jazykovou verzi.  
  
 [!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
 [!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]  
  
<a name="DatesAndTimes_Persist"></a>   
### <a name="persisting-dates-and-times"></a>Trvalé uchovávání hodnot data a času  
 Nikdy musí zachovat data datum a čas ve formátu, který se může lišit podle jazykové verze. Toto je běžné chybě programování, jejímž výsledkem poškozená data nebo spuštění výjimka. V následujícím příkladu jsou dva kalendářní data, 9 leden 2013 a 18 srpen 2013 jako řetězce pomocí konvencí formátování jazykové verze Angličtina (Spojené státy). Když jsou data načíst a analyzovat pomocí konvencí jazykové verze Angličtina (Spojené státy), je úspěšně obnoven. Ale když je načíst a analyzovat pomocí konvencí jazykové verze Angličtina (Velká Británie), první datum je nesprávně interpretován jako září 1 a druhý se nepodařilo analyzovat, protože gregoriánský kalendář nemá měsícem.  
  
 [!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
 [!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]  
  
 Tento problém tři způsoby se můžete vyhnout:  
  
-   Serializuje data a času v binárním formátu a nikoli jako řetězec.  
  
-   Uložte a analyzovat řetězcovou reprezentaci datum a čas pomocí řetězec vlastní formát, který je stejný bez ohledu na jazykové verzi daného uživatele.  
  
-   Řetězec uložte pomocí konvencí formátování neutrální jazykovou verzi.  
  
 Následující příklad ilustruje poslední přístup. Použije formátování pravidla neutrální jazykovou verzi, vrácený statických <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
 [!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
 [!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]  
  
<a name="DatesAndTimes_TimeZones"></a>   
### <a name="serialization-and-time-zone-awareness"></a>Serializace a zohlednění časového pásma  
 Hodnota data a času může mít několik interpretace, od obecné času ("úložiště otevřít na 2 leden 2013 v 9:00") na konkrétní chvíli v čase ("datum narození: 2 leden 2013 6:32:00 ráno"). Když hodnotu času představuje konkrétní chvíli v čase a obnovte ji ze serializovaná hodnota, měli byste zajistit reprezentuje stejný okamžik v čase bez ohledu na zeměpisném umístění a časovém pásmu uživatele.  
  
 Následující příklad ilustruje tento problém. Uloží jeden místní datum a čas hodnota jako řetězec v tři [standardní formáty](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ("G" pro obecné datum dlouho čas, "s" pro řazení datum a čas a "o" pro operace round-trip pro datum a čas) i jako v binárním formátu.  
  
 [!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
 [!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]  
  
 Při obnovení dat systému ve stejném časovém pásmu jako systém, na kterém byl serializován deserializovat datum a čas hodnoty přesně odrážel původní hodnota, jak ukazuje výstup:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Ale pokud obnovujete data na systém v jiném časovém pásmu, uchovává informace o časovém pásmu pouze datum a čas hodnotu, který je naformátovaný pomocí standardní formátovací řetězec "o" (round-trip) a proto představuje stejné rychlých v čase. Toto je výstup, když se obnoví data datum a čas v systému v láska standardního časového pásma:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Aby přesně odpovídaly datum a čas hodnotu, která představuje jednu chvíli času bez ohledu na časové pásmo systému, na kterém je deserializovat data, můžete provést některé z následujících:  
  
-   Uložte hodnota jako řetězec s použitím (odezvy) standardní formátovací řetězec "o". Následné deserializaci v cílovém systému.  
  
-   Převést na čas UTC a uložte ho jako řetězec pomocí standardní formátovací řetězec "r" (RFC1123). Potom deserializovat v cílovém systému a převeďte ho na místní čas.  
  
-   Převést na čas UTC a uložte ho jako řetězec pomocí standardní formátovací řetězec "u" (universal řazení). Potom deserializovat v cílovém systému a převeďte ho na místní čas.  
  
-   Převést na čas UTC a uložte jej v binárním formátu. Potom deserializovat v cílovém systému a převeďte ho na místní čas.  
  
 Následující příklad ilustruje postupy.  
  
 [!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
 [!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]  
  
 Pokud se data serializovat v systému v časovém pásmu Tichomoří standardní a deserializovat na systém v láska standardního časového pásma, příklad zobrazí následující výstup:  
  
```  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local  
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local  
  
3/31/2013 3:00:00 AM Local  
```  
  
 Další informace najdete v tématu [převádění časy mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).  
  
<a name="DatesAndTimes_Arithmetic"></a>   
### <a name="performing-date-and-time-arithmetic"></a>Aritmetické operace s hodnotami data a času  
 Jak <xref:System.DateTime> a <xref:System.DateTimeOffset> typy podporují aritmetické operace. Můžete vypočítat rozdíl mezi dvěma hodnotami data, nebo můžete přidat nebo odečíst konkrétní časové intervaly do nebo z hodnotu data. Ale aritmetické operace na hodnoty data a času nepřebírají časových pásem a pravidla úprav časové pásmo v úvahu. Z toho důvodu může vrátit data a času aritmetické na hodnotách, které představují situacích v čase nepřesné výsledky.  
  
 Například k přechodu z Tichomoří (běžný čas) na tichomořského letního času na druhou neděli března, což je 10. března roku 2013. Jako následující příklad ukazuje, je-li vypočítat datum a čas, který je 48 hodin po 9 březnem 2013 v 10:30 hodin v systému v Tichomoří standardní časové pásmo výsledek 11 březnem 2013 v 10:30 hodin, nevyžaduje použité nastavení času v úvahu.  
  
 [!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
 [!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]  
  
 A zajistit tak aritmetické operace na hodnoty data a času přesné výsledky, postupujte takto:  
  
1.  Převeďte čas v časovém pásmu zdroje na UTC.  
  
2.  Provádění aritmetických operací.  
  
3.  Pokud je výsledek hodnota data a času, ji převeďte od času UTC čas v časovém pásmu zdroje.  
  
 Následující příklad je podobně jako v předchozím příkladu s tím rozdílem, že ho zahrnuje následující tři kroky správně v 10:30 hodin přidat do 9 březnem 2013 48 hodin  
  
 [!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
 [!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]  
  
 Další informace najdete v tématu [provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md).  
  
### <a name="using-culture-sensitive-names-for-date-elements"></a>Používání názvů zohledňujících jazykovou verzi pro elementy kalendářního data  
 Aplikace může třeba zobrazit název v měsíci nebo den v týdnu. K tomu je běžné, například následující kód.  
  
 [!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
 [!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]  
  
 Tento kód však vždy vrátí názvy dnů v týdnu v angličtině. Kód, který extrahuje název měsíce je často i více pevná. Často předpokládá kalendář dvanácti měsíců s názvy měsíců v určitém jazyce.  
  
 Pomocí [vlastní datum a čas řetězce formátu](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) nebo vlastnosti <xref:System.Globalization.DateTimeFormatInfo> objekt, je snadné k extrakci řetězce, které odráží názvy dnů v týdnu nebo měsíců ve jazykovou verzi uživatele, jak ukazuje následující příklad. Se změní aktuální jazykovou verzi na Francouzština (Francie) a zobrazí název den v týdnu a název v měsíci pro 1 července 2013.  
  
 [!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
 [!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]  
  
<a name="Numbers"></a>   
## <a name="handling-numeric-values"></a>Zpracování číselných hodnot  
 Zpracování čísel závisí na tom, zda se zobrazí v uživatelském rozhraní nebo trvalé. Tento oddíl se zabývá obě použití.  
  
> [!NOTE]
>  Analýza a formátování operace, rozhraní .NET Framework rozpoznává jenom základní Latinské znaky 0 až 9 (U + 0030 až U + 0039) jako číslice.  
  
<a name="Numbers_Display"></a>   
### <a name="displaying-numeric-values"></a>Zobrazení číselných hodnot  
 Obvykle, když čísla se zobrazí v uživatelském rozhraní, měli byste použít konvencí formátování jazykové verze uživatele, který je definovaný <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti a <xref:System.Globalization.NumberFormatInfo> objekt vrácený `CultureInfo.CurrentCulture.NumberFormat` vlastnost. Formátování konvence aktuální jazykové verze automaticky se použijí při formátování data pomocí některé z následujících metod:  
  
-   Bezparametrový `ToString` žádné číselného typu – metoda  
  
-   `ToString(String)` Číselného typu, který obsahuje řetězec formátu jako argument – metoda  
  
-   [Složené formátování](../../../docs/standard/base-types/composite-formatting.md) funkce, pokud se používá s číselné hodnoty.  
  
 Následující příklad zobrazí průměrnou teplotu měsíčně v Paříž, Francie. Nejprve nastaví aktuální jazykovou verzi, francouzština (Francie) před zobrazením dat a pak ji nastaví na angličtinu (Spojené státy). V každém případě se zobrazí názvy měsíců a teploty ve formátu, který je vhodný pro danou jazykovou verzi. Upozorňujeme, že dvě jazykové verze použít jiné oddělovače desetinných míst v hodnotě teploty. Všimněte si, že příklad používá "MMMM" vlastní datum a čas řetězec formátu zobrazení jména úplný měsíc a jeho přiděluje odpovídající velikost místa pro názvy měsíců ve výsledném řetězci tak, že určíte délka názvu měsíc nejdelší <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType></C0>pole.  
  
 [!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
 [!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]  
  
<a name="Numbers_Persist"></a>   
### <a name="persisting-numeric-values"></a>Trvalé uchovávání číselných hodnot  
 Nikdy musí zachovat číselná data ve formátu specifické pro jazykovou verzi. Toto je běžné chybě programování, jejímž výsledkem poškozená data nebo spuštění výjimka. Následující příklad generuje deset náhodná čísla s plovoucí desetinnou čárkou a pak je serializuje jako řetězce pomocí konvencí formátování jazykové verze Angličtina (Spojené státy). Když jsou data načíst a analyzovat pomocí konvencí jazykové verze Angličtina (Spojené státy), je úspěšně obnoven. Ale když je načíst a analyzovat pomocí konvencí jazykové verze francouzština (Francie), žádný z čísla lze analyzovat protože jazykových verzí používají jiné oddělovače desetinných míst.  
  
 [!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
 [!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]  
  
 K tomuto problému nedošlo, můžete použít některý z následujících postupů:  
  
-   Uložte a analyzovat řetězcovou reprezentaci číslo pomocí řetězec vlastní formát, který je stejný bez ohledu na jazykové verzi daného uživatele.  
  
-   Uložit číslo jako řetězec pomocí konvencí formátování neutrální jazykovou verzi, která je vrácena <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Serializuje číslo v binárním místo formát řetězce.  
  
 Následující příklad ilustruje poslední přístup. Ho serializuje pole <xref:System.Double> hodnoty a pak deserializuje a zobrazí je pomocí konvencí formátování Czech (Czech Republic) a kultur francouzština (Francie).  
  
 [!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
 [!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]  
  
 Serializaci hodnoty měny je zvláštní případ. Protože hodnotu měny závisí na jednotku měny, ve které je vyjádřena; má smysl málo považovat za nezávislé číselná hodnota. Ale pokud uložíte hodnotu měny jako formátovaný řetězec, který zahrnuje symbolu měny, ho nelze deserializovat systému, jejíž výchozí jazykovou verzi používá jiný symbol měny, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
 [!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]  
  
 Místo toho můžete serializovat číselnou hodnotu některé kulturního informace, jako je například název jazykové verze, tak, aby hodnota a její symbolu měny lze deserializovat nezávisle na aktuální jazykové verze. Následující příklad nemá, tak, že definujete `CurrencyValue` struktura s dva členy: <xref:System.Decimal> hodnota a název jazykové verze, do které patří hodnota.  
  
 [!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
 [!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]  
  
<a name="Cultures"></a>   
## <a name="working-with-culture-specific-settings"></a>Práce s nastaveními specifickými pro jazykovou verzi  
 V rozhraní .NET Framework <xref:System.Globalization.CultureInfo> třída reprezentuje konkrétní jazykové verze nebo oblast. Některé jeho vlastnosti vrátit objekty, které obsahují konkrétní informace o určitý aspekt jazykové verze:  
  
-   <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> Vlastnost vrátí <xref:System.Globalization.CompareInfo> objekt, který obsahuje informace o tom, jak jazyková verze, porovná a řadí řetězce.  
  
-   <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> Vlastnost vrátí <xref:System.Globalization.DateTimeFormatInfo> objekt, který obsahuje informace specifické pro jazykovou verzi použité při formátování data a času.  
  
-   <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> Vlastnost vrátí <xref:System.Globalization.NumberFormatInfo> objekt, který obsahuje informace specifické pro jazykovou verzi použité při formátování číselná data.  
  
-   <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> Vlastnost vrátí <xref:System.Globalization.TextInfo> objekt, který obsahuje informace o jazykové verzi je zápis systému.  
  
 Obecně platí, neprovádějte žádné předpoklady o hodnotách konkrétní <xref:System.Globalization.CultureInfo> vlastnosti a jejich související objekty. Místo toho by měla zobrazit specifické pro jazykovou verzi dat jako mohou podléhat změnám, z těchto důvodů:  
  
-   Jednotlivé hodnoty vlastností se vztahují změn a revize časem, jako data po opravě, bude k dispozici lepší dat nebo změnit konvence specifické pro jazykovou verzi.  
  
-   Jednotlivé hodnoty vlastností se může lišit mezi verzemi verze rozhraní .NET Framework nebo operačního systému.  
  
-   Rozhraní .NET Framework podporuje náhradní jazykové verze. Díky tomu je možné definovat nové vlastní jazykové verze, který nahrazuje stávající standardní jazykové verze nebo zcela nahradí existující standardní jazykovou verzi.  
  
-   Uživatele můžete upravit nastavení specifické pro jazykovou verzi pomocí **oblast a jazyk** aplikace v Ovládacích panelech. Při vytváření instancí <xref:System.Globalization.CultureInfo> objekt, můžete určit, zda odráží toto vlastní nastavení uživatele voláním <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktor. Obvykle pro koncového uživatele aplikace by měly dodržovat uživatelských předvoleb tak, aby se uživateli s daty ve formátu, který potvrdí očekává.  
  
## <a name="see-also"></a>Viz také  
 [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)  
 [Doporučené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md)
