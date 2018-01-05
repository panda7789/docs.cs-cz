---
title: "V rozhraní .NET kódování znaků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoding, understanding
- encoding, choosing
- encoding, fallback strategy
ms.assetid: bf6d9823-4c2d-48af-b280-919c5af66ae9
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 29296261deb2cd94db339595464e3dcdf245fc82
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="character-encoding-in-net"></a>V rozhraní .NET kódování znaků
Znaky jsou abstraktní entit, které může být reprezentován v mnoha různými způsoby. Kódování znaků je systém, který páry každý znak v znakovou sadu podporovaných s určitou hodnotu, která představuje tento znak. Například morseovkou je kódování této páry každý znak v latinku pomocí vzoru teček znaků a pomlčky, které jsou vhodné pro přenos přes telegrafní řádky. Kódování pro dvojice počítače každý znak v znakovou sadu podporovaných s číselnou hodnotu, která představuje tento znak znaků. Kódování znaků má dvě odlišné součásti:  
  
-   Kodér, který překládá posloupnosti znaků do posloupnost číselných hodnot (v bajtech).  
  
-   Dekodér, což znamená, že je pořadí bajtů do posloupnosti znaků.  
  
 Kódování znaků popisuje pravidla, podle kterých kodér a dekodér fungovat. Například <xref:System.Text.UTF8Encoding> třída popisuje pravidla pro kódování a dekódování z 8bitové Unicode transformace formátu (ve formátu UTF-8), který používá jeden až čtyři bajtů, které představují jeden znak Unicode. Kódování a dekódování může zahrnovat ověření. Například <xref:System.Text.UnicodeEncoding> třída zkontroluje všechny náhrady, abyste měli jistotu, že představují platné náhradní dvojice. (Náhradní pár obsahuje znak s bodem kód, který se pohybuje od U + D800 do U + DBFF následuje znak s bodem kód, který se pohybuje od U + DC00 do U + DFFF.)  Nouzová strategie Určuje, jak Kodér zpracovává neplatné znaky nebo jak dekodér zpracovává neplatný bajtů.  
  
> [!WARNING]
>  Kódování třídy rozhraní .NET poskytují způsob, jak ukládat a převést textová data. Se nesmí použít k uložení binární data ve formátu řetězce. V závislosti na kódování použité, převádění binární data na řetězec formátu pomocí kódování třídy můžete zavést neočekávanému chování a vytvořit nesprávné nebo poškozená data. Chcete-li převést binární data do formuláře jako řetězec, použijte <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> metoda.  
  
 Rozhraní .NET používá kódování UTF-16 (reprezentována <xref:System.Text.UnicodeEncoding> třída) představují znaky a řetězce. Aplikace cílených modul common language runtime použijte kodéry pro mapování Unicode znaků nepodporuje modul common language runtime pro jiná schémata kódování. Dekódovací moduly používají pro mapování znaků z kódování Unicode kódování na kódování Unicode.  
  
 Toto téma se skládá z následujících částí:  
  
-   [Kódování v rozhraní .NET](../../../docs/standard/base-types/character-encoding.md#Encodings)  
  
-   [Výběr třídy kódování](../../../docs/standard/base-types/character-encoding.md#Selecting)  
  
-   [Pomocí objektu kódování](../../../docs/standard/base-types/character-encoding.md#Using)  
  
-   [Výběr strategie záložní](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)  
  
-   [Implementace vlastních nouzová strategie](../../../docs/standard/base-types/character-encoding.md#Custom)  
  
<a name="Encodings"></a>   
## <a name="encodings-in-net"></a>Kódování v rozhraní .NET  
 Kódování třídy v rozhraní .NET dědí všechny znak <xref:System.Text.Encoding?displayProperty=nameWithType> třída, která je abstraktní třída, která definuje funkce, které jsou společné pro všechny kódování znaků. Pro přístup k jednotlivé kódování objekty, které jsou implementované v rozhraní .NET, postupujte takto:  
  
-   Pomocí statické vlastnosti <xref:System.Text.Encoding> třídy, která vrátí objektů, představuje kódování standardní znaků, který je k dispozici v rozhraní .NET (ASCII, znakové sady UTF-7, UTF-8, UTF-16 a UTF-32). Například <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> vlastnost vrátí <xref:System.Text.UnicodeEncoding> objektu. Každý objekt používá nahrazení náhradní řetězce popisovače, které nelze dekódovat a bajtů, které nelze dekódovat. (Další informace najdete v tématu [nahrazení záložního](../../../docs/standard/base-types/character-encoding.md#Replacement) části.)  
  
-   Volání kódování je konstruktoru třídy. Tímto způsobem můžete vytvořit instance objektů pro ASCII, znakové sady UTF-7, UTF-8, UTF-16 a kódování UTF-32. Ve výchozím nastavení každý objekt používá záložní nahrazení pro zpracování řetězců, které nelze dekódovat a bajtů, které nelze dekódovat, ale můžete zadat, že místo toho by měla vyvolána výjimka. (Další informace najdete v tématu [nahrazení záložního](../../../docs/standard/base-types/character-encoding.md#Replacement) a [výjimka záložního](../../../docs/standard/base-types/character-encoding.md#Exception) oddíly.)  
  
-   Volání <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> konstruktor a předejte ji celé číslo, které představuje kódování. Standardní kódování objekty používají nahrazení záložního a znaková stránka a dvoubajtové znakové sady (DBCS) kódování objekty použití přizpůsobený přechod na popisovač řetězce, které budou nelze dekódovat a bajtů, které se nedá dekódovat. (Další informace najdete v tématu [Best-Fit záložního](../../../docs/standard/base-types/character-encoding.md#BestFit) části.)  
  
-   Volání <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metoda, která vrátí všechny standardní režim, znaková stránka nebo kódování DBCS k dispozici v rozhraní .NET. Přetížení umožňují určit pro kodér a dekodér záložního objektu.  
  
> [!NOTE]
>  Standardu Unicode přiřadí každému znaku v každé podporované skriptu bod kódu (číslo) a název. Znak "A" je například reprezentována bod kódu U + 0041 a název "LATIN velké písmeno A". Kódování Unicode Transformation Format (UTF) definovat jak kódování tohoto bodu kódu do sekvenci jeden nebo více bajtů. Schéma kódování Unicode usnadňuje vývoj aplikací připravených, protože umožňuje znaky z libovolného znaku nastaven a nelze v jednom kódování. Vývojáři aplikací mít už ke sledování schéma kódování, které se používají k vytvoření znaků pro konkrétní jazyk nebo zápis systému a data mohou být sdílená mezi systémy mezinárodní úrovni bez poškození.  
>   
>  Rozhraní .NET podporuje tři kódování definované ve standardu Unicode: UTF-8, UTF-16 a UTF-32. Další informace najdete v tématu ve standardu Unicode na [Unicode domovskou stránku](http://go.microsoft.com/fwlink/?LinkId=37123).  
  
 Informace o všech kódování, které jsou k dispozici v rozhraní .NET můžete načíst pomocí volání <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> metoda. Rozhraní .NET podporuje kódování systémů uvedených v následující tabulce znaků.  
  
|Kódování|Třída|Popis|Výhod i nevýhod|  
|--------------|-----------|-----------------|-------------------------------|  
|ASCII|<xref:System.Text.ASCIIEncoding>|Kóduje omezený rozsah znaků pomocí nižší sedm bity bajtů.|Protože toto kódování podporuje pouze znakových hodnot z U + 0000 do U + 007F, ve většině případů je nedostatečná pro mezinárodní aplikace.|  
|ZNAKOVÉ SADY UTF-7|<xref:System.Text.UTF7Encoding>|Reprezentuje znaky jako sekvence znaků ASCII 7 bitů. Znaky znakové sady Unicode jiného typu než ASCII jsou reprezentované pomocí – řídicí sekvence znaků ASCII.|Znakové sady UTF-7 podporuje protokoly, například e-mailu a protokoly v diskusní skupině. Však ve formátu UTF-7 není zvlášť bezpečné ani robustní. V některých případech může změna jeden bit radikálně změnit výklad celý řetězec ve formátu UTF-7. V ostatních případech můžete zakódovat různé řetězce ve formátu UTF-7 stejný text. Pořadí, které obsahují jiné znaky než ASCII znakové sady UTF-7 vyžaduje více místa, než UTF-8, a kódování a dekódování je pomalejší. Proto byste měli používat UTF-8 namísto znakové sady UTF-7-li to možné.|  
|ZNAKOVÉ SADY UTF-8|<xref:System.Text.UTF8Encoding>|Každý bod kódování Unicode představuje jako sekvenci bajtů, jeden až čtyři.|Znakové sady UTF-8 podporuje velikosti dat 8bitové a pracuje s mnoha existující operační systémy. Pro řadu znaků ASCII UTF-8 je stejný jako při kódování ASCII a umožňuje širší sadu znaků. Ale pro skripty čínština. Japonština Korejština (CJK) UTF-8 může vyžadovat tři bajtů pro každý znak a mohou způsobit větší velikosti dat než UTF-16. Všimněte si, že někdy množství dat ASCII, jako je například značky jazyka HTML, opravňuje vyšší velikost pro rozsah CJK.|  
|ZNAKOVÉ SADY UTF-16|<xref:System.Text.UnicodeEncoding>|Každý bod kódování Unicode představuje jako posloupnost celých čísel 16bitové jedno nebo dvě. Nejběžnější znaky znakové sady Unicode vyžadují pouze jeden bod kódování UTF-16, i když doplňkové znaky znakové sady Unicode (U + 10000 a vyšší) vyžadují dva body kódu náhradní UTF-16. Podporovány jsou obě pořadí bajtů little endian a big endian.|Kódování UTF-16 modul se používá k reprezentování <xref:System.Char> a <xref:System.String> hodnoty a se v operačním systému Windows používá k reprezentování `WCHAR` hodnoty.|  
|ZNAKOVÉ SADY UTF-32|<xref:System.Text.UTF32Encoding>|Každý bod kódování Unicode představuje jako 32bitové celé číslo. Podporovány jsou obě pořadí bajtů little endian a big endian.|Kódování UTF-32 se používá při aplikace se chcete vyhnout chování náhradní kód bodu v operačních systémech, pro které je příliš důležitá kódovaného místo kódování UTF-16. Jeden glyfů vykreslený na obrazovce můžete stále zakódovaných pomocí více znaky znakové sady UTF-32.|  
|Kódování ANSI/ISO||Poskytuje podporu pro celou řadu znakové stránky. V operačních systémech Windows znakové stránky slouží k podpoře konkrétní jazyk nebo skupinu jazyků. Tabulka, která uvádí znakové stránky nepodporuje rozhraní .NET, naleznete v části <xref:System.Text.Encoding> třídy. Objekt kódování pro konkrétní znakovou stránku můžete načíst pomocí volání <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metoda.|Znaková stránka obsahuje 256 body kódu a je počítáno od nuly. Ve většině znakových stránek body kód 0 až 127 představují znaková sada ASCII a body kódu 128 až 255 výrazně liší znakové stránky. Například znaková stránka 1252 poskytuje znaky pro Latin zápis systémů, včetně angličtinu, němčinu a francouzštinu. Poslední body 128 kódu v znaková stránka 1252 obsahovat znaky zvýraznění. Znaková stránka 1253 poskytuje kódy znaků, které jsou potřeba v řecké abecedě. Poslední body 128 kódu v znaková stránka 1253 obsahovat řecké znaky. V důsledku toho aplikace, které jsou závislé na ANSI znakové stránky nelze uložit řečtina a němčina do stejného datového proudu textu pokud obsahuje identifikátor, který označuje odkazované znaková stránka.|  
|Dvoubajtové znakové sady (DBCS) kódování||Podporuje jazyky, jako je čínština, japonština nebo korejština, které obsahují více než 256 znaků. V sadě DBCS pár bodů kódu (dvoubajtovými) představuje každý znak. <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> Vlastnost vrátí `false` pro znaky DBCS kódování. Načíst objekt kódování pro konkrétní znaky DBCS voláním <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> metoda.|V sadě DBCS pár bodů kódu (dvoubajtovými) představuje každý znak. Když aplikace zpracovává DBCS data, první bajt znaku DBCS (vedoucí byte) zpracování v kombinaci s druhým bajtem, který následuje ho. Protože jeden pár dvoubajtové kód bodů může představovat různé znaky v závislosti na znakové stránky, toto schéma stále nepovoluje kombinace dvou jazyků, jako je například japonštiny a čínština v stejný datový proud.|  
  
 Tyto kódování umožňují pracovat s znaky znakové sady Unicode, a dále s kódováním nejčastěji používané v starší verze aplikace. Kromě toho můžete vytvořit vlastní kódování definováním třídu odvozenou z <xref:System.Text.Encoding> a přepsáním její členy.  
  
### <a name="platform-notes-includenetcoreincludesnet-core-mdmd"></a>Poznámky k platformě:[!INCLUDE[net_core](../../../includes/net-core-md.md)]  
 Ve výchozím nastavení [!INCLUDE[net_core](../../../includes/net-core-md.md)] zpřístupnění žádné kódu stránky kódováním než znaková stránka 28591 a kódování Unicode, jako je UTF-8 a UTF-16. Můžete však přidat kódování kódu stránky v standardní aplikace pro Windows najít cílených .NET do aplikace. Úplné informace najdete v tématu <xref:System.Text.CodePagesEncodingProvider> tématu.  
  
<a name="Selecting"></a>   
## <a name="selecting-an-encoding-class"></a>Výběr třídy kódování  
 Pokud máte možnost vybrat kódování, které vaše aplikace používat, měli byste použít kódování Unicode, pokud možno buď <xref:System.Text.UTF8Encoding> nebo <xref:System.Text.UnicodeEncoding>. (.NET podporuje také třetí kódování Unicode, <xref:System.Text.UTF32Encoding>.)  
  
 Pokud máte v úmyslu používat kódování ASCII (<xref:System.Text.ASCIIEncoding>), zvolte <xref:System.Text.UTF8Encoding> místo. Dvě kódování jsou stejná pro znakové sadě ASCII, ale <xref:System.Text.UTF8Encoding> má následující výhody:  
  
-   Vzhledem k tomu může představovat každý znak Unicode <xref:System.Text.ASCIIEncoding> podporuje pouze hodnoty znak Unicode mezi U + 0000 a U + 007F.  
  
-   Poskytuje detekce chyb a lepší zabezpečení.  
  
-   To má byla přizpůsobená pro jako možné a by měla být rychlejší než jiné kódování. I pro obsah, který je zcela v ASCII, provést operace s <xref:System.Text.UTF8Encoding> je rychlejší než operace provedené pomocí <xref:System.Text.ASCIIEncoding>.  
  
 Měli byste zvážit použití <xref:System.Text.ASCIIEncoding> pouze pro starší verze aplikace. Ale i u starších verzí aplikací <xref:System.Text.UTF8Encoding> může být vhodnější (za předpokladu, že výchozí nastavení) z následujících důvodů:  
  
-   Pokud aplikace obsahuje obsah, který není striktně ASCII a kóduje ho s <xref:System.Text.ASCIIEncoding>, jednotlivé znaky jiné než ASCII zakóduje jako otazník (?). Aplikace se pak dekóduje tato data, dojde ke ztrátě informací.  
  
-   Pokud aplikace obsahuje obsah, který není striktně ASCII a kóduje ho s <xref:System.Text.UTF8Encoding>, výsledek zdá se, že nesrozumitelné, pokud interpretován jako ASCII. Ale pokud aplikace se pak použije decoder UTF-8 k dekódování tato data, data provede dobu odezvy úspěšně.  
  
 Ve webové aplikaci by měla odpovídat znaků může odeslat klientovi v odpovědi na žádost webové kódování používá na klientovi. Ve většině případů byste měli nastavit <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> vlastnost na hodnotu vrácenou <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> vlastnost zobrazení textu v kódování, které uživatel očekává.  
  
<a name="Using"></a>   
## <a name="using-an-encoding-object"></a>Pomocí objektu kódování  
 Kodér převede řetězec znaků (nejčastěji, znaky Unicode) na jeho číselnou (bajtů) ekvivalentní. Můžete například použít kodér ASCII ASCII převést znaky znakové sady Unicode, aby bylo možné zobrazit v konzole. Chcete-li provést převod, zavolejte <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> metoda. Pokud chcete určit, kolik bajtů jsou potřeba k uložení zakódované znaky před provedením kódování, můžete zavolat <xref:System.Text.Encoding.GetByteCount%2A> metoda.  
  
 Následující příklad používá ke kódování řetězců v dvě samostatné operace jeden bajtové pole. Udržuje index, který určuje počáteční pozici v bajtové pole pro další sadu kódováním ASCII bajtů. Zavolá <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> metoda pro zajištění dostatečně velké na to, aby dokázala pojmout řetězec s kódováním bajtové pole. Potom zavolá <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metoda ke kódování znaků v řetězci.  
  
 [!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
 [!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]  
  
 Dekodér převede bajtové pole, která odráží konkrétní znaky kódování do sady znaků, v poli znak nebo v řetězci. Chcete-li dekódovat bajtové pole do pole znaků, zavolejte <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metoda. Chcete-li dekódovat pole bajtů na řetězec, zavolejte <xref:System.Text.Encoding.GetString%2A> metoda. Pokud chcete určit, kolik znaků jsou potřeba k uložení dekódované bajtů před provedením dekódování, můžete zavolat <xref:System.Text.Encoding.GetCharCount%2A> metoda.  
  
 V následujícím příkladu kóduje tři řetězce a pak je dekóduje do jednoho pole znaků. Udržuje index, který určuje počáteční pozici v poli znaků pro další sadu dekódované znaků. Zavolá <xref:System.Text.ASCIIEncoding.GetCharCount%2A> metoda pro zajištění dostatečně velké na to, aby dokázala pojmout všechny dekódované znaky pole znaků. Potom zavolá <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> metodu za účelem dekódování bajtové pole.  
  
 [!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
 [!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]  
  
 Kódování a dekódování metody třídy odvozené od <xref:System.Text.Encoding> jsou navrženy pro práci na kompletní sadu dat; to znamená, že poskytuje všechny data kódování nebo dekódovat v rámci jednoho volání metody. V některých případech však v datovém proudu je k dispozici data a data, která mají být kódovaný nebo dekódovat, může být k dispozici pouze v samostatné operace čtení. To vyžaduje kódování nebo dekódování operaci pamatovat žádný uložený stav z jeho předchozí volání. Metody třídy odvozené od <xref:System.Text.Encoder> a <xref:System.Text.Decoder> jsou schopná zpracovat kódování a dekódování operace, které jsou rozmístěny v několika volání metody.  
  
 <xref:System.Text.Encoder> Objektu pro konkrétní kódování je k dispozici z této tabulky kódování na <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> vlastnost. A <xref:System.Text.Decoder> objektu pro konkrétní kódování je k dispozici z této tabulky kódování na <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> vlastnost. Pro dekódování operace, Všimněte si, že třídy odvozené od <xref:System.Text.Decoder> zahrnují <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metoda, ale nemají metodu, která odpovídá <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>.  
  
 Následující příklad ukazuje rozdíl mezi použitím <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> a <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metody pro dekódování pole bajtů kódování Unicode. V příkladu kóduje řetězec, který obsahuje některé znaky kódování Unicode do souboru a pak používá tyto dvě metody dekódování k dekódování deset bajtů v čase. Protože náhradní pár dojde v bajtech desetinu a jedenáctá, dekóduje v samostatné metodě volání. Jak ukazuje výstup <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> metoda není správně dekódovat bajtů a místo toho nahrazuje je U + FFFD (nahrazení používá znak). Na druhé straně <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> metoda je úspěšně dekódovat bajtové pole pro získání původního řetězce.  
  
 [!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
 [!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]  
  
<a name="FallbackStrategy"></a>   
## <a name="choosing-a-fallback-strategy"></a>Výběr strategie záložní  
 Pokud metoda pokusí zakódování nebo dekódování znak, ale neexistuje žádné mapování, musí implementovat nouzová strategie, která určuje způsob zpracování se nezdařilo mapování. Existují tři typy záložní strategií:  
  
-   Přizpůsobená záložního  
  
-   Nahrazení záložní  
  
-   Výjimka záložní  
  
> [!IMPORTANT]
>  Nejběžnější problémy vzniklé při kódování operations nastane, když znak Unicode nelze namapovat na konkrétní kódu stránky kódování. Nejběžnější problémy vzniklé při dekódování operations nastane, když pořadí bajtů neplatný nelze přeložit na platný znaky znakové sady Unicode. Z těchto důvodů měli byste vědět záložní strategii, kterou používá určitý objekt kódování. Pokud je to možné, musíte zadat nouzová strategie objekt kódování použité při vytvořte instanci objektu.  
  
<a name="BestFit"></a>   
### <a name="best-fit-fallback"></a>Přizpůsobená záložního  
 Když znak nemá přesnou shodu v cílovém kódování, můžete zkusit kodér namapovat je podobný znak. (Přizpůsobený záložního je většinou kódování místo dekódování problém. Existují jen několik znakové stránky, které obsahují znaky, které nelze úspěšně namapován na kódování Unicode.) Přizpůsobená záložního je výchozí znakové stránky a dvoubajtové znakové nastavení kódování, které jsou načteny <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> a <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> přetížení.  
  
> [!NOTE]
>  Teoreticky kódování Unicode třídy zadaný v rozhraní .NET (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding>, a <xref:System.Text.UTF32Encoding>) podporují každý znak v každé znaková sada, takže je můžete použít k vyloučení přizpůsobený záložní problémy.  
  
 Přizpůsobená strategie lišit pro různé znakové stránky, a nejsou podrobně popsáno. Například pro některé znakové stránky znaky latinky s plnou šířkou mapu, která častější poloviční šířkou Latinské znaky. Toto mapování není provedeno pro jiné znakové stránky. I v rámci agresivní přizpůsobený strategie neexistuje žádný vůbec přizpůsobení pro některé znaky v některé kódování. Například čínština znak nemá žádné přiměřené mapování na znaková stránka 1252. V takovém případě se používá náhradní řetězec. Ve výchozím nastavení je tento řetězec pouze jeden OTAZNÍK (U + 003F).  
  
 Následující příklad používá znaková stránka 1252 (kódové stránky systému Windows pro západní Evropské jazyky) pro ilustraci přizpůsobený mapování a jeho nevýhody. <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> Metoda se používá k načtení objektu kódování pro znaková stránka 1252. Ve výchozím nastavení použije přizpůsobený mapování znaky kódování Unicode nepodporuje. Tento příklad vytvoří řetězec, který obsahuje tři jiné znaky než ASCII – v KROUŽKU velké písmeno LATINKY S (U + 24C 8), horní index PĚT (U + 2075) a INFINITY (U + 221E) - oddělené mezerami. Jak ukazuje výstup z příkladu, pokud řetězec s kódováním tři původní není mezera znaky jsou nahrazovány OTAZNÍK (U + 003F), PĚT ČÍSLIC (U + 0035) a OSMI ČÍSLICE (U + 0038). ČÍSLICE OSM je zvláště nízký náhradní server pro nepodporovaný znak INFINITY a OTAZNÍK znamená, že byla k dispozici pro původní znak žádné mapování.  
  
 [!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
 [!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]  
  
 Výchozí chování je přizpůsobená mapování <xref:System.Text.Encoding> objekt která kóduje Unicode data data znakové stránky, a neexistují starší aplikace, které spoléhají na toto chování. Většina nových aplikací však byste neměli přizpůsobený chování z bezpečnostních důvodů. Například aplikace by neměla umístit název domény prostřednictvím přizpůsobený kódování.  
  
> [!NOTE]
>  Můžete také implementovat vlastní přizpůsobená záložní mapování pro kódování. Další informace najdete v tématu [implementace strategie záložního vlastní](../../../docs/standard/base-types/character-encoding.md#Custom) části.  
  
 Pokud přizpůsobený záložního je výchozí pro objekt kódování, můžete vybrat jiný nouzová strategie při načítání <xref:System.Text.Encoding> objekt voláním <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> nebo <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> přetížení. Následující části najdete příklad, který nahrazuje každý znak, který nejde mapovat na znaková stránka 1252 s hvězdičkou (*).  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
<a name="Replacement"></a>   
### <a name="replacement-fallback"></a>Záložní nahrazení  
 Pokud znak nemá přesnou shodu v cílové schéma, ale neexistuje žádné odpovídající znak, který může být namapovaný na, můžete určit aplikace k nahrazení používá znak nebo řetězec. Toto je výchozí chování pro kódování Unicode dekodér, která nahradí dvoubajtovou sekvenci, která nelze dekódovat REPLACEMENT_CHARACTER (U + FFFD). Je také výchozí chování <xref:System.Text.ASCIIEncoding> třídy, která nahradí otazník každý znak, který nelze zakódování nebo dekódování. Následující příklad ilustruje náhradní znak pro řetězec znaků Unicode z předchozího příkladu. Jak ukazuje výstup se každý znak, který nelze dekódovat do hodnotu bajtů ASCII nahrazuje 0x3F, což je kód ASCII otazník.  
  
 [!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
 [!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]  
  
 Zahrnuje rozhraní .NET <xref:System.Text.EncoderReplacementFallback> a <xref:System.Text.DecoderReplacementFallback> třídy, které nahraďte náhradní řetězec, pokud znak nemapuje přesně v kódování nebo dekódování operaci. Ve výchozím nastavení je tento řetězec nahrazení otazník, ale můžete volat přetížení konstruktoru třídy zvolit jiný řetězec. Náhradní řetězec je obvykle jeden znak, i když to není povinné. Následující příklad změní chování kodér stránka 1252 kódu po vytvoření instance <xref:System.Text.EncoderReplacementFallback> objekt, který používá znak hvězdičky (*) jako náhradní řetězec.  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
> [!NOTE]
>  Můžete taky implementovat náhradní třída pro kódování. Další informace najdete v tématu [implementace strategie záložního vlastní](../../../docs/standard/base-types/character-encoding.md#Custom) části.  
  
 Kromě OTAZNÍK (U + 003F) se náhradní znak Unicode (U + FFFD) často používá jako náhradní řetězec, zejména při dekódování pořadí bajtů, které nelze úspěšně přeložit na znaky znakové sady Unicode. Nicméně můžete vybrat všechny náhradní řetězec a může obsahovat více znaků.  
  
<a name="Exception"></a>   
### <a name="exception-fallback"></a>Záložní výjimky  
 Místo přizpůsobený zálohu nebo náhradní řetězec, můžete vyvolat kodér <xref:System.Text.EncoderFallbackException> Pokud není možné kódování sadu znaků a může výjimku dekodér <xref:System.Text.DecoderFallbackException> Pokud nelze dekódovat bajtové pole. Chcete-li vyvolána výjimka v kódování a dekódování operace, je zadat <xref:System.Text.EncoderExceptionFallback> objektu a <xref:System.Text.DecoderExceptionFallback> objekt, v uvedeném pořadí, na <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metoda. Následující příklad ilustruje výjimka záložní s <xref:System.Text.ASCIIEncoding> třídy.  
  
 [!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
 [!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]  
  
> [!NOTE]
>  Můžete také implementovat vlastní výjimky obslužnou rutinu pro operace kódování. Další informace najdete v tématu [implementace strategie záložního vlastní](../../../docs/standard/base-types/character-encoding.md#Custom) části.  
  
 <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> objekty zadejte následující informace o stavu, který způsobil výjimku:  
  
-   <xref:System.Text.EncoderFallbackException> Objekt zahrnuje <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> metodu, která označuje, zda znak nebo znaků, které nelze zakódovat představují dvojici neznámé náhradní (v takovém případě vrátí metoda `true`) nebo neznámé jednoho znaku (v které případu, vrátí metoda `false`). Znaků v páru náhradní jsou k dispozici na <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> a <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> vlastnosti. Neznámý jeden znak, který má k dispozici <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> vlastnost. <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> Vlastnost označuje pozici v řetězci, kdy byl nalezen prvního znaku, který nelze zakódován.  
  
-   <xref:System.Text.DecoderFallbackException> Objekt zahrnuje <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> vlastnost, která vrátí pole bajtů, které nelze dekódovat. <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> Vlastnost určuje počáteční pozici Neznámý bajtů.  
  
 I když <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> objekty zadejte odpovídající diagnostické informace o výjimce, neposkytují přístup k kódování nebo dekódování vyrovnávací paměti. Proto že neumožňují neplatná data k opravě v rámci metodu kódování nebo dekódování nebo nahradit.  
  
<a name="Custom"></a>   
## <a name="implementing-a-custom-fallback-strategy"></a>Implementace vlastních nouzová strategie  
 Kromě přizpůsobený mapování, která je implementována interně pomocí znakové stránky, .NET zahrnuje následující třídy pro implementaci nouzová strategie:  
  
-   Použití <xref:System.Text.EncoderReplacementFallback> a <xref:System.Text.EncoderReplacementFallbackBuffer> nahradit znaky v kódování operace.  
  
-   Použití <xref:System.Text.DecoderReplacementFallback> a <xref:System.Text.DecoderReplacementFallbackBuffer> nahradit znaky v dekódování operace.  
  
-   Použití <xref:System.Text.EncoderExceptionFallback> a <xref:System.Text.EncoderExceptionFallbackBuffer> má být vyvolána <xref:System.Text.EncoderFallbackException> při nemůže být znak zakódován.  
  
-   Použití <xref:System.Text.DecoderExceptionFallback> a <xref:System.Text.DecoderExceptionFallbackBuffer> má být vyvolána <xref:System.Text.DecoderFallbackException> při nelze dekódovat znak.  
  
 Kromě toho můžete implementovat vlastní řešení, které využívá přizpůsobený záložního, nahrazení záložního nebo záložní výjimky, pomocí následujících kroků:  
  
1.  Odvození třídy z <xref:System.Text.EncoderFallback> pro kódování operace a z <xref:System.Text.DecoderFallback> pro dekódování operace.  
  
2.  Odvození třídy z <xref:System.Text.EncoderFallbackBuffer> pro kódování operace a z <xref:System.Text.DecoderFallbackBuffer> pro dekódování operace.  
  
3.  Pro použití náhradní, pokud výjimka předdefinovanou <xref:System.Text.EncoderFallbackException> a <xref:System.Text.DecoderFallbackException> třídy nevyhovuje vašim potřebám, jako například odvození třídy z objektu výjimky <xref:System.Exception> nebo <xref:System.ArgumentException>.  
  
### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Odvozování z EncoderFallback nebo DecoderFallback  
 Pokud chcete implementovat vlastní záložní řešení, je nutné vytvořit třídu, která dědí z <xref:System.Text.EncoderFallback> pro kódování operace a z <xref:System.Text.DecoderFallback> pro dekódování operace. Jsou předávány instancemi těchto tříd <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metoda a používat jako zprostředkovatel mezi třídě kódování a záložní implementace.  
  
 Když vytvoříte vlastní záložní řešení pro kodér nebo dekodér, je nutné implementovat následující členy:  
  
-   <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> vlastnost, která vrátí hodnotu maximální možný počet znaků, který může záložní přizpůsobený, náhrada nebo výjimka vraťte se do nahradí jediný znak. Pro vlastní výjimky záložní jeho hodnota může být nula.  
  
-   <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metoda, která vrátí vaše vlastní <xref:System.Text.EncoderFallbackBuffer> nebo <xref:System.Text.DecoderFallbackBuffer> implementace. Metoda je volána kodér, pokud se setká s prvního znaku, který se nepodařilo úspěšně kódování nebo dekodér, když zjistí prvním bajtem, který nelze úspěšně dekódovat.  
  
### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Odvozování z EncoderFallbackBuffer nebo DecoderFallbackBuffer  
 Pokud chcete implementovat vlastní záložní řešení, musíte také vytvořit třídu, která dědí z <xref:System.Text.EncoderFallbackBuffer> pro kódování operace a z <xref:System.Text.DecoderFallbackBuffer> pro dekódování operace. Jsou instancemi těchto tříd vrácené <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> metodu <xref:System.Text.EncoderFallback> a <xref:System.Text.DecoderFallback> třídy. <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> Metoda je volána pomocí kodéru, když zjistí první znak, který ke kódování, nedokáže a <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> metoda je volána podle dekodér, když zjistí jeden nebo více bajtů, které není dekódovat. <xref:System.Text.EncoderFallbackBuffer> a <xref:System.Text.DecoderFallbackBuffer> třídy poskytují záložní implementace. Jednotlivé instance představují vyrovnávací paměť, která obsahuje náhradní znaky, které nahradí znak, který nemůže být zakódován nebo pořadí bajtů, které nelze dekódovat.  
  
 Když vytvoříte vlastní záložní řešení pro kodér nebo dekodér, je nutné implementovat následující členy:  
  
-   <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> metoda. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>je volána službou kodér poskytnout informace o znak, který nelze dekódovat náhradní velikost vyrovnávací paměti. Znak, který má být zakódován může být náhradní pár, tato metoda je přetížena. Jedním přetížením předán znak, který má být zakódován a její index v řetězci. Druhý přetížení je předán maximální a minimální náhradník společně s jeho indexu v řetězci. <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> Metoda je volána metodou dekodér poskytnout informace o bajtů, které nelze dekódovat náhradní velikost vyrovnávací paměti. Tato metoda je předán pole bajtů, které nelze dekódovat, společně s index prvním bajtem. Záložní metoda by měla vrátit `true` Pokud záložní vyrovnávací paměť můžete zadat nejvíce vyhovuje nebo nahrazení používá znak nebo znaky; jinak má být vrácen `false`. Pro záložní výjimky základní metoda by měla vyvolat výjimku.  
  
-   <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> metoda, která se nazývá opakovaně kodér nebo dekodér, chcete-li získat další znak ze záložního vyrovnávací paměti. Pokud byly vráceny všechny záložní znaky, metoda by měla vrátit U + 0000.  
  
-   <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> vlastnosti, která vrátí počet znaků zbývající náhradní velikost vyrovnávací paměti.  
  
-   <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> metodu, která přesune aktuální pozice ve vyrovnávací paměti pro použití náhradní na předchozí znak.  
  
-   <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> Nebo <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> metodu, která znovu inicializuje náhradní velikost vyrovnávací paměti.  
  
 Pokud záložní implementace přizpůsobený zálohu nebo nahrazení zálohu, třídy odvozené od <xref:System.Text.EncoderFallbackBuffer> a <xref:System.Text.DecoderFallbackBuffer> také udržovat dva privátní instance pole: přesný počet znaků v vyrovnávací paměti; a index další znak ve vyrovnávací paměti vrátit.  
  
### <a name="an-encoderfallback-example"></a>Příklad EncoderFallback  
 Příklad starší nahrazení záložní používá k nahrazení znaky znakové sady Unicode, které neodpovídá znaky ASCII s hvězdičkou (*). Následující příklad používá vlastní přizpůsobená záložní implementaci místo zajistit lepší mapování jiné znaky než ASCII.  
  
 Následující kód definuje třídu s názvem `CustomMapper` je odvozena z <xref:System.Text.EncoderFallback> pro zpracování přizpůsobený mapování jiné znaky než ASCII. Jeho `CreateFallbackBuffer` metoda vrátí `CustomMapperFallbackBuffer` objekt, který poskytuje <xref:System.Text.EncoderFallbackBuffer> implementace. `CustomMapper` Třídy používá <xref:System.Collections.Generic.Dictionary%602> objekt pro uložení mapování nepodporované znaky kódování Unicode (hodnota klíče) a jejich odpovídající 8bitové znaky (které jsou uloženy ve dvou po sobě jdoucích bajtů v 64bitové celé číslo). Tato mapování chcete zpřístupnit záložní vyrovnávací paměť, `CustomMapper` instanci předávána jako parametr, který se `CustomMapperFallbackBuffer` konstruktoru třídy. Protože je řetězec "INF" pro znak Unicode U + 221E, nejdelší mapování `MaxCharCount` vlastnost vrací 3.  
  
 [!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
 [!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]  
  
 Následující kód definuje `CustomMapperFallbackBuffer` třídy, která je odvozená od <xref:System.Text.EncoderFallbackBuffer>. Slovník obsahující přizpůsobený mapování, která je definovaná v `CustomMapper` instance je k dispozici z jeho konstruktoru třídy. Jeho `Fallback` metoda vrátí `true` pokud platí jedna z znaky Unicode, které nelze dekódovat kodér ASCII jsou definované ve slovníku mapování; jinak vrátí `false`. Pro každý záložní privátní `count` proměnná Určuje počet znaků, které má být vrácen, zůstanou a privátní `index` proměnné označuje pozici ve vyrovnávací paměti řetězců, `charsToReturn`, z další znak, který má vrátit.  
  
 [!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
 [!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]  
  
 Následující kód pak vytvoří `CustomMapper` objektu a předává jej do instance <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> metoda. Výstup obsahuje přizpůsobený záložní implementace úspěšně zpracovává tři znaky jiné než ASCII v původní řetězec.  
  
 [!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
 [!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Text.Encoder>  
 <xref:System.Text.Decoder>  
 <xref:System.Text.DecoderFallback>  
 <xref:System.Text.Encoding>  
 <xref:System.Text.EncoderFallback>  
 [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
