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
ms.openlocfilehash: ce2f127858305a96b358c1661b98a359ae565f57
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393117"
---
# <a name="globalization"></a>Globalizace

Globalizace zahrnuje návrh a vývoj špičkové aplikace, které podporují lokalizované rozhraní a regionální data pro uživatele v různých jazykových verzích. Před zahájením fáze návrhu byste měli určit, které kultury bude vaše aplikace podporovat. I když aplikace cílí na jednu jazykovou verzi nebo oblast jako výchozí, můžete ji navrhnout a zapsat, aby ji bylo možné snadno rozšířit na uživatele v jiných jazykových verzích nebo oblastech.

Jako vývojáři máme všechny předpoklady o uživatelských rozhraních a datech, která jsou vytvořená v naší jazykové verzi. Například pro vývojáře v angličtině v USA serializace dat data a času jako řetězce ve formátu `MM/dd/yyyy hh:mm:ss` vypadá dokonale rozumným. Deserializace tohoto řetězce v systému v jiné jazykové verzi však může vyvolat výjimku <xref:System.FormatException> nebo vytvořit nepřesná data. Globalizace nám umožňuje identifikovat takové předpoklady specifické pro jazykovou verzi a zajistit, aby neovlivnily návrh nebo kód naší aplikace.

Tento článek popisuje některé hlavní problémy, které byste měli vzít v úvahu, a osvědčené postupy, které můžete sledovat při zpracování řetězců, hodnot data a času a číselných hodnot v globální aplikaci.

## <a name="strings"></a>Řetězce

Zpracování znaků a řetězců je centrální soustředění na globalizaci, protože každá jazyková verze nebo oblast může používat jiné znaky a znakové sady a řadit je odlišně. V této části najdete doporučení pro použití řetězců v globálních aplikacích.

### <a name="use-unicode-internally"></a>Interně používejte Unicode

Ve výchozím nastavení používá .NET řetězce Unicode. Řetězec Unicode se skládá z nuly, jednoho nebo více objektů @no__t 0, z nichž každý představuje jednotku kódu UTF-16. V každé znakové sadě, která se používá po celém světě, je reprezentace v kódování Unicode pro téměř každý znak.

Mnoho aplikací a operačních systémů, včetně operačního systému Windows, může použít také znakové stránky pro reprezentaci znakových sad. Znakové stránky obvykle obsahují standardní hodnoty ASCII od 0x00 do 0x7F a mapují jiné znaky na zbývající hodnoty od 0x80 do 0xFF. Interpretace hodnot od 0x80 do 0xFF závisí na konkrétní znakové stránce. Z tohoto důvodu byste se měli vyhnout použití znakových stránek v globální aplikaci, pokud je to možné.

Následující příklad znázorňuje nebezpečí interpretace dat znakové stránky, pokud je výchozí znaková stránka v systému odlišná od znakové stránky, na které byla data uložena. (Pro simulaci tohoto scénáře, příklad explicitně určuje různé znakové stránky.) Nejprve příklad definuje pole, které obsahuje velká písmena řecké abecedy. Zakóduje je do bajtového pole pomocí znakové stránky 737 (označované také jako MS-DOS řečtina) a ukládá pole bajtů do souboru. Pokud je soubor načten a jeho bajtové pole je dekódovat pomocí znakové stránky 737, původní znaky budou obnoveny. Pokud je však soubor načten a jeho bajtové pole je dekódovat pomocí znakové stránky 1252 (nebo Windows-1252, která představuje znaky v abecední abecedě), jsou původní znaky ztraceny.

[!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
[!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]

Použití kódování Unicode zajistí, že stejné jednotky kódu vždy budou namapovány na stejné znaky a že stejné znaky vždy budou namapovány na stejná Bajtová pole.

### <a name="use-resource-files"></a>Použití souborů prostředků

I když vyvíjíte aplikaci, která se zaměřuje na jednu jazykovou verzi nebo oblast, měli byste použít soubory prostředků k ukládání řetězců a dalších prostředků, které se zobrazí v uživatelském rozhraní. Nikdy byste je neměli přidávat přímo do kódu. Použití souborů prostředků má několik výhod:

- Všechny řetězce jsou v jednom umístění. Nemusíte hledat v celém zdrojovém kódu, abyste mohli identifikovat řetězce, které se mají upravit pro konkrétní jazyk nebo jazykovou verzi.

- Nemusíte duplikovat řetězce. Vývojáři, kteří nepoužívají soubory prostředků, často nadefinují stejný řetězec ve více souborech zdrojového kódu. Tato duplicita zvyšuje pravděpodobnost, že jedna nebo více instancí bude při úpravě řetězce přehledáno.

- Do souboru prostředků můžete zahrnout neřetězcové prostředky, jako jsou obrázky nebo binární data, místo jejich uložení do samostatného samostatného souboru, aby je bylo možné snadno načíst.

Použití souborů prostředků má zvláštní výhody, pokud vytváříte lokalizovanou aplikaci. Při nasazení prostředků do satelitních sestavení modul CLR (Common Language Runtime) automaticky vybere prostředek odpovídající jazykové verzi na základě aktuální jazykové verze uživatelského rozhraní, jak je definováno vlastností <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>. Pokud zadáte vhodný prostředek specifický pro jazykovou verzi a správně vytvoříte objekt <xref:System.Resources.ResourceManager> nebo používáte třídu prostředků se silnými typy, modul runtime zpracuje podrobnosti o načítání příslušných prostředků.

Další informace o vytváření souborů prostředků najdete v tématu [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Informace o vytváření a nasazování satelitních sestavení naleznete v tématu [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) a [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

### <a name="search-and-compare-strings"></a>Hledat a porovnat řetězce

Kdykoli je to možné, byste měli zpracovávat řetězce jako celé řetězce místo jejich zpracování jako řady jednotlivých znaků. To je obzvláště důležité při řazení nebo hledání podřetězců, aby nedocházelo k problémům spojeným s analýzou kombinovaných znaků.

> [!TIP]
> Třídu <xref:System.Globalization.StringInfo> lze použít pro práci s textovými prvky namísto jednotlivých znaků v řetězci.

V případě vyhledávání a porovnávání řetězců je běžné omylem zacházet s řetězcem jako s kolekcí znaků, z nichž každý je reprezentován objektem <xref:System.Char>. Ve skutečnosti může být jeden znak tvořen jedním, dvěma nebo více objekty @no__t 0. Tyto znaky se nejčastěji nacházejí v řetězcích z kultur, jejichž abecedy se skládají z znaků mimo rozsah znaků Latinské úrovně Basic v kódování Unicode (U + 0021 až U + 007E). Následující příklad se pokusí najít index pro velké písmeno latinky A s ČÁRKou (U + 00C0) v řetězci. Tento znak však může být reprezentován dvěma různými způsoby: jako jediná jednotka kódu (U + 00C0) nebo jako složený znak (dvě jednotky kódu: U + 0021 a U + 007E). V tomto případě je znak reprezentován v instanci řetězce pomocí dvou objektů <xref:System.Char>, U + 0021 a U + 007E. Vzorový kód volá přetížení <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> a <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> k nalezení pozice tohoto znaku v instanci řetězce, ale vrátí různé výsledky. První volání metody má argument <xref:System.Char>; provede ordinální porovnávání, a proto nemůže najít shodu. Druhé volání má argument <xref:System.String>; provádí porovnání zohledňující jazykovou verzi, a proto najde shodu.

[!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
[!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]

Můžete se vyhnout některé z nejednoznačnosti tohoto příkladu (volání dvou podobných přetížení metody vracející různé výsledky) voláním přetížení, které zahrnuje parametr <xref:System.StringComparison>, například metodou <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> nebo <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType>.

Hledání však nejsou vždy závislá na jazykové verzi. Pokud účelem hledání je učinit rozhodnutí zabezpečení nebo povolit nebo zakázat přístup k některému prostředku, porovnání by mělo být ordinální, jak je popsáno v následující části.

### <a name="test-strings-for-equality"></a>Testovací řetězce pro rovnost

Pokud chcete otestovat rovnost dvou řetězců namísto určení způsobu jejich porovnání v pořadí řazení, použijte metodu <xref:System.String.Equals%2A?displayProperty=nameWithType> namísto metody porovnávání řetězců, jako je například <xref:System.String.Compare%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.

Porovnání rovnosti se obvykle provádí pro podmíněné přístup k určitému prostředku. Můžete například provést porovnání rovnosti a ověřit heslo nebo potvrdit, že soubor existuje. Taková nelingvistická porovnání by měla být vždy pořadová a nikoli citlivá na jazykovou verzi. Obecně byste měli volat instanci @no__t 0 nebo statickou metodu <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> s hodnotou <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> pro řetězce, jako jsou hesla a hodnota <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro řetězce, jako jsou názvy souborů nebo identifikátory URI.

Porovnání rovnosti někdy zahrnuje hledání nebo porovnávání podřetězců, nikoli volání metody <xref:System.String.Equals%2A?displayProperty=nameWithType>. V některých případech můžete použít hledání podřetězce k určení, zda se tento dílčí řetězec rovná jinému řetězci. Pokud účelem tohoto porovnání je nelingvistické, hledání by mělo být také ordinální místo, nikoli citlivé na jazykovou verzi.

Následující příklad ilustruje nebezpečí vyhledávání zohledňující jazykovou verzi v nelingvistických datech. Metoda `AccessesFileSystem` je navržena tak, aby zakázala přístup k systému souborů pro identifikátory URI, které začínají podřetězcem "FILE". Za tímto účelem provede porovnání bez rozlišení velkých a malých písmen od začátku identifikátoru URI s řetězcem "FILE". Vzhledem k tomu, že identifikátor URI, který přistupuje k systému souborů, může začínat znakem "FILE:" nebo "File:", implicitní předpokládáme, že "i" (U + 0069) je vždy malým ekvivalentem "I" (U + 0049). V turečtině a Ázerbájdžánština se však používá velká a malá písmena i verze i (U + 0130). Z důvodu této nesrovnalosti umožňuje porovnání zohledňující jazykovou verzi přístup k systému souborů, pokud by měl být zakázán.

[!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
[!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]

Tomuto problému se lze vyhnout prováděním pořadového porovnání, které ignoruje velikost písmen, jak ukazuje následující příklad.

[!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
[!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]

### <a name="order-and-sort-strings"></a>Pořadí a řazení řetězců

Běžně seřazené řetězce, které se mají zobrazit v uživatelském rozhraní, by měly být seřazeny na základě jazykové verze. Ve většině případů se takové porovnávání řetězců zpracovává implicitně .NET při volání metody, která seřadí řetězce, například <xref:System.Array.Sort%2A?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Ve výchozím nastavení jsou řetězce seřazeny pomocí konvencí řazení aktuální jazykové verze. Následující příklad ukazuje rozdíl v případě, že je pole řetězců seřazeno pomocí konvencí jazykové verze Angličtina (USA) a švédské jazykové verze (Švédsko).

[!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
[!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]

Porovnání řetězců závislé na jazykové verzi je definováno objektem @no__t 0, který je vrácen vlastností <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> každé jazykové verze. Porovnávání řetězců závislé na jazykové verzi, které používá přetížení metody <xref:System.String.Compare%2A?displayProperty=nameWithType>, také používá objekt <xref:System.Globalization.CompareInfo>.

Rozhraní .NET používá tabulky k provádění řazení zohledňující jazykovou verzi podle řetězcových dat. Obsah těchto tabulek, které obsahují data o váhu řazení a normalizaci řetězců, je určen verzí standardu Unicode implementovaného určitou verzí rozhraní .NET. V následující tabulce jsou uvedeny verze sady Unicode implementované specifikovanými verzemi .NET Framework a .NET Core. Všimněte si, že tento seznam podporovaných verzí Unicode se vztahuje pouze na porovnání znaků a řazení; netýká se klasifikace znaků Unicode podle kategorií. Další informace najdete v části "řetězce a Standard Unicode" v článku <xref:System.String>.

|Verze rozhraní .NET Framework|Operační systém|Verze Unicode|
|----------------------------|----------------------|---------------------|
|.NET Framework 2.0|Všechny operační systémy|Unicode 4,1|
|.NET Framework 3.0|Všechny operační systémy|Unicode 4,1|
|.NET Framework 3.5|Všechny operační systémy|Unicode 4,1|
|.NET Framework 4|Všechny operační systémy|Unicode 5,0|
|.NET Framework 4,5 a novější ve Windows 7|Unicode 5,0|
|.NET Framework 4,5 a novější ve Windows 8 a novějších operačních systémech|6\.3.0 Unicode|
|.NET core (všechny verze)|Závisí na verzi standardu Unicode, kterou podporuje základní operační systém.|

Počínaje .NET Framework 4,5 a ve všech verzích .NET Core je porovnávání a řazení řetězců závislé na operačním systému. .NET Framework 4,5 a novější verze spuštěné v systému Windows 7 načte data z vlastních tabulek, které implementují Unicode 5,0. .NET Framework 4,5 a novější verze spuštěné v systému Windows 8 a novějších načte data z tabulek operačního systému, které implementují Unicode 6,3. V .NET Core závisí podporovaná verze Unicode na podkladovém operačním systému. Pokud jste serializováni Setříděná data závislá na jazykové verzi, můžete použít třídu <xref:System.Globalization.SortVersion> k určení, kdy musí být Serializovaná data řazena, aby byla konzistentní s rozhraním .NET a pořadím řazení operačního systému. Příklad naleznete v tématu třídy <xref:System.Globalization.SortVersion>.

Pokud vaše aplikace provádí rozsáhlou škálu řetězcových dat specifických pro jazykovou verzi, můžete pracovat s třídou <xref:System.Globalization.SortKey> pro porovnávání řetězců. Klíč řazení odráží váhu řazení specifickou pro jazykovou verzi, včetně závaží abecedy, písmen a diakritiky určitého řetězce. Vzhledem k tomu, že porovnání pomocí klíčů řazení jsou binární, jsou rychlejší než porovnání, které používají objekt <xref:System.Globalization.CompareInfo> implicitně nebo explicitně. Můžete vytvořit klíč řazení specifický pro jazykovou verzi pro konkrétní řetězec předáním řetězce metodě <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType>.

Následující příklad je podobný předchozímu příkladu. Nicméně namísto volání metody <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType>, která implicitně volá metodu <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>, definuje implementaci <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>, která porovnává klíče řazení, které vytváří instance a předává do metody <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
[!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]

### <a name="avoid-string-concatenation"></a>Vyhnout se zřetězení řetězců

Pokud je to možné, nepoužívejte složené řetězce, které jsou vytvořeny v době běhu ze zřetězených frází. Složené řetězce je obtížné lokalizovat, protože často předpokládají gramatické pořadí v původním jazyce aplikace, které neplatí pro jiné lokalizované jazyky.

## <a name="handle-dates-and-times"></a>Zpracování dat a časů

Způsob zpracování hodnot data a času závisí na tom, zda jsou zobrazeny v uživatelském rozhraní nebo trvale. V této části jsou zkontrolována obě použití. Také popisuje, jak můžete zpracovávat rozdíly v časových pásmech a aritmetické operace při práci s daty a časy.

### <a name="display-dates-and-times"></a>Zobrazit data a časy

Pokud jsou data a časy zobrazeny v uživatelském rozhraní, měli byste použít konvence formátování jazykové verze uživatele, která je definována vlastností <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> a objektem <xref:System.Globalization.DateTimeFormatInfo> vráceným vlastností `CultureInfo.CurrentCulture.DateTimeFormat`. Konvence formátování aktuální jazykové verze se automaticky použijí, když formátujete datum pomocí některé z těchto metod:

- Metoda bez parametrů @no__t 0

- Metoda <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, která obsahuje formátovací řetězec

- Metoda bez parametrů @no__t 0

- @No__t-0, který obsahuje formátovací řetězec

- Funkce [složeného formátování](../../../docs/standard/base-types/composite-formatting.md) , když se používá s kalendářními daty

Následující příklad zobrazuje data slunce a slunce dvakrát z 11. října 2012. Nejprve nastaví aktuální jazykovou verzi na chorvatština (Chorvatsko) a pak na angličtinu (Velká Británie). V každém případě jsou data a časy zobrazeny ve formátu, který je vhodný pro danou jazykovou verzi.

[!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
[!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]

### <a name="persist-dates-and-times"></a>Zachovat data a časy

Nikdy byste neměli zachovat data data a času ve formátu, který se může lišit podle jazykové verze. Jedná se o běžnou chybu programování, která má za následek poškozená data nebo výjimku za běhu. Následující příklad serializace dvě data, 9. ledna 2013 a 18. srpna 2013 jako řetězce pomocí formátovacích úmluv jazykové verze Angličtina (USA). Když jsou data načtena a analyzována pomocí konvencí jazykové verze anglické (USA), je úspěšně obnovena. Pokud je však načten a analyzován pomocí konvencí jazykové verze Angličtina (Spojené království), je první datum nesprávně interpretováno jako 1. září a druhý nedokáže analyzovat, protože gregoriánský kalendář nemá osmnáct měsíc.

[!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
[!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]

Tomuto problému se můžete vyhnout některým ze tří způsobů:

- Serializovat datum a čas v binárním formátu, nikoli jako řetězec.

- Uložte a analyzujte řetězcovou reprezentaci data a času pomocí vlastního formátovacího řetězce, který je stejný bez ohledu na jazykovou verzi uživatele.

- Uložte řetězec pomocí formátovacích konvencí invariantní jazykové verze.

Následující příklad ukazuje poslední přístup. Používá konvence formátování invariantní jazykové verze vrácené vlastností static <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
[!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]

### <a name="serialization-and-time-zone-awareness"></a>Serializace a povědomí o časovém pásmu

Hodnota data a času může mít několik výkladů v rozsahu od obecné doby ("obchody otevřené od 2. ledna 2013, v 9:00 ráno") k určitému časovému okamžiku ("datum narození: 2. ledna 2013 6:32:00 dop. "). Pokud časová hodnota představuje konkrétní moment v čase a Vy ji obnovíte ze serializované hodnoty, měli byste zajistit, aby to představovalo stejný okamžik v čase bez ohledu na zeměpisnou polohu nebo časové pásmo uživatele.

Následující příklad ukazuje tento problém. Ukládá jednu hodnotu místního data a času jako řetězec ve třech [standardních formátech](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ("G" pro obecné datum, dlouhý čas, "s" pro řazení data a času a "o" pro datum a čas Round-Trip) a také v binárním formátu.

[!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
[!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]

Když se data obnoví v systému ve stejném časovém pásmu jako systém, na kterém byla serializovaná, deserializované hodnoty data a času přesně odrážejí původní hodnotu, jak ukazuje výstup:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local

3/30/2013 6:00:00 PM Local
```

Pokud však obnovíte data v systému v jiném časovém pásmu, pouze hodnota datum a čas, která byla naformátována pomocí standardního formátovacího řetězce "o" (round-trip), zachovává informace o časovém pásmu a proto představuje stejné okamžité v čase. Zde je výstup, když jsou data a čas obnovena v systému v normálním časovém pásmu románské země:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local

3/30/2013 6:00:00 PM Local
```

Chcete-li přesně odrážet hodnotu data a času, která představuje jediný časový okamžik bez ohledu na časové pásmo systému, ve kterém jsou data deserializována, můžete provést následující akce:

- Uložte hodnotu jako řetězec pomocí standardního formátovacího řetězce "o" (round-trip). Pak ho deserializovat v cílovém systému.

- Převeďte ji na čas UTC a uložte ji jako řetězec pomocí standardního formátovacího řetězce "r" (RFC1123). Pak ho deserializovat v cílovém systému a převeďte na místní čas.

- Převeďte ji na čas UTC a uložte ji jako řetězec pomocí standardního formátovacího řetězce "u" (universald). Pak ho deserializovat v cílovém systému a převeďte na místní čas.

- Převeďte ho na čas UTC a uložte ho v binárním formátu. Pak ho deserializovat v cílovém systému a převeďte na místní čas.

Následující příklad znázorňuje každou techniku.

[!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
[!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]

V případě, že jsou data serializována v systému v tichomořském časovém pásmu a v systému v normálním časovém pásmu, v tomto příkladu se zobrazí následující výstup:

```console
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local

3/31/2013 3:00:00 AM Local
```

Další informace najdete v tématu [Převod časů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).

### <a name="perform-date-and-time-arithmetic"></a>Provést aritmetické operace s datem a časem

Typy <xref:System.DateTime> i <xref:System.DateTimeOffset> podporují aritmetické operace. Rozdíl mezi dvěma hodnotami data můžete vypočítat nebo můžete přidat nebo odebrat konkrétní časové intervaly do nebo z hodnoty data. Aritmetické operace s hodnotami data a času však nevezmou časová pásma a pravidla upravující časová pásma v účtu. Z toho důvodu aritmetické operace s hodnotami data a času, které reprezentují časový okamžik, můžou vracet nepřesné výsledky.

Například přechod z tichomořského Tichomoří (běžný čas) do Tichomoří (letní čas) se vyskytuje v druhé neděli v březnu, což je 10. března v roce 2013. Jak ukazuje následující příklad, pokud vypočítáte datum a čas, který je 48 hodin po 9. března 2013 při 10:30. v systému v tichomořském časovém pásmu, výsledek, 11. března 2013 v 10:30 ráno, nebere v úvahu úpravu v daném čase.

[!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
[!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]

Chcete-li zajistit, že aritmetické operace s hodnotami data a času vytváří přesné výsledky, postupujte podle těchto kroků:

1. Převede čas v časovém pásmu zdroje na čas UTC.

2. Proveďte aritmetickou operaci.

3. Pokud je výsledkem hodnota data a času, převeďte ji z času UTC na čas v časovém pásmu zdroje.

Následující příklad je podobný předchozímu příkladu s tím rozdílem, že se podle těchto tří kroků správně přidá 48 hodin do 9. března 2013 při 10:30.

[!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
[!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]

Další informace najdete v tématu [provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md).

### <a name="use-culture-sensitive-names-for-date-elements"></a>Použití názvů závislých na jazykové verzi pro prvky data

Vaše aplikace může potřebovat zobrazit název měsíce nebo den v týdnu. V takovém případě jsou běžné následující kódy:

[!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
[!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]

Tento kód však vždy vrátí názvy dnů v týdnu v angličtině. Kód, který extrahuje název měsíce, je často ještě více flexibilní. Často se předpokládá 12měsíční kalendář s názvy měsíců v konkrétním jazyce.

Pomocí [vlastních formátovacích řetězců pro datum a čas](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) nebo vlastností objektu <xref:System.Globalization.DateTimeFormatInfo> lze snadno extrahovat řetězce, které odráží názvy dnů v týdnu nebo měsíců v jazykové verzi uživatele, jak ukazuje následující příklad. Změní aktuální jazykovou verzi na francouzština (Francie) a zobrazí název dne v týdnu a název měsíce od 1. července 2013.

[!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
[!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]

## <a name="numeric-values"></a>Číselné hodnoty

Manipulace s čísly závisí na tom, zda jsou zobrazeny v uživatelském rozhraní nebo trvale. V této části jsou zkontrolována obě použití.

> [!NOTE]
> V rámci operací analýzy a formátování rozpoznává .NET pouze základní znaky latinky 0 až 9 (U + 0030 až U + 0039) jako číselné číslice.

### <a name="display-numeric-values"></a>Zobrazit číselné hodnoty

Při zobrazení čísel v uživatelském rozhraní byste obvykle měli použít konvence formátování jazykové verze uživatele, která je definována vlastností <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> a objektem <xref:System.Globalization.NumberFormatInfo> vrácenou vlastností `CultureInfo.CurrentCulture.NumberFormat`. Konvence formátování aktuální jazykové verze se automaticky použijí, když formátujete datum pomocí některé z následujících metod:

- Metoda bez parametrů @no__t 0 libovolného číselného typu

- Metoda `ToString(String)` libovolného číselného typu, který zahrnuje formátovací řetězec jako argument

- Funkce [složeného formátování](../../../docs/standard/base-types/composite-formatting.md) , když se používá s číselnými hodnotami

Následující příklad zobrazuje průměrnou teplotu za měsíc v Paříži, Francii. Před zobrazením dat nejprve nastaví aktuální jazykovou verzi na francouzština (Francie) a pak ji nastaví na angličtinu (USA). V každém případě jsou názvy měsíců a teploty zobrazeny ve formátu, který je vhodný pro danou jazykovou verzi. Všimněte si, že obě jazykové verze používají jiné oddělovače desetinných míst v hodnotě teploty. Všimněte si také, že v příkladu se používá vlastní řetězec formátu data a času "MMMM" k zobrazení úplného názvu měsíce a který přiděluje příslušné množství místa pro název měsíce ve výsledném řetězci určením délky názvu nejdelšího měsíce v <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> ar. paprsek.

[!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
[!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]

### <a name="persist-numeric-values"></a>Zachovat číselné hodnoty

Nikdy byste neměli zachovat číselná data ve formátu specifickém pro jazykovou verzi. Jedná se o běžnou chybu programování, která má za následek poškozená data nebo výjimku za běhu. Následující příklad generuje deset náhodných čísel s plovoucí desetinnou čárkou a poté je serializován jako řetězce pomocí formátovacích úmluv jazykové verze Angličtina (USA). Když jsou data načtena a analyzována pomocí konvencí jazykové verze anglické (USA), je úspěšně obnovena. Nicméně pokud je načten a analyzován pomocí konvencí francouzské jazykové verze (Francie), nelze analyzovat žádné číslo, protože jazykové verze používají jiné oddělovače desetinných míst.

[!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
[!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]

Chcete-li se tomuto problému vyhnout, můžete použít jeden z následujících postupů:

- Uložte a analyzujte řetězcovou reprezentaci čísla pomocí vlastního formátovacího řetězce, který je stejný bez ohledu na jazykovou verzi uživatele.

- Uložte číslo jako řetězec pomocí formátovacích konvencí invariantní jazykové verze, který je vrácen vlastností <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Serializovat číslo v binárním souboru namísto formátu řetězce.

Následující příklad ukazuje poslední přístup. Serializace pole hodnot <xref:System.Double> a pak je deserializace a zobrazí pomocí formátovacích úmluv jazykových verzí angličtina (USA) a francouzština (Francie).

[!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
[!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]

Serializace hodnot měny je zvláštní případ. Vzhledem k tomu, že hodnota měny závisí na jednotce měny, ve které je vyjádřena; nedoporučujeme ho považovat za nezávislou číselnou hodnotu. Pokud však uložíte hodnotu měny jako formátovaný řetězec, který obsahuje symbol měny, nelze jej deserializovat v systému, jehož výchozí jazyková verze používá jiný symbol měny, jak ukazuje následující příklad.

[!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
[!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]

Místo toho byste měli serializovat číselnou hodnotu společně s některými kulturními informacemi, jako je název jazykové verze, aby hodnota a její symbol měny mohli být deserializovány nezávisle na aktuální jazykové verzi. Následující příklad provede definováním struktury `CurrencyValue` se dvěma členy: hodnotou <xref:System.Decimal> a názvem jazykové verze, do které hodnota patří.

[!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
[!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]

## <a name="work-with-culture-specific-settings"></a>Práce s nastaveními specifickými pro jazykovou verzi

V rozhraní .NET třída <xref:System.Globalization.CultureInfo> představuje konkrétní jazykovou verzi nebo oblast. Některé vlastnosti vrátí objekty, které poskytují konkrétní informace o některém aspektu jazykové verze:

- Vlastnost <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> vrátí objekt <xref:System.Globalization.CompareInfo>, který obsahuje informace o tom, jak jazyková verze porovnává a seřadí řetězce.

- Vlastnost <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vrátí objekt <xref:System.Globalization.DateTimeFormatInfo>, který poskytuje informace specifické pro jazykovou verzi používané při formátování data a času.

- Vlastnost <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> vrátí objekt <xref:System.Globalization.NumberFormatInfo>, který poskytuje informace specifické pro jazykovou verzi používané při formátování číselných dat.

- Vlastnost <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> vrátí objekt <xref:System.Globalization.TextInfo>, který poskytuje informace o systému zápisu jazykové verze.

Obecně neprovádějte žádné předpoklady o hodnotách specifických vlastností <xref:System.Globalization.CultureInfo> a jejich souvisejících objektů. Místo toho byste měli zobrazit data specifická pro jazykovou verzi, která se mohou změnit, z těchto důvodů:

- Jednotlivé hodnoty vlastností se mohou měnit a revisionovat v průběhu času, protože data jsou opravena, lepší data jsou k dispozici nebo se změní konvence specifické pro jazykovou verzi.

- Jednotlivé hodnoty vlastností se můžou v různých verzích .NET nebo verzích operačních systémů lišit.

- Rozhraní .NET podporuje náhradní kultury. Díky tomu je možné definovat novou vlastní jazykovou verzi, která buď doplňuje stávající standardní jazykové verze, nebo zcela nahradí stávající standardní jazykovou verzi.

- V systémech Windows může uživatel přizpůsobit nastavení specifické pro jazykovou verzi pomocí aplikace **oblast a jazyk** v Ovládacích panelech. Když vytváříte instanci objektu <xref:System.Globalization.CultureInfo>, můžete určit, zda odráží tyto vlastní uživatelské přizpůsobení voláním konstruktoru <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>. Pro aplikace pro koncové uživatele byste obvykle měli respektovat uživatelské preference, takže se uživateli zobrazí data ve formátu, který očekává.

## <a name="see-also"></a>Viz také:

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Doporučené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md)
