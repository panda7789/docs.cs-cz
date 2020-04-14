---
title: Použití tříd kódování znaků v rozhraní .NET
description: Přečtěte si, jak používat třídy kódování znaků v rozhraní .NET.
ms.date: 12/22/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoding, understanding
- encoding, choosing
- encoding, fallback strategy
ms.assetid: bf6d9823-4c2d-48af-b280-919c5af66ae9
ms.openlocfilehash: 1a294a577d10b3e621871b168344f2b0610693dd
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242735"
---
# <a name="how-to-use-character-encoding-classes-in-net"></a>Použití tříd kódování znaků v rozhraní .NET

Tento článek vysvětluje, jak používat třídy, které rozhraní .NET poskytuje kódování a dekódování textu pomocí různých schémat kódování. Pokyny předpokládají, že jste si přečetli [Úvod do kódování znaků v rozhraní .NET](character-encoding-introduction.md).

## <a name="encoders-and-decoders"></a>Kodéry a dekodéry

Rozhraní .NET poskytuje kódování tříd, které kódují a dekódují text pomocí různých kódovacích systémů. <xref:System.Text.UTF8Encoding> Například třída popisuje pravidla pro kódování a dekódování z UTF-8. Rozhraní .NET používá kódování UTF-16 <xref:System.Text.UnicodeEncoding> (reprezentované třídou) pro `string` instance. Kodéry a dekodéry jsou k dispozici pro další schémata kódování.

Kódování a dekódování může také zahrnovat ověření. Například <xref:System.Text.UnicodeEncoding> třída kontroluje `char` všechny instance v oblasti náhradní, abyste se ujistili, že jsou v platných náhradních párech. Záložní strategie určuje, jak kodér zpracovává neplatné znaky nebo jak dekodér zpracovává neplatné bajty.

> [!WARNING]
> Třídy kódování .NET poskytují způsob ukládání a převodu dat znaků. Neměly by být použity k ukládání binárních dat ve formě řetězce. V závislosti na použitém kódování může převod binárních dat do formátu řetězce s třídami kódování zavést neočekávané chování a vytvořit nepřesná nebo poškozená data. Chcete-li převést binární data <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> na řetězec formuláře, použijte metodu.

Všechny třídy kódování znaků v <xref:System.Text.Encoding?displayProperty=nameWithType> rozhraní .NET dědí z třídy, což je abstraktní třída, která definuje funkce společné pro všechna kódování znaků. Chcete-li získat přístup k jednotlivým objektům kódování implementovaným v rozhraní .NET, postupujte takto:

- Použijte statické vlastnosti <xref:System.Text.Encoding> třídy, které vracejí objekty, které představují standardní kódování znaků, které jsou k dispozici v rozhraní .NET (ASCII, UTF-7, UTF-8, UTF-16 a UTF-32). Například <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> vlastnost vrátí <xref:System.Text.UnicodeEncoding> objekt. Každý objekt používá náhradní záložní ke zpracování řetězců, které nelze zakódovat a bajtů, které nelze dekódovat. Další informace naleznete v tématu [Náhradní záložní](../../../docs/standard/base-types/character-encoding.md#Replacement).

- Volání konstruktoru třídy kódování. Objekty pro kódování ASCII, UTF-7, UTF-8, UTF-16 a UTF-32 lze vytvořit instanci tímto způsobem. Ve výchozím nastavení každý objekt používá náhradní záložní pro zpracování řetězců, které nelze zakódovat a bajtů, které nelze dekódovat, ale můžete určit, že by měla být vyvolána výjimka místo. Další informace naleznete v [tématech Náhradní záložní](../../../docs/standard/base-types/character-encoding.md#Replacement) a [výjimka záložní](../../../docs/standard/base-types/character-encoding.md#Exception).

- Volání <xref:System.Text.Encoding.%23ctor%28System.Int32%29> konstruktoru a předat celé číslo, které představuje kódování. Standardní kódování objekty používají náhradní záložní a znakové stránky a dvoubajtové znakové sady (DBCS) kódování objektů použít nejvhodnější záložní pro zpracování řetězců, které nemohou kódovat a bajty, které nemohou dekódovat. Další informace naleznete v tématu [Best-fit fallback](../../../docs/standard/base-types/character-encoding.md#BestFit).

- Volání <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metody, která vrací všechny standardní, znakové stránky nebo kódování DBCS k dispozici v rozhraní .NET. Přetížení umožňují určit záložní objekt pro kodér i dekodér.

Informace o všech kódováních dostupných v rozhraní .NET můžete načíst voláním <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> metody. Rozhraní .NET podporuje schémata kódování znaků uvedená v následující tabulce.

|Třída kódování|Popis|
|--------------|-----------|
|[Ascii](xref:System.Text.ASCIIEncoding)|Zakóduje omezený rozsah znaků pomocí dolních sedmi bitů bajtu. Vzhledem k tomu, že toto kódování podporuje pouze hodnoty znaků od U + 0000 až U + 007F, ve většině případů je nedostatečná pro internacionalizované aplikace.|
|[UTF-7](xref:System.Text.UTF7Encoding)|Představuje znaky jako sekvence 7bitových znaků ASCII. Znaky Unicode, které nejsou součástí ASCII, jsou reprezentovány řídicí sekvencí znaků ASCII. UTF-7 podporuje protokoly, jako je e-mail a diskusní skupina. UTF-7 však není příliš bezpečný nebo robustní. V některých případech může změna jednoho bitu radikálně změnit interpretaci celého řetězce UTF-7. V ostatních případech mohou různé řetězce UTF-7 kódovat stejný text. Pro sekvence, které obsahují znaky bez ASCII, UTF-7 vyžaduje více místa než UTF-8 a kódování/dekódování je pomalejší. V důsledku toho byste měli použít UTF-8 namísto UTF-7, pokud je to možné.|
|[UTF-8](xref:System.Text.UTF8Encoding)|Představuje každý bod kódu Unicode jako posloupnost jednoho až čtyř bajtů. UTF-8 podporuje velikosti 8bitových dat a dobře spolupracuje s mnoha stávajícími operačními systémy. Pro rozsah znaků ASCII je UTF-8 shodný s kódováním ASCII a umožňuje širší sadu znaků. Pro skripty CJK čínština a japonština (CJK) však může UTF-8 vyžadovat tři bajty pro každý znak a může způsobit větší velikosti dat než UTF-16. Někdy množství dat ASCII, jako jsou značky HTML, odůvodňuje zvětšenou velikost rozsahu CJK.|
|[UTF-16](xref:System.Text.UnicodeEncoding)|Představuje každý bod kódu Unicode jako posloupnost jednoho nebo dvou 16bitových čísel. Nejběžnější znaky Unicode vyžadují pouze jeden bod kódu UTF-16, ačkoli doplňkové znaky Unicode (U + 10000 a vyšší) vyžadují dva body náhradního kódu UTF-16. Jsou podporovány objednávky bajtů little-endian i big-endian. Kódování UTF-16 používá běžný jazyk runtime <xref:System.Char> k <xref:System.String> reprezentaci a hodnotám a používá `WCHAR` se operačním systémem Windows k reprezentaci hodnot.|
|[UTF-32](xref:System.Text.UTF32Encoding)|Představuje každý bod kódu Unicode jako 32bitové celé číslo. Jsou podporovány objednávky bajtů little-endian i big-endian. Kódování UTF-32 se používá, když se aplikace chtějí vyhnout chování náhradního bodu kódu kódování UTF-16 v operačních systémech, pro které je kódovaný prostor příliš důležitý. Jednotlivé glyfy vykreslené na displeji mohou být stále kódovány více než jedním znakem UTF-32.|
|Kódování ANSI/ISO|Poskytuje podporu pro různé znakové stránky. V operačních systémech Windows se znakové stránky používají k podpoře určitého jazyka nebo skupiny jazyků. Tabulka se seznamem znakových stránek podporovaných <xref:System.Text.Encoding> rozhraním .NET naleznete v části Třída. Objekt kódování pro určitou znakovou stránku <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> můžete načíst voláním metody. Znaková stránka obsahuje 256 bodů kódu a je založen na nule. Ve většině znakových stránek představují body kódu 0 až 127 znakovou sadu ASCII a body kódu 128 až 255 se mezi znakovými stránkami výrazně liší. Například znaková stránka 1252 obsahuje znaky pro systémy psaní latinky, včetně angličtiny, němčiny a francouzštiny. Posledních 128 bodů kódu v znakové stránce 1252 obsahují znaky zvýraznění. Znaková stránka 1253 obsahuje kódy znaků, které jsou požadovány v řeckém systému zápisu. Posledních 128 bodů kódu v znakové stránce 1253 obsahuje řecké znaky. V důsledku toho aplikace, která spoléhá na znakové stránky ANSI nelze uložit řečtina a němčina ve stejném textovém proudu, pokud obsahuje identifikátor, který označuje odkazované znakové stránky.|
|Dvoubajtové znakové sady (DBCS)|Podporuje jazyky, jako je čínština, japonština a korejština, které obsahují více než 256 znaků. V DBCS dvojice bodů kódu (dvojitý bajt) představuje každý znak. Vlastnost <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> vrátí `false` kódování DBCS. Kódovací objekt pro konkrétní soubor DBCS můžete <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> načíst voláním metody. Když aplikace zpracovává data DBCS, první bajt znaku DBCS (úvodní bajt) je zpracován v kombinaci s bajtem trail, který bezprostředně následuje. Vzhledem k tomu, že jeden pár dvoubajtových bodů kódu může představovat různé znaky v závislosti na znakové stránce, toto schéma stále neumožňuje kombinaci dvou jazyků, například japonštiny a čínštiny, ve stejném datovém proudu.|

Tato kódování umožňují pracovat se znaky Unicode i s kódováními, která se nejčastěji používají ve starších aplikacích. Kromě toho můžete vytvořit vlastní kódování definováním třídy, <xref:System.Text.Encoding> která je odvozena od a přepsání majedly jeho členů.

## <a name="net-core-encoding-support"></a>Podpora kódování jádra .NET

Ve výchozím nastavení rozhraní .NET Core nezpřístupní žádné kódování znakové stránky než znaková stránka 28591 a kódování Unicode, například UTF-8 a UTF-16. Můžete však přidat kódování znakové stránky nalezené ve standardních aplikacích pro Windows, které cílí na rozhraní .NET do vaší aplikace. Další informace naleznete <xref:System.Text.CodePagesEncodingProvider> v tématu.

<a name="Selecting"></a>

## <a name="selecting-an-encoding-class"></a>Výběr třídy kódování

Pokud máte možnost zvolit kódování, které má být použito vaší aplikací, měli byste použít <xref:System.Text.UTF8Encoding> <xref:System.Text.UnicodeEncoding>kódování Unicode, nejlépe buď nebo . (.NET také podporuje třetí kódování <xref:System.Text.UTF32Encoding>Unicode, .)

Pokud plánujete použít kódování ASCII<xref:System.Text.ASCIIEncoding>( <xref:System.Text.UTF8Encoding> ), zvolte místo toho. Dvě kódování jsou shodná pro znakovou sadu <xref:System.Text.UTF8Encoding> ASCII, ale má následující výhody:

- Může představovat každý znak Unicode, zatímco <xref:System.Text.ASCIIEncoding> podporuje pouze hodnoty znaků Unicode mezi U + 0000 a U + 007F.

- Poskytuje detekci chyb a lepší zabezpečení.

- Byla vyladěna tak, aby byla co nejrychlejší a měla by být rychlejší než jakékoli jiné kódování. I pro obsah, který je zcela ASCII, operace prováděné s <xref:System.Text.UTF8Encoding> jsou rychlejší než operace prováděné s <xref:System.Text.ASCIIEncoding>.

Měli byste <xref:System.Text.ASCIIEncoding> zvážit použití pouze pro starší aplikace. Nicméně, i pro <xref:System.Text.UTF8Encoding> starší aplikace, může být lepší volbou z následujících důvodů (za předpokladu, že výchozí nastavení):

- Pokud vaše aplikace obsahuje obsah, který není striktně ASCII a kóduje ji <xref:System.Text.ASCIIEncoding>, každý znak bez ASCII kóduje jako otazník (?). Pokud aplikace pak dekóduje tato data, informace se ztratí.

- Pokud vaše aplikace obsahuje obsah, který není výhradně <xref:System.Text.UTF8Encoding>ASCII a kóduje s , výsledek se zdá nesrozumitelné, pokud interpretován jako ASCII. Pokud však aplikace používá dekodér UTF-8 k dekódování těchto dat, data úspěšně provede odezvu.

Ve webové aplikaci by znaky odeslané klientovi v reakci na webový požadavek měly odrážet kódování použité v klientovi. Ve většině případů byste <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> měli nastavit vlastnost na <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> hodnotu vrácenou vlastností, aby se zobrazil text v kódování, které uživatel očekává.

<a name="Using"></a>

## <a name="using-an-encoding-object"></a>Použití objektu kódování

Kodér převede řetězec znaků (nejčastěji znaky Unicode) na jeho číselný (bajtový) ekvivalent. Můžete například použít kodér ASCII k převodu znaků Unicode na ASCII, aby mohly být zobrazeny v konzole. Chcete-li provést převod, <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> volání metody. Pokud chcete zjistit, kolik bajtů je potřeba uložit kódované znaky před provedením kódování, můžete volat metodu. <xref:System.Text.Encoding.GetByteCount%2A>

Následující příklad používá jednobajtové pole ke kódování řetězců ve dvou samostatných operacích. Udržuje index, který označuje počáteční pozici v bajtovém poli pro další sadu bajtů kódovaných ascii. Volá metodu <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> k zajištění, že bajtové pole je dostatečně velký, aby se přizpůsobil kódovanému řetězci. Potom volá <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metodu pro kódování znaků v řetězci.

[!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
[!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]

Dekodér převede bajtové pole, které odráží určité kódování znaků, na sadu znaků, buď v poli znaků, nebo v řetězci. Chcete-li dekódovat bajtové pole do <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> pole znaků, zavolejte metodu. Chcete-li dekódovat bajtové pole <xref:System.Text.Encoding.GetString%2A> do řetězce, zavolejte metodu. Pokud chcete zjistit, kolik znaků je potřeba k uložení dekódovaných bajtů před provedením dekódování, můžete volat metodu. <xref:System.Text.Encoding.GetCharCount%2A>

Následující příklad kóduje tři řetězce a pak je dekóduje do jednoho pole znaků. Udržuje index, který označuje počáteční pozici v poli znaků pro další sadu dekódovaných znaků. Volá metodu, <xref:System.Text.ASCIIEncoding.GetCharCount%2A> která zajišťuje, že pole znaků je dostatečně velké, aby vyhovovalo všem dekódovaním znakům. Potom volá <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metodu dekódování bajtového pole.

[!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
[!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]

Metody kódování a dekódování třídy odvozené z <xref:System.Text.Encoding> třídy jsou navrženy tak, aby fungovaly na kompletní sadě dat; to znamená, že všechna data, která mají být kódována nebo dekódována, jsou dodávána v volání jedné metody. V některých případech jsou však data k dispozici v datovém proudu a data, která mají být kódována nebo dekódována, mohou být k dispozici pouze ze samostatných operací čtení. To vyžaduje, aby si operace kódování nebo dekódování pamatovala jakýkoli uložený stav z předchozího vyvolání. Metody tříd odvozené <xref:System.Text.Encoder> <xref:System.Text.Decoder> z a jsou schopny zpracovat kódování a dekódování operace, které pokrývají více volání metody.

Objekt <xref:System.Text.Encoder> pro konkrétní kódování je k dispozici z <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> této vlastnosti kódování. Objekt <xref:System.Text.Decoder> pro konkrétní kódování je k dispozici z <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> této vlastnosti kódování. Pro dekódování operace, všimněte <xref:System.Text.Decoder> si, <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> že třídy odvozené z zahrnují <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>metodu, ale nemají metodu, která odpovídá .

Následující příklad ilustruje rozdíl mezi <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> použitím <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metody a pro dekódování bajtového pole Unicode. Příklad zakóduje řetězec, který obsahuje některé znaky Unicode do souboru, a potom použije dvě metody dekódování k dekódování najednou. Vzhledem k tomu, že náhradní pár se vyskytuje v desátém a jedenáctém bajtu, je dekódován v samostatných voláních metod. Jak ukazuje výstup, <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metoda není schopna správně dekódovat bajty a místo toho je nahradí U + FFFD (NÁHRADNÍ ZNAK). Na druhou stranu <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metoda je schopna úspěšně dekódovat bajtové pole získat původní řetězec.

[!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
[!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]

<a name="FallbackStrategy"></a>

## <a name="choosing-a-fallback-strategy"></a>Výběr záložní strategie

Když se metoda pokusí zakódovat nebo dekódovat znak, ale neexistuje žádné mapování, musí implementovat záložní strategii, která určuje, jak by mělo být zpracováno mapování, které selhalo. Existují tři typy záložních strategií:

- Nejvhodnější záložní

- Náhradní záložní

- Záložní výjimka

> [!IMPORTANT]
> K nejčastějším problémům při operacích kódování dochází, když znak Unicode nelze namapovat na kódování určité znakové stránky. K nejčastějším problémům při dekódování dochází v případě, že neplatné bajtové sekvence nelze přeložit do platných znaků Unicode. Z těchto důvodů byste měli vědět, kterou záložní strategii konkrétní kódovací objekt používá. Kdykoli je to možné, měli byste určit záložní strategii používanou objektem kódování při vytváření instancí objektu.

<a name="BestFit"></a>

### <a name="best-fit-fallback"></a>Nejvhodnější záložní

Pokud znak nemá přesnou shodu v cílovém kódování, kodér se může pokusit mapovat na podobný znak. (Nejvhodnější záložní je většinou kódování spíše než problém dekódování. Existuje velmi málo znakové stránky, které obsahují znaky, které nelze úspěšně mapovat na Unicode.) Nejvhodnější záložní je výchozí pro kódovou stránku a dvoubajtové kódování znakové <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> sady, které jsou načteny a přetížení.

> [!NOTE]
> Teoreticky podporují třídy kódování Unicode v<xref:System.Text.UTF8Encoding>rozhraní <xref:System.Text.UnicodeEncoding>.NET ( , , a <xref:System.Text.UTF32Encoding>) každý znak v každé znakové sadě, takže je lze použít k odstranění problémů s návrhem záložního nastavení.

Strategie přizpůsobení se u různých znakových stránek liší. Například u některých znakových stránek se znaky latinky s plnou šířkou mapují na běžnější znaky latinky s poloviční šířkou. Pro jiné znakové stránky toto mapování není provedeno. Dokonce i v rámci agresivní strategie best-fit, není představitelné vhodné pro některé znaky v některých kódování. Například čínský ideograf nemá žádné přiměřené mapování na znakovou stránku 1252. V tomto případě se použije náhradní řetězec. Ve výchozím nastavení je tento řetězec pouze jeden otazník (U + 003F).

> [!NOTE]
> Strategie přizpůsobení nejsou podrobně popsány. Několik znakových stránek je však dokumentováno na webu [konsorcia Unicode Consortium.](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) Zkontrolujte soubor **readme.txt** v této složce, kde naleznete popis interpretace mapových souborů.

Následující příklad používá znakovou stránku 1252 (kódová stránka systému Windows pro jazyky západní Evropy) pro ilustraci nejvhodnějšímapování a jeho nevýhody. Metoda <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> se používá k načtení objektu kódování pro znakovou stránku 1252. Ve výchozím nastavení používá nejvhodnější mapování znaků Unicode, které nepodporuje. Příklad vytvoří instance řetězce, který obsahuje tři znaky bez ASCII - v kroužku latinka velké písmeno S (U + 24C8), SUPERSCRIPT PĚT (U + 2075) a INFINITY (U + 221E) - oddělené mezery. Jak ukazuje výstup z příkladu, když je řetězec kódován, tři původní nemezerové znaky jsou nahrazeny otazníkem (U + 003F), číslicí pět (U + 0035) a číslicí osm (U + 0038). ČÍSLICE OSM je obzvláště špatná náhrada za nepodporovaný znak INFINITY a otazník označuje, že pro původní znak nebylo k dispozici žádné mapování.

[!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
[!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]

Nejvhodnější mapování je výchozí chování <xref:System.Text.Encoding> pro objekt, který kóduje data Unicode do dat znakové stránky a existují starší aplikace, které spoléhají na toto chování. Většina nových aplikací by se však měla z bezpečnostních důvodů vyhnout nejvhodnějšímu chování. Aplikace by například neměly umístit název domény prostřednictvím kódování vhodného přizpůsobení.

> [!NOTE]
> Můžete také implementovat vlastní nejvhodnější záložní mapování pro kódování. Další informace naleznete [v části Implementace vlastní záložní strategie.](../../../docs/standard/base-types/character-encoding.md#Custom)

Pokud nejvhodnější záložní je výchozí pro kódování objektu, můžete zvolit jinou záložní <xref:System.Text.Encoding> strategii při <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> načtení objektu voláním nebo přetížení. Následující část obsahuje příklad, který nahradí každý znak, který nelze mapovat na znakovou stránku 1252 hvězdičkou (*).

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

<a name="Replacement"></a>

### <a name="replacement-fallback"></a>Náhradní záložní

Pokud znak nemá přesnou shodu v cílovém schématu, ale neexistuje žádný vhodný znak, který lze mapovat, aplikace může určit náhradní znak nebo řetězec. Toto je výchozí chování dekodérunicode, který nahradí všechny dvoubajtové sekvence, které nelze dekódovat REPLACEMENT_CHARACTER (U + FFFD). Je to také výchozí <xref:System.Text.ASCIIEncoding> chování třídy, která nahrazuje každý znak, který nelze zakódovat nebo dekódovat otazníkem. Následující příklad ilustruje nahrazení znaku pro řetězec Unicode z předchozího příkladu. Jak ukazuje výstup, každý znak, který nelze dekódovat na hodnotu bajtu ASCII, je nahrazen hodnotou 0x3F, což je kód ASCII pro otazník.

[!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
[!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]

.NET obsahuje <xref:System.Text.EncoderReplacementFallback> <xref:System.Text.DecoderReplacementFallback> třídy a, které nahrazují náhradní řetězec, pokud znak není přesně mapován v operaci kódování nebo dekódování. Ve výchozím nastavení je tento náhradní řetězec otazníkem, ale můžete volat přetížení konstruktoru třídy a zvolit jiný řetězec. Náhradní řetězec je obvykle jeden znak, i když to není požadavek. Následující příklad změní chování kódové stránky 1252 kodéru vytvořením instance objektu, <xref:System.Text.EncoderReplacementFallback> který používá hvězdičku (*) jako náhradní řetězec.

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

> [!NOTE]
> Můžete také implementovat náhradní třídu pro kódování. Další informace naleznete [v části Implementace vlastní záložní strategie.](../../../docs/standard/base-types/character-encoding.md#Custom)

Kromě otazníku (U + 003F) se znak Nahrazení unicode (U + FFFD) běžně používá jako náhradní řetězec, zejména při dekódování bajtových sekvencí, které nelze úspěšně přeložit do znaků Unicode. Můžete však zvolit libovolný náhradní řetězec a může obsahovat více znaků.

<a name="Exception"></a>

### <a name="exception-fallback"></a>Záložní výjimka

Místo toho, aby nejvhodnější záložní nebo náhradní řetězec, kodér <xref:System.Text.EncoderFallbackException> může vyvolat, pokud není schopen kódovat sadu znaků a <xref:System.Text.DecoderFallbackException> dekodér může vyvolat, pokud není schopen dekódovat bajt pole. Chcete-li vyvolat výjimku v kódování a <xref:System.Text.EncoderExceptionFallback> dekódování <xref:System.Text.DecoderExceptionFallback> operace, zadejte objekt <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> a objekt, respektive metody. Následující příklad ilustruje výjimku záložní <xref:System.Text.ASCIIEncoding> s třídou.

[!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
[!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]

> [!NOTE]
> Můžete také implementovat vlastní obslužnou rutinu výjimky pro operaci kódování. Další informace naleznete [v části Implementace vlastní záložní strategie.](../../../docs/standard/base-types/character-encoding.md#Custom)

<xref:System.Text.EncoderFallbackException> Objekty <xref:System.Text.DecoderFallbackException> a poskytují následující informace o podmínce, která způsobila výjimku:

- Objekt <xref:System.Text.EncoderFallbackException> obsahuje <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> metodu, která označuje, zda znak nebo znaky, které nelze kódovat představují neznámý `true`náhradní pár (v takovém případě metoda `false`vrátí ) nebo neznámý jeden znak (v takovém případě metoda vrátí ). Znaky v náhradní pár jsou <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> k <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> dispozici z vlastnosti a. Neznámý jeden znak je <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> k dispozici z vlastnosti. Vlastnost <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> označuje pozici v řetězci, ve kterém byl nalezen první znak, který nelze zakódovat.

- Objekt <xref:System.Text.DecoderFallbackException> obsahuje <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> vlastnost, která vrací pole bajtů, které nelze dekódovat. Vlastnost <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> označuje počáteční pozici neznámých bajtů.

<xref:System.Text.EncoderFallbackException> Přestože <xref:System.Text.DecoderFallbackException> a objekty poskytují odpovídající diagnostické informace o výjimce, neposkytují přístup k kódování nebo dekódování vyrovnávací paměti. Proto neumožňují neplatná data, která mají být nahrazena nebo opraveny v rámci metody kódování nebo dekódování.

<a name="Custom"></a>

## <a name="implementing-a-custom-fallback-strategy"></a>Implementace vlastní záložní strategie

Kromě nejvhodnějšímapování, které je implementováno interně pomocí znakové stránky, .NET obsahuje následující třídy pro implementaci záložní strategie:

- Použijte <xref:System.Text.EncoderReplacementFallback> <xref:System.Text.EncoderReplacementFallbackBuffer> a nahraďte znaky v operacích kódování.

- Použijte <xref:System.Text.DecoderReplacementFallback> <xref:System.Text.DecoderReplacementFallbackBuffer> a nahraďte znaky v dekódovacích operacích.

- Použijte <xref:System.Text.EncoderExceptionFallback> <xref:System.Text.EncoderExceptionFallbackBuffer> a hodit <xref:System.Text.EncoderFallbackException> když znak nelze zakódovat.

- Použijte <xref:System.Text.DecoderExceptionFallback> <xref:System.Text.DecoderExceptionFallbackBuffer> a hodit <xref:System.Text.DecoderFallbackException> když znak nelze dekódovat.

Kromě toho můžete implementovat vlastní řešení, které používá nejvhodnější záložní, náhradní záložní nebo výjimku záložní, pomocí následujících kroků:

1. Odvodit <xref:System.Text.EncoderFallback> třídu z pro <xref:System.Text.DecoderFallback> kódování operací a z pro dekódování operací.

2. Odvodit <xref:System.Text.EncoderFallbackBuffer> třídu z pro <xref:System.Text.DecoderFallbackBuffer> kódování operací a z pro dekódování operací.

3. Pro výjimku záložní, pokud <xref:System.Text.EncoderFallbackException> <xref:System.Text.DecoderFallbackException> předdefinované a třídy neodpovídají vašim potřebám, <xref:System.Exception> <xref:System.ArgumentException>odvodit třídu z objektu výjimky, jako je například nebo .

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Odvození z EncoderFallback nebo DecoderFallback

Chcete-li implementovat vlastní záložní řešení, musíte vytvořit <xref:System.Text.EncoderFallback> třídu, která <xref:System.Text.DecoderFallback> dědí z pro operace kódování a z dekódování operací. Instance těchto tříd jsou předány metodě <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> a slouží jako prostředník mezi třídou kódování a záložní implementací.

Při vytváření vlastního záložního řešení pro kodér nebo dekodér je nutné implementovat následující členy:

- Vlastnost <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> nebo, která vrátí maximální možný počet znaků, které se mohou vrátit k záložnímu znaku nejvhodnějšímu, náhradnímu nebo výjimce, a nahradit tak jeden znak. Pro vlastní výjimku záložní, jeho hodnota je nulová.

- Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> nebo, která vrací <xref:System.Text.EncoderFallbackBuffer> <xref:System.Text.DecoderFallbackBuffer> vlastní nebo implementaci. Metoda je volána kodéru, když narazí na první znak, který není schopen úspěšně zakódovat, nebo dekodér, když narazí na první bajt, který není schopen úspěšně dekódovat.

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Odvození z EncoderFallbackBuffer nebo DecoderFallbackBuffer

Chcete-li implementovat vlastní záložní řešení, musíte také <xref:System.Text.EncoderFallbackBuffer> vytvořit třídu, která <xref:System.Text.DecoderFallbackBuffer> dědí z pro operace kódování a z dekódování operací. Instance těchto tříd jsou vráceny <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> metodou <xref:System.Text.EncoderFallback> <xref:System.Text.DecoderFallback> a třídy. Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> je volána kodérem, když narazí na první znak, který není <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> schopen kódovat, a metoda je volána dekodérum, když narazí na jeden nebo více bajtů, které není schopen dekódovat. A <xref:System.Text.EncoderFallbackBuffer> <xref:System.Text.DecoderFallbackBuffer> třídy poskytují záložní implementace. Každá instance představuje vyrovnávací paměť, která obsahuje záložní znaky, které nahradí znak, který nelze zakódovat, nebo sekvenci bajtů, kterou nelze dekódovat.

Při vytváření vlastního záložního řešení pro kodér nebo dekodér je nutné implementovat následující členy:

- Metoda <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> nebo. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>je volána kodérem poskytnout záložní vyrovnávací paměti s informacemi o znaku, který nelze zakódovat. Vzhledem k tomu, že znak, který má být kódován, může být náhradní pár, je tato metoda přetížena. Jeden přetížení je předán znak, který má být kódován a jeho index v řetězci. Druhé přetížení je předán vysoké a nízké náhradní spolu s jeho index v řetězci. Metoda <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> je volána dekodérem poskytnout záložní vyrovnávací paměti s informacemi o bajtů, které nelze dekódovat. Tato metoda je předána pole bajtů, které nelze dekódovat, spolu s indexem prvníbajt. Záložní metoda by `true` měla vrátit, pokud záložní vyrovnávací paměť může poskytnout nejvhodnější nebo náhradní znak nebo znaky; v opačném případě `false`by se měl vrátit . Pro záložní výjimku by měla záložní metoda vyvolat výjimku.

- Metoda <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> nebo, která je opakovaně volána kodérem nebo dekodérem, aby získala další znak ze záložní vyrovnávací paměti. Po vrácení všech záložních znaků by metoda měla vrátit U +0000.

- Vlastnost <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> or, která vrací počet znaků zbývajících do záložní vyrovnávací paměti.

- Metoda <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> nebo, která přesune aktuální pozici v záložní vyrovnávací paměti na předchozí znak.

- Metoda <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> nebo, která znovu inicializuje záložní vyrovnávací paměť.

Pokud je záložní implementace nejvhodnější záložní nebo náhradní záložní, třídy odvozené z <xref:System.Text.EncoderFallbackBuffer> a <xref:System.Text.DecoderFallbackBuffer> také udržovat dvě pole soukromé instance: přesný počet znaků ve vyrovnávací paměti; a index další znak ve vyrovnávací paměti vrátit.

### <a name="an-encoderfallback-example"></a>Příklad kodéruFallback

Dřívější příklad použitý náhradní záložní nahradit znaky Unicode, které neodpovídaly znaky ASCII s hvězdičkou (*). Následující příklad používá vlastní nejvhodnější záložní implementaci místo toho poskytnout lepší mapování znaků bez ASCII.

Následující kód definuje třídu `CustomMapper` s názvem, <xref:System.Text.EncoderFallback> která je odvozena od pro zpracování nejvhodnější mapování znaků bez ASCII. Jeho `CreateFallbackBuffer` metoda `CustomMapperFallbackBuffer` vrátí objekt, <xref:System.Text.EncoderFallbackBuffer> který poskytuje implementaci. Třída `CustomMapper` používá <xref:System.Collections.Generic.Dictionary%602> objekt k uložení mapování nepodporovaných znaků Unicode (hodnota klíče) a jejich odpovídajících 8bitových znaků (které jsou uloženy ve dvou po sobě jdoucích bajtů v 64bitovém celočíselném) znaku). Chcete-li toto mapování zpřístupnit záložní `CustomMapper` vyrovnávací paměti, instance `CustomMapperFallbackBuffer` je předána jako parametr konstruktoru třídy. Vzhledem k tomu, že nejdelší mapování je řetězec "INF" pro `MaxCharCount` znak Unicode U + 221E, vlastnost vrátí 3.

[!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
[!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]

Následující kód definuje `CustomMapperFallbackBuffer` třídu, která je <xref:System.Text.EncoderFallbackBuffer>odvozena od . Slovník, který obsahuje nejvhodnější mapování a který je `CustomMapper` definován v instanci je k dispozici z jeho konstruktoru třídy. Jeho `Fallback` metoda `true` vrátí, pokud některý z unicode znaků, které kodéru ASCII nelze kódovat jsou definovány ve slovníku mapování; v opačném `false`případě vrátí . Pro každý záložní proměnná `count` označuje počet znaků, které zbývá vrátit `index` a soukromé proměnné označuje pozici `charsToReturn`ve vyrovnávací paměti řetězce , další znak vrátit.

[!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
[!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]

Následující kód pak konkretizovat `CustomMapper` objekt a předá jeho instanci metodě. <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> Výstup označuje, že nejvhodnější záložní implementace úspěšně zpracovává tři znaky bez ASCII v původním řetězci.

[!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
[!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]

## <a name="see-also"></a>Viz také

- [Úvod k kódování znaků v rozhraní .NET](character-encoding-introduction.md)
- <xref:System.Text.Encoder>
- <xref:System.Text.Decoder>
- <xref:System.Text.DecoderFallback>
- <xref:System.Text.Encoding>
- <xref:System.Text.EncoderFallback>
- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
