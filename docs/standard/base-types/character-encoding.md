---
title: Kódování znaků v rozhraní .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cac7e0fca4a009b7f5b6f677abed70cf2519052d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138471"
---
# <a name="character-encoding-in-net"></a>Kódování znaků v rozhraní .NET
Znaky jsou abstraktní entity, které může být reprezentována mnoha různými způsoby. Kódování znaků je systém, který páry každý znak v podporované znakové sady s některá z hodnot, který představuje daný znak. Například morseovkou je znak kódování této páry každý znak v latinku pomocí vzoru tečky a spojovníky, které jsou vhodné pro přenos přes telegrafní řádky. Znak kódování dvojice počítačů pro každý znak v podporované znakové sady s číselnou hodnotu, která představuje tento znak. Kódování znaků má dvě různé součásti:  
  
-   Kodér, což znamená posloupnost znaků na sekvenci číselných hodnot (v bajtech).  
  
-   Dekodér, což znamená posloupnost bajtů na sekvenci znaků.  
  
 Kódování znaků popisuje pravidla, podle kterých kodér a dekodér pracovat. Například <xref:System.Text.UTF8Encoding> třída popisuje pravidla pro kódování a dekódování z formátu pro Unicode transformace 8 bitů (UTF-8), který používá jednu až čtyři bajty k zastupování jednoho znaku Unicode. Kódování a dekódování můžete také zahrnout ověřování. Například <xref:System.Text.UnicodeEncoding> třída zkontroluje všechny náhrady, abyste měli jistotu, představují platný náhradní páry. (Náhradní pár obsahuje znak s bodem kódu od U + D800 do U + DBFF následovaný znakem s bodem kódu od U + DC00 do U + DFFF.)  Nouzová strategie určuje způsob, jakým zpracovává kodéru neplatné znaky nebo způsob, jakým zpracovává dekodér neplatné bajty.  
  
> [!WARNING]
>  Kódování třídy .NET poskytují způsob, jak ukládat a převádí znak data. Nesmí se používají k ukládání binárních dat ve formátu řetězce. V závislosti na kódování použité, převádění binární data na řetězec formátu pomocí tříd kódování můžete zavést neočekávané chování a produkovat nesprávné nebo poškozená data. Chcete-li binární data převést do formátu řetězce, použijte <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metody.  
  
 .NET používá kódování UTF-16 (představované <xref:System.Text.UnicodeEncoding> třídy) k reprezentaci znaků a řetězce. Aplikace, které se zaměřují modul common language runtime používají kodérů pro mapování reprezentace znaku Unicode podporuje modul common language runtime na jiná schémata kódování. Dekodérů používají k mapování znaků z kódování Unicode kódování na kódování Unicode.  
  
 Toto téma se skládá z následujících částí:  
  
-   [Kódování v .NET](../../../docs/standard/base-types/character-encoding.md#Encodings)  
  
-   [Výběr kódování třídy](../../../docs/standard/base-types/character-encoding.md#Selecting)  
  
-   [Pomocí objektu kódování](../../../docs/standard/base-types/character-encoding.md#Using)  
  
-   [Výběr strategie použití náhradní lokality](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)  
  
-   [Implementace vlastního nouzová strategie](../../../docs/standard/base-types/character-encoding.md#Custom)  
  
<a name="Encodings"></a>   
## <a name="encodings-in-net"></a>Kódování v .NET  
 Všechny znakové kódování třídy v rozhraní .NET dědí z <xref:System.Text.Encoding?displayProperty=nameWithType> třídu, která je abstraktní třída, která definuje funkce, které jsou společné pro všechny kódování znaků. Pro přístup k jednotlivým kódování objekty implementováno v rozhraní .NET, postupujte takto:  
  
-   Použití statických vlastností <xref:System.Text.Encoding> třídu, která vrátí objekty, které představují kódování standard znaků, která je k dispozici v rozhraní .NET (ASCII, UTF-7, UTF-8, UTF-16 a UTF-32). Například <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> vrátí vlastnost <xref:System.Text.UnicodeEncoding> objektu. Každý objekt používá nahrazení náhradní řetězce popisovače, které nelze dekódovat a počet bajtů, které nelze dekódovat. (Další informace najdete v tématu [nahrazení záložní](../../../docs/standard/base-types/character-encoding.md#Replacement) části.)  
  
-   Volání konstruktoru třídy kódování společnosti. Tímto způsobem můžete vytvořit instanci objektů pro ASCII, UTF-7, UTF-8, UTF-16 a UTF-32 kódování. Ve výchozím nastavení každý objekt používá náhradní použití náhradní lokality pro zpracování řetězců, které nelze dekódovat a počet bajtů, které nelze dekódovat, ale můžete zadat, že místo toho by měl vyvolána výjimka. (Další informace najdete v tématu [nahrazení záložní](../../../docs/standard/base-types/character-encoding.md#Replacement) a [výjimka záložní](../../../docs/standard/base-types/character-encoding.md#Exception) oddíly.)  
  
-   Volání <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> konstruktor a předejte jí celé číslo, které představuje kódování. Standard kódování objekty pomocí záložní nahrazení a znakovou stránku a dvoubajtové znakové sady (DBCS) kódování objekty použití přizpůsobený nouzového řešení ověření pomocí popisovač řetězce, které nelze dekódovat a počet bajtů, které nelze dekódovat. (Další informace najdete v tématu [Best-Fit záložní](../../../docs/standard/base-types/character-encoding.md#BestFit) části.)  
  
-   Volání <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metoda, která vrátí všechny standardní režim, znakovou stránku nebo DBCS kódování k dispozici v rozhraní .NET. Přetížení umožňují určit objekt pro použití náhradní lokality pro kodér a dekodér.  
  
> [!NOTE]
>  Unicode Standard přiřadí bod kódu (číslo) a název každý znak v každé podporované skriptu. Například znak "A" představuje bod kódu U + 0041 a název "LATINKY velké písmeno A". Kódování formátu transformace Unicode (UTF) definovat způsoby, jak kódovat tohoto bodu kódu na sekvenci jednoho nebo více bajtů. Schéma kódování Unicode zjednodušuje vývoj světově připravených aplikací, protože umožňuje znaky z jakékoli znakovou sadu dat v jednom kódování. Vývojáři aplikací se už nemusíte udržovat přehled o schéma kódování, která byla použita k vytvoření znaků pro konkrétní jazyk nebo zápis systému a dat je možné sdílet mezi systémy mezinárodně bez poškození.  
>   
>  .NET podporuje tři kódování definované ve standardu Unicode: UTF-8, UTF-16 a UTF-32. Další informace najdete v tématu ve standardu Unicode na [Unicode domovskou stránku](https://www.unicode.org/).  
  
 Informace o kódování k dispozici v rozhraní .NET můžete načíst pomocí volání <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> metody. .NET podporuje znak kódování systémů uvedených v následující tabulce.  
  
|Kódování|Třída|Popis|Výhody a nevýhody|  
|--------------|-----------|-----------------|-------------------------------|  
|ASCII|<xref:System.Text.ASCIIEncoding>|Zakóduje omezený rozsah znaků pomocí nižší sedm bitů na bajt.|Protože toto kódování podporuje pouze znakových hodnot z U + 0000 až U + 007F, ve většině případů je nedostatečná pro mezinárodní aplikace.|  
|UTF-7|<xref:System.Text.UTF7Encoding>|Reprezentuje znaků jako sekvence 7bitových znaků ASCII. Ne-ASCII Unicode znaky jsou reprezentovány řídicí sekvence znaků ASCII.|Kódování UTF-7 podporuje diskusní skupiny protokoly a protokoly, například e-mailu. Ale UTF-7 není zejména zabezpečené a robustní. V některých případech se změna jeden bit může výrazně tak pozměnit výklad celý řetězec UTF-7. V ostatních případech můžete kódovat různé řetězce UTF-7 stejný text. Pořadí, které zahrnují jiné znaky než ASCII UTF-7 vyžaduje více místa než UTF-8 a kódování/dekódování je pomalejší. V důsledku toho používejte UTF-8 namísto UTF-7-li to možné.|  
|UTF-8|<xref:System.Text.UTF8Encoding>|Jako posloupnost jednu až čtyři bajty představuje každý bod kódu Unicode.|UTF-8 podporuje velikosti 8 bitů dat a pracuje s mnoha existujících systémech. UTF-8 pro řadu znaků ASCII je stejné jako kódování ASCII a širší sadu znaků. Však pro skripty čínština – Japonština-Korejština (CJK), UTF-8 můžou vyžadovat třech bajtech pro každý znak a mohou způsobit větší velikosti dat než UTF-16. Všimněte si, že někdy množství data ve standardu ASCII, jako jsou například značky HTML, zarovná zvětšení velikosti pro rozsah CJK.|  
|UTF-16|<xref:System.Text.UnicodeEncoding>|Představuje každý bod kódu Unicode jako posloupnost jednu nebo dvě 16bitová celá čísla. Nejběžnější znaky znakové sady Unicode vyžadují pouze jeden bod kódu UTF-16, i když doplňkové znaky znakové sady Unicode (U + 10000 nebo novější) vyžadují dva body kódu náhradní UTF-16. Podporují se obě pořadí bajtů ve formátu little endian a formát big-endian.|Kódování UTF-16 modul common language runtime se používá k reprezentování <xref:System.Char> a <xref:System.String> hodnoty a to se používá v operačním systému Windows k reprezentaci `WCHAR` hodnoty.|  
|UTF-32|<xref:System.Text.UTF32Encoding>|Představuje každý bod kódu Unicode jako 32bitové celé číslo. Podporují se obě pořadí bajtů ve formátu little endian a formát big-endian.|Kódování UTF-32 se používá při aplikace chcete vyhnout chování náhradní bod kódu kódování UTF-16 operačních systémech, pro které je příliš důležité kódovaného místa. Jeden glyfy vykresleného v zobrazení může být zakódován stále s více než jeden znak kódování UTF-32.|  
|Kódování ANSI/ISO||Poskytuje podporu pro širokou škálu znakové stránky. V operačních systémech Windows znakové stránky slouží k podpoře konkrétní jazyk nebo skupinu jazyků. Tabulka obsahující seznam znakových stránek podporovaných .NET, najdete v článku <xref:System.Text.Encoding> třídy. Objekt kódování pro konkrétní kódové stránky můžete načíst pomocí volání <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metody.|Znaková stránka obsahuje 256 body kódu a je založený na nule. Ve většině znakových stránek body kódu 0 až 127 představují znaková sada ASCII a kódových bodů 128 až 255 se výrazně liší mezi znakové stránky. Například znaková stránka 1252 zajišťující znaky latinky písmových systémech, včetně angličtinu, němčinu a francouzštinu. Poslední bod 128 kód v znaková stránka 1252 obsahovat znaky znaky s diakritikou. Znaková stránka 1253 obsahuje kódy znaků, které jsou nutné v řecké písmo. Poslední bod 128 kód v kódové stránce 1253 obsahovat znaků řecké abecedy. V důsledku toho aplikaci, která závisí na znakové stránky ANSI nelze uložit, řečtina a němčina ve stejném textového datového proudu pokud obsahuje identifikátor, který označuje odkazované znakovou stránku.|  
|Dvoubajtové znakové sady (DBCS) kódování||Podporuje jazyky, jako je čínštiny, japonštiny a korejštiny, které obsahují více než 256 znaků. V sadě DBCS pár nástroje kódových bodů (double byte) představuje každý znak. <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> Vrátí vlastnost `false` pro znaky DBCS kódování. Kódování objektu můžete načíst pro konkrétní DBCS voláním <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metody.|V sadě DBCS pár nástroje kódových bodů (double byte) představuje každý znak. Když aplikace zpracovává DBCS data, první bajt znaku DBCS (vedoucí bajt) jsou zpracovávána v kombinaci s druhý bajt, který bezprostředně následuje. Vzhledem k tomu, že jeden pár dvoubajtových kódových bodů může představovat různých znaků v závislosti na znakovou stránku, toto schéma stále neumožňuje kombinací dva jazyků, jako je například japonštinu a čínštinu ve stejném datovém proudu.|  
  
 Těchto kódováních umožňují pracovat se znaky Unicode, a také s kódování, které se běžně používají starší verzi aplikace. Kromě toho můžete vytvořit vlastního kódování tak, že definujete třídu, která je odvozena z <xref:System.Text.Encoding> a přepsáním jejích členů.  
  
### <a name="platform-notes-includenetcoreincludesnet-core-mdmd"></a>Poznámky k platformě: [!INCLUDE[net_core](../../../includes/net-core-md.md)]  
 Ve výchozím nastavení [!INCLUDE[net_core](../../../includes/net-core-md.md)] Nedovolte, aby byly k dispozici žádné kódování znakových stránek než znaková stránka 28591 a kódování Unicode, jako je například UTF-8 a UTF-16. Můžete však přidat kódování znakových stránek, které jsou součástí standardní aplikace Windows, které se zaměřují .NET do vaší aplikace. Podrobnější informace najdete v článku <xref:System.Text.CodePagesEncodingProvider> tématu.  
  
<a name="Selecting"></a>   
## <a name="selecting-an-encoding-class"></a>Výběr kódování třídy  
 Pokud budete mít možnost vybrat kódování používané aplikace, měli byste použít kódování Unicode, pokud možno buď <xref:System.Text.UTF8Encoding> nebo <xref:System.Text.UnicodeEncoding>. (.NET podporuje také třetí kódování Unicode, <xref:System.Text.UTF32Encoding>.)  
  
 Pokud máte v úmyslu používat kódování ASCII (<xref:System.Text.ASCIIEncoding>), zvolte <xref:System.Text.UTF8Encoding> místo. Dvě kódování jsou stejná pro znaková sada ASCII, ale <xref:System.Text.UTF8Encoding> má následující výhody:  
  
-   Vzhledem k tomu může představovat každý znak Unicode <xref:System.Text.ASCIIEncoding> podporuje pouze hodnoty znaků Unicode mezi U + 0000 a U + 007F.  
  
-   Poskytuje lepší zabezpečení a detekce chyb.  
  
-   Má se vyladěné tak, aby se co nejrychleji a mělo by být rychlejší než jiné kódování. I pro obsah, který je zcela ASCII, provést operace s <xref:System.Text.UTF8Encoding> jsou rychlejší než operace prováděné s <xref:System.Text.ASCIIEncoding>.  
  
 Měli byste zvážit použití <xref:System.Text.ASCIIEncoding> pouze pro starší verze aplikací. Ale i pro starší verze aplikací, <xref:System.Text.UTF8Encoding> může být lepší volbou z následujících důvodů (za předpokladu, že výchozí nastavení):  
  
-   Pokud aplikace obsahuje obsah, který není striktně ASCII a kóduje ho s <xref:System.Text.ASCIIEncoding>, zakóduje jednotlivé znaky nepocházející ze sady ASCII jako otazník (?). Aplikace pak dekóduje tato data, dojde ke ztrátě informací.  
  
-   Pokud aplikace obsahuje obsah, který není striktně ASCII a kóduje ho s <xref:System.Text.UTF8Encoding>, výsledek nesrozumitelný, pokud interpretován jako ASCII. Nicméně pokud aplikace pak pomocí dekodér UTF-8 k dekódování dat, data provede odezvy úspěšně.  
  
 Ve webové aplikaci by měly odrážet odeslat klientovi v reakci na webový požadavek, znaky kódování použité na straně klienta. Ve většině případů byste měli nastavit <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> vlastnost na hodnotu vrácenou <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> vlastnosti k zobrazení textu v kódování, které uživatel očekává.  
  
<a name="Using"></a>   
## <a name="using-an-encoding-object"></a>Pomocí objektu kódování  
 Kodér převede řetězec znaků (nejčastěji, znaky Unicode) na jeho číselnou hodnotu (bajty) ekvivalentní. Můžete například použít kodér ASCII převést na ASCII znaky znakové sady Unicode, tak, že je možné zobrazit v konzole. K provedení převodu zavolat <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> metody. Pokud chcete určit, kolik bajtů jsou potřeba k uložení kódovaných znaků, než se pustíte do kódování, můžete volat <xref:System.Text.Encoding.GetByteCount%2A> metody.  
  
 Následující příklad používá jeden bajtové pole ke kódování řetězce v dvě samostatné operace. Udržuje index určující počáteční pozici v bajtové pole pro další sadu kódováním ASCII bajtů. Volá <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> metodou, jak zajistit, že je příliš velká tak, aby vyhovovaly kódovaný řetězec bajtové pole. Poté zavolá <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metoda ke kódování znaků v řetězci.  
  
 [!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
 [!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]  
  
 Dekodér převede bajtové pole, která odráží určitý znak kódování do sady znaků, pole znaků nebo v řetězci. Chcete-li dekódovat bajtové pole na pole znaků, zavolejte <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metody. Chcete-li dekódovat bajtové pole na řetězec, zavolejte <xref:System.Text.Encoding.GetString%2A> metody. Pokud chcete určit, kolik znaků jsou potřeba k uložení dekódovaný bajtů před provedením dekódování, můžete volat <xref:System.Text.Encoding.GetCharCount%2A> metody.  
  
 V následujícím příkladu tři řetězce kóduje a dekóduje je do jediného pole znaků. Udržuje index určující počáteční pozici pro další sadu dekódované znaky jako pole znaků. Volá <xref:System.Text.ASCIIEncoding.GetCharCount%2A> metodou, jak zajistit, že je příliš velká pro dekódované znaky pole znaků. Poté zavolá <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metoda dekódovat bajtové pole.  
  
 [!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
 [!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]  
  
 Kódování a dekódování metody dané třídy odvozené z <xref:System.Text.Encoding> jsou navrženy pro práci na kompletní sadu dat; to znamená, se v rámci jednoho volání metody pochází všechna data na kódován nebo dekódován. V některých případech se ale data jsou k dispozici v datovém proudu a data, která mají být kódován nebo dekódován může být k dispozici pouze v samostatné operace čtení. To vyžaduje kódování nebo dekódování operace pamatovat jakýkoliv uložený stav z jeho předchozí volání. Metody třídy odvozené z <xref:System.Text.Encoder> a <xref:System.Text.Decoder> dokážou zpracovat kódování a dekódování operace napříč několika volání metody.  
  
 <xref:System.Text.Encoder> Objektu pro konkrétní kódování je k dispozici z kódování na <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> vlastnost. A <xref:System.Text.Decoder> objektu pro konkrétní kódování je k dispozici z kódování na <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> vlastnost. Dekódování operace, mějte na paměti, že třídy odvozené z <xref:System.Text.Decoder> zahrnout <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metody, ale nemáte metodu, která odpovídá <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>.  
  
 Následující příklad ukazuje rozdíl mezi použitím nástrojů <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> a <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metody dekódování pole bajtů kódování Unicode. V příkladu kóduje řetězec, který obsahuje některé znaky Unicode do souboru a potom použije dvě metody dekódování k dekódování deset bajtů v čase. Vzhledem k tomu, že dojde k náhradní pár v bajtech desátý a jedenáctý, je dekódováno v samostatné metodě volání. Jak výstup znázorňuje, <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metoda není schopen správně dekódování bajty a místo toho je nahradí U + FFFD (náhradní znak). Na druhé straně <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metoda je úspěšně dekódovat bajtové pole pro získání původní řetězec.  
  
 [!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
 [!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]  
  
<a name="FallbackStrategy"></a>   
## <a name="choosing-a-fallback-strategy"></a>Výběr strategie použití náhradní lokality  
 Pokud metoda se pokusí k zakódování nebo dekódování znak, ale neexistuje žádné mapování, musí implementovat nouzová strategie, která určuje způsob zpracování neúspěšných mapování. Existují tři typy použití náhradní lokality strategií:  
  
-   Přizpůsobený použití náhradní lokality  
  
-   Náhradní použití náhradní lokality  
  
-   Výjimka použití náhradní lokality  
  
> [!IMPORTANT]
>  Nejběžnějších problémů v kódování operací dojít, když znak Unicode nelze mapovat na konkrétní kódové stránky kódování. Nejběžnějších problémů v dekódování operací dojít, když sekvence neplatný typ byte nelze přeložit na platné znaky Unicode. Z těchto důvodů měli byste vědět záložní strategii, kterou používá určitý objekt kódování. Kdykoli je to možné, měli byste určit nouzová strategie používá objekt kódování, když vytvoříte instanci objektu.  
  
<a name="BestFit"></a>   
### <a name="best-fit-fallback"></a>Přizpůsobený použití náhradní lokality  
 Znak nemá přesnou shodu v kódování cílové verze, můžete zkusit kodér mapovat na podobně jako znak. (Přizpůsobený element fallback je většinou kódování místo dekódování problém. Existují velmi málo znakových stránek, které obsahují znaky, které nelze úspěšně namapován na kódování Unicode). Přizpůsobený fallback je výchozí znaková stránka a dvoubajtové znakové sady kódování, které jsou načteny <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> a <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> přetížení.  
  
> [!NOTE]
>  Teoreticky vzato kódování Unicode třídy zadaný v rozhraní .NET (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding>, a <xref:System.Text.UTF32Encoding>) podporují každý znak v každé znakové sadě, takže je možné odstranit přizpůsobený záložní problémy.  
  
 Přizpůsobený strategie lišit pro různé znakové stránky. Například pro některé kódové stránky, znaky latinky s plnou šířkou mapu, aby běžné znaky latinky poloviční šířku. Toto mapování není provedeno pro jiné znakové stránky. I v rámci agresivní strategie přizpůsobený neexistuje žádný vůbec vhodný pro některé znaky v některých kódování. Například čínský znak nemá žádné přiměřené mapování na znaková stránka 1252. V takovém případě se používá řetězci pro nahrazení. Ve výchozím nastavení tento řetězec představuje pouze jednu OTAZNÍK (U + 003F).  
  
> [!NOTE]
>  Přizpůsobený strategie nejsou podrobně zdokumentovány. Ale několik znakové stránky jsou zdokumentované v [Unicode Consortium](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) webu. Podívejte se prosím **readme.txt** soubor v této složce popis toho, jak interpretovat mapování souborů.
  
 Následující příklad používá znakovou stránkou 1252 (znaková stránka Windows západní evropských jazyků) pro ilustraci nejlepšího mapování a jejích nevýhod. <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> Metoda se používá k načtení objektu kódování pro znaková stránka 1252. Ve výchozím nastavení použije přizpůsobený mapování znaků Unicode, které se nepodporuje. Tento příklad vytvoří řetězec, který obsahuje tři jiné znaky než ASCII - KRUHU S VELKÝM PÍSMENEM LATIN (U + 24C 8), horní index pěti (U + 2075) a NEKONEČNO (U + 221E) - oddělené mezerami. Jak výstup z příkladu ukazuje, kdy je zakódovaný řetězec, jsou tři původní znaky bez mezery nahrazené OTAZNÍK (U + 003F), PĚT ČÍSLIC (U + 0035) a OSMI ČÍSLICE (U + 0038). ČÍSLICE 8 je zvláště špatné nahrazení pro nepodporovaný znak NEKONEČNO a OTAZNÍK označuje, že nebylo k dispozici pro původní znakovou žádné mapování.  
  
 [!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
 [!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]  
  
 Nejlepšího mapování je výchozí chování <xref:System.Text.Encoding> objekt, který kóduje Unicode data data znakové stránky a starší verze aplikace, které jsou závislé na toto chování. Většina nových aplikací se ale měli vyhnout přizpůsobený chování z bezpečnostních důvodů. Aplikace by neměla například umístit názvu domény prostřednictvím nejvhodnější kódování.  
  
> [!NOTE]
>  Můžete také implementovat vlastní přizpůsobený záložní mapování pro kódování. Další informace najdete v tématu [implementaci strategie použití náhradní lokality vlastní](../../../docs/standard/base-types/character-encoding.md#Custom) oddílu.  
  
 Pokud přizpůsobený fallback je výchozí nastavení pro objekt kódování, můžete vybrat jiný nouzová strategie při načtení <xref:System.Text.Encoding> objektu voláním <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> nebo <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> přetížení. Následující části najdete příklad, který nahrazuje každý znak, který nelze mapovat na znakovou stránkou 1252 s hvězdičkou (*).  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
<a name="Replacement"></a>   
### <a name="replacement-fallback"></a>Náhradní použití náhradní lokality  
 Když znak nemá přesnou shodu v cílové schéma, ale neexistuje žádná odpovídající znak, který je možné mapovat na, může aplikace určit náhradní znak nebo řetězec. Toto je výchozí chování pro Unicode dekodér, která nahradí jakékoli dva bajty sekvenci, který nelze dekódovat REPLACEMENT_CHARACTER (U + FFFD). Je také výchozí chování <xref:System.Text.ASCIIEncoding> třídu, která nahrazuje každý znak, který nelze zakódování nebo dekódování otazníkem. Následující příklad ukazuje znak nahrazení pro řetězec znaků Unicode z předchozího příkladu. Jak ukazuje výstup, každý znak, který není možné dekódovat na hodnotu bajtu ASCII je nahrazena 0x3F, což je kód ASCII pro otazníkem.  
  
 [!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
 [!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]  
  
 Zahrnuje .NET <xref:System.Text.EncoderReplacementFallback> a <xref:System.Text.DecoderReplacementFallback> třídy, které nahrazení řetězci pro nahrazení, pokud znak není namapované přesně v kódování nebo dekódování operace. Ve výchozím nastavení je tento řetězec nahrazení otazník, ale můžete volat přetížení konstruktoru třídy zvolit jiný řetězec. Obvykle řetězci pro nahrazení je jednoho znaku, i když to není povinné. Následující příklad změní chování nástroje stránkou 1252 kodér kódu po vytvoření instance <xref:System.Text.EncoderReplacementFallback> objekt, který používá hvězdičku (*) jako řetězec nahrazení.  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
> [!NOTE]
>  Můžete také implementovat třídu nahrazení pro kódování. Další informace najdete v tématu [implementaci strategie použití náhradní lokality vlastní](../../../docs/standard/base-types/character-encoding.md#Custom) oddílu.  
  
 Kromě OTAZNÍK (U + 003F) náhradní znak Unicode (U + FFFD) běžně slouží jako řetězec nahrazení, zejména při dekódování sekvence bajtů, které nelze úspěšně přeložit na znaky znakové sady Unicode. Ale můžete libovolně vybrat libovolný řetězec nahrazení a může obsahovat více znaků.  
  
<a name="Exception"></a>   
### <a name="exception-fallback"></a>Výjimka použití náhradní lokality  
 Namísto zadávání přizpůsobený záložní nebo nahrazení řetězce, může vyvolat kodéru <xref:System.Text.EncoderFallbackException> Pokud nemůže zakódovat sady znaků a může vyvolat dekodér <xref:System.Text.DecoderFallbackException> Pokud nemůže dekódovat bajtové pole. Vyvolání výjimky v kódování a dekódování operace, můžete zadat <xref:System.Text.EncoderExceptionFallback> objektu a <xref:System.Text.DecoderExceptionFallback> objektu, respektive, na <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> – metoda. Následující příklad ukazuje výjimka záložní s <xref:System.Text.ASCIIEncoding> třídy.  
  
 [!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
 [!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]  
  
> [!NOTE]
>  Můžete také implementovat vlastní výjimka obslužné rutiny pro kódování operace. Další informace najdete v tématu [implementaci strategie použití náhradní lokality vlastní](../../../docs/standard/base-types/character-encoding.md#Custom) oddílu.  
  
 <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> objekty zadejte následující informace o stavu, který způsobil výjimku:  
  
-   <xref:System.Text.EncoderFallbackException> Objekt zahrnuje <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> metodu, která označuje, zda znak nebo znaky, které nemůže být kódovaný představují Neznámý náhradní pár (v takovém případě vrátí metoda `true`) nebo Neznámý znak (v takovém, metoda vrátí `false`). Znaky v náhradní pár jsou k dispozici <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> a <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> vlastnosti. Neznámý znak je k dispozici <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> vlastnost. <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> Vlastnost označuje pozici v řetězci, ve kterém byl nalezen prvního znaku, který nemůže být zakódován.  
  
-   <xref:System.Text.DecoderFallbackException> Objekt zahrnuje <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> vlastnost, která vrátí pole bajtů, které nelze dekódovat. <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> Vlastnost určuje počáteční pozici Neznámý bajtů.  
  
 I když <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> objekty poskytují odpovídající diagnostické informace o výjimce, se neposkytuje přístup ke kódování nebo dekódování vyrovnávací paměti. Proto se nepovolují neplatná data nahradit, nebo opraven v rámci metody kódování nebo dekódování.  
  
<a name="Custom"></a>   
## <a name="implementing-a-custom-fallback-strategy"></a>Implementace vlastního nouzová strategie  
 Kromě přizpůsobený mapování, která je implementována interně modulem znakových stránek, .NET obsahuje následující třídy pro implementaci strategii pro použití náhradní lokality:  
  
-   Použití <xref:System.Text.EncoderReplacementFallback> a <xref:System.Text.EncoderReplacementFallbackBuffer> nahradit znaky v kódování operace.  
  
-   Použití <xref:System.Text.DecoderReplacementFallback> a <xref:System.Text.DecoderReplacementFallbackBuffer> k nahrazení znaků v dekódování operace.  
  
-   Použití <xref:System.Text.EncoderExceptionFallback> a <xref:System.Text.EncoderExceptionFallbackBuffer> vyvolání <xref:System.Text.EncoderFallbackException> při nemůže být zakódován znak.  
  
-   Použití <xref:System.Text.DecoderExceptionFallback> a <xref:System.Text.DecoderExceptionFallbackBuffer> vyvolávat <xref:System.Text.DecoderFallbackException> když znak nelze dekódovat.  
  
 Kromě toho můžete implementovat vlastní řešení, která používá přizpůsobený použití náhradní lokality, záložní nahrazení nebo záložní výjimky, pomocí následujících kroků:  
  
1.  Odvodit třídu z <xref:System.Text.EncoderFallback> pro kódování operace a z <xref:System.Text.DecoderFallback> pro dekódování operace.  
  
2.  Odvodit třídu z <xref:System.Text.EncoderFallbackBuffer> pro kódování operace a z <xref:System.Text.DecoderFallbackBuffer> pro dekódování operace.  
  
3.  Pro použití náhradní lokality, pokud výjimka předdefinovaného <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> třídy nevyhovuje vašim potřebám, jako například odvodit třídu z objektu výjimky <xref:System.Exception> nebo <xref:System.ArgumentException>.  
  
### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Odvozování z EncoderFallback nebo DecoderFallback  
 Chcete-li implementovat vlastní řešení pro použití náhradní lokality, musíte vytvořit třídu, která dědí z <xref:System.Text.EncoderFallback> pro kódování operace a z <xref:System.Text.DecoderFallback> pro dekódování operace. Instance těchto tříd jsou předány <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metoda a slouží jako zprostředkovatel mezi kódování třídy a záložní implementace.  
  
 Když vytvoříte vlastní záložní řešení pro kodér nebo dekodér, musí implementovat následující členy:  
  
-   <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> vlastnost, která vrátí maximální možný počet znaků, které může záložní přizpůsobený, nahrazení nebo výjimky vrácené nahradí jediný znak. Pro použití náhradní lokality vlastní výjimka jeho hodnota je nula.  
  
-   <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metody, které vrací vlastní <xref:System.Text.EncoderFallbackBuffer> nebo <xref:System.Text.DecoderFallbackBuffer> implementace. Metoda se nazývá kodér, pokud se setká s první znak, který se nedokáže úspěšně kódování nebo dekodérem, pokud se setká s prvním bajtem, který se nedokáže úspěšně dekódovat.  
  
### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Odvozování z EncoderFallbackBuffer nebo DecoderFallbackBuffer  
 Chcete-li implementovat vlastní řešení pro použití náhradní lokality, musíte také vytvořit třídu, která dědí z <xref:System.Text.EncoderFallbackBuffer> pro kódování operace a z <xref:System.Text.DecoderFallbackBuffer> pro dekódování operace. Instance těchto tříd jsou vráceny pomocí <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> metodu <xref:System.Text.EncoderFallback> a <xref:System.Text.DecoderFallback> třídy. <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> Metoda je volána metodou kodér, pokud se setká s první znak, který není možné zakódovat, a <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metoda je volána metodou dekodér, pokud se setká s jednoho nebo více bajtů, které není možné dekódovat. <xref:System.Text.EncoderFallbackBuffer> a <xref:System.Text.DecoderFallbackBuffer> třídy poskytují záložní implementace. Každá instance představuje vyrovnávací paměť, která obsahuje náhradní znaky, které nahradí znak, který nemůže být kódovaný nebo sekvence bajtů, který nelze dekódovat.  
  
 Když vytvoříte vlastní záložní řešení pro kodér nebo dekodér, musí implementovat následující členy:  
  
-   <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metody. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> je volán kodér vyrovnávací paměti pro použití náhradní lokality poskytnout informace o znak, který nelze dekódovat. Protože znak, který má být zakódován může být náhradní pár, tato metoda je přetížen. Jedním přetížením je předán znak, který má být zakódován a jeho index v řetězci. Druhé přetížení je předán vysoké a nízké náhradníků spolu s jejich indexu v řetězci. <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> Metoda je volána metodou dekodér vyrovnávací paměti pro použití náhradní lokality poskytnout informace o bajtů, které nelze dekódovat. Této metodě se předává pole bajtů, které nelze dekódovat, spolu s index prvního bajtu. Náhradní metoda by měla vrátit `true` Pokud vyrovnávací paměti záložní verze můžete zadat přizpůsobený nebo náhradní znak nebo znaky; v opačném případě měla by vrátit `false`. Pro použití náhradní lokality výjimky by měl záložní metoda vyvolat výjimku.  
  
-   <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> metody, které je voláno opakovaně kodér nebo dekodéru získání další znak z vyrovnávací paměti záložní verze. Když byly vráceny všechny náhradní znaky, metoda by měla vrátit U + 0000.  
  
-   <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> vlastnost, která vrátí počet znaků zbývajících ve vyrovnávací paměti pro použití náhradní lokality.  
  
-   <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> metodu, která přesune aktuální pozice ve vyrovnávací paměti pro použití náhradní lokality předchozí znak.  
  
-   <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> metodu, která znovu inicializuje vyrovnávací paměti záložní verze.  
  
 Pokud je záložní implementace přizpůsobený záložní nebo záložní nahrazení, třídy odvozené z <xref:System.Text.EncoderFallbackBuffer> a <xref:System.Text.DecoderFallbackBuffer> také udržovat dvě instance privátní pole: přesný počet znaků ve vyrovnávací paměti; a index na další znak ve vyrovnávací paměti k vrácení.  
  
### <a name="an-encoderfallback-example"></a>Příklad EncoderFallback  
 Předchozí příklad náhradní použití náhradní lokality používá k nahrazení znaků Unicode, které neodpovídá znaky ASCII je hvězdička (*). Následující příklad používá vlastní přizpůsobený záložní implementace místo toho k poskytují lepší mapování jiné znaky než ASCII.  
  
 Následující kód definuje třídu s názvem `CustomMapper` , která je odvozena od <xref:System.Text.EncoderFallback> zpracování přizpůsobený mapování jiné znaky než ASCII. Jeho `CreateFallbackBuffer` metoda vrátí hodnotu `CustomMapperFallbackBuffer` objektu, který poskytuje <xref:System.Text.EncoderFallbackBuffer> implementace. `CustomMapper` Třídy používá <xref:System.Collections.Generic.Dictionary%602> objekt pro uložení mapování nepodporované znaky kódování Unicode (hodnota klíče) a jejich odpovídající znaky 8 bitů (které jsou uloženy ve dvou po sobě jdoucích bajtů v 64bitové celé číslo). Zpřístupnění tato mapování do vyrovnávací paměti záložní verze `CustomMapper` instance je předán jako parametr, který se `CustomMapperFallbackBuffer` konstruktoru třídy. Protože je řetězec "INF" pro znak Unicode U + 221E, nejdelší mapování `MaxCharCount` vlastnost vrací 3.  
  
 [!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
 [!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]  
  
 Následující kód definuje `CustomMapperFallbackBuffer` třídu, která je odvozena od <xref:System.Text.EncoderFallbackBuffer>. Slovník, který obsahuje nejlepšího mapování a která je definována v `CustomMapper` instance je k dispozici z konstruktoru třídy. Jeho `Fallback` vrátí metoda `true` Pokud některé znaky Unicode, které nelze kódování ASCII kodér jsou definovány ve slovníku mapování; v opačném případě vrátí `false`. Pro každý záložní, soukromého `count` proměnné označuje počet znaků, které zůstávají má být vrácen a privátní `index` proměnné označuje pozice ve vyrovnávací paměti pro řetězec `charsToReturn`, dalšího znaku vrátit.  
  
 [!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
 [!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]  
  
 Následující kód poté vytvoří instanci `CustomMapper` objektu a předá instance tak, <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> – metoda. Výstup označuje, že přizpůsobená záložní implementace úspěšně zpracuje tři znaky nepocházející ze sady ASCII v původním řetězci.  
  
 [!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
 [!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Text.Encoder>  
- <xref:System.Text.Decoder>  
- <xref:System.Text.DecoderFallback>  
- <xref:System.Text.Encoding>  
- <xref:System.Text.EncoderFallback>  
- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
