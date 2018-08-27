---
title: Cesta formáty souborů v systémech Windows
ms.date: 06/28/2018
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8342f1389718eb41d1138e0bdd166530c1f2a10e
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42907713"
---
# <a name="file-path-formats-on-windows-systems"></a>Cesta formáty souborů v systémech Windows

Členy typů v mnoha <xref:System.IO> zahrnovat obor názvů `path` parametr, který vám umožní zadat absolutní nebo relativní cesta k souboru systémového prostředku. Tato cesta je pak předán [výtahem rozhraní API file Windows](https://msdn.microsoft.com/library/windows/desktop/aa364407(v=vs.85).aspx). Toto téma popisuje formáty pro cesty k souborům, které vám v systémech Windows.

## <a name="traditional-dos-paths"></a>Tradiční DOS cesty

Standardní cesta systému DOS se může skládat ze tří komponent:

- Na svazku nebo písmeno jednotky, za nímž následuje oddělovač svazků (`:`).
- Název adresáře. [Znakem oddělovače adresářů](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje podadresáře v rámci hierarchie vnořené adresářů.
- Volitelný název souboru. [Znakem oddělovače adresářů](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje cestu k souboru a název souboru.

Pokud jsou k dispozici všechny tři komponenty, je absolutní cesta. Pokud je zadán žádný svazku nebo písmeno jednotky a názvy adresářů začne adresářem [znakem oddělovače adresářů](<xref:System.IO.Path.DirectorySeparatorChar>), cesta je relativní od kořenové aktuální jednotku. V opačném případě cesta je relativní vzhledem k aktuálnímu adresáři. V následující tabulce jsou uvedeny některé možné adresáře a cesty k souborům.

|Cesta  |Popis  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Absolutní cestu k souboru z kořenové složky jednotky C: |
| `\Program Files\Custom Utilities\StringFinder.exe` | Absolutní cesta z kořenového adresáře aktuální jednotku. |
| `2018\January.xlsx` | Relativní cesta k souboru v podadresáři aktuálního adresáře. |
| `..\Publications\TravelBrochure.pdf` | Relativní cesta k souboru v adresáři, který je partnerské zařízení do aktuálního adresáře. |
| `C:\Projects\apilibrary\apilibrary.sln` | Absolutní cesta k souboru z kořenové složky jednotky C: |
| `C:Projects\apilibrary\apilibrary.sln` | Relativní cesta z aktuálního adresáře jednotku C:. |

> [!IMPORTANT]
> Všimněte si rozdílu mezi poslední dvě cesty. Jak zadat volitelný svazku specifikátor (C: v obou případech), ale první začíná kořenové zadaný svazek, zatímco druhá ne. První je jako výsledek, absolutní cesta z kořenového adresáře jednotku C:, zatímco druhá je relativní cesta z aktuálního adresáře jednotce C:. Použijte druhý formulář, když je první určené je běžné příčiny chyby, které se týkají cesty k souborům Windows.

Můžete určit, zda je plně kvalifikovanou cestu k souboru (to znamená, ho cesta je nezávislý na aktuálním adresáři a nemění, když se změní aktuální adresář) voláním <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> metody. Všimněte si, že tyto cesty může obsahovat relativní directory segmentů (`.` a `..`) a i nadále plně kvalifikovaný Pokud Vyhodnocená cesta vždy odkazuje na stejném umístění.

Následující příklad ukazuje rozdíl mezi absolutní a relativní cesty. Předpokládá, že existuje adresář D:\FY2018\ a, že jste nenastavili žádné aktuální adresář pro D:\ z příkazového řádku před spuštěním v příkladu.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

## <a name="unc-paths"></a>Cesty UNC

Universal naming convention (UNC) cesty, které se používají pro přístup k síťovým prostředkům, mají tento formát:

- Název serveru nebo hostitele, která je uvedena ve \\ \\. Název serveru může být název počítače pro rozhraní NetBIOS nebo IP nebo plně kvalifikovaný název domény adresy (IPv4 a IPv6 jsou podporovány).
- Název sdílené složky, která je oddělená od názvu hostitele ve \\. Název sdílené složky serveru a tvoří společně svazku.
- Název adresáře. [Znakem oddělovače adresářů](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje podadresáře v rámci hierarchie vnořené adresářů.
- Volitelný název souboru. [Znakem oddělovače adresářů](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje cestu k souboru a název souboru.

Následují příklady cesty UNC:

|Cesta  |Popis  |
| -- | -- |
| `\\system07\C$\` | Do kořenového adresáře C: jednotky na `system07`. |
| `\\Server2\Share\Test\Foo.txt` | Foo.txt soubor v adresáři Test \\ \\Server2\\sdílet svazku.|

Musí být vždy plně kvalifikované cesty UNC. Mohou obsahovat relativní directory segmentů (`.` a `..`), ale musí být součástí plně kvalifikovanou cestu. Pouze pomocí mapování cestu UNC k písmenu jednotky můžete použít relativní cesty.

## <a name="dos-device-paths"></a>Umístění zařízení DOS

Operační systém Windows obsahuje jednotné objektový model, který odkazuje na všechny prostředky, včetně souborů. Tyto cesty k objektům jsou přístupné z okna konzoly a jsou přístupné prostřednictvím speciální složky symbolické odkazy, které jsou starší verze programů DOS a UNC cesty mapované na vrstvě Win32. Tato zvláštní složka se přistupuje přes syntaxe cesty zařízení DOS, což je jedna z:

`\\.\C:\Test\Foo.txt`  
`\\?\C:\Test\Foo.txt`

> [!NOTE]
> Syntaxe cesty zařízení DOS je podporovaná v implementace .NET běžící na Windows od verze 1.1 rozhraní .NET Core a .NET Framework 4.6.2.

Cesta systému DOS zařízení se skládá z následujících součástí:

- Specifikátor cesta zařízení (`\\.\` nebo `\\?\`), který určuje cestu jako cesta systému DOS zařízení.

   > [!NOTE]
   > `\\?\` Je podporována ve všech verzích .NET Core a .NET Framework, od verze 4.6.2.
   
- Symbolický odkaz na objekt "real" zařízení (v tomto případě C:).

   První segment cesty zařízení DOS po specifikátoru cesta zařízení identifikuje svazku nebo jednotce. (Například `\\?\C:\` a `\\.\BootPartition\`.)

   Konkrétní odkaz pro UNC, která je volána, nejsou překvapivě `UNC`. Příklad:

      `\\.\UNC\Server\Share\Test\Foo.txt`
      `\\?\UNC\Server\Share\Test\Foo.txt`

    Pro zařízení UNC, část server a sdílet je formulářů svazku. Například v `\\?\server1\e:\utilities\\filecomparer\`, část server a sdílet je server1\utilities. To je důležité při volání metody, jako <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> relativní directory segmenty; se nikdy možné přejít po svazku. 

Podle definice jsou plně kvalifikované cesty zařízení DOS. Relativní directory segmentů (`.` a `..`) nejsou povoleny. Aktuální adresáře nikdy odsouhlasit jejich využití.

## <a name="example-ways-to-refer-to-the-same-file"></a>Příklad: Způsoby, jak odkazovat na stejný soubor

Následující příklad ukazuje několik způsobů jak, ve kterém najdete soubor při použití rozhraní API v <xref:System.IO> oboru názvů. Příkladu je vytvořena instance <xref:System.IO.FileInfo> a použije jeho <xref:System.IO.FileInfo.Name> a <xref:System.IO.FileInfo.Length> vlastnosti, které chcete zobrazit název souboru a délku souboru.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Normalizace cesta

Jsou normalizovány téměř všechny cesty předán rozhraní Windows API. Během normalizace Windows provede následující kroky:

- Určuje cestu.
- Částečně kvalifikované (relativní) cesty se týká aktuální adresář.
- Canonicalizes oddělovače komponentu a adresáře.
- Vyhodnotí jako relativní directory součásti (`.` pro aktuální adresář a `..` pro nadřazený adresář).
- Ořízne určitých znaků.

Implicitně se stane toto normalizace, ale můžete to provést explicitně voláním <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> metoda, která zabalí volání [GetFullPathName() funkce](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx). Můžete také volat Windows [GetFullPathName() funkce](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) přímo pomocí deklarace P/Invoke. Můžete také volat 

### <a name="identifying-the-path"></a>Určení cesty

Prvním krokem při normalizaci cesta je identifikace typu cesty. Cesty spadají do jedné z několika kategorií:

- Jsou cesty zařízení; To znamená, že začínat dva oddělovače a otazník nebo období (`\\?` nebo `\\.`).
- Jsou cesty UNC; To znamená že začínat dva oddělovače bez otazník nebo období. 
- Jsou plně kvalifikovanou cestou DOS; To znamená, začněte s písmenem jednotky, oddělovač svazků a oddělovač komponent (`C:\`).
- Určí starší zařízení (`CON`, `LPT1`).
- Jsou kořeni aktuální jednotce. To znamená, začínat oddělovačem jednotlivé součásti (`\`).
- Jsou relativní vzhledem k aktuální adresář zadané jednotky. To znamená, začněte s písmenem jednotky, oddělovač svazků a žádný oddělovač komponent (`C:`).
- Jsou relativní vzhledem k aktuálnímu adresáři; To znamená, že začínat cokoli jiného (`temp\testfile.txt`).

Typ cesty určuje, zda je nějakým způsobem použít aktuální adresář. Také určuje, co je "root" cesty.

### <a name="handling-legacy-devices"></a>Manipulace se zařízením starší verze

Pokud cestu, jako je starší verze zařízení DOS `CON`, `COM1`, nebo `LPT1`, je převeden na cestu zařízení předponou v podobě `\\.\` a vrátilo. 

Cestu, která začíná názvem starší zařízení je vždy interpretováno jako starší zařízení podle <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> metody. Například zařízení cesta systému DOS pro `CON.TXT` je `\\.\CON`a cesta systému DOS zařízení pro `COM1.TXT\file1.txt` je `\\.\COM1`.

### <a name="applying-the-current-directory"></a>Použití aktuální adresář

Pokud není plně kvalifikovanou cestu, Windows použije aktuální adresář na něj. UNC a cesty k zařízení není nutné použít aktuální adresář. Ani nemá jednotku úplné oddělovačem C:\\.

Pokud cesta musí začínat znakem oddělovače jednu součást, použije se jednotky z aktuálního adresáře. Například, pokud je cesta k souboru `\utilities` a aktuální adresář je `C:\temp\`, vytvoří normalizace `C:\utilities`.

Pokud cesta musí začínat písmenem jednotky, oddělovač svazků a žádný oddělovač komponent, použije se poslední aktuální adresář sady z příkazového okna na zadané jednotce. Pokud poslední aktuální adresář nebyla nastavena, použije se na jednotku, samotného. Například, pokud je cesta k souboru `D:sources`, aktuální adresář je `C:\Documents\`, a poslední aktuální adresář na jednotce D: `D:\sources\`, výsledkem je `D:\sources\sources`. Tyto cesty "jednotka relativní" jsou běžné příčiny chyby logiku programu a skript. Za předpokladu, že se relativní cesta začínající písmenem a dvojtečky je samozřejmě není správná.

Pokud cesta musí začínat znakem něco jiného než oddělovač, se použijí aktuální jednotky a aktuální adresář. Například, pokud je cesta `filecompare` a aktuální adresář je `C:\utilities\`, výsledkem je `C:\utilities\filecompare\`.

> [!IMPORTANT]
> Relativní cesty jsou nebezpečné ve vícevláknových aplikacích (to znamená, že většina aplikací), protože aktuální adresář je na úrovni jednotlivého procesu nastavení. Jakékoli vlákno může kdykoli změnit aktuální adresář. Počínaje .NET Core 2.1, lze volat <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> metodu k získání absolutní cesta relativní cestu a základní cesta (aktuální adresář), který chcete vyřešit proti. 

### <a name="canonicalizing-separators"></a>Kanonizace oddělovače

Všechna lomítka (`/`) se převedou na standardní oddělovač Windows zpětné lomítko (`\`). Pokud jsou k dispozici, řadu lomítka, které následují první dvě lomítka, jsou sbaleny do jedné lomítko.

### <a name="evaluating-relative-components"></a>Hodnocení relativní komponenty

Po zpracování cestu žádné komponenty nebo segmenty, které se skládají z jednoho ani dvojitou tečku (`.` nebo `..`) jsou vyhodnoceny: 

- Pro jedno období aktuální segment Odebereme, protože odkazuje na aktuální adresář.

- Pro dvojitou tečku aktuální segment a tento segment nadřazené jsou odebrané, protože dvojitou tečku odkazuje na nadřazený adresář.

   Nadřazené adresáře se odeberou, pouze pokud nejsou po kořen cesty. Kořenovou cestu, závisí na typu cesty. Je na jednotce (`C:\`) pro cesty DOS, nebo sdílené složky na serveru pro UNC (`\\Server\Share`) a předpona cesty zařízení pro zařízení cesty (`\\?\` nebo `\\.\`).

### <a name="trimming-characters"></a>Oříznutí znaků

Spolu s výskytů oddělovače a relativní segmenty odebrat dříve odeberou se nějakými dalšími znaky během normalizace:

- Segment, který končí na jednu tečku, odeberou se tohoto období. (Segment jednoduchých nebo dvojitých období je normalizovány v předchozím kroku. Segment tři nebo více období není normalizovaná a je ve skutečnosti název platný soubor nebo adresář.)

- Pokud cesta není končit oddělovačem, všechny koncové tečky ani mezery (U + 0020) se odeberou. Pokud poslední segment je jednoduše jednoduchých nebo dvojitých období, spadají do výše uvedené pravidlo relativní komponenty. 

   Toto pravidlo znamená, že můžete vytvořit název adresáře s koncovou mezerou přidáním koncové oddělovače za prostor.  

   > [!IMPORTANT]
   > Měli byste **nikdy** vytvořit adresář nebo název souboru s koncovou mezerou. Koncové mezery může být obtížné nebo nemožné pro přístup k adresáři a aplikace běžně selhání při pokusu o zpracování adresářů a souborů, jejichž názvy obsahují koncové mezery.

## <a name="skipping-normalization"></a>Přeskakuje se normalizace

Za normálních okolností libovolnou cestu předán rozhraní API Windows (efektivně) předán [GetFullPathName funkce](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) a normalizovaná. Existuje jedna důležitá výjimka: cesta zařízení, která začíná otazníkem místo tečku. Pokud cesta musí začínat znakem přesně `\\?\` (Všimněte si použití canonical zpětné lomítko), je normalizovat.

Proč byste měli přeskočit normalizace? Existují tři hlavní důvody:

1. Chcete-li získat přístup k cesty, které jsou běžně k dispozici, ale jsou platné. Soubor nebo adresář volá `hidden.`, například je možné pro přístup k žádným jiným způsobem. 

1. Ke zlepšení výkonu přeskočením normalizace, pokud jste již normalizovat.

1. Na rozhraní .NET Framework pouze, přejděte `MAX_PATH` vyhledat délka cesty umožňující cesty, které jsou větší než 259 znaků. Většina rozhraní API povolí tato, s několika výjimkami.

> [!NOTE]
> .NET core implicitně zpracovává dlouhé cesty a nebude provádět `MAX_PATH` zkontrolovat. `MAX_PATH` Kontrola platí, pouze na rozhraní .NET Framework.

Přeskočení kontroly cesta normalizace a maximální počet je jediným rozdílem mezi syntaxe cesty dvě zařízení; jinak jsou identické. Buďte opatrní při přeskočení normalizace, protože můžete snadno vytvořit cesty, které jsou pro "normální" aplikace řešit složité používání.

Cesty, které začínají `\\?\` jsou stále normalized, pokud jim explicitně předávat [GetFullPathName funkce](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).

Všimněte si, že je možné cesty více než `MAX_PATH` znaků [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) bez `\\?\`. Podporuje libovolné délky cesty až maximální velikost řetězce, který dokáže zpracovat Windows.

## <a name="case-and-the-windows-file-system"></a>Případ a systému souborů Windows

Zvláštností systému souborů Windows, který není Windows uživatele a vývojáře najít matoucí této cesty a názvy adresářů jsou malá a velká písmena. To znamená adresáře a souboru názvy odrážet malých a velkých písmen řetězců používané při jejich vytváření. Například volání metody

```csharp
Directory.Create(TeStDiReCtOrY);
```
Vytvoří adresář s názvem TeStDiReCtOrY. Pokud přejmenujete adresář nebo soubor změnit jeho velikost písmen, názvu adresáře nebo souboru odráží případ řetězec použitý při jeho přejmenování. Následující kód například přejmenuje soubor s názvem test.txt do Test.txt:

```csharp
using System;
using System.IO;

class Example
{
   public static void Main()
   {
      var fi = new FileInfo(@".\test.txt");
      fi.MoveTo(@".\Test.txt");
   }
}
``` 
```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim fi As New FileInfo(".\test.txt")
      fi.MoveTo(".\Test.txt")
   End Sub
End Module
```

Porovnání název adresáře a souboru jsou však malá a velká písmena. Je-li vyhledat soubor s názvem "test.txt" rozhraní API pro .NET systému souborů ignorovat velikost písmen při porovnání. Test.txt, testu. TXT, testu. "Test.txt" bude odpovídat TXT a jinou kombinaci velkých a malých písmen.
