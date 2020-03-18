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
ms.openlocfilehash: fe03bbdd7d037a9f1fb4985b62b447c6ef9c6535
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79174781"
---
# <a name="globalization"></a>Globalizace

Globalizace zahrnuje návrh a vývoj aplikace připravené pro svět, která podporuje lokalizovaná rozhraní a regionální data pro uživatele ve více kulturách. Před zahájením fáze návrhu byste měli určit, které jazykové verze bude vaše aplikace podporovat. Přestože aplikace cílí na jednu jazykovou verzi nebo oblast jako výchozí, můžete ji navrhnout a zapsat tak, aby ji bylo možné snadno rozšířit na uživatele v jiných kulturách nebo oblastech.

Jako vývojáři máme všichni předpoklady o uživatelských rozhraních a datech, které jsou tvořeny našimi kulturami. Například pro anglicky mluvící vývojářve Spojených státech serializace data data a času `MM/dd/yyyy hh:mm:ss` jako řetězec ve formátu se zdá být naprosto rozumné. Však deserializace tohoto řetězce v systému v jiné <xref:System.FormatException> jazykové verzi je však pravděpodobně vyvolat výjimku nebo vytvořit nepřesná data. Globalizace nám umožňuje identifikovat takové předpoklady specifické pro jazykovou verzi a zajistit, aby neovlivnily návrh nebo kód naší aplikace.

Tento článek popisuje některé hlavní problémy, které byste měli zvážit, a osvědčené postupy, které můžete dodržovat při zpracování řetězců, hodnot data a času a číselných hodnot v globalizované aplikaci.

## <a name="strings"></a>Řetězce

Zpracování znaků a řetězců je ústředním cílem globalizace, protože každá jazyková verze nebo oblast může používat různé znaky a znakové sady a seřadit je odlišně. Tato část obsahuje doporučení pro použití řetězců v globalizovaných aplikacích.

### <a name="use-unicode-internally"></a>Interní použití unicode

Ve výchozím nastavení používá rozhraní .NET řetězce Unicode. Řetězec Unicode se skládá z nuly, jednoho nebo více <xref:System.Char> objektů, z nichž každý představuje jednotku kódu UTF-16. K dispozici je reprezentace Unicode pro téměř každý znak v každé znakové sadě, která se používá po celém světě.

Mnoho aplikací a operačních systémů, včetně operačního systému Windows, může také používat znakové stránky k reprezentaci znakových sad. Znakové stránky obvykle obsahují standardní hodnoty ASCII od 0x00 do 0x7F a mapují další znaky na zbývající hodnoty od 0x80 do 0xFF. Interpretace hodnot od 0x80 do 0xFF závisí na konkrétní znakové stránce. Z tohoto důvodu byste se měli vyhnout použití znakových stránek v globalizované aplikaci, pokud je to možné.

Následující příklad ilustruje nebezpečí interpretace dat znakové stránky, pokud se výchozí znaková stránka v systému liší od znakové stránky, na které byla data uložena. (Chcete-li simulovat tento scénář, příklad explicitně určuje různé znakové stránky.) Příklad nejprve definuje pole, které se skládá z velkých znaků řecké abecedy. Zakóduje je do bajtového pole pomocí znakové stránky 737 (označované také jako MS-DOS Greek) a uloží bajtové pole do souboru. Pokud je soubor načten a jeho bajtové pole je dekódováno pomocí znakové stránky 737, původní znaky jsou obnoveny. Pokud je však soubor načten a jeho bajtové pole je dekódováno pomocí znakové stránky 1252 (nebo systému Windows-1252, který představuje znaky v latince), budou původní znaky ztraceny.

[!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
[!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]

Použití unicode zajišťuje, že stejné jednotky kódu vždy mapovány na stejné znaky a že stejné znaky vždy mapovat na stejné bajtpole.

### <a name="use-resource-files"></a>Použití souborů prostředků

I v případě, že vyvíjíte aplikaci, která se zaměřuje na jednu jazykovou verzi nebo oblast, měli byste použít soubory prostředků k ukládání řetězců a dalších prostředků, které jsou zobrazeny v uživatelském rozhraní. Nikdy byste je neměli přidávat přímo do kódu. Použití souborů prostředků má řadu výhod:

- Všechny řetězce jsou na jednom místě. Není nutné hledat v celém zdrojovém kódu k identifikaci řetězců upravit pro konkrétní jazyk nebo jazykovou verzi.

- Není třeba duplikovat řetězce. Vývojáři, kteří nepoužívají soubory prostředků, často definují stejný řetězec ve více zdrojových kódových souborech. Tato duplikace zvyšuje pravděpodobnost, že jeden nebo více instancí bude přehlédnuto při změně řetězce.

- Do souboru prostředků můžete zahrnout prostředky, které nejsou řetězce, například obrázky nebo binární data, namísto jejich uložení do samostatného samostatného souboru, aby je bylo možné snadno načíst.

Použití souborů prostředků má zvláštní výhody, pokud vytváříte lokalizovanou aplikaci. Při nasazování prostředků v satelitních sestaveních soubor ový čas jazyka automaticky vybere prostředek odpovídající jazykové verzi <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> na základě aktuální jazykové verze uživatelského rozhraní uživatele definované vlastností. Pokud zadáte odpovídající prostředek specifický pro jazykovou verzi a <xref:System.Resources.ResourceManager> správně nastolíte objekt nebo použijete třídu prostředků silného typu, zpracovat podrobnosti o načtení příslušných prostředků.

Další informace o vytváření souborů prostředků naleznete v [tématu Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Informace o vytváření a nasazování satelitních sestavení naleznete [v tématu Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) a [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

### <a name="search-and-compare-strings"></a>Hledání a porovnávání řetězců

Kdykoli je to možné, měli byste zpracovat řetězce jako celé řetězce namísto jejich zpracování jako řada jednotlivých znaků. To je obzvláště důležité při řazení nebo hledání podřetězců, aby se zabránilo problémům spojeným s analýzou kombinovaných znaků.

> [!TIP]
> Třídu <xref:System.Globalization.StringInfo> můžete použít k práci s textovými prvky, nikoli s jednotlivými znaky v řetězci.

Při hledání řetězce a porovnávání je běžnou chybou považovat řetězec za kolekci znaků, <xref:System.Char> z nichž každá je reprezentována objektem. Ve skutečnosti jeden znak může být tvořen jeden, <xref:System.Char> dva nebo více objektů. Tyto znaky se nejčastěji nacházejí v řetězcích z kultur, jejichž abecedy se skládají ze znaků mimo rozsah znaků Unicode Basic Latin (U + 0021 až U + 007E). Následující příklad se pokusí najít index znaku Velké písmeno latinky A s hrobem (U + 00C0) v řetězci. Tento znak však může být reprezentován dvěma různými způsoby: jako jedna jednotka kódu (U + 00C0) nebo jako složený znak (dvě jednotky kódu: U + 0041 a U + 0300). V tomto případě je znak reprezentován v <xref:System.Char> instanci řetězce dvěma objekty, U + 0041 a U + 0300. Ukázkový kód <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> volá <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> a přetížení najít pozici tohoto znaku v instanci řetězce, ale tyto vrátit různé výsledky. První volání metody <xref:System.Char> má argument; provede řadové porovnání a proto nemůže najít shodu. Druhý hovor má <xref:System.String> argument; provede porovnání citlivé na jazykovou verzi a proto najde shodu.

[!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
[!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]

Můžete se vyhnout některé nejednoznačnosti tohoto příkladu (volání dvou podobných přetížení metody vrácení různých <xref:System.StringComparison> výsledků) voláním <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> přetížení, který obsahuje parametr, jako je například nebo metoda.

Hledání však nejsou vždy citlivé na jazykovou verzi. Pokud je účelem hledání učinit rozhodnutí o zabezpečení nebo povolit nebo zakázat přístup k některému prostředku, mělo by být porovnání řadové, jak je popsáno v další části.

### <a name="test-strings-for-equality"></a>Testovací řetězce pro rovnost

Pokud chcete otestovat dva řetězce pro rovnost spíše než určit, jak <xref:System.String.Equals%2A?displayProperty=nameWithType> porovnat v pořadí řazení, <xref:System.String.Compare%2A?displayProperty=nameWithType> použijte <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>metodu namísto metody porovnání řetězců, jako je například nebo .

Porovnání rovnosti se obvykle provádí pro podmíněný přístup k některému prostředku. Můžete například provést porovnání rovnosti k ověření hesla nebo k potvrzení, že soubor existuje. Taková nejazyková srovnání by měla být vždy ordinální, nikoli citlivá na jazykovou verzi. Obecně byste měli volat <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodu instance <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> nebo statickou <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> metodu s hodnotou pro řetězce, jako jsou hesla, a hodnotu <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro řetězce, jako jsou názvy souborů nebo identifikátory URI.

Porovnání rovnosti někdy zahrnují vyhledávání nebo porovnání podřetězců spíše <xref:System.String.Equals%2A?displayProperty=nameWithType> než volání metody. V některých případech můžete použít hledání podřetězce k určení, zda tento podřetězec rovná jiný řetězec. Pokud je účelem tohoto porovnání nejazykové, hledání by mělo být také ordinální spíše než jazykovou verzi.

Následující příklad ilustruje nebezpečí vyhledávání nejazykového zabezpečení zjizení jazykové verze. Metoda `AccessesFileSystem` je navržena tak, aby zakázala přístup k systému souborů pro identifikátory URI, které začínají podřetězcem "FILE". Chcete-li to provést, provede porovnání pro jazykovou verzi, nerozlišující malá a velká písmena začátku identifikátoru URI s řetězcem "FILE". Vzhledem k tomu, že identifikátor URI, který přistupuje k systému souborů, může začínat buď "FILE:" nebo "file:", implicitní předpoklad je, že "i" (U + 0069) je vždy malý ekvivalent "I" (U + 0049). V turečtině a ázerbájdžánština je však velká verze "i" "İ" (U + 0130). Z důvodu tohoto rozdílu umožňuje porovnání zjištovaní jazykovou verzi přístup k systému souborů, pokud by měl být zakázán.

[!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
[!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]

Tomuto problému se můžete vyhnout provedením pořadového porovnání, které ignoruje případ, jak ukazuje následující příklad.

[!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
[!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]

### <a name="order-and-sort-strings"></a>Pořadí a řazení řetězců

Obvykle objednané řetězce, které mají být zobrazeny v uživatelském rozhraní by měly být seřazeny na základě jazykové verze. Z větší části jsou tyto porovnání řetězců zpracovány implicitně rozhraním .NET při <xref:System.Array.Sort%2A?displayProperty=nameWithType> volání <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>metody, která seřadí řetězce, například nebo . Ve výchozím nastavení jsou řetězce seřazeny pomocí konvencí řazení aktuální jazykové verze. Následující příklad ilustruje rozdíl při řazení pole řetězců pomocí konvencí jazykové verze angličtiny (Spojené státy) a švédské (Švédsko) jazykové verze.

[!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
[!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]

Porovnání řetězců citlivých na jazykovou verzi je definováno objektem, <xref:System.Globalization.CompareInfo> který je vrácen <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> vlastností každé jazykové verze. Porovnání řetězců citlivých na jazykovou verzi, které používají <xref:System.String.Compare%2A?displayProperty=nameWithType> přetížení metody, také používají <xref:System.Globalization.CompareInfo> objekt.

Rozhraní .NET používá tabulky k provádění řazení citlivých na jazykovou verzi na řetězcová data. Obsah těchto tabulek, které obsahují data o hmotnosti řazení a normalizaci řetězců, je určen verzí standardu Unicode implementovanou konkrétní verzí rozhraní .NET. V následující tabulce jsou uvedeny verze kódování Unicode implementované zadanými verzemi rozhraní .NET Framework a rozhraní MNo Core. Všimněte si, že tento seznam podporovaných verzí Unicode platí pouze pro porovnání znaků a řazení; nevztahuje se na klasifikaci znaků Unicode podle kategorie. Další informace naleznete v části Řetězce a standard Unicode <xref:System.String> v článku.

|Verze rozhraní .NET Framework|Operační systém|Verze Unicode|
|----------------------------|----------------------|---------------------|
|.NET Framework 2,0|Všechny operační systémy|Unicode 4,1|
|.NET Framework 3.0|Všechny operační systémy|Unicode 4,1|
|.NET Framework 3.5|Všechny operační systémy|Unicode 4,1|
|.NET Framework 4|Všechny operační systémy|Unicode 5,0|
|Rozhraní .NET Framework 4.5 a novější v systému Windows 7|Unicode 5,0|
|Rozhraní .NET Framework 4.5 a novější v operačních systémech Windows 8 a novějších|Unicode 6.3.0|
|.NET Core (všechny verze)|Závisí na verzi standardu Unicode podporované základním operačním systémem.|

Počínaje rozhraním .NET Framework 4.5 a ve všech verzích rozhraní .NET Core závisí porovnání a řazení řetězců na operačním systému. Rozhraní .NET Framework 4.5 a novější v systému Windows 7 načítá data z vlastních tabulek, které implementují Unicode 5.0. Rozhraní .NET Framework 4.5 a novější v systému Windows 8 a novější načítá data z tabulek operačního systému, které implementují unicode 6.3. V rozhraní .NET Core závisí podporovaná verze unicode na základním operačním systému. Pokud serializujete seřazená data citlivá <xref:System.Globalization.SortVersion> na jazykovou verzi, můžete pomocí třídy určit, kdy je třeba serializovaná data seřadit tak, aby byla konzistentní s rozhraním .NET a pořadí řazení operačního systému. Příklad najdete v <xref:System.Globalization.SortVersion> tématu třídy.

Pokud vaše aplikace provádí rozsáhlé druhy řetězcových dat specifické <xref:System.Globalization.SortKey> pro jazykovou verzi, můžete s třídou porovnat řetězce. Klíč řazení odráží vah řazení specifické pro jazykovou verzi, včetně abecedních, case a diakritikových vah určitého řetězce. Vzhledem k tomu, že porovnání pomocí klíčů řazení <xref:System.Globalization.CompareInfo> jsou binární, jsou rychlejší než porovnání, které používají objekt implicitně nebo explicitně. Vytvoření klíče řazení specifické pro jazykovou verzi pro určitý <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> řetězec předáním řetězce metodě.

Následující příklad je podobný předchozímu příkladu. Však místo volání <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> metody, která implicitně volá metodu, <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> definuje <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementaci, která porovnává klíče řazení, které <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> konkretizuje a předá metodě.

[!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
[!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]

### <a name="avoid-string-concatenation"></a>Vyhněte se zřetězení řetězců

Pokud je to možné, vyhněte se použití složených řetězců, které jsou vytvořeny za běhu z zřetězených frází. Složené řetězce je obtížné lokalizovat, protože často předpokládají gramatické pořadí v původním jazyce aplikace, který se nevztahuje na jiné lokalizované jazyky.

## <a name="handle-dates-and-times"></a>Zpracování dat a časů

Způsob zpracování hodnot data a času závisí na tom, zda jsou zobrazeny v uživatelském rozhraní nebo trvalé. Tato část zkoumá obě použití. Popisuje také, jak můžete zpracovat rozdíly v časových pásmech a aritmetické operace při práci s daty a časy.

### <a name="display-dates-and-times"></a>Zobrazení dat a časů

Obvykle při data a časy jsou zobrazeny v uživatelském rozhraní, měli byste použít formátování konvence jazykové verze <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> uživatele, <xref:System.Globalization.DateTimeFormatInfo> který je `CultureInfo.CurrentCulture.DateTimeFormat` definován vlastnost a objekt vrácený vlastností. Konvence formátování aktuální jazykové verze se automaticky používají při formátování data pomocí některé z těchto metod:

- Metoda bez <xref:System.DateTime.ToString?displayProperty=nameWithType> parametrů

- Metoda, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> která obsahuje formátovací řetězec

- Metoda bez <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> parametrů

- <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>V , který obsahuje formátovací řetězec

- Funkce [složeného formátování](../../../docs/standard/base-types/composite-formatting.md) při použití s daty

Následující příklad zobrazuje data východu a západu slunce dvakrát pro říjen 11, 2012. Nejprve nastaví současnou kulturu na chorvatštinu (Chorvatsko) a poté na angličtinu (Velká Británie). V každém případě jsou zobrazeny data a časy ve formátu, který je vhodný pro tuto jazykovou verzi.

[!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
[!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]

### <a name="persist-dates-and-times"></a>Zachovat data a časy

Nikdy byste neměli uchovávat data a čas dat ve formátu, který se může lišit podle jazykové verze. Toto je běžná chyba programování, která má za následek poškozená data nebo výjimku za běhu. Následující příklad serializuje dvě data, leden 9, 2013 a srpen 18, 2013, jako řetězce pomocí konvencí formátování jazykové verze Angličtina (Spojené státy). Při načítání a analýzy dat pomocí konvencí jazykové verze angličtiny (Spojené státy), je úspěšně obnovena. Však při načtení a analyzovat pomocí konvence jazykové verze Angličtina (Spojené království), první datum je nesprávně interpretován jako 1.

[!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
[!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]

Tomuto problému se můžete vyhnout libovolným ze tří způsobů:

- Serialize data a času v binárním formátu, nikoli jako řetězec.

- Uložte a analyzujte řetězcovou reprezentaci data a času pomocí vlastního formátovacího řetězce, který je stejný bez ohledu na jazykovou verzi uživatele.

- Uložte řetězec pomocí konvencí formátování invariantní jazykové verze.

Následující příklad ilustruje poslední přístup. Používá konvence formátování invariantní jazykové verze vrácené <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> statickou vlastností.

[!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
[!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]

### <a name="serialization-and-time-zone-awareness"></a>Serializace a povědomí o časovém pásmu

Hodnota data a času může mít více interpretací, od obecného času ("Obchody otevřené v lednu 2, 2013, v 9:00.") až po konkrétní okamžik v čase ("Datum narození: Leden 2, 2013 6:32:00 A.M."). Pokud hodnota času představuje určitý okamžik v čase a obnovíte jej z serializované hodnoty, měli byste zajistit, že představuje stejný okamžik v čase bez ohledu na zeměpisnou polohu nebo časové pásmo uživatele.

Následující příklad ilustruje tento problém. Uloží jednu místní hodnotu data a času jako řetězec ve třech [standardních formátech](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ("G" pro obecné datum dlouhé hodu, "s" pro seřaditelné datum a čas a "o" pro datum a čas odezvy) a také v binárním formátu.

[!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
[!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]

Pokud jsou data obnovena v systému ve stejném časovém pásmu jako systém, ve kterém byla serializována, deserializované hodnoty data a času přesně odrážejí původní hodnotu, jak ukazuje výstup:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local

3/30/2013 6:00:00 PM Local
```

Pokud však obnovíte data v systému v jiném časovém pásmu, pouze hodnota data a času, která byla formátována standardním formátovacím řetězcem "o" (round-trip), zachová informace o časovém pásmu a proto představuje stejný okamžik v čase. Zde je výstup při obnovení dat a času v systému v romantickém standardním časovém pásmu:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local

3/30/2013 6:00:00 PM Local
```

Chcete-li přesně zohlednit hodnotu data a času, která představuje jediný okamžik času bez ohledu na časové pásmo systému, ve kterém jsou data deserializována, můžete provést některou z následujících akcí:

- Uložte hodnotu jako řetězec pomocí standardního formátovacího řetězce "o" (round-trip). Pak ji dekrezujte v cílovém systému.

- Převeďte jej na UTC a uložte jej jako řetězec pomocí standardního formátovacího řetězce "r" (RFC1123). Potom jej dekonstruujte v cílovém systému a převeďte na místní čas.

- Převeďte jej na UTC a uložte jej jako řetězec pomocí standardního formátovacího řetězce "u" (universal sortable). Potom jej dekonstruujte v cílovém systému a převeďte na místní čas.

- Převeďte jej na UTC a uložte jej v binárním formátu. Potom jej dekonstruujte v cílovém systému a převeďte na místní čas.

Následující příklad ilustruje každou techniku.

[!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
[!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]

Pokud jsou data serializována v systému v tichomořském standardním časovém pásmu a deknokace v systému v romantickém standardním časovém pásmu, zobrazí se v příkladu následující výstup:

```console
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local

3/31/2013 3:00:00 AM Local
```

Další informace naleznete [v tématu Převod časů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).

### <a name="perform-date-and-time-arithmetic"></a>Provedení aritmetiky data a času

Typy <xref:System.DateTime> a <xref:System.DateTimeOffset> typy podporují aritmetické operace. Můžete vypočítat rozdíl mezi dvěma hodnotami kalendářních dat nebo můžete přidat nebo odečíst určité časové intervaly do nebo od hodnoty data. Aritmetické operace na hodnoty data a času však neberou v úvahu časová pásma a pravidla úpravy časového pásma. Z tohoto důvodu může aritmetika data a času na hodnoty, které představují okamžiky v čase, vrátit nepřesné výsledky.

Například přechod z tichomořského standardního času na tichomořský letní čas nastane na druhou neděli v březnu, což je 10. Jak ukazuje následující příklad, pokud vypočítáte datum a čas, který je 48 hodin po 9. v systému v tichomořském standardním časovém pásmu výsledek, březen 11, 2013 v 10:30, nebere v úvahu úpravu času zasahování.

[!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
[!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]

Chcete-li zajistit, aby aritmetické operace na datum a čas hodnoty poskytuje přesné výsledky, postupujte takto:

1. Převeďte čas ve zdrojovém časovém pásmu na Čas UTC.

2. Proveďte aritmetické operace.

3. Pokud je výsledkem hodnota data a času, převeďte ji z času UTC na čas ve zdrojovém časovém pásmu.

Následující příklad je podobný předchozímu příkladu, s tím rozdílem, že následuje tyto tři kroky správně přidat 48 hodin na 9 března 2013 v 10:30.

[!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
[!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]

Další informace naleznete [v tématu Provádění aritmetické operace s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md).

### <a name="use-culture-sensitive-names-for-date-elements"></a>Použití názvů citlivých na jazykovou verzi pro prvky kalendářních dat

Aplikace může potřebovat zobrazit název měsíce nebo dne v týdnu. Chcete-li to provést, kód, jako je například následující je běžné.

[!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
[!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]

Tento kód však vždy vrátí názvy dnů v týdnu v angličtině. Kód, který extrahuje název měsíce je často ještě nepružnější. Často předpokládá dvanáctiměsíční kalendář s názvy měsíců v určitém jazyce.

Pomocí [vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) <xref:System.Globalization.DateTimeFormatInfo> nebo vlastnosti objektu, je snadné extrahovat řetězce, které odrážejí názvy dnů v týdnu nebo měsících v jazykové verzi uživatele, jak ukazuje následující příklad. Změní aktuální jazykovou verzi na francouzštinu (Francie) a zobrazí název dne v týdnu a název měsíce pro červenec 1, 2013.

[!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
[!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]

## <a name="numeric-values"></a>Číselné hodnoty

Zpracování čísel závisí na tom, zda jsou zobrazeny v uživatelském rozhraní nebo trvalé. Tato část zkoumá obě použití.

> [!NOTE]
> V operacích analýzy a formátování .NET rozpozná pouze základní znaky latinky 0 až 9 (U + 0030 až U + 0039) jako číselné číslice.

### <a name="display-numeric-values"></a>Zobrazení číselných hodnot

Obvykle při čísla jsou zobrazeny v uživatelském rozhraní, měli byste použít formátování konvence jazykové verze uživatele, který je definován <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost a <xref:System.Globalization.NumberFormatInfo> objekt `CultureInfo.CurrentCulture.NumberFormat` vrácený vlastností. Konvence formátování aktuální jazykové verze se automaticky používají při formátování data pomocí některé z následujících metod:

- Metoda bez `ToString` parametrů libovolného číselného typu

- Metoda `ToString(String)` libovolného číselného typu, která obsahuje formátovací řetězec jako argument

- Funkce [složeného formátování](../../../docs/standard/base-types/composite-formatting.md) při použití s číselnými hodnotami

Následující příklad zobrazuje průměrnou teplotu za měsíc v Paříž, Francie. Nejprve nastaví aktuální jazykovou verzi na francouzštinu (Francie) před zobrazením dat a potom ji nastaví na angličtinu (Spojené státy). V každém případě jsou názvy měsíců a teploty zobrazeny ve formátu, který je vhodný pro tuto jazykovou verzi. Všimněte si, že dvě jazykové verze používají různé oddělovače desetinných míst v hodnotě teploty. Všimněte si také, že příklad používá "MMMM" vlastní datum a čas formátovací řetězec pro zobrazení celého názvu měsíce a že přiděluje odpovídající <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> množství místa pro název měsíce ve výsledném řetězci určením délky nejdelší název měsíce v poli.

[!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
[!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]

### <a name="persist-numeric-values"></a>Zachovat číselné hodnoty

Nikdy byste neměli uchovávat číselná data ve formátu specifickém pro jazykovou verzi. Toto je běžná chyba programování, která má za následek poškozená data nebo výjimku za běhu. Následující příklad generuje deset náhodných čísel s plovoucí desetinnou desetnou desetnou desetnou desetnou desetnou desetnou desetinnou desetiťovou a potom je serializuje jako řetězce pomocí konvencí formátování jazykové verze Angličtina (Spojené státy). Při načítání a analýzy dat pomocí konvencí jazykové verze angličtiny (Spojené státy), je úspěšně obnovena. Však při načítání a analýzy pomocí konvence francouzské (Francie) jazykové verze, žádná z čísel lze analyzovat, protože jazykové verze používají různé oddělovače desetinných míst.

[!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
[!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]

Chcete-li se tomuto problému vyhnout, můžete použít jednu z těchto technik:

- Uložte a analyzujte řetězcovou reprezentaci čísla pomocí vlastního formátovacího řetězce, který je stejný bez ohledu na jazykovou verzi uživatele.

- Uložte číslo jako řetězec pomocí konvencí formátování invariantní jazykové verze, která je vrácena <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastností.

- Serialize číslo v binárním formátu namísto formátu řetězce.

Následující příklad ilustruje poslední přístup. Serializuje pole <xref:System.Double> hodnot a potom je reserializuje a zobrazuje pomocí konvencí formátování jazykové verze Angličtina (Spojené státy) a Francouzština (Francie).

[!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
[!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]

Serializace hodnot měny je zvláštní případ. Protože hodnota měny závisí na jednotce měny, ve které je vyjádřena; nemá smysl s ním zacházet jako s nezávislou číselnou hodnotou. Pokud však uložíte hodnotu měny jako formátovaný řetězec, který obsahuje symbol měny, nelze ji rekonstruovat v systému, jehož výchozí jazyková verze používá jiný symbol měny, jak ukazuje následující příklad.

[!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
[!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]

Místo toho byste měli serializovat číselnou hodnotu spolu s některými kulturními informacemi, jako je například název jazykové verze, aby hodnota a její symbol měny mohly být reserializovány nezávisle na aktuální jazykové verzi. Následující příklad to umožňuje definováním struktury se `CurrencyValue` <xref:System.Decimal> dvěma členy: hodnotou a názvem jazykové verze, do které hodnota patří.

[!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
[!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]

## <a name="work-with-culture-specific-settings"></a>Práce s nastavením specifickým pro jazykovou verzi

V rozhraní .NET <xref:System.Globalization.CultureInfo> představuje třída určitou jazykovou verzi nebo oblast. Některé jeho vlastnosti vrátí objekty, které poskytují konkrétní informace o některé aspekty jazykové verze:

- Vlastnost <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> vrátí <xref:System.Globalization.CompareInfo> objekt, který obsahuje informace o tom, jak jazyková verze porovnává a objednávky řetězce.

- Vlastnost <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vrátí <xref:System.Globalization.DateTimeFormatInfo> objekt, který poskytuje informace specifické pro jazykovou verzi používané ve formátování data a času dat.

- Vlastnost <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> vrátí <xref:System.Globalization.NumberFormatInfo> objekt, který poskytuje informace specifické pro jazykovou verzi používané při formátování číselných dat.

- Vlastnost <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> vrátí <xref:System.Globalization.TextInfo> objekt, který poskytuje informace o systému zápisu jazykové verze.

Obecně nevytvářejte žádné předpoklady o hodnotách určitých <xref:System.Globalization.CultureInfo> vlastností a jejich souvisejících objektech. Místo toho byste měli zobrazit data specifická pro jazykovou verzi jako předmět změny, z těchto důvodů:

- Jednotlivé hodnoty vlastností se mohou měnit a revize v průběhu času, jako data jsou opraveny, lepší data jsou k dispozici nebo konvence specifické pro jazykovou verzi změnit.

- Hodnoty jednotlivých vlastností se mohou lišit v různých verzích rozhraní .NET nebo verzí operačního systému.

- Rozhraní .NET podporuje náhradní jazykové verze. To umožňuje definovat novou vlastní jazykovou verzi, která doplňuje existující standardní jazykové verze nebo zcela nahrazuje existující standardní jazykovou verzi.

- V systémech Windows může uživatel přizpůsobit nastavení specifická pro jazykovou verzi pomocí ovládacího panelu **Oblast a jazyk.** Při vytváření instanci <xref:System.Globalization.CultureInfo> objektu můžete určit, zda odráží tyto uživatelské <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> úpravy voláním konstruktoru. Obvykle pro aplikace koncových uživatelů byste měli respektovat uživatelské předvolby tak, aby uživateli byla nabídnuta data ve formátu, který očekává.

## <a name="see-also"></a>Viz také

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Doporučené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md)
