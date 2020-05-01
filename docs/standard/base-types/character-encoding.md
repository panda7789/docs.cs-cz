---
title: Jak používat třídy kódování znaků v rozhraní .NET
description: Naučte se používat třídy kódování znaků v rozhraní .NET.
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
ms.openlocfilehash: 8e0cf961f4d6b481c354bdc854806f971458ce21
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624940"
---
# <a name="how-to-use-character-encoding-classes-in-net"></a>Jak používat třídy kódování znaků v rozhraní .NET

Tento článek vysvětluje, jak používat třídy, které .NET poskytuje pro kódování a dekódování textu pomocí různých schémat kódování. V těchto pokynech se předpokládá, že jste si přečetli [Úvod do kódování znaků v rozhraní .NET](character-encoding-introduction.md).

## <a name="encoders-and-decoders"></a>Kodéry a dekodéry

Rozhraní .NET poskytuje třídy kódování, které kódují a dekódují text pomocí různých systémů kódování. Například <xref:System.Text.UTF8Encoding> Třída popisuje pravidla pro kódování a dekódování v kódování UTF-8. .NET používá pro <xref:System.Text.UnicodeEncoding> `string` instance kódování UTF-16 (reprezentované třídou). Kodéry a dekodéry jsou k dispozici pro jiná schémata kódování.

Kódování a dekódování může také zahrnovat ověřování. Například <xref:System.Text.UnicodeEncoding> třída kontroluje všechny `char` instance v rozsahu nahrazení, aby se ujistily, že jsou v platných náhradních páru. Záložní strategie určuje, jak kodér zpracovává neplatné znaky nebo jak dekodér zpracovává neplatné bajty.

> [!WARNING]
> Třídy kódování .NET poskytují způsob, jak uložit a převést znaková data. Neměly by se používat k ukládání binárních dat ve formě řetězce. V závislosti na použitém kódování může převod binárních dat na formát řetězce pomocí tříd kódování způsobit neočekávané chování a vydávat nepřesná nebo poškozená data. Chcete-li převést binární data do formuláře řetězce, použijte <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metodu.

Všechny třídy kódování znaků v rozhraní .NET dědí z <xref:System.Text.Encoding?displayProperty=nameWithType> třídy, což je abstraktní třída, která definuje funkce společné pro všechna kódování znaků. Chcete-li získat přístup k jednotlivým objektům kódování implementovaným v rozhraní .NET, postupujte následovně:

- Použijte statické vlastnosti <xref:System.Text.Encoding> třídy, které vracejí objekty, které reprezentují standardní kódování znaků dostupné v rozhraní .NET (ASCII, UTF-7, UTF-8, UTF-16 a utf-32). <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> Vlastnost například vrátí <xref:System.Text.UnicodeEncoding> objekt. Každý objekt používá náhradní zálohu ke zpracování řetězců, které nelze kódovat, a bajtů, které nelze dekódovat. Další informace najdete v tématu [náhradní záloha](../../../docs/standard/base-types/character-encoding.md#Replacement).

- Volejte konstruktor třídy kódování. Tímto způsobem lze vytvořit instanci objektů pro kódování ASCII, UTF-7, UTF-8, UTF-16 a UTF-32. Ve výchozím nastavení každý objekt používá náhradní zálohu ke zpracování řetězců, které nemohou zakódovat a bajtů, které nelze dekódovat, ale můžete určit, že namísto toho by měla být vyvolána výjimka. Další informace najdete v tématu [náhradní záložní](../../../docs/standard/base-types/character-encoding.md#Replacement) a náhradní [výjimka](../../../docs/standard/base-types/character-encoding.md#Exception).

- Zavolejte <xref:System.Text.Encoding.%23ctor%28System.Int32%29> konstruktor a předejte mu celé číslo, které představuje kódování. Objekty úrovně Standard pro kódování používají náhradní zálohu a znakové stránky a dvoubajtové objekty znakové sady (DBCS) používají pro zpracování řetězců nejlepší zálohu ke zpracování řetězců, které nemohou kódovat a v bajtech, které nemohou dekódovat. Další informace najdete v tématu [co nejlépe pro použití](../../../docs/standard/base-types/character-encoding.md#BestFit).

- Zavolejte <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metodu, která vrátí všechny standardní, znakové stránky nebo kódování DBCS dostupné v rozhraní .NET. Přetížení umožňují určit záložní objekt pro kodér i dekodér.

Můžete načíst informace o všech kódováních dostupných v rozhraní .NET voláním <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> metody. Rozhraní .NET podporuje schémata kódování znaků uvedená v následující tabulce.

|Encoding – třída|Popis|
|--------------|-----------|
|[Abecední](xref:System.Text.ASCIIEncoding)|Zakóduje omezený rozsah znaků pomocí nižších sedmi bitů bajtů. Protože toto kódování podporuje pouze hodnoty znaků z U + 0000 až U + 007F, ve většině případů není pro mezinárodní aplikace nedostatečné.|
|[UTF-7](xref:System.Text.UTF7Encoding)|Představuje znaky jako sekvence pro znaky 7 bitů ASCII. Znaky Unicode jiné než ASCII jsou reprezentovány řídicí sekvencí znaků ASCII. UTF-7 podporuje protokoly jako e-mail a diskusní skupiny. UTF-7 ale není obzvláště zabezpečená nebo robustní. V některých případech může změna jednoho bitu oddáleně měnit výklad celého řetězce v kódování UTF-7. V jiných případech mohou různé řetězce UTF-7 kódovat stejný text. Pro sekvence, které obsahují znaky jiné než ASCII, vyžaduje UTF-7 více místa než UTF-8 a kódování/dekódování je pomalejší. V důsledku toho byste měli použít UTF-8 místo UTF-7, pokud je to možné.|
|[UTF-8](xref:System.Text.UTF8Encoding)|Představuje každý bod kódu Unicode jako sekvenci jednoho až čtyř bajtů. UTF-8 podporuje 8bitové velikosti dat a funguje dobře s mnoha stávajícími operačními systémy. Pro rozsah ASCII znaků je UTF-8 totožný s kódováním ASCII a umožňuje širší skupinu znaků. Pro skripty čínského japonštiny (CJK) ale může UTF-8 vyžadovat pro každý znak tři bajty a může způsobit větší velikost dat než UTF-16. V některých případech množství dat ASCII, jako jsou značky HTML, zarovnává větší velikost pro rozsah CJK.|
|[UTF-16](xref:System.Text.UnicodeEncoding)|Představuje každý bod kódu Unicode jako sekvenci jednoho nebo 2 16 celých čísel. Většina běžných znaků Unicode vyžaduje jenom jeden bod kódu UTF-16, i když doplňkové znaky Unicode (U + 10000 a větší) vyžadují dva body náhrady v kódu UTF-16. Podporují se tyto objednávky ve Little endian a v bajtech big-endian. Kódování UTF-16 je používáno modulem CLR (Common Language <xref:System.Char> runtime <xref:System.String> ) k reprezentování a hodnotám a používá ho operační systém `WCHAR` Windows k reprezentaci hodnot.|
|[UTF-32](xref:System.Text.UTF32Encoding)|Představuje každý bod kódu Unicode jako 32 celé číslo. Podporují se tyto objednávky ve Little endian a v bajtech big-endian. Kódování UTF-32 se používá v případě, že aplikace chtějí zabránit tomu, aby se při kódování UTF-16 v operačních systémech, které zakódované místo příliš důležité, nepoužívaly kódování UTF-16. Jednoduché glyfy vykreslené na displeji mohou být zakódovány pomocí více než jednoho znaku UTF-32.|
|Kódování ANSI/ISO|Poskytuje podporu pro nejrůznější znakové stránky. V operačních systémech Windows se znakové stránky používají k podpoře konkrétního jazyka nebo skupiny jazyků. Tabulku, která obsahuje seznam kódových stránek podporovaných rozhraním .NET, naleznete <xref:System.Text.Encoding> v tématu Třída. Objekt kódování pro konkrétní znakovou stránku lze načíst voláním <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metody. Znaková stránka obsahuje 256 kódových bodů a je počítána od nuly. Ve většině kódových stránek představuje body kódu 0 až 127 znakovou sadu ASCII a body kódu 128 až 255 se výrazně liší mezi kódovými stránkami. Například znaková stránka 1252 poskytuje znaky pro systémy psaní latinkou, včetně angličtiny, němčiny a francouzštiny. Poslední 128 body kódu v kódové stránce 1252 obsahují znaky zvýraznění. Znaková stránka 1253 poskytuje kódy znaků, které jsou požadovány v systému řeckého zápisu. Poslední 128 body kódu v kódové stránce 1253 obsahují řecké znaky. V důsledku toho aplikace, která spoléhá na znakové stránky ANSI, nemůže ukládat Řecká a Německo do stejného textového streamu, pokud neobsahuje identifikátor, který označuje odkazovanou znakovou stránku.|
|Kódování dvoubajtové znakové sady (DBCS)|Podporuje jazyky, jako jsou čínština, japonština a korejština, které obsahují více než 256 znaků. Ve znakové sadě DBCS dvojice kódových bodů (Double Byte) představuje každý znak. <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> Vlastnost vrátí `false` pro kódování znakové sady DBCS. Můžete načíst objekt kódování pro konkrétní sadu DBCS voláním <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metody. Když aplikace zpracovává data sady DBCS, první bajt znaku DBCS (vedoucí bajt) se zpracuje v kombinaci s koncovým bajtem, který hned následuje. Vzhledem k tomu, že jedna dvojice dvoubajtových bodů kódu může představovat různé znaky v závislosti na znakové stránce, toto schéma stále nepovoluje kombinaci dvou jazyků, jako jsou japonština a čínština, ve stejném datovém proudu.|

Tato kódování umožňují pracovat s znaky Unicode a s kódováními, které se nejčastěji používají ve starších verzích aplikací. Kromě toho můžete vytvořit vlastní kódování definováním třídy, která je odvozena z <xref:System.Text.Encoding> a přepsání jejích členů.

## <a name="net-core-encoding-support"></a>Podpora kódování .NET Core

Ve výchozím nastavení .NET Core nezpřístupňuje žádné kódování znakových stránek kromě znakové stránky 28591 a kódování Unicode, jako jsou UTF-8 a UTF-16. Můžete ale přidat kódování znakové stránky nalezené ve standardních aplikacích pro Windows, které cílí na rozhraní .NET do vaší aplikace. Další informace najdete v <xref:System.Text.CodePagesEncodingProvider> tématu.

<a name="Selecting"></a>

## <a name="selecting-an-encoding-class"></a>Výběr třídy kódování

Pokud máte příležitost zvolit kódování, které má vaše aplikace používat, měli byste použít kódování Unicode, a to, pokud je to <xref:System.Text.UTF8Encoding> možné, <xref:System.Text.UnicodeEncoding>nebo. (.NET také podporuje třetí kódování Unicode, <xref:System.Text.UTF32Encoding>.)

Pokud plánujete použít kódování ASCII (<xref:System.Text.ASCIIEncoding>), vyberte <xref:System.Text.UTF8Encoding> místo toho. Tato dvě kódování jsou shodná se znakovou sadou ASCII, ale <xref:System.Text.UTF8Encoding> mají následující výhody:

- Může představovat každý znak Unicode, zatímco <xref:System.Text.ASCIIEncoding> podporuje pouze hodnoty znaků Unicode mezi U + 0000 a U + 007F.

- Poskytuje detekci chyb a lepší zabezpečení.

- Byla vyladěna tak, aby byla co nejrychlejší a měla by být rychlejší než jakékoli jiné kódování. I pro obsah, který je zcela ve formátu ASCII, <xref:System.Text.UTF8Encoding> operace prováděné s jsou rychlejší <xref:System.Text.ASCIIEncoding>než operace prováděné s nástrojem.

Měli byste zvážit použití <xref:System.Text.ASCIIEncoding> jenom pro starší verze aplikací. Nicméně i u starších aplikací <xref:System.Text.UTF8Encoding> může být lepší volbou z následujících důvodů (předpokládá se výchozí nastavení):

- Pokud má vaše aplikace obsah, který není výhradně ASCII a zakóduje ho, <xref:System.Text.ASCIIEncoding>každý znak bez ASCII kódování se zakóduje jako otazník (?). Pokud aplikace potom tato data dekóduje, dojde ke ztrátě informací.

- Pokud má vaše aplikace obsah, který není výhradně ve formátu ASCII a zakóduje <xref:System.Text.UTF8Encoding>ho pomocí, výsledek se zdá být nečitelný, pokud je INTERPRETOVÁN jako ASCII. Pokud však aplikace použije k dekódování těchto dat dekodér UTF-8, data se úspěšně vykoná pomocí odezvy.

Ve webové aplikaci by se měly znaky odeslané klientovi v reakci na webový požadavek projevit kódováním použitým v klientovi. Ve většině případů byste měli nastavit <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> vlastnost na hodnotu vrácenou <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> vlastností pro zobrazení textu v kódování, které uživatel očekává.

<a name="Using"></a>

## <a name="using-an-encoding-object"></a>Použití objektu Encoding

Kodér převede řetězec znaků (nejčastěji znaků Unicode) na jeho číselný ekvivalent (Byte). Například můžete použít kodér ASCII k převedení znaků Unicode na ASCII, aby se mohly zobrazit v konzole. Chcete-li provést převod, zavolejte <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> metodu. Chcete-li určit, kolik bajtů je potřeba k uložení zakódovaných znaků před provedením kódování, můžete zavolat <xref:System.Text.Encoding.GetByteCount%2A> metodu.

Následující příklad používá jedno bajtové pole ke kódování řetězců ve dvou samostatných operacích. Udržuje index, který označuje počáteční pozici v bajtovém poli pro další sadu bajtů zakódovaných ve formátu ASCII. Volá <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> metodu, aby zajistila, že bajtové pole je dostatečně velké pro přizpůsobení kódovaného řetězce. Poté volá <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metodu pro kódování znaků v řetězci.

[!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
[!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]

Dekodér převede pole bajtů, které odráží konkrétní kódování znaků, do množiny znaků, buď v poli znaků nebo v řetězci. Chcete-li dekódovat pole bajtů do pole znaků, zavoláte <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metodu. Chcete-li dekódovat pole bajtů do řetězce, zavoláte <xref:System.Text.Encoding.GetString%2A> metodu. Chcete-li určit, kolik znaků je potřeba k uložení dekódovaných bajtů před provedením dekódování, můžete zavolat <xref:System.Text.Encoding.GetCharCount%2A> metodu.

Následující příklad kóduje tři řetězce a poté je dekóduje do jednoho pole znaků. Udržuje index, který označuje počáteční pozici v poli znaků pro další sadu dekódových znaků. Volá <xref:System.Text.ASCIIEncoding.GetCharCount%2A> metodu, aby zajistila, že je pole znaků dostatečně velké, aby se vešly všechny Dekódovatelné znaky. Pak zavolá <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metodu pro dekódování pole bajtů.

[!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
[!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]

Metody kódování a dekódování třídy odvozené z <xref:System.Text.Encoding> jsou navrženy tak, aby fungovaly na kompletní sadě dat; To znamená, že všechna data, která mají být kódována nebo Dekódovaná, jsou uvedena v jediném volání metody. V některých případech jsou však data k dispozici v datovém proudu a data, která mají být kódována nebo Dekódovaná, mohou být k dispozici pouze ze samostatných operací čtení. K tomu je potřeba, aby operace kódování nebo dekódování pamatovala kterýkoli uložený stav z předchozího vyvolání. Metody tříd odvozené z <xref:System.Text.Encoder> a <xref:System.Text.Decoder> jsou schopny zpracovávat operace kódování a dekódování, které přesahují více volání metody.

<xref:System.Text.Encoder> Objekt pro konkrétní kódování je k dispozici z <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> vlastnosti tohoto kódování. <xref:System.Text.Decoder> Objekt pro konkrétní kódování je k dispozici z <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> vlastnosti tohoto kódování. Pro dekódování operací si všimněte, že třídy odvozené <xref:System.Text.Decoder> z obsahují <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metodu, ale nemají metodu, která odpovídá <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>.

Následující příklad znázorňuje rozdíl mezi použitím metod <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType> a <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> pro dekódování pole bajtů Unicode. Příklad zakóduje řetězec, který obsahuje některé znaky Unicode do souboru, a poté používá dvě metody dekódování k dekódování těchto desíti bajtů současně. Vzhledem k tomu, že náhradní pár vychází z desáté a jedenáctá bajty, je dekódovat v samostatných voláních metody. Jak ukazuje výstup, <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType> metoda není schopna správně dekódovat bajty a místo toho je nahradí znakem U + FFFD (nahrazující znak). Na druhé straně <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metoda může úspěšně dekódovat pole bajtů a získat tak původní řetězec.

[!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
[!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]

<a name="FallbackStrategy"></a>

## <a name="choosing-a-fallback-strategy"></a>Výběr záložní strategie

Když se metoda pokusí kódovat nebo dekódovat znak, ale neexistuje žádné mapování, musí implementovat záložní strategii, která určuje, jak by mělo být zpracování neúspěšného mapování. Existují tři typy nouzových strategií:

- Nejlépe přizpůsobit záložním

- Náhradní záložní

- Záložní výjimka

> [!IMPORTANT]
> Nejběžnější problémy v operacích kódování dochází, když znak Unicode nelze namapovat na konkrétní kódování znakové stránky. Nejběžnější problémy při dekódování se vyskytují, když neplatné sekvence bajtů nejde přeložit na platné znaky Unicode. Z těchto důvodů byste měli znát, kterou záložní strategii konkrétní objekt kódování používá. Kdykoli je to možné, měli byste určit záložní strategii použitou objektem kódování při vytváření instance objektu.

<a name="BestFit"></a>

### <a name="best-fit-fallback"></a>Nejlépe přizpůsobit záložním

Pokud znak nemá přesnou shodu v cílovém kódování, kodér se může pokusit namapovat na podobný znak. (Co nejlépe vyhovuje záložnímu řešení, je většinou kódování, nikoli problém dekódování. Existuje několik znakových stránek, které obsahují znaky, které nelze úspěšně namapovat na kódování Unicode.) Nejlepší je jako výchozí pro kódování znakové stránky a dvoubajtové znakové sady, které jsou načteny pomocí přetížení <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> a. <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType>

> [!NOTE]
> Teoreticky, třídy kódování Unicode poskytované v rozhraní .NET (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding>a <xref:System.Text.UTF32Encoding>) podporují každý znak v každé znakové sadě, takže je lze použít k odstranění nejlepšího problému s nouzovou velikostí.

Strategie pro nejlepší přizpůsobení se liší u různých znakových stránek. Například pro některé znakové stránky jsou znaky latinky s plnou šířkou mapovány na obecnější znaky s poloviční šířkou. Pro jiné znakové stránky se toto mapování neprovede. I v rámci agresivní strategie nejlepšího přizpůsobení není pro některé znaky v některých kódování dostatek. Například čínský znak nemá žádné rozumné mapování na znakovou stránku 1252. V tomto případě je použit náhradní řetězec. Ve výchozím nastavení je tento řetězec pouze jedním OTAZNÍKem (U + 003F).

> [!NOTE]
> Strategie pro nejlepší přizpůsobení nejsou podrobně dokumentovány. Na webu [konsorcia Unicode](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) je však uvedeno několik kódových stránek. Popis Interpretace souborů mapování najdete v souboru **Readme. txt** v této složce.

V následujícím příkladu je použita znaková stránka 1252 (znaková stránka systému Windows pro jazyky západní Evropa) k ilustraci mapování nejlepšího přizpůsobení a jejich nevýhod. <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> Metoda se používá k načtení objektu kódování pro znakovou stránku 1252. Ve výchozím nastavení používá standardně mapování pro znaky Unicode, které nepodporuje. V tomto příkladu se vytvoří instance řetězce, který obsahuje tři znaky, které nepatří do ASCII – BRAILLOVO písmo latinky S (U + 24C8), horní index pět (u + 2075) a nekonečno (U + 221E) – oddělené mezerami. Jak ukazuje výstup z příkladu, při kódování řetězce jsou tři původní znaky bez mezer nahrazeny OTAZNÍKem (U + 003F), ČÍSLICí pět (U + 0035) a ČÍSLICí osm (U + 0038). ČÍSLICE osm je obzvláště špatná náhrada pro nepodporovaný nekonečný znak a otazník indikuje, že pro původní znak nebylo k dispozici žádné mapování.

[!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
[!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]

Mapování nejlepšího umístění je výchozím chováním pro <xref:System.Text.Encoding> objekt, který kóduje data v kódování Unicode na data znakové stránky a obsahuje starší aplikace, které jsou závislé na tomto chování. Většina nových aplikací se však musí z bezpečnostních důvodů vyhnout tomu, co nejlépe vyhovuje chování. Například aplikace by neměly uvádět název domény pomocí kódování, které nejlépe vyhovuje.

> [!NOTE]
> Pro kódování můžete také implementovat vlastní sekundární mapování pro nejlepší přizpůsobení. Další informace najdete v části [implementace vlastní nouzové strategie](../../../docs/standard/base-types/character-encoding.md#Custom) .

Pokud je pro objekt kódování výchozí možnost nejlepšího nastavení, můžete zvolit jinou záložní strategii při načítání <xref:System.Text.Encoding> objektu voláním metody <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> nebo <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> přetížení. Následující část obsahuje příklad, který nahradí každý znak, který nelze namapovat na znakovou stránku 1252 hvězdičkou (*).

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

<a name="Replacement"></a>

### <a name="replacement-fallback"></a>Náhradní záložní

Pokud znak nemá přesnou shodu v cílovém schématu, ale neexistuje žádný vhodný znak, který lze namapovat na, aplikace může určit náhradní znak nebo řetězec. Toto je výchozí chování pro dekodér Unicode, které nahradí každou posloupnost dvou bajtů, kterou nemůže dekódovat pomocí REPLACEMENT_CHARACTER (U + FFFD). Je to také výchozí chování <xref:System.Text.ASCIIEncoding> třídy, které nahradí každý znak, který nemůže kódování ani dekódovat pomocí otazníku. Následující příklad ukazuje nahrazení znaku pro řetězec Unicode z předchozího příkladu. Jak výstup ukazuje, každý znak, který nelze dekódovat do bajtové hodnoty ASCII, je nahrazen hodnotou 0x3F, což je kód ASCII pro otazník.

[!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
[!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]

Rozhraní .NET zahrnuje <xref:System.Text.EncoderReplacementFallback> třídy <xref:System.Text.DecoderReplacementFallback> a, které nahradí náhradní řetězec, pokud znak není přesně mapován v operaci kódování nebo dekódování. Ve výchozím nastavení je tento nahrazující řetězec otazník, ale můžete volat přetížení konstruktoru třídy pro výběr jiného řetězce. Obvykle je nahrazující řetězec jedním znakem, přestože to není požadavek. Následující příklad změní chování kodéru kódové stránky 1252 vytvořením <xref:System.Text.EncoderReplacementFallback> objektu, který používá hvězdičku (*) jako náhradní řetězec.

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

> [!NOTE]
> Pro kódování můžete také implementovat náhradní třídu. Další informace najdete v části [implementace vlastní nouzové strategie](../../../docs/standard/base-types/character-encoding.md#Custom) .

Kromě OTAZNÍKu (U + 003F) se znak nahrazení Unicode (U + FFFD) běžně používá jako náhradní řetězec, zejména při dekódování sekvencí bajtů, které se nedají úspěšně přeložit do znaků Unicode. Můžete však vybrat libovolný řetězec pro nahrazení a může obsahovat více znaků.

<a name="Exception"></a>

### <a name="exception-fallback"></a>Záložní výjimka

Namísto poskytnutí nejlepšího náhradního nebo náhradního řetězce může kodér vyvolat výjimku <xref:System.Text.EncoderFallbackException> , pokud není schopen zakódovat sadu znaků a dekodér může vyvolat, <xref:System.Text.DecoderFallbackException> Pokud není schopen dekódovat bajtové pole. Chcete-li vyvolat výjimku při operacích kódování a dekódování, zadejte <xref:System.Text.EncoderExceptionFallback> objekt a <xref:System.Text.DecoderExceptionFallback> objekt, v uvedeném pořadí, do <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metody. Následující příklad ukazuje použití výjimky s <xref:System.Text.ASCIIEncoding> třídou.

[!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
[!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]

> [!NOTE]
> Můžete také implementovat vlastní obslužnou rutinu výjimky pro operaci kódování. Další informace najdete v části [implementace vlastní nouzové strategie](../../../docs/standard/base-types/character-encoding.md#Custom) .

Objekty <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> poskytují následující informace o stavu, který způsobil výjimku:

- <xref:System.Text.EncoderFallbackException> Objekt <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> obsahuje metodu, která označuje, zda znak nebo znaky, které nemohou být zakódovány, představuje neznámý náhradní pár (v takovém případě se `true`metoda vrátí) nebo neznámý jediný znak (v takovém případě se `false`Metoda vrátí). Znaky v náhradní dvojici jsou k dispozici z <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> vlastností <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> a. Z <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> vlastnosti je k dispozici neznámý jeden znak. <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> Vlastnost určuje pozici v řetězci, na které byl nalezen první znak, který nelze zakódovat.

- <xref:System.Text.DecoderFallbackException> Objekt obsahuje <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> vlastnost, která vrací pole bajtů, které nelze dekódovat. <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> Vlastnost označuje počáteční pozici neznámých bajtů.

I když <xref:System.Text.EncoderFallbackException> objekty <xref:System.Text.DecoderFallbackException> a poskytují dostatečné diagnostické informace o výjimce, neposkytují přístup k vyrovnávací paměti pro kódování nebo dekódování. Proto neumožňují nahradit nebo opravit neplatná data v rámci metody Encoding nebo dekódování.

<a name="Custom"></a>

## <a name="implementing-a-custom-fallback-strategy"></a>Implementace vlastní nouzové strategie

Kromě nejlepšího mapování, které je implementováno interně pomocí znakových stránek, .NET zahrnuje následující třídy pro implementaci záložní strategie:

- Použijte <xref:System.Text.EncoderReplacementFallback> a <xref:System.Text.EncoderReplacementFallbackBuffer> k nahrazení znaků v operacích kódování.

- Použijte <xref:System.Text.DecoderReplacementFallback> a <xref:System.Text.DecoderReplacementFallbackBuffer> k nahrazení znaků v operacích dekódování.

- Použijte <xref:System.Text.EncoderExceptionFallback> a <xref:System.Text.EncoderExceptionFallbackBuffer> k vyvolání, <xref:System.Text.EncoderFallbackException> když znak nelze kódovat.

- Použijte <xref:System.Text.DecoderExceptionFallback> a <xref:System.Text.DecoderExceptionFallbackBuffer> k vyvolání, <xref:System.Text.DecoderFallbackException> když znak nelze dekódovat.

Pomocí následujících kroků můžete navíc implementovat vlastní řešení, které se nejlépe hodí pro nouzové účely, náhradní zálohu nebo výjimku.

1. Odvození třídy z <xref:System.Text.EncoderFallback> pro operace kódování a z <xref:System.Text.DecoderFallback> pro operace dekódování.

2. Odvození třídy z <xref:System.Text.EncoderFallbackBuffer> pro operace kódování a z <xref:System.Text.DecoderFallbackBuffer> pro operace dekódování.

3. Pro záložní výjimku, pokud <xref:System.Text.EncoderFallbackException> předdefinované a <xref:System.Text.DecoderFallbackException> třídy nevyhovují vašim potřebám, odvozuje třídu od objektu výjimky, jako je například <xref:System.Exception> nebo. <xref:System.ArgumentException>

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Odvození z EncoderFallback nebo DecoderFallback

Chcete-li implementovat vlastní nouzové řešení, je nutné vytvořit třídu, která <xref:System.Text.EncoderFallback> dědí z pro operace kódování a <xref:System.Text.DecoderFallback> z pro dekódování operací. Instance těchto tříd jsou předány <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metodě a slouží jako prostředník mezi třídou kódování a záložní implementací.

Při vytváření vlastního záložního řešení pro kodér nebo dekodér je nutné implementovat následující členy:

- Vlastnost <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> , která vrací maximální možný počet znaků, které se nejlépe hodí, nahrazuje nebo nevýjimka, může vrátit, aby nahradila jediný znak. U vlastní nouzové výjimky má jeho hodnota hodnotu nula.

- Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> , která vrátí vlastní <xref:System.Text.EncoderFallbackBuffer> nebo <xref:System.Text.DecoderFallbackBuffer> implementaci. Metoda je volána kodérem při výskytu prvního znaku, který není schopen úspěšně kódovat, nebo dekodérem, když nalezne první bajt, který nemůže úspěšně dekódovat.

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Odvození z EncoderFallbackBuffer nebo DecoderFallbackBuffer

Pro implementaci vlastního záložního řešení je nutné také vytvořit třídu, která dědí z <xref:System.Text.EncoderFallbackBuffer> pro operace kódování a z <xref:System.Text.DecoderFallbackBuffer> pro dekódování operací. Instance těchto tříd jsou vráceny <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> metodou třídy <xref:System.Text.EncoderFallback> a. <xref:System.Text.DecoderFallback> <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> Metoda je volána kodérem, když nalezne první znak, který není možné kódovat, a <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metoda je volána dekodérem, když narazí na jeden nebo více bajtů, které není možné dekódovat. Třídy <xref:System.Text.EncoderFallbackBuffer> a <xref:System.Text.DecoderFallbackBuffer> poskytují záložní implementaci. Každá instance představuje vyrovnávací paměť, která obsahuje záložní znaky, které nahradí znak, který nelze zakódovat, nebo posloupnost bajtů, které nelze dekódovat.

Při vytváření vlastního záložního řešení pro kodér nebo dekodér je nutné implementovat následující členy:

- Metoda <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> . <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>je volána kodérem k poskytnutí záložní vyrovnávací paměti s informacemi o znaku, který nelze kódovat. Vzhledem k tomu, že znak pro kódování může být náhradní pár, je tato metoda přetížená. Jednomu přetížení se předal znak, který se má zakódovat, a jeho index v řetězci. Druhé přetížení je předání vysoké a nízké náhrady spolu s indexem v řetězci. <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> Metoda je volána dekodérem k poskytnutí záložní vyrovnávací paměti s informacemi o bajtech, které nelze dekódovat. Tato metoda předává pole bajtů, které nelze dekódovat, spolu s indexem prvního bajtu. Záložní metoda by měla vrátit `true` , pokud záložní vyrovnávací paměť může dodat nejlépe vyhovující nebo náhradní znak nebo znaky. v opačném případě by `false`měla vrátit. Pro zálohu výjimky by měla metoda Fallback vyvolat výjimku.

- Metoda <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> , která je volána opakovaně kodérem nebo dekodérem k získání dalšího znaku z záložní vyrovnávací paměti. Pokud byly vráceny všechny záložní znaky, metoda by měla vracet U + 0000.

- Vlastnost <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> , která vrací počet znaků zbývajících v záložní vyrovnávací paměti.

- Metoda <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> , která přesune aktuální pozici v záložní vyrovnávací paměti na předchozí znak.

- Metoda <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> , která znovu inicializuje záložní vyrovnávací paměť.

Pokud je nouzová implementace nejlépe vyhovující záložnímu nebo náhradnímu Fallback, třídy odvozené z <xref:System.Text.EncoderFallbackBuffer> a <xref:System.Text.DecoderFallbackBuffer> také udržují dvě soukromá pole instance: přesný počet znaků ve vyrovnávací paměti; a indexem dalšího znaku ve vyrovnávací paměti, který se má vrátit.

### <a name="an-encoderfallback-example"></a>EncoderFallback příklad

Předchozí příklad používá náhradní zálohu k nahrazení znaků Unicode, které neodpovídaly znakům ASCII hvězdičkou (*). Následující příklad používá vlastní implementaci záložní implementace, která je vhodná pro zajištění lepšího mapování znaků, které nejsou ASCII.

Následující kód definuje třídu s názvem `CustomMapper` , která je odvozena <xref:System.Text.EncoderFallback> z a zpracovává tak nejlepší mapování znaků, které nejsou ASCII. Jeho `CreateFallbackBuffer` metoda vrátí `CustomMapperFallbackBuffer` objekt, který poskytuje <xref:System.Text.EncoderFallbackBuffer> implementaci. `CustomMapper` Třída používá <xref:System.Collections.Generic.Dictionary%602> objekt k uložení mapování nepodporovaných znaků Unicode (hodnota klíče) a jejich odpovídajících 8bitových znaků (které jsou uloženy ve dvou po sobě jdoucích bajtech v 64ovém Integer). Chcete-li toto mapování zpřístupnit pro záložní vyrovnávací paměť, `CustomMapper` je instance předána jako parametr konstruktoru `CustomMapperFallbackBuffer` třídy. Vzhledem k tomu, že nejdelší mapování je řetězec "INF" pro znak Unicode U + 221E, `MaxCharCount` vrátí vlastnost hodnotu 3.

[!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
[!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]

Následující kód definuje `CustomMapperFallbackBuffer` třídu, která je odvozena z <xref:System.Text.EncoderFallbackBuffer>. Slovník, který obsahuje mapování nejlepšího umístění a který je definován v `CustomMapper` instanci, je k dispozici z jeho konstruktoru třídy. Jeho `Fallback` metoda vrátí `true` , pokud některý ze znaků Unicode, které kodér ASCII nemůže kódovat, je definován ve slovníku mapování; v opačném případě `false`vrátí. Pro každou zálohu určuje soukromá `count` proměnná počet znaků, které budou vráceny, a soukromá `index` proměnná označuje pozici v bufferu `charsToReturn`řetězce, a to u dalšího znaku, který chcete vrátit.

[!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
[!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]

Následující kód potom vytvoří instanci `CustomMapper` objektu a předá jeho instanci <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metodě. Výstup označuje, že pro záložní implementaci, který nejlépe vyhovuje, se v původním řetězci zpracovávají tři znaky jiné než ASCII.

[!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
[!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]

## <a name="see-also"></a>Viz také

- [Úvod do kódování znaků v rozhraní .NET](character-encoding-introduction.md)
- <xref:System.Text.Encoder>
- <xref:System.Text.Decoder>
- <xref:System.Text.DecoderFallback>
- <xref:System.Text.Encoding>
- <xref:System.Text.EncoderFallback>
- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
