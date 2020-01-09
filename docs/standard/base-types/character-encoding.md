---
title: Kódování znaků v rozhraní .NET
description: Přečtěte si o kódování a dekódování znaků v rozhraní .NET.
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
ms.openlocfilehash: 3cd461d8c56c3f31bf3ffe04acf239ecd32fe328
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711438"
---
# <a name="character-encoding-in-net"></a>Kódování znaků v rozhraní .NET

Znaky jsou abstraktní entity, které mohou být reprezentovány mnoha různými způsoby. Kódování znaků je systém, který spáruje každý znak v podporované znakové sadě s určitou hodnotou, která představuje tento znak. Například kód MORSE je kódování znaků, které spáruje každý znak v římské abecedě se vzorem teček a pomlčkami, které jsou vhodné pro přenos přes telegrafní řádky. Kódování znaků pro počítače spáruje každý znak v podporované znakové sadě s číselnou hodnotou, která představuje tento znak. Kódování znaků má dvě odlišné komponenty:

- Kodér, který překládá sekvenci znaků do sekvence číselných hodnot (bajtů).

- Dekodér, který překládá sekvenci bajtů do sekvence znaků.

Kódování znaků popisuje pravidla, podle kterých kodér a dekodér pracují. Například třída <xref:System.Text.UTF8Encoding> popisuje pravidla pro kódování a dekódování z, 8bitové transformačního formátu Unicode (UTF-8), který používá jeden až čtyři bajty pro reprezentaci jednoho znaku Unicode. Kódování a dekódování může také zahrnovat ověřování. Například třída <xref:System.Text.UnicodeEncoding> kontroluje všechny náhrady, aby se zajistilo, že tvoří platné náhradní páry. (Náhradní pár se skládá ze znaku s kódovým bodem, který je v rozsahu od U + D800 do U + DBFF následovaný znakem a bodem kódu, který je v rozsahu od U + DC00 do U + DFFF.)  Záložní strategie určuje, jak kodér zpracovává neplatné znaky nebo jak dekodér zpracovává neplatné bajty.

> [!WARNING]
> Třídy kódování .NET poskytují způsob, jak uložit a převést znaková data. Neměly by se používat k ukládání binárních dat ve formě řetězce. V závislosti na použitém kódování může převod binárních dat na formát řetězce pomocí tříd kódování způsobit neočekávané chování a vydávat nepřesná nebo poškozená data. Chcete-li převést binární data do formuláře řetězce, použijte metodu <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType>.

Rozhraní .NET používá kódování UTF-16 (reprezentované <xref:System.Text.UnicodeEncoding> třídou) k reprezentaci znaků a řetězců. Aplikace určené pro modul CLR (Common Language Runtime) používají kodéry k mapování reprezentace znaků Unicode podporované modulem CLR (Common Language Runtime) na jiná schémata kódování. Používají dekodéry k mapování znaků z kódování jiných než Unicode do kódování Unicode.

Toto téma se skládá z následujících částí:

- [Kódování v rozhraní .NET](../../../docs/standard/base-types/character-encoding.md#Encodings)

- [Výběr třídy kódování](../../../docs/standard/base-types/character-encoding.md#Selecting)

- [Použití objektu Encoding](../../../docs/standard/base-types/character-encoding.md#Using)

- [Výběr záložní strategie](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)

- [Implementace vlastní nouzové strategie](../../../docs/standard/base-types/character-encoding.md#Custom)

<a name="Encodings"></a>

## <a name="encodings-in-net"></a>Kódování v rozhraní .NET

Všechny třídy kódování znaků v rozhraní .NET dědí z třídy <xref:System.Text.Encoding?displayProperty=nameWithType>, což je abstraktní třída, která definuje funkce společné pro všechna kódování znaků. Chcete-li získat přístup k jednotlivým objektům kódování implementovaným v rozhraní .NET, postupujte následovně:

- Použijte statické vlastnosti třídy <xref:System.Text.Encoding>, které vracejí objekty, které reprezentují standardní kódování znaků dostupné v rozhraní .NET (ASCII, UTF-7, UTF-8, UTF-16 a UTF-32). Například vlastnost <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> vrátí objekt <xref:System.Text.UnicodeEncoding>. Každý objekt používá náhradní zálohu ke zpracování řetězců, které nelze kódovat, a bajtů, které nelze dekódovat. (Další informace najdete v části [náhradní záložní](../../../docs/standard/base-types/character-encoding.md#Replacement) oddíl.)

- Volejte konstruktor třídy kódování. Tímto způsobem lze vytvořit instanci objektů pro kódování ASCII, UTF-7, UTF-8, UTF-16 a UTF-32. Ve výchozím nastavení každý objekt používá náhradní zálohu ke zpracování řetězců, které nemohou zakódovat a bajtů, které nelze dekódovat, ale můžete určit, že namísto toho by měla být vyvolána výjimka. (Další informace najdete v oddílech [náhradní záložní](../../../docs/standard/base-types/character-encoding.md#Replacement) a [záložní výjimky](../../../docs/standard/base-types/character-encoding.md#Exception) .)

- Zavolejte konstruktor <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> a předejte mu celé číslo, které představuje kódování. Objekty úrovně Standard pro kódování používají náhradní zálohu a znakové stránky a dvoubajtové objekty znakové sady (DBCS) používají pro zpracování řetězců nejlepší zálohu ke zpracování řetězců, které nemohou kódovat a v bajtech, které nemohou dekódovat. (Další informace najdete v části [co nejlépe pro použití](../../../docs/standard/base-types/character-encoding.md#BestFit) .)

- Zavolejte metodu <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>, která vrací jakékoli standardní kódování, znakovou stránku nebo kódování DBCS dostupné v rozhraní .NET. Přetížení umožňují určit záložní objekt pro kodér i dekodér.

> [!NOTE]
> Standard Unicode přiřadí bod kódu (číslo) a název každému znaku v každém podporovaném skriptu. Například znak "A" je reprezentován bodem kódu U + 0041 a názvem "velké písmeno latinky A". Kódování UTF (Unicode Transformation Format) definuje způsoby kódování tohoto bodu kódu do sekvence jednoho nebo více bajtů. Schéma kódování Unicode zjednodušuje vývoj aplikací připravených pro použití ve světě, protože umožňuje znakům z libovolné znakové sady znázornit v jednom kódování. Vývojáři aplikací již nemusí sledovat schéma kódování, které bylo použito k vytváření znaků pro konkrétní jazyk nebo systém zápisu, a data lze sdílet mezi systémy mezinárodně bez poškození.
>
> Rozhraní .NET podporuje tři kódování definovaná standardem Unicode: UTF-8, UTF-16 a UTF-32. Další informace najdete na [domovské stránce Unicode](https://www.unicode.org/)na standardu Unicode.

Můžete získat informace o všech kódováních dostupných v rozhraní .NET voláním metody <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType>. Rozhraní .NET podporuje systémy kódování znaků uvedené v následující tabulce.

|Kódování|Třída|Popis|Výhody a nevýhody|
|--------------|-----------|-----------------|-------------------------------|
|ASCII|<xref:System.Text.ASCIIEncoding>|Zakóduje omezený rozsah znaků pomocí nižších sedmi bitů bajtů.|Protože toto kódování podporuje pouze hodnoty znaků z U + 0000 až U + 007F, ve většině případů není pro mezinárodní aplikace nedostatečné.|
|UTF-7|<xref:System.Text.UTF7Encoding>|Představuje znaky jako sekvence pro znaky 7 bitů ASCII. Znaky Unicode jiné než ASCII jsou reprezentovány řídicí sekvencí znaků ASCII.|UTF-7 podporuje protokoly, jako jsou e-maily a protokoly diskusních skupin. UTF-7 ale není obzvláště zabezpečená nebo robustní. V některých případech může změna jednoho bitu oddáleně měnit výklad celého řetězce v kódování UTF-7. V jiných případech mohou různé řetězce UTF-7 kódovat stejný text. Pro sekvence, které obsahují znaky jiné než ASCII, vyžaduje UTF-7 více místa než UTF-8 a kódování/dekódování je pomalejší. V důsledku toho byste měli použít UTF-8 místo UTF-7, pokud je to možné.|
|UTF-8|<xref:System.Text.UTF8Encoding>|Představuje každý bod kódu Unicode jako sekvenci jednoho až čtyř bajtů.|UTF-8 podporuje 8bitové velikosti dat a funguje dobře s mnoha stávajícími operačními systémy. Pro rozsah ASCII znaků je UTF-8 totožný s kódováním ASCII a umožňuje širší skupinu znaků. Pro skripty čínského japonštiny (CJK) ale může UTF-8 vyžadovat pro každý znak tři bajty a může potenciálně způsobit větší velikost dat než UTF-16. Všimněte si, že v některých případech množství dat ASCII, jako jsou značky HTML, zarovnává větší velikost pro rozsah CJK.|
|UTF-16|<xref:System.Text.UnicodeEncoding>|Představuje každý bod kódu Unicode jako sekvenci jednoho nebo 2 16 celých čísel. Většina běžných znaků Unicode vyžaduje jenom jeden bod kódu UTF-16, i když doplňkové znaky Unicode (U + 10000 a větší) vyžadují dva body náhrady v kódu UTF-16. Podporují se tyto objednávky ve Little endian a v bajtech big-endian.|Kódování UTF-16 je používáno modulem CLR (Common Language Runtime) k reprezentaci hodnot <xref:System.Char> a <xref:System.String> a používá ho operační systém Windows k reprezentaci `WCHAR`ch hodnot.|
|UTF-32|<xref:System.Text.UTF32Encoding>|Představuje každý bod kódu Unicode jako 32 celé číslo. Podporují se tyto objednávky ve Little endian a v bajtech big-endian.|Kódování UTF-32 se používá v případě, že aplikace chtějí zabránit tomu, aby se při kódování UTF-16 v operačních systémech, které zakódované místo příliš důležité, nepoužívaly kódování UTF-16. Jednoduché glyfy vykreslené na displeji mohou být zakódovány pomocí více než jednoho znaku UTF-32.|
|Kódování ANSI/ISO||Poskytuje podporu pro nejrůznější znakové stránky. V operačních systémech Windows se znakové stránky používají k podpoře konkrétního jazyka nebo skupiny jazyků. Tabulku, která obsahuje seznam kódových stránek podporovaných rozhraním .NET, naleznete v tématu Třída <xref:System.Text.Encoding>. Můžete načíst objekt kódování pro konkrétní znakovou stránku voláním metody <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType>.|Znaková stránka obsahuje 256 kódových bodů a je počítána od nuly. Ve většině kódových stránek představuje body kódu 0 až 127 znakovou sadu ASCII a body kódu 128 až 255 se výrazně liší mezi kódovými stránkami. Například znaková stránka 1252 poskytuje znaky pro systémy psaní latinkou, včetně angličtiny, němčiny a francouzštiny. Poslední 128 body kódu v kódové stránce 1252 obsahují znaky zvýraznění. Znaková stránka 1253 poskytuje kódy znaků, které jsou požadovány v systému řeckého zápisu. Poslední 128 body kódu v kódové stránce 1253 obsahují řecké znaky. V důsledku toho aplikace, která spoléhá na znakové stránky ANSI, nemůže ukládat Řecká a Německo do stejného textového streamu, pokud neobsahuje identifikátor, který označuje odkazovanou znakovou stránku.|
|Kódování dvoubajtové znakové sady (DBCS)||Podporuje jazyky, jako jsou čínština, japonština a korejština, které obsahují více než 256 znaků. Ve znakové sadě DBCS dvojice kódových bodů (Double Byte) představuje každý znak. Vlastnost <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> vrací `false` pro kódování znakové sady DBCS. Můžete načíst objekt kódování pro konkrétní sadu DBCS voláním metody <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType>.|Ve znakové sadě DBCS dvojice kódových bodů (Double Byte) představuje každý znak. Když aplikace zpracovává data sady DBCS, první bajt znaku DBCS (vedoucí bajt) se zpracuje v kombinaci s koncovým bajtem, který hned následuje. Vzhledem k tomu, že jedna dvojice dvoubajtových bodů kódu může představovat různé znaky v závislosti na znakové stránce, toto schéma stále nepovoluje kombinaci dvou jazyků, jako jsou japonština a čínština, ve stejném datovém proudu.|

Tato kódování umožňují pracovat s znaky Unicode a s kódováními, které se nejčastěji používají ve starších verzích aplikací. Kromě toho můžete vytvořit vlastní kódování definováním třídy, která je odvozena z <xref:System.Text.Encoding> a přepsání jejích členů.

### <a name="platform-notes-net-core"></a>Poznámky k platformě: .NET Core

Ve výchozím nastavení .NET Core nezpřístupňuje žádné kódování znakových stránek kromě znakové stránky 28591 a kódování Unicode, jako jsou UTF-8 a UTF-16. Můžete ale přidat kódování znakové stránky nalezené ve standardních aplikacích pro Windows, které cílí na rozhraní .NET do vaší aplikace. Úplné informace najdete v tématu <xref:System.Text.CodePagesEncodingProvider>.

<a name="Selecting"></a>

## <a name="selecting-an-encoding-class"></a>Výběr třídy kódování

Pokud máte příležitost vybrat kódování, které má aplikace používat, měli byste použít kódování Unicode, pokud je to vhodné <xref:System.Text.UTF8Encoding> nebo <xref:System.Text.UnicodeEncoding>. (.NET podporuje také třetí kódování Unicode, <xref:System.Text.UTF32Encoding>.)

Pokud plánujete použít kódování ASCII (<xref:System.Text.ASCIIEncoding>), vyberte místo toho možnost <xref:System.Text.UTF8Encoding>. Tato dvě kódování jsou shodná se znakovou sadou ASCII, ale <xref:System.Text.UTF8Encoding> mají následující výhody:

- Může představovat každý znak Unicode, zatímco <xref:System.Text.ASCIIEncoding> podporuje pouze hodnoty znaků Unicode mezi U + 0000 a U + 007F.

- Poskytuje detekci chyb a lepší zabezpečení.

- Byla vyladěna tak, aby byla co nejrychlejší a měla by být rychlejší než jakékoli jiné kódování. I pro obsah, který je zcela ve formátu ASCII, jsou operace prováděné s <xref:System.Text.UTF8Encoding> rychlejší než operace prováděné s <xref:System.Text.ASCIIEncoding>.

Měli byste zvážit použití <xref:System.Text.ASCIIEncoding> jenom pro starší verze aplikací. Nicméně i u starších aplikací může být <xref:System.Text.UTF8Encoding> lepší volbou z následujících důvodů (předpokládá se výchozí nastavení):

- Pokud má vaše aplikace obsah, který není výhradně ASCII a zakóduje ho pomocí <xref:System.Text.ASCIIEncoding>, každý znak bez ASCII kódování se zakóduje jako otazník (?). Pokud aplikace potom tato data dekóduje, dojde ke ztrátě informací.

- Pokud má vaše aplikace obsah, který není výhradně ASCII, a zakóduje ho pomocí <xref:System.Text.UTF8Encoding>, výsledek se zdá být nečitelný, pokud je interpretován jako ASCII. Pokud však aplikace použije k dekódování těchto dat dekodér UTF-8, data se úspěšně vykoná pomocí odezvy.

Ve webové aplikaci by se měly znaky odeslané klientovi v reakci na webový požadavek projevit kódováním použitým v klientovi. Ve většině případů byste měli nastavit vlastnost <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> na hodnotu vrácenou vlastností <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType>, aby se zobrazil text v kódování, které uživatel očekává.

<a name="Using"></a>

## <a name="using-an-encoding-object"></a>Použití objektu Encoding

Kodér převede řetězec znaků (nejčastěji znaků Unicode) na jeho číselný ekvivalent (Byte). Například můžete použít kodér ASCII k převedení znaků Unicode na ASCII, aby se mohly zobrazit v konzole. Chcete-li provést převod, zavolejte metodu <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType>. Chcete-li určit, kolik bajtů je potřeba k uložení kódovaných znaků před provedením kódování, můžete zavolat metodu <xref:System.Text.Encoding.GetByteCount%2A>.

Následující příklad používá jedno bajtové pole ke kódování řetězců ve dvou samostatných operacích. Udržuje index, který označuje počáteční pozici v bajtovém poli pro další sadu bajtů zakódovaných ve formátu ASCII. Volá metodu <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType>, aby se zajistilo, že bajtové pole je dostatečně velké pro přizpůsobení kódovaného řetězce. Pak zavolá metodu <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> pro kódování znaků v řetězci.

[!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
[!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]

Dekodér převede pole bajtů, které odráží konkrétní kódování znaků, do množiny znaků, buď v poli znaků nebo v řetězci. Chcete-li dekódovat pole bajtů do pole znaků, zavoláte metodu <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType>. Chcete-li dekódovat pole bajtů do řetězce, zavolejte metodu <xref:System.Text.Encoding.GetString%2A>. Chcete-li určit, kolik znaků je potřeba k uložení dekódovaných bajtů před provedením dekódování, můžete zavolat metodu <xref:System.Text.Encoding.GetCharCount%2A>.

Následující příklad kóduje tři řetězce a poté je dekóduje do jednoho pole znaků. Udržuje index, který označuje počáteční pozici v poli znaků pro další sadu dekódových znaků. Volá metodu <xref:System.Text.ASCIIEncoding.GetCharCount%2A>, aby se zajistilo, že je pole znaků dostatečně velké, aby se vešly všechny Dekódovatelné znaky. Pak zavolá metodu <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> k dekódování pole bajtů.

[!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
[!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]

Metody kódování a dekódování třídy odvozené od <xref:System.Text.Encoding> jsou navrženy tak, aby fungovaly na kompletní sadě dat; To znamená, že všechna data, která mají být kódována nebo Dekódovaná, jsou uvedena v jediném volání metody. V některých případech jsou však data k dispozici v datovém proudu a data, která mají být kódována nebo Dekódovaná, mohou být k dispozici pouze ze samostatných operací čtení. K tomu je potřeba, aby operace kódování nebo dekódování pamatovala kterýkoli uložený stav z předchozího vyvolání. Metody tříd odvozené z <xref:System.Text.Encoder> a <xref:System.Text.Decoder> jsou schopny zpracovávat operace kódování a dekódování, které přesahují více volání metody.

Objekt <xref:System.Text.Encoder> pro konkrétní kódování je k dispozici z vlastnosti <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> tohoto kódování. Objekt <xref:System.Text.Decoder> pro konkrétní kódování je k dispozici z vlastnosti <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> tohoto kódování. Pro dekódování operací si všimněte, že třídy odvozené od <xref:System.Text.Decoder> zahrnují metodu <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType>, ale nemají metodu, která by odpovídala <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>.

Následující příklad znázorňuje rozdíl mezi použitím <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> a <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metod dekódování pole bajtů Unicode. Příklad zakóduje řetězec, který obsahuje některé znaky Unicode do souboru, a poté používá dvě metody dekódování k dekódování těchto desíti bajtů současně. Vzhledem k tomu, že náhradní pár vychází z desáté a jedenáctá bajty, je dekódovat v samostatných voláních metody. Jak ukazuje výstup, <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metoda není schopna správně dekódovat bajty a místo toho je nahradí ZNAKem U + FFFD (NAHRAZUJÍCÍ znak). Na druhé straně, metoda <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> může úspěšně dekódovat pole bajtů a získat tak původní řetězec.

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

Pokud znak nemá přesnou shodu v cílovém kódování, kodér se může pokusit namapovat na podobný znak. (Co nejlépe vyhovuje záložnímu řešení, je většinou kódování, nikoli problém dekódování. Existuje několik znakových stránek, které obsahují znaky, které nelze úspěšně namapovat na kódování Unicode.) Nejlepší je jako výchozí pro kódování znakové stránky a dvoubajtové znakové sady, které jsou načteny <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> a <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> přetížení.

> [!NOTE]
> Teoreticky, třídy kódování Unicode poskytované v rozhraní .NET (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding>a <xref:System.Text.UTF32Encoding>) podporují každý znak v každé znakové sadě, takže je lze použít k odstranění vysoce vyhovujících záložním problémům.

Strategie pro nejlepší přizpůsobení se liší u různých znakových stránek. Například pro některé znakové stránky jsou znaky latinky s plnou šířkou mapovány na obecnější znaky s poloviční šířkou. Pro jiné znakové stránky se toto mapování neprovede. I v rámci agresivní strategie nejlepšího přizpůsobení není pro některé znaky v některých kódování dostatek. Například čínský znak nemá žádné rozumné mapování na znakovou stránku 1252. V tomto případě je použit náhradní řetězec. Ve výchozím nastavení je tento řetězec pouze jedním OTAZNÍKem (U + 003F).

> [!NOTE]
> Strategie pro nejlepší přizpůsobení nejsou podrobně dokumentovány. Na webu [konsorcia Unicode](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) je však uvedeno několik kódových stránek. Popis Interpretace souborů mapování najdete v souboru **Readme. txt** v této složce.

V následujícím příkladu je použita znaková stránka 1252 (znaková stránka systému Windows pro jazyky západní Evropa) k ilustraci mapování nejlepšího přizpůsobení a jejich nevýhod. Metoda <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> slouží k načtení objektu kódování pro znakovou stránku 1252. Ve výchozím nastavení používá standardně mapování pro znaky Unicode, které nepodporuje. V tomto příkladu se vytvoří instance řetězce, který obsahuje tři znaky, které nepatří do ASCII – BRAILLOVO písmo latinky S (U + 24C8), horní index pět (u + 2075) a nekonečno (U + 221E) – oddělené mezerami. Jak ukazuje výstup z příkladu, při kódování řetězce jsou tři původní znaky bez mezer nahrazeny OTAZNÍKem (U + 003F), ČÍSLICí pět (U + 0035) a ČÍSLICí osm (U + 0038). ČÍSLICE osm je obzvláště špatná náhrada pro nepodporovaný nekonečný znak a otazník indikuje, že pro původní znak nebylo k dispozici žádné mapování.

[!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
[!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]

Mapování nejlepšího hlediska je výchozím chováním pro objekt <xref:System.Text.Encoding>, který kóduje data Unicode na data znakové stránky a obsahuje starší aplikace, které se na toto chování spoléhají. Většina nových aplikací se však musí z bezpečnostních důvodů vyhnout tomu, co nejlépe vyhovuje chování. Například aplikace by neměly uvádět název domény pomocí kódování, které nejlépe vyhovuje.

> [!NOTE]
> Pro kódování můžete také implementovat vlastní sekundární mapování pro nejlepší přizpůsobení. Další informace najdete v části [implementace vlastní nouzové strategie](../../../docs/standard/base-types/character-encoding.md#Custom) .

Pokud je pro objekt kódování výchozí možnost nejlepšího nastavení, můžete zvolit jinou záložní strategii při načítání <xref:System.Text.Encoding> objektu voláním <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> nebo <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> přetížení. Následující část obsahuje příklad, který nahradí každý znak, který nelze namapovat na znakovou stránku 1252 hvězdičkou (*).

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

<a name="Replacement"></a>

### <a name="replacement-fallback"></a>Náhradní záložní

Pokud znak nemá přesnou shodu v cílovém schématu, ale neexistuje žádný vhodný znak, který lze namapovat na, aplikace může určit náhradní znak nebo řetězec. Toto je výchozí chování pro dekodér Unicode, které nahradí každou posloupnost dvou bajtů, kterou nemůže dekódovat pomocí REPLACEMENT_CHARACTER (U + FFFD). Je také výchozím chováním třídy <xref:System.Text.ASCIIEncoding>, která nahradí každý znak, který nemůže kódování ani dekódovat pomocí otazníku. Následující příklad ukazuje nahrazení znaku pro řetězec Unicode z předchozího příkladu. Jak výstup ukazuje, každý znak, který nelze dekódovat do bajtové hodnoty ASCII, je nahrazen hodnotou 0x3F, což je kód ASCII pro otazník.

[!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
[!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]

Rozhraní .NET zahrnuje třídy <xref:System.Text.EncoderReplacementFallback> a <xref:System.Text.DecoderReplacementFallback>, které nahradí náhradní řetězec, pokud znak není přesně mapován v operaci kódování nebo dekódování. Ve výchozím nastavení je tento nahrazující řetězec otazník, ale můžete volat přetížení konstruktoru třídy pro výběr jiného řetězce. Obvykle je nahrazující řetězec jedním znakem, přestože to není požadavek. Následující příklad změní chování kodéru kódové stránky 1252 vytvořením objektu <xref:System.Text.EncoderReplacementFallback>, který používá hvězdičku (*) jako náhradní řetězec.

[!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
[!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]

> [!NOTE]
> Pro kódování můžete také implementovat náhradní třídu. Další informace najdete v části [implementace vlastní nouzové strategie](../../../docs/standard/base-types/character-encoding.md#Custom) .

Kromě OTAZNÍKu (U + 003F) se znak nahrazení Unicode (U + FFFD) běžně používá jako náhradní řetězec, zejména při dekódování sekvencí bajtů, které se nedají úspěšně přeložit do znaků Unicode. Můžete však vybrat libovolný řetězec pro nahrazení a může obsahovat více znaků.

<a name="Exception"></a>

### <a name="exception-fallback"></a>Záložní výjimka

Namísto poskytnutí nejlepšího náhradního nebo náhradního řetězce může kodér vyvolat <xref:System.Text.EncoderFallbackException>, pokud není schopen zakódovat sadu znaků a dekodér může vyvolat <xref:System.Text.DecoderFallbackException>, pokud není schopen dekódovat pole bajtů. Chcete-li vyvolat výjimku při operacích kódování a dekódování, zadejte objekt <xref:System.Text.EncoderExceptionFallback> a objekt <xref:System.Text.DecoderExceptionFallback>, v uvedeném pořadí, do metody <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType>. Následující příklad znázorňuje metodu Fallback s výjimkou třídy <xref:System.Text.ASCIIEncoding>.

[!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
[!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]

> [!NOTE]
> Můžete také implementovat vlastní obslužnou rutinu výjimky pro operaci kódování. Další informace najdete v části [implementace vlastní nouzové strategie](../../../docs/standard/base-types/character-encoding.md#Custom) .

Objekty <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> poskytují následující informace o stavu, který způsobil výjimku:

- Objekt <xref:System.Text.EncoderFallbackException> obsahuje metodu <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A>, která označuje, zda znak nebo znaky, které nelze zakódovat, reprezentují neznámý náhradní pár (v takovém případě metoda vrátí `true`) nebo neznámý jediný znak (v takovém případě metoda vrátí `false`). Znaky v náhradní dvojici jsou k dispozici z vlastností <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> a <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType>. Z vlastnosti <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> je k dispozici neznámý jediný znak. Vlastnost <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> označuje pozici v řetězci, na které byl nalezen první znak, který nelze zakódovat.

- Objekt <xref:System.Text.DecoderFallbackException> obsahuje vlastnost <xref:System.Text.DecoderFallbackException.BytesUnknown%2A>, která vrací pole bajtů, které nelze dekódovat. Vlastnost <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> označuje počáteční pozici neznámých bajtů.

I když objekty <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> poskytují dostatečné diagnostické informace o výjimce, neposkytují přístup k vyrovnávací paměti pro kódování nebo dekódování. Proto neumožňují nahradit nebo opravit neplatná data v rámci metody Encoding nebo dekódování.

<a name="Custom"></a>

## <a name="implementing-a-custom-fallback-strategy"></a>Implementace vlastní nouzové strategie

Kromě nejlepšího mapování, které je implementováno interně pomocí znakových stránek, .NET zahrnuje následující třídy pro implementaci záložní strategie:

- K nahrazení znaků v operacích kódování použijte <xref:System.Text.EncoderReplacementFallback> a <xref:System.Text.EncoderReplacementFallbackBuffer>.

- K nahrazení znaků v operacích dekódování použijte <xref:System.Text.DecoderReplacementFallback> a <xref:System.Text.DecoderReplacementFallbackBuffer>.

- Použijte <xref:System.Text.EncoderExceptionFallback> a <xref:System.Text.EncoderExceptionFallbackBuffer> k vyvolání <xref:System.Text.EncoderFallbackException>, když znak nelze kódovat.

- Použijte <xref:System.Text.DecoderExceptionFallback> a <xref:System.Text.DecoderExceptionFallbackBuffer> k vyvolání <xref:System.Text.DecoderFallbackException>, když znak nelze dekódovat.

Pomocí následujících kroků můžete navíc implementovat vlastní řešení, které se nejlépe hodí pro nouzové účely, náhradní zálohu nebo výjimku.

1. Odvození třídy z <xref:System.Text.EncoderFallback> pro operace kódování a z <xref:System.Text.DecoderFallback> pro operace dekódování.

2. Odvození třídy z <xref:System.Text.EncoderFallbackBuffer> pro operace kódování a z <xref:System.Text.DecoderFallbackBuffer> pro operace dekódování.

3. V případě Fallback pro výjimku, pokud předdefinované <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> třídy nevyhovují vašim potřebám, odvozuje třídu od objektu výjimky, jako je například <xref:System.Exception> nebo <xref:System.ArgumentException>.

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Odvození z EncoderFallback nebo DecoderFallback

Chcete-li implementovat vlastní nouzové řešení, je nutné vytvořit třídu, která dědí z <xref:System.Text.EncoderFallback> pro operace kódování a z <xref:System.Text.DecoderFallback> pro operace dekódování. Instance těchto tříd jsou předány metodě <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> a slouží jako prostředník mezi třídou kódování a záložní implementací.

Při vytváření vlastního záložního řešení pro kodér nebo dekodér je nutné implementovat následující členy:

- Vlastnost <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType>, která vrací maximální možný počet znaků, který nejlépe vyhovuje, nahrazuje nebo má záložní záloha, může vrátit jeden znak. U vlastní nouzové výjimky má jeho hodnota hodnotu nula.

- Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType>, která vrací vlastní <xref:System.Text.EncoderFallbackBuffer> nebo <xref:System.Text.DecoderFallbackBuffer> implementaci. Metoda je volána kodérem při výskytu prvního znaku, který není schopen úspěšně kódovat, nebo dekodérem, když nalezne první bajt, který nemůže úspěšně dekódovat.

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Odvození z EncoderFallbackBuffer nebo DecoderFallbackBuffer

K implementaci vlastního záložního řešení je nutné také vytvořit třídu, která dědí z <xref:System.Text.EncoderFallbackBuffer> pro operace kódování a z <xref:System.Text.DecoderFallbackBuffer> pro operace dekódování. Instance těchto tříd jsou vráceny metodou <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> tříd <xref:System.Text.EncoderFallback> a <xref:System.Text.DecoderFallback>. Metoda <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> je volána kodérem, když nalezne první znak, který není možné kódovat, a metoda <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> je volána dekodérem, když narazí na jeden nebo více bajtů, které není možné dekódovat. Třídy <xref:System.Text.EncoderFallbackBuffer> a <xref:System.Text.DecoderFallbackBuffer> poskytují záložní implementaci. Každá instance představuje vyrovnávací paměť, která obsahuje záložní znaky, které nahradí znak, který nelze zakódovat, nebo posloupnost bajtů, které nelze dekódovat.

Při vytváření vlastního záložního řešení pro kodér nebo dekodér je nutné implementovat následující členy:

- Metoda <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> je volána kodérem k poskytnutí záložní vyrovnávací paměti s informacemi o znaku, který nelze kódovat. Vzhledem k tomu, že znak pro kódování může být náhradní pár, je tato metoda přetížená. Jednomu přetížení se předal znak, který se má zakódovat, a jeho index v řetězci. Druhé přetížení je předání vysoké a nízké náhrady spolu s indexem v řetězci. Metoda <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> je volána dekodérem k poskytnutí záložní vyrovnávací paměti s informacemi o bajtech, které nelze dekódovat. Tato metoda předává pole bajtů, které nelze dekódovat, spolu s indexem prvního bajtu. Metoda Fallback by měla vracet `true`, pokud záložní vyrovnávací paměť může dodat nejlépe vyhovující nebo náhradní znak nebo znaky. v opačném případě by měla vracet `false`. Pro zálohu výjimky by měla metoda Fallback vyvolat výjimku.

- Metoda <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType>, která je volána opakovaně nástrojem Encoder nebo dekodérem pro získání dalšího znaku z záložní vyrovnávací paměti. Pokud byly vráceny všechny záložní znaky, metoda by měla vracet U + 0000.

- Vlastnost <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType>, která vrací počet znaků zbývajících v záložní vyrovnávací paměti.

- Metoda <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType>, která přesouvá aktuální pozici v záložní vyrovnávací paměti na předchozí znak.

- Metoda <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> nebo <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType>, která znovu inicializuje záložní vyrovnávací paměť.

Pokud je nouzová implementace ideálním řešením nebo náhradní zálohou, třídy odvozené od <xref:System.Text.EncoderFallbackBuffer> a <xref:System.Text.DecoderFallbackBuffer> také udržovat dvě soukromá pole instance: přesný počet znaků ve vyrovnávací paměti; a indexem dalšího znaku ve vyrovnávací paměti, který se má vrátit.

### <a name="an-encoderfallback-example"></a>EncoderFallback příklad

Předchozí příklad používá náhradní zálohu k nahrazení znaků Unicode, které neodpovídaly znakům ASCII hvězdičkou (*). Následující příklad používá vlastní implementaci záložní implementace, která je vhodná pro zajištění lepšího mapování znaků, které nejsou ASCII.

Následující kód definuje třídu s názvem `CustomMapper`, která je odvozena z <xref:System.Text.EncoderFallback> pro zpracování nejlepšího mapování znaků, které nejsou ASCII. Jeho metoda `CreateFallbackBuffer` vrátí objekt `CustomMapperFallbackBuffer`, který poskytuje <xref:System.Text.EncoderFallbackBuffer> implementaci. Třída `CustomMapper` používá objekt <xref:System.Collections.Generic.Dictionary%602> k ukládání mapování nepodporovaných znaků Unicode (hodnota klíče) a jejich odpovídajících 8 bitových znaků (které jsou uloženy ve dvou po sobě jdoucích bajtech v 64ovém čísle bitové kopie). Chcete-li toto mapování zpřístupnit pro záložní vyrovnávací paměť, je instance `CustomMapper` předána jako parametr konstruktoru `CustomMapperFallbackBuffer` třídy. Vzhledem k tomu, že nejdelší mapování je řetězec "INF" pro znak Unicode U + 221E, vlastnost `MaxCharCount` vrátí hodnotu 3.

[!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
[!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]

Následující kód definuje třídu `CustomMapperFallbackBuffer`, která je odvozena z <xref:System.Text.EncoderFallbackBuffer>. Slovník, který obsahuje mapování nejlepšího umístění a který je definován v instanci `CustomMapper`, je k dispozici z jeho konstruktoru třídy. Jeho metoda `Fallback` vrátí `true`, pokud některý ze znaků Unicode, které kodér ASCII nemůže kódovat, je definován ve slovníku mapování; v opačném případě vrátí `false`. Pro každou zálohu proměnná Private `count` označuje počet znaků, které se budou vracet, a soukromá `index` proměnná označuje pozici v vyrovnávací paměti řetězců, `charsToReturn`dalšího znaku, který se má vrátit.

[!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
[!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]

Následující kód potom vytvoří instanci objektu `CustomMapper` a předá jeho instanci metodě <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType>. Výstup označuje, že pro záložní implementaci, který nejlépe vyhovuje, se v původním řetězci zpracovávají tři znaky jiné než ASCII.

[!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
[!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]

## <a name="see-also"></a>Viz také:

- <xref:System.Text.Encoder>
- <xref:System.Text.Decoder>
- <xref:System.Text.DecoderFallback>
- <xref:System.Text.Encoding>
- <xref:System.Text.EncoderFallback>
- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
