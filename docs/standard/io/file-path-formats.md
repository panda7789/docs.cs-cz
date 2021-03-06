---
title: Formáty cesty k souborům v systémech Windows
description: V tomto článku se dozvíte o formátech souborů cest v systémech Windows, například tradičních cestách DOS, cestách zařízení se systémem DOS a cestách UNC (Universal Naming Convention).
ms.date: 06/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
ms.openlocfilehash: 8cbb687b0c7cfb69d3f3807c083f1c25e9d39594
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271786"
---
# <a name="file-path-formats-on-windows-systems"></a>Formáty cesty k souborům v systémech Windows

Členové mnoha typů v <xref:System.IO> oboru názvů zahrnují `path` parametr, který umožňuje zadat absolutní nebo relativní cestu k prostředku systému souborů. Tato cesta je pak předána [rozhraním API systému souborů systému Windows](/windows/desktop/fileio/file-systems). Toto téma pojednává o formátech pro cesty k souborům, které můžete použít v systémech Windows.

## <a name="traditional-dos-paths"></a>Tradiční cesty DOS

Standardní cesta systému DOS se může skládat ze tří součástí:

- Svazek nebo písmeno jednotky následované oddělovačem svazků ( `:` ).
- Název adresáře. [Znak oddělovače adresáře](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje podadresáře v rámci hierarchie vnořeného adresáře.
- Nepovinný název souboru. [Znak oddělovače adresáře](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje cestu k souboru a název souboru.

Pokud jsou k dispozici všechny tři komponenty, je cesta absolutní. Pokud není zadán žádný svazek ani písmeno jednotky a název adresáře začíná [znakem oddělovače adresáře](<xref:System.IO.Path.DirectorySeparatorChar>), bude cesta relativní od kořene aktuální jednotky. V opačném případě je cesta relativní vzhledem k aktuálnímu adresáři. V následující tabulce jsou uvedeny některé možné cesty k adresářům a souborům.

|Cesta  |Popis  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Absolutní cesta k souboru z kořene jednotky `C:` . |
| `\Program Files\Custom Utilities\StringFinder.exe` | Absolutní cesta z kořene aktuální jednotky. |
| `2018\January.xlsx` | Relativní cesta k souboru v podadresáři aktuálního adresáře. |
| `..\Publications\TravelBrochure.pdf` | Relativní cesta k souboru v adresáři, který je partnerským uzlem aktuálního adresáře. |
| `C:\Projects\apilibrary\apilibrary.sln` | Absolutní cesta k souboru z kořene jednotky `C:` . |
| `C:Projects\apilibrary\apilibrary.sln` | Relativní cesta z aktuálního adresáře `C:` jednotky. |

> [!IMPORTANT]
> Všimněte si rozdílu mezi posledními dvěma cestami. Oba určují volitelné specifikátory svazku ( `C:` v obou případech), ale první začíná kořenem zadaného svazku, zatímco druhý ne. V důsledku toho je první absolutní cesta z kořenového adresáře jednotky `C:` , zatímco druhá je relativní cesta z aktuálního adresáře jednotky `C:` . Použití druhého formuláře, pokud je první záměr, je běžným zdrojem chyb, které obsahují cesty k souborům Windows.

Můžete určit, zda je cesta k souboru plně kvalifikovaná (to znamená, že cesta je nezávislá na aktuálním adresáři a nemění se, když se změní aktuální adresář) voláním <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> metody. Všimněte si, že taková cesta může zahrnovat relativní segmenty adresářů ( `.` a `..` ) a pořád musí být plně kvalifikované, pokud se přeložená cesta vždy odkazuje na stejné umístění.

Následující příklad znázorňuje rozdíl mezi absolutními a relativními cestami. Předpokládá, že adresář `D:\FY2018\` existuje a že jste před spuštěním tohoto příkladu nestavili žádný aktuální adresář pro `D:\` z příkazového řádku.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="unc-paths"></a>Cesty UNC

Cesty UNC (Universal Naming Convention), které se používají pro přístup k síťovým prostředkům, mají následující formát:

- Název serveru nebo hostitele, který je v rámci `\\` . Název serveru může být název počítače pro rozhraní NetBIOS nebo adresa IP nebo plně kvalifikovaného názvu domény (IPv4 a i taky 6 – podporované).
- Název sdílené složky, který je oddělený od názvu hostitele `\` . Společně se název serveru a sdílené složky skládá ze svazku.
- Název adresáře. [Znak oddělovače adresáře](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje podadresáře v rámci hierarchie vnořeného adresáře.
- Nepovinný název souboru. [Znak oddělovače adresáře](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje cestu k souboru a název souboru.

Následuje několik příkladů cest UNC:

|Cesta  |Popis  |
| -- | -- |
| `\\system07\C$\` | Kořenový adresář `C:` jednotky `system07` . |
| `\\Server2\Share\Test\Foo.txt` | `Foo.txt`Soubor v adresáři testu `\\Server2\Share` svazku.|

Cesty UNC musí být vždy plně kvalifikované. Můžou zahrnovat relativní segmenty adresářů ( `.` a `..` ), ale musí být součástí plně kvalifikované cesty. Relativní cesty můžete použít jenom tak, že namapujete cestu UNC k písmenu jednotky.

## <a name="dos-device-paths"></a>Cesty zařízení DOS

Operační systém Windows má jednotný objektový model, který odkazuje na všechny prostředky, včetně souborů. Tyto cesty k objektům jsou přístupné z okna konzoly a jsou zpřístupněny vrstvě Win32 prostřednictvím speciální složky symbolických odkazů, na které jsou namapovány starší verze DOS a cesty UNC. K této speciální složce se dostanete pomocí syntaxe cesty zařízení DOS, což je jedna z těchto:

`\\.\C:\Test\Foo.txt`
`\\?\C:\Test\Foo.txt`

Kromě identifikace jednotky podle písmene jednotky můžete určit svazek pomocí identifikátoru GUID svazku. To má podobu:

`\\.\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`
`\\?\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`

> [!NOTE]
> Syntaxe cest zařízení DOS je podporovaná u implementací .NET běžících na Windows počínaje .NET Core 1,1 a .NET Framework 4.6.2.

Cesta k zařízení DOS se skládá z následujících součástí:

- Specifikátor cesty zařízení ( `\\.\` nebo `\\?\` ), který identifikuje cestu jako cestu k zařízení DOS.

   > [!NOTE]
   > `\\?\`Je podporován ve všech verzích rozhraní .NET Core a v .NET Framework počínaje verzí 4.6.2.

- Symbolický odkaz na "reálný" objekt zařízení (C: v případě názvu jednotky nebo svazek {b75e2c83-0000-0000-0000-602f00000000} v případě identifikátoru GUID svazku).

   První segment cesty zařízení systému DOS po určení svazku cesty zařízení, který identifikuje svazek nebo jednotku. (Například `\\?\C:\` a `\\.\BootPartition\` .)

   Pro UNCs je k dispozici konkrétní odkaz, který se nazývá, nikoli překvapivě `UNC` . Příklad:

  `\\.\UNC\Server\Share\Test\Foo.txt`
  `\\?\UNC\Server\Share\Test\Foo.txt`

    V případě UNCs zařízení tvoří část server/sdílení svazku svazek. Například v nástroji `\\?\server1\e:\utilities\\filecomparer\` je část serveru nebo sdílené složky `server1\utilities` . To je důležité při volání metody, jako je například <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> s relativními segmenty adresářů; není nikdy možné přejít na předchozí svazek.

Cesty zařízení DOS jsou plně kvalifikované podle definice. Relativní segmenty adresářů ( `.` a `..` ) nejsou povoleny. Aktuální adresáře nikdy nevstoupí do jejich použití.

## <a name="example-ways-to-refer-to-the-same-file"></a>Příklad: způsoby, jak odkazovat na stejný soubor

Následující příklad znázorňuje některé způsoby, jak můžete odkazovat na soubor při použití rozhraní API v <xref:System.IO> oboru názvů. Příklad vytvoří instanci <xref:System.IO.FileInfo> objektu a pomocí jeho <xref:System.IO.FileInfo.Name> <xref:System.IO.FileInfo.Length> vlastností a zobrazí název souboru a délku souboru.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Normalizace cest

Skoro všechny cesty předané rozhraním API systému Windows jsou normalizovány. Během normalizace systém Windows provede následující kroky:

- Identifikuje cestu.
- Použije aktuální adresář na částečně kvalifikované (relativní) cesty.
- Canonicalizes součásti a oddělovače adresářů.
- Vyhodnotí relativní součásti adresáře ( `.` pro aktuální adresář a `..` pro nadřazený adresář).
- Ořízne určité znaky.

Tato normalizace proběhne implicitně, ale můžete ji provést explicitně voláním <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> metody, která zabalí volání  [funkce GetFullPathName ()](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea). [Funkci Windows GetFullPathName ()](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) můžete také volat přímo pomocí volání nespravovaného volání.

### <a name="identify-the-path"></a>Identifikujte cestu

Prvním krokem normalizace cesty je určení typu cesty. Cesty spadají do jedné z několika kategorií:

- Jsou to cesty zařízení; To znamená, že začínají dvěma oddělovači a otazníkem nebo tečkou ( `\\?` nebo `\\.` ).
- Jsou to cesty UNC; To znamená, že začínají dvěma oddělovači bez otazníku nebo tečky.
- Jsou to plně kvalifikované cesty DOS; To znamená, že začínají písmenem jednotky, oddělovačem svazků a oddělovačem součásti ( `C:\` ).
- Určují starší zařízení ( `CON` , `LPT1` ).
- Jsou relativní vzhledem ke kořenu aktuální jednotky; To znamená, že začínají jedním oddělovačem součásti ( `\` ).
- Jsou relativní vzhledem k aktuálnímu adresáři zadané jednotky; To znamená, že začínají písmenem jednotky, oddělovačem svazků a bez oddělovače komponent ( `C:` ).
- Jsou relativní vzhledem k aktuálnímu adresáři. To znamená, že začínají cokoliv jiného ( `temp\testfile.txt` ).

Typ cesty určuje, zda je aktuální adresář použit nějakým způsobem. Také určuje, co je "kořen" cesty.

### <a name="handle-legacy-devices"></a>Zpracování starších zařízení

Pokud se jedná o starší zařízení se systémem DOS, jako je `CON` , `COM1` , nebo `LPT1` se převede na cestu k zařízení pomocí předpřipraveného `\\.\` a vráceného.

Cesta začínající starším názvem zařízení je vždy interpretována jako starší zařízení <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> metodou. Například cesta zařízení DOS pro `CON.TXT` je `\\.\CON` a cesta k zařízení DOS pro `COM1.TXT\file1.txt` je `\\.\COM1` .

### <a name="apply-the-current-directory"></a>Použít aktuální adresář

Pokud cesta není plně kvalifikovaná, systém Windows použije pro něj aktuální adresář. UNCs a cesty zařízení nemají použit aktuální adresář. Ani celá jednotka s oddělovačem `C:\` .

Pokud cesta začíná jediným oddělovačem komponent, použije se jednotka z aktuálního adresáře. Například pokud je cesta k souboru `\utilities` a aktuální adresář je `C:\temp\` , normalizace vytvoří `C:\utilities` .

Pokud cesta začíná písmenem jednotky, oddělovačem svazků a žádným oddělovačem komponent, použije se poslední aktuální adresářová sada z příkazového prostředí pro zadanou jednotku. Pokud nebyl poslední aktuální adresář nastaven, použije se samotný disk. Pokud je například cesta k souboru `D:sources` , aktuální adresář je `C:\Documents\` a poslední aktuální adresář na jednotce D: `D:\sources\` , výsledkem je `D:\sources\sources` . Tyto "relativní" cesty k jednotce jsou běžným zdrojem chyb logiky programu a skriptu. Za předpokladu, že cesta začínající písmenem a dvojtečkou není relativní, je zjevně nesprávná.

Pokud cesta začíná jinou než oddělovačem, použije se aktuální jednotka a aktuální adresář. Například pokud je cesta `filecompare` a aktuální adresář je `C:\utilities\` , je výsledkem `C:\utilities\filecompare\` .

> [!IMPORTANT]
> Relativní cesty jsou nebezpečné v aplikacích s více vlákny (tj. ve většině aplikací), protože aktuální adresář je nastavení pro jednotlivé procesy. V každém vlákně může aktuální adresář kdykoli změnit. Počínaje rozhraním .NET Core 2,1 můžete zavolat <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> metodu a získat tak absolutní cestu z relativní cesty a základní cestu (aktuální adresář), pro kterou ji chcete vyřešit.

### <a name="canonicalize-separators"></a>Oddělovače kanonického tvaru

Všechna lomítka ( `/` ) jsou převedena do standardního oddělovače systému Windows, zpětného lomítka ( `\` ). Pokud jsou k dispozici, řada lomítek, které následují dvě lomítka, jsou sbaleny do jednoho lomítka.

### <a name="evaluate-relative-components"></a>Vyhodnotit relativní součásti

Jak je cesta zpracována, `.` jsou vyhodnoceny všechny součásti nebo segmenty, které se skládají z jedné nebo dvě tečky (nebo `..` ):

- V rámci jednoho období je aktuální segment odebraný, protože odkazuje na aktuální adresář.

- Pro dvojitou dobu se odstraní aktuální segment a nadřazený segment, protože dvojitá tečka odkazuje na nadřazený adresář.

   Nadřazené adresáře jsou odebrány pouze v případě, že nejsou za kořenem cesty. Kořen cesty závisí na typu cesty. Je to jednotka ( `C:\` ) pro cesty DOS, server/sdílená složka pro UNCS ( `\\Server\Share` ) a Předpona cesty zařízení pro cesty zařízení ( `\\?\` nebo `\\.\` ).

### <a name="trim-characters"></a>Oříznout znaky

Společně s odebranými oddělovači a relativními segmenty odebranými dříve byly některé další znaky během normalizace odebrány:

- Pokud segment skončí v jednom období, toto období se odebere. (V předchozím kroku jsou normalizovány segmenty jedné nebo dvojité tečky. Segment tří nebo více teček není normalizován a ve skutečnosti je platný název souboru nebo adresáře.)

- Pokud cesta nekončí oddělovačem, odeberou se všechna koncová tečka a mezery (U + 0020). Pokud je poslední segment jednoduše jedna nebo dvojitá tečka, spadá do výše uvedeného pravidla relativních součástí.

   Toto pravidlo znamená, že můžete vytvořit název adresáře s koncovým místem přidáním koncového oddělovače za mezerou.

   > [!IMPORTANT]
   > **Nikdy** byste neměli vytvořit adresář nebo název souboru s koncovým místem. Koncové mezery můžou ztížit nebo nemožné získat přístup k adresáři a aplikace se často nezdaří při pokusu o zpracování adresářů nebo souborů, jejichž názvy obsahují koncové mezery.

## <a name="skip-normalization"></a>Přeskočit normalizaci

V normálním případě je jakákoli Cesta předaná do rozhraní API systému Windows (efektivně) předána [funkci GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) a normalizována. Existuje jedna důležitá výjimka: cesta zařízení, která začíná otazníkem místo tečky. Pokud cesta začíná přesně s `\\?\` (Všimněte si použití kanonického zpětného lomítka), je normalizovaná.

Proč byste chtěli přeskočit normalizaci? Existují tři hlavní důvody:

1. Získat přístup k cestám, které jsou normálně nedostupné, ale jsou právní. K souboru nebo adresáři s názvem například `hidden.` nelze přistupovat jiným způsobem.

1. Chcete-li zvýšit výkon, přeskočí normalizace, pokud jste již byli normalizováni.

1. Pouze v .NET Framework, pokud chcete přeskočit `MAX_PATH` kontrolu délky cesty, aby bylo možné použít cesty větší než 259 znaků. Většina rozhraní API to umožňuje s některými výjimkami.

> [!NOTE]
> .NET Core zpracovává dlouhé cesty implicitně a neprovádí `MAX_PATH` kontrolu. Tato `MAX_PATH` kontroly se vztahuje pouze na .NET Framework.

Normalizace a maximální počet kontrol cest se přeskočí jediným rozdílem mezi těmito dvěma syntaxemi cesty zařízení: jsou jinak identické. Při přeskočení normalizace buďte opatrní, protože můžete snadno vytvářet cesty, které jsou obtížné pro práci s běžnými aplikacemi.

`\\?\`Pokud explicitně předáte [funkci GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea), cesty začínající na jsou stále normalizovány.

Můžete předat cesty více než znaků, které `MAX_PATH` mají být [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) bez `\\?\` . Podporuje cesty s libovolnou délkou až do maximální velikosti řetězce, kterou může systém Windows zpracovat.

## <a name="case-and-the-windows-file-system"></a>Případ a systém souborů systému Windows

V systému souborů systému Windows, který nepoužívají uživatelé a vývojáři systému Windows, se v názvech cest a adresářů nerozlišují velká a malá písmena. To znamená, že názvy adresářů a souborů odrážejí velikost písmen řetězců použitých při jejich vytvoření. Například volání metody

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

vytvoří adresář s názvem TeStDiReCtOrY. Pokud přejmenujete adresář nebo soubor, aby se změnil jeho případ, název adresáře nebo souboru bude odpovídat velikosti řetězce použitého při jeho přejmenování. Například následující kód přejmenuje soubor s názvem test.txt na Test.txt:

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

Porovnávání názvů adresářů a souborů ale nerozlišuje velká a malá písmena. Pokud vyhledáte soubor s názvem "test.txt", rozhraní API systému souborů .NET ignorují velikost písmen v porovnání. "Test.txt", "TEST.TXT", "test.TXT" a jakékoli další kombinace velkých a malých písmen budou odpovídat "test.txt".
