---
title: Formáty cesty k souborům v systémech Windows
ms.date: 06/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
ms.openlocfilehash: b3510be5d417b555d2db163636eac5ce0c0779e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628043"
---
# <a name="file-path-formats-on-windows-systems"></a>Formáty cesty k souborům v systémech Windows

Členové mnoha typů v <xref:System.IO> oboru názvů `path` zahrnují parametr, který umožňuje určit absolutní nebo relativní cestu k prostředku systému souborů. Tato cesta je pak předána [souborům API systému Windows](/windows/desktop/fileio/file-systems). Toto téma popisuje formáty cest k souborům, které lze použít v systémech Windows.

## <a name="traditional-dos-paths"></a>Tradiční cesty DOSu

Standardní cesta DOS umět se může skládat ze tří součástí:

- Písmeno svazku nebo jednotky následované`:`oddělovačem svazku ( ).
- Název adresáře. [Znak oddělovače adresářů](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje podadresáře v hierarchii vnořených adresářů.
- Volitelný název souboru. [Znak oddělovače adresáře](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje cestu k souboru a název souboru.

Pokud jsou přítomny všechny tři součásti, cesta je absolutní. Pokud není zadán žádný svazek nebo písmeno jednotky a název adresáře začíná [znakem oddělovače adresáře](<xref:System.IO.Path.DirectorySeparatorChar>), je cesta relativní od kořenového adresáře aktuální jednotky. V opačném případě je cesta relativní k aktuálnímu adresáři. V následující tabulce jsou uvedeny některé možné cesty k adresářům a souborům.

|Cesta  |Popis  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Absolutní cesta k souboru z kořenového adresáře jednotky C: |
| `\Program Files\Custom Utilities\StringFinder.exe` | Absolutní cesta z kořenového adresáře aktuální jednotky. |
| `2018\January.xlsx` | Relativní cesta k souboru v podadresáři aktuálního adresáře. |
| `..\Publications\TravelBrochure.pdf` | Relativní cesta k souboru v adresáři, který je partnerem aktuálního adresáře. |
| `C:\Projects\apilibrary\apilibrary.sln` | Absolutní cesta k souboru z kořenového adresáře jednotky C: |
| `C:Projects\apilibrary\apilibrary.sln` | Relativní cesta z aktuálního adresáře jednotky C: . |

> [!IMPORTANT]
> Všimněte si rozdílu mezi posledními dvěma cestami. Obě určují volitelný specifikátor svazku (C: v obou případech), ale první začíná kořenem zadaného svazku, zatímco druhý nikoli. Výsledkem je absolutní cesta z kořenového adresáře jednotky C:, zatímco druhá je relativní cesta z aktuálního adresáře jednotky C:. Použití druhého formuláře, pokud je zamýšleno první je běžným zdrojem chyb, které zahrnují cesty k souborům systému Windows.

Můžete určit, zda je cesta k souboru plně kvalifikovaná (to znamená, že cesta je nezávislá <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> na aktuálním adresáři a nezmění se při změně aktuálního adresáře) voláním metody. Všimněte si, že taková cesta`.` může `..`obsahovat relativní segmenty adresáře ( a ) a stále musí být plně kvalifikovaná, pokud přeložená cesta vždy odkazuje na stejné umístění.

Následující příklad ukazuje rozdíl mezi absolutní a relativní cesty. Předpokládá, že adresář D:\FY2018\ existuje a že jste nenastavili žádný aktuální adresář pro D:\ z příkazového řádku před spuštěním příkladu.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="unc-paths"></a>Cesty UNC

Cesty univerzální konvence pojmenování (UNC), které se používají pro přístup k síťovým prostředkům, mají následující formát:

- Název serveru nebo hostitele, který \\ \\je předchází . Název serveru může být název počítače NetBIOS nebo adresa IP/FQDN (podporovány jsou iPv4 a v6).
- Název sdílené položky, který je \\oddělen od názvu hostitele . Společně tvoří svazek název serveru a sdílené položky.
- Název adresáře. [Znak oddělovače adresářů](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje podadresáře v hierarchii vnořených adresářů.
- Volitelný název souboru. [Znak oddělovače adresáře](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje cestu k souboru a název souboru.

Níže jsou uvedeny některé příklady cest UNC:

|Cesta  |Popis  |
| -- | -- |
| `\\system07\C$\` | Kořenový adresář jednotky C: `system07`zapnuto . |
| `\\Server2\Share\Test\Foo.txt` | Soubor Foo.txt v adresáři \\ \\Test\\svazku Sdílení serveru Server2.|

Cesty UNC musí být vždy plně kvalifikované. Mohou obsahovat relativní segmenty adresáře (`.` a `..`), ale musí být součástí plně kvalifikované cesty. Relativní cesty lze použít pouze mapováním cesty UNC na písmeno jednotky.

## <a name="dos-device-paths"></a>Cesty zařízení DOS

Operační systém Windows má jednotný objektový model, který odkazuje na všechny prostředky, včetně souborů. Tyto objektové cesty jsou přístupné z okna konzoly a jsou vystaveny vrstvě Win32 prostřednictvím speciální složky symbolických odkazů, na které jsou mapovány starší cesty DOS a UNC. Tato speciální složka je přístupná prostřednictvím syntaxe cesty zařízení DOS, která je jednou z následujících:

`\\.\C:\Test\Foo.txt`
`\\?\C:\Test\Foo.txt`

Kromě identifikace jednotky podle písmena jednotky můžete identifikovat svazek pomocí identifikátoru GUID svazku. To má podobu:

`\\.\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`
`\\?\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`

> [!NOTE]
> Syntaxe cesty zařízení SYSTÉMU DOS je podporována v implementacích rozhraní .NET spuštěných v systému Windows počínaje rozhraními .NET Core 1.1 a .NET Framework 4.6.2.

Cesta zařízení DOS se skládá z následujících součástí:

- Specifikátor cesty zařízení`\\.\` `\\?\`( nebo ), který identifikuje cestu jako cestu zařízení DOS.

   > [!NOTE]
   > Je `\\?\` podporován ve všech verzích rozhraní .NET Core a v rozhraní .NET Framework počínaje verzí 4.6.2.

- Symbolický odkaz na "skutečný" objekt zařízení (C: v případě názvu jednotky nebo svazek{b75e2c83-0000-0000-0000-602f00000000} v případě identifikátoru GUID svazku).

   První segment cesty zařízení DOS po specifikátoru cesty zařízení identifikuje svazek nebo jednotku. (Například `\\?\C:\` a `\\.\BootPartition\`.)

   Existuje konkrétní odkaz pro uncs, který se `UNC`nazývá, není divu, . Například:

  `\\.\UNC\Server\Share\Test\Foo.txt`
  `\\?\UNC\Server\Share\Test\Foo.txt`

    Pro zařízení UNC tvoří svazek serverová/sdílená část. Například v `\\?\server1\e:\utilities\\filecomparer\`, server/sdílená část je server1\utilities. To je důležité při volání <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> metody, například s relativní segmenty adresáře; nikdy není možné procházet kolem svazku.

Cesty zařízení DOS jsou plně kvalifikované podle definice. Relativní segmenty`.` adresáře ( a `..`) nejsou povoleny. Aktuální adresáře nikdy vstoupit do jejich použití.

## <a name="example-ways-to-refer-to-the-same-file"></a>Příklad: Způsoby, jak odkazovat na stejný soubor

Následující příklad ilustruje některé způsoby, ve kterých můžete odkazovat na <xref:System.IO> soubor při použití api v oboru názvů. Příklad inkoniuje <xref:System.IO.FileInfo> objekt <xref:System.IO.FileInfo.Name> a <xref:System.IO.FileInfo.Length> používá jeho vlastnosti a zobrazí název souboru a délku souboru.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Normalizace cesty

Téměř všechny cesty předané do oken WINDOWS jsou normalizovány. Během normalizace provede systém Windows následující kroky:

- Identifikuje cestu.
- Použije aktuální adresář na částečně kvalifikované (relativní) cesty.
- Kanonikáty komponenty a oddělovače adresářů.
- Vyhodnotí relativní součásti adresáře`.` `..` ( pro aktuální adresář a pro nadřazený adresář).
- Ořízne určité znaky.

K této normalizaci dochází implicitně, ale můžete <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> to provést explicitně voláním metody, která zabalí volání [funkce GetFullPathName().](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) Můžete také volat [Windows GetFullPathName() funkce](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) přímo pomocí P/Invoke.

### <a name="identifying-the-path"></a>Identifikace cesty

Prvním krokem v normalizaci cesty je identifikace typu cesty. Cesty spadají do jedné z několika kategorií:

- Jsou to cesty zařízení; to znamená, že začínají dvěma oddělovači`\\?` a `\\.`otazníkem nebo tečkou ( nebo ).
- Jsou to cesty UNC; to znamená, že začínají dvěma oddělovači bez otazníku nebo tečky.
- Jsou to plně kvalifikované CESTY DOS; to znamená, že začínají písmenem jednotky, oddělovačem svazků a oddělovačem součásti (`C:\`).
- Označují starší zařízení`CON`( `LPT1`, ).
- Jsou relativní ke kořenovému adresáři aktuální jednotky; to znamená, že začínají oddělovačem jedné součásti (`\`).
- Jsou relativní k aktuálnímu adresáři zadané jednotky; to znamená, že začínají písmenem jednotky, oddělovačem svazků a žádným oddělovačem součástí (`C:`).
- Jsou relativní k aktuálnímu adresáři; to znamená, že začínají`temp\testfile.txt`s čímkoli jiným ( ).

Typ cesty určuje, zda je aktuální adresář nějakým způsobem použit. Také určuje, co je "kořen" cesty.

### <a name="handling-legacy-devices"></a>Manipulace se staršími zařízeními

Pokud je cesta starší zařízení DOS, `CON`například , `COM1`, nebo `LPT1`, je `\\.\` převedena na cestu zařízení prepending a vrácena.

Cesta, která začíná starší název zařízení je vždy interpretován jako <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> starší zařízení metodou. Například cesta zařízení DOS `CON.TXT` `\\.\CON`pro je a cesta `COM1.TXT\file1.txt` zařízení `\\.\COM1`DOS pro je .

### <a name="applying-the-current-directory"></a>Použití aktuálního adresáře

Pokud cesta není plně kvalifikovaná, systém Windows na něj použije aktuální adresář. Nepoužívané řadiče domény a cesty zařízení nemají použít aktuální adresář. Ani úplný pohon s oddělovačem C:\\.

Pokud cesta začíná oddělovačem jedné součásti, použije se jednotka z aktuálního adresáře. Pokud je `\utilities` například cesta k souboru `C:\temp\`a aktuální `C:\utilities`adresář , normalizace vytvoří .

Pokud cesta začíná písmenem jednotky, oddělovačem svazků a žádným oddělovačem součástí, použije se poslední aktuální sada adresářů z příkazového prostředí pro určenou jednotku. Pokud nebyl nastaven poslední aktuální adresář, použije se samotná jednotka. Pokud `D:sources`je například cesta k souboru `C:\Documents\`, je aktuální adresář a `D:\sources\`poslední aktuální `D:\sources\sources`adresář na jednotce D: byl , výsledkem je . Tyto cesty "relativní jednotky" jsou běžným zdrojem chyb logiky programu a skriptu. Za předpokladu, že cesta začínající písmenem a dvojtečkou není relativní, zjevně není správná.

Pokud cesta začíná něčím jiným než oddělovačem, použije se aktuální jednotka a aktuální adresář. Pokud je `filecompare` například cesta a aktuální `C:\utilities\`adresář je `C:\utilities\filecompare\`, výsledkem je .

> [!IMPORTANT]
> Relativní cesty jsou nebezpečné v aplikacích s více vlákny (to znamená, že většina aplikací), protože aktuální adresář je nastavení pro proces. Libovolné vlákno může kdykoli změnit aktuální adresář. Počínaje rozhraním .NET Core 2.1 <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> můžete volat metodu, abyste získali absolutní cestu z relativní cesty a základní cestu (aktuální adresář), proti které ji chcete vyřešit.

### <a name="canonicalizing-separators"></a>Oddělovače kanonizace

Všechna lomítka (`/`) jsou převedena na standardní`\`oddělovač systému Windows, zadní lomítko ( ). Pokud jsou k dispozici, řada lomítka, které následují po prvních dvou lomítka jsou sbaleny do jednoho lomítko.

### <a name="evaluating-relative-components"></a>Vyhodnocení relativních součástí

Při zpracování cesty jsou vyhodnoceny všechny součásti nebo segmenty,`.` které `..`se skládají z jednoho nebo dvojitého období ( nebo ):

- Pro jedno období je aktuální segment odebrán, protože odkazuje na aktuální adresář.

- Pro dvojité období jsou odebrány aktuální segment a nadřazený segment, protože dvojité období odkazuje na nadřazený adresář.

   Nadřazené adresáře jsou odebrány pouze v případě, že nejsou za kořenem cesty. Kořen cesty závisí na typu cesty. Jedná se o`C:\`jednotku ( ) pro cesty DOS,`\\Server\Share`server/sdílenou složku pro uncs`\\?\` `\\.\`( ) a předponu cesty zařízení pro cesty zařízení ( nebo ).

### <a name="trimming-characters"></a>Oříznutí znaků

Spolu s spuštěníoddělů a relativní segmenty odstraněny dříve, některé další znaky jsou odstraněny během normalizace:

- Pokud segment končí v jednom období, bude toto období odebráno. (Segment jednoho nebo dvojitého období je normalizován v předchozím kroku. Segment tří nebo více období není normalizován a je ve skutečnosti platný název souboru nebo adresáře.)

- Pokud cesta nekončí oddělovačem, budou odebrány všechny koncové tečky a mezery (U + 0020). Pokud je poslední segment pouze jednonebo dvojité období, spadá pod pravidlo relativních součástí výše.

   Toto pravidlo znamená, že můžete vytvořit název adresáře s koncovou mezerou přidáním koncového oddělovače za mezeru.

   > [!IMPORTANT]
   > **Nikdy** byste neměli vytvářet adresář nebo název souboru s koncovým prostorem. Koncové mezery mohou ztížit nebo znemožnit přístup k adresáři a aplikace se při pokusu o zpracování adresářů nebo souborů, jejichž názvy obsahují koncové mezery, běžně selžou.

## <a name="skipping-normalization"></a>Přeskočení normalizace

Za normálních okolností je jakákoli cesta předaná rozhraní API systému Windows (efektivně) předána [funkci GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) a normalizována. Existuje jedna důležitá výjimka: cesta zařízení, která začíná otazníkem namísto tečky. Pokud cesta nezačíná `\\?\` přesně (všimněte si použití kanonického zpětného lomítka), je normalizována.

Proč byste chtěli přeskočit normalizaci? Existují tři hlavní důvody:

1. Chcete-li získat přístup k cestám, které jsou obvykle nedostupné, ale jsou legální. Například soubor `hidden.`nebo adresář s názvem není možné získat přístup žádným jiným způsobem.

1. Chcete-li zlepšit výkon přeskočením normalizace, pokud jste již normalizovali.

1. Pouze v rozhraní .NET Framework `MAX_PATH` přeskočíte kontrolu délky cesty, abyste povolili cesty, které jsou větší než 259 znaků. Většina api to umožňují, s některými výjimkami.

> [!NOTE]
> .NET Core zpracovává dlouhé cesty implicitně a `MAX_PATH` neprovádí kontrolu. Kontrola `MAX_PATH` se vztahuje pouze na rozhraní .NET Framework.

Přeskočení normalizace a kontroly maximální cesty je jediný rozdíl mezi dvěma syntaxí cesty zařízení; jsou jinak totožné. Buďte opatrní při přeskočení normalizace, protože můžete snadno vytvořit cesty, které jsou obtížné pro "normální" aplikace řešit.

Cesty, které `\\?\` začínají, jsou stále normalizovány, pokud je explicitně předáte [funkci GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).

Můžete předat cesty více `MAX_PATH` než znaky [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) bez `\\?\`. Podporuje libovolné délky cesty až do maximální velikostřetězce, který systém Windows zvládne.

## <a name="case-and-the-windows-file-system"></a>Případ a systém souborů Windows

Zvláštností systému souborů Windows, který uživatelé a vývojáři bez systému Windows považují za matoucí, je, že názvy cest a adresářů nerozlišují malá a velká písmena. To znamená, že názvy adresářů a souborů odrážejí velikost písmen řetězců použitých při jejich vytvoření. Například volání metody

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

vytvoří adresář s názvem TeStDiReCtOrY. Pokud přejmenujete adresář nebo soubor, abyste změnili jeho velikost, bude název adresáře nebo souboru odrážet velikost písmen řetězce použitého při přejmenování. Například následující kód přejmenuje soubor s názvem test.txt na Test.txt:

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

Porovnání názvů adresářů a souborů však nerozlišují malá a velká písmena. Pokud hledáte soubor s názvem "test.txt", rozhraní API systému souborů .NET ignorují případ porovnání. Test.txt, TEST. TXT, test. TXT a jakákoli jiná kombinace velkých a malých písmen bude odpovídat "test.txt".
