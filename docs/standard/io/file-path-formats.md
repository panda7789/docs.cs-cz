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
ms.openlocfilehash: a5fccf5ea86469f14963fad8e7d2af0f7c68d2df
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106938"
---
# <a name="file-path-formats-on-windows-systems"></a>Cesta formáty souborů v systémech Windows

Členové mnoho typů v <xref:System.IO> zahrnují obor názvů `path` parametr, který umožňuje zadat absolutní nebo relativní cesta k souboru Systémový prostředek. Tato cesta se pak předá do [Windows souboru výtahem rozhraní API](https://msdn.microsoft.com/library/windows/desktop/aa364407(v=vs.85).aspx). Toto téma popisuje formáty cesty k souborům, které můžete použít v systémech Windows.

## <a name="traditional-dos-paths"></a>Tradiční DOS cesty

Standardní DOS cesta se může skládat z tří součástí:

- Na svazku nebo písmeno jednotky následované oddělovače svazek (`:`).
- Název adresáře. [Directory oddělovací znak](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje podadresáře v rámci hierarchie vnořené adresáře.
- Volitelný název souboru. [Directory oddělovací znak](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje cesta k souboru a název souboru.

Pokud jsou k dispozici všechny tři součásti, je absolutní cesta. Pokud je zadán žádný svazek nebo písmeno jednotky a názvy adresářů začíná [directory oddělovací znak](<xref:System.IO.Path.DirectorySeparatorChar>), cesta je relativní z kořene aktuální jednotku. Jinak cesta je relativní vzhledem k aktuálnímu adresáři. V následující tabulce jsou uvedeny některé možné adresáře a cesty k souborům.

|Cesta  |Popis  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Absolutní cestu k souboru z kořenové složky jednotky C: |
| `\Program Files\Custom Utilities\StringFinder.exe` | Absolutní cestu z kořene aktuální jednotku. |
| `2018\January.xlsx` | Relativní cesta k souboru v podadresáři aktuálního adresáře. |
| `..\Publications\TravelBrochure.pdf` | Relativní cesta k souboru v adresáři, který je rovnocenný aktuálního adresáře. |
| `C:\Projects\apilibrary\apilibrary.sln` | Absolutní cestu k souboru z kořenové složky jednotky C: |
| `C:Projects\apilibrary\apilibrary.sln` | Relativní cesta z aktuálního adresáře na jednotce C:. |

> [!IMPORTANT]
> Poznámka: rozdíl mezi poslední dvě cesty. Jak určit specifikátor volitelné svazek (C: v obou případech), ale první začíná kořenovém zadaný svazek, zatímco druhý není. Jako výsledek je první absolutní cestu z kořenového adresáře jednotky C:, zatímco druhý je relativní cestu z aktuálního adresáře jednotky C:. Použití druhý formulář, pokud je první určený je společný zdroj chyby, které zahrnují cesty k souborům systému Windows.

Můžete určit, zda je plně kvalifikovanou cestu k souboru (to znamená, že cesta je nezávisle na aktuální adresář a nezmění při změně aktuálního adresáře) voláním <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> metoda. Všimněte si, že takové cesta může obsahovat relativní directory segmenty (`.` a `..`) a přesto být plně kvalifikovaná Pokud přeložená cesta vždycky směřuje na stejné umístění.

Následující příklad ukazuje rozdíl mezi absolutní a relativní cesty. Přitom se předpokládá, že existuje adresář D:\FY2018\ a že jste nenastavili libovolného asi adresáře pro D:\ z příkazového řádku před spuštěním v příkladu.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

## <a name="unc-paths"></a>Cesty UNC

Universal naming convention (UNC) cesty, které se používají k přístupu k síťovým prostředkům, mají tento formát:

- Název serveru nebo hostitele, který je uvedena ve \\ \\. Název serveru může být název počítače pro rozhraní NetBIOS nebo adresu IP nebo plně kvalifikovaný název domény (IPv4 i IPv6 se podporují).
- Název sdílené složky, která je oddělená od názvu hostitele ve \\. Server a název sdílené složky tvoří společně svazku.
- Název adresáře. [Directory oddělovací znak](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje podadresáře v rámci hierarchie vnořené adresáře.
- Volitelný název souboru. [Directory oddělovací znak](<xref:System.IO.Path.DirectorySeparatorChar>) odděluje cesta k souboru a název souboru.

Toto jsou některé příklady cesty UNC:

|Cesta  |Popis  |
| -- | -- |
| `\\system07\C$\` | Kořenový adresář c:, jednotka v `system07`. |
| `\\Server2\Share\Test\Foo.txt` | Foo.txt soubor v adresáři Test \\ \\Server2\\, nesdílejí sdílené svazky.|

Musí být vždy plně kvalifikované cesty UNC. Obsahují segmenty relativní adresáře (`.` a `..`), ale tyto musí být součástí plně kvalifikovanou cestu. Můžete použít relativní cesty pouze pomocí cesty UNC mapování na písmeno jednotky.

## <a name="dos-device-paths"></a>Cesty zařízení DOS

Operační systém Windows obsahuje jednotná objektový model, který odkazuje na všechny prostředky, včetně souborů. Tyto cesty objektu jsou přístupné z okna konzoly a jsou viditelné na vrstvě Win32 prostřednictvím speciální složky symbolické odkazy, které jsou starší verze programů DOS a UNC cesty mapované na. Tato složka speciální přistupuje prostřednictvím syntaxe cesty zařízení DOS, což je jedna z:

`\\.\C:\Test\Foo.txt`  
`\\?\C:\Test\Foo.txt`

> [!NOTE]
> Syntaxe cesty zařízení DOS je podporována v v systému Windows od verze .NET Core 1.1 a rozhraní .NET Framework 4.6.2 implementace rozhraní .NET.

Cestu zařízení DOS se skládá z následujících součástí:

- Specifikátor cesta zařízení (`\\.\` nebo `\\?\`), který identifikuje cesty jako cesty zařízení DOS.

   > [!NOTE]
   > `\\?\` Je podporována ve všech verzích .NET Core a v rozhraní .NET Framework verze 4.6.2 počínaje.
   
- Symbolický odkaz na objekt "Skutečná" zařízení (v tomto případě C:).

   První segment cesty zařízení DOS po specifikátor cesta zařízení identifikuje svazek nebo jednotku. (Například `\\?\C:\` a `\\.\BootPartition\`.)

   Konkrétní odkaz pro adresy UNC, která je volána logicky `UNC`. Příklad:

      `\\.\UNC\Server\Share\Test\Foo.txt`
      `\\?\UNC\Server\Share\Test\Foo.txt`

    Pro zařízení adresy UNC, je část nebo sdílená složka serveru forms svazku. Například v `\\?\server1\e:\utilities\\filecomparer\`, část nebo sdílené složky serveru není server1\utilities. To je důležité při volání metody, jako <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> s relativní directory segmenty; se nikdy možné přejít po svazku. 

Podle definice jsou plně kvalifikované cesty zařízení DOS. Relativní directory segmenty (`.` a `..`) nejsou povoleny. Aktuální adresáře nikdy zadat do jejich využití.

## <a name="example-ways-to-refer-to-the-same-file"></a>Příklad: Jak odkazovat na stejný soubor

Následující příklad ukazuje některé způsoby, ve kterém najdete soubor při použití rozhraní API v <xref:System.IO> oboru názvů. V příkladu vytvoří <xref:System.IO.FileInfo> objekt a používá jeho <xref:System.IO.FileInfo.Name> a <xref:System.IO.FileInfo.Length> vlastnosti, které chcete zobrazit název souboru a délku souboru.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Cesta normalizaci

Téměř všechny cesty předaný rozhraní API systému Windows se normalizovalo. Windows během normalizace, provede následující kroky:

- Určuje cestu.
- Aktuální adresář se vztahuje na částečně kvalifikovaný (relativní) cesty.
- Canonicalizes oddělovače součásti a adresář.
- Vyhodnotí relativní directory součásti (`.` pro aktuální adresář a `..` pro nadřazený adresář).
- Ořízne určitých znaků.

Tato normalizaci se stane implicitně, ale můžete provést explicitně voláním <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> metodu, která zabalí volání [GetFullPathName() funkce](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx). Můžete také zavolat Windows [GetFullPathName() funkce](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) přímo pomocí protokolu P/Invoke. Můžete také zavolat 

### <a name="identifying-the-path"></a>Identifikace cesta

Prvním krokem při normalizaci cesta je identifikace typu cesty. Cesty lze rozdělit do několika kategorií:

- Jsou cesty zařízení; To znamená, že začínat dva oddělovače a otazník nebo období (`\\?` nebo `\\.`).
- Jsou cesty UNC; To znamená že začínat dva oddělovače bez otazník nebo období. 
- Jsou plně kvalifikované cesty DOS; To znamená, začněte s písmenem jednotky, oddělovač svazku a součást oddělovače (`C:\`).
- Určí starší zařízení (`CON`, `LPT1`).
- Jsou relativní vůči kořenovému adresáři na aktuální jednotce; To znamená, začínat oddělovač jedna součást (`\`).
- Jsou vůči aktuálnímu adresáři zadané jednotky. To znamená, začněte s písmenem jednotky, oddělovač svazku a žádné komponenty oddělovače (`C:`).
- Jsou relativní vzhledem k aktuálnímu adresáři; To znamená, že začínat cokoliv jiného (`temp\testfile.txt`).

Typ cesty určuje, zda je nějakým způsobem použít aktuální adresář. Také určuje, co je "root" cesty.

### <a name="handling-legacy-devices"></a>Zařízení se starší verzí zpracování

Pokud cesta, jako je starší verze programů DOS zařízení `CON`, `COM1`, nebo `LPT1`, se převede do cesty zařízení předponou `\\.\` a vrácená. 

Cestu, která začíná název starší zařízení je vždy interpretován jako starší verze zařízení pomocí <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> metoda. Například cestu zařízení DOS pro `CON.TXT` je `\\.\CON`a cesty zařízení DOS `COM1.TXT\file1.txt` je `\\.\COM1`.

### <a name="applying-the-current-directory"></a>Použití aktuálního adresáře

Pokud není plně kvalifikovanou cestu, systém Windows použije k němu aktuální adresář. Zařízení cesty UNC a nemají aktuální adresář použít. Ani nemá úplné jednotku s oddělovačem C:\\.

Pokud cesta začíná oddělovač jedinou komponentu, použije se jednotku z aktuálního adresáře. Například, pokud je cesta k souboru `\utilities` a aktuální adresář je `C:\temp\`, vytváří normalizaci `C:\utilities`.

Pokud cesta začíná písmenem jednotky, oddělovače svazku a žádné součásti oddělovač, použije se poslední aktuální adresář nastavit z příkazového prostředí pro vybranou jednotku. Pokud poslední aktuálního adresáře nebyl nastaven, je použita samostatné jednotky. Například, pokud je cesta k souboru `D:sources`, aktuální adresář je `C:\Documents\`, a byl poslední aktuální adresář na jednotce D: `D:\sources\`, výsledkem je `D:\sources\sources`. Tyto cesty "jednotka relativní" se společný zdroj logické chyby programu a skript. Za předpokladu, že není relativní cesta začínající písmenem a dvojtečkou je samozřejmě není správná.

Pokud cesta začíná něco jiného než oddělovač, se použijí aktuální jednotce a aktuální adresář. Například, pokud je cesta `filecompare` a aktuální adresář je `C:\utilities\`, výsledkem je `C:\utilities\filecompare\`.

> [!IMPORTANT]
> Relativní cesty jsou nebezpečné v vícevláknové aplikace (to znamená, že většina aplikací), protože aktuální adresář je nastavení v rámci procesu. Jakékoli vlákno můžete kdykoli změnit aktuální adresář. Od verze rozhraní .NET Core 2.1, můžete zavolat <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> metoda sám absolutní cesta je relativní cesta a základní cesta (aktuální adresář), kterou chcete ho proti vyřešit. 

### <a name="canonicalizing-separators"></a>Kanonizace oddělovačů

Všechny lomítka (`/`) se převedou na standardní oddělovače Windows zpětné lomítko (`\`). Pokud jsou přítomna, řadu lomítka, které následují první dva lomítka sbalené do jednoho lomítko.

### <a name="evaluating-relative-components"></a>Vyhodnocení relativní součásti

Při zpracování cesta se jakékoli součásti nebo segmentů, které se skládají z jedné nebo dvojité období (`.` nebo `..`) se vyhodnocují: 

- Pro jedno období se odebere aktuální segment, protože odkazuje na aktuální adresář.

- Dvojité dobu, aktuální segment segment nadřazené budou odebrány a, protože dvojité období odkazuje na nadřazený adresář.

   Nadřazené adresáře se odstraní pouze, pokud nejsou po kořen cesty. Kořen cesty závisí na typu cesty. Je jednotka (`C:\`) pro DOS cesty, nebo sdílené složky na serveru pro adresy UNC (`\\Server\Share`) a předponu cesta zařízení pro zařízení cesty (`\\?\` nebo `\\.\`).

### <a name="trimming-characters"></a>Oříznutí znaků

Společně běží oddělovačů a relativní segmenty odebrána dříve jsou během normalizace odebrány některé další znaky:

- Pokud segment končí na jedno období, odeberou se toto období. (Segment jednociferné nebo období je normalized v předchozím kroku. Segment tři nebo více období není normalized a je ve skutečnosti název platný soubor nebo adresář.)

- Pokud cesta není končit oddělovač, všechny koncové tečky a mezery (U + 0020) jsou odebrány. Pokud se poslední segment jednoduše jednociferné nebo období, klesne pod výše uvedené pravidlo relativní součásti. 

   Toto pravidlo znamená, že můžete vytvořit název adresáře s koncovou mezeru přidáním koncové oddělovače za mezerou.  

   > [!IMPORTANT]
   > Měli byste **nikdy** vytvořit adresář nebo název souboru s koncovou mezeru. Koncové mezery může být obtížné nebo dokonce znemožňují přístup adresáře a aplikace běžně selže při pokusu o zpracování adresáře nebo soubory, jejichž názvy obsahovat koncové mezery.

## <a name="skipping-normalization"></a>Přeskočení normalizaci

Za normálních okolností jakoukoli cestu předaný rozhraní API systému Windows (efektivně) předaný [GetFullPathName funkce](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) a normalizovaný. Existuje jedna výjimka důležité: cestu k zařízení, která začíná otazník místo období. Pokud cesta začíná přesně `\\?\` (Všimněte si použití kanonický zpětné lomítko), je normalized.

Proč by chcete přeskočit normalizaci? Existují tři hlavní příčiny:

1. Chcete-li získat přístup k cesty, které nejsou obvykle dostupné, ale jsou právní. Soubor nebo adresář s názvem `hidden.`, například je možné pro přístup k žádným jiným způsobem. 

1. Chcete-li vylepšit výkon přeskočení normalizaci, pokud jste již normalized.

1. V rozhraní .NET Framework, tak, aby přeskočil `MAX_PATH` zkontrolujte délka cesty umožňující cesty, které jsou větší než 259 znaků. Většina rozhraní API, povolit na několik výjimek.

> [!NOTE]
> .NET core implicitně zpracovává dlouhé cesty a nebude provádět `MAX_PATH` zkontrolujte. `MAX_PATH` Zaškrtněte platí pouze pro rozhraní .NET Framework.

Přeskočení kontroly cesta normalizaci a maximální počet je jediným rozdílem mezi syntaxe cesta dvě zařízení; jinak jsou totožné. Pečlivě s přeskočení normalizaci vzhledem k tomu, že můžete snadno vytvořit cesty, které jsou těžko "normální" aplikace k řešení.

Cesty, které začínají `\\?\` jsou stále normalized, pokud jim předáte explicitně [GetFullPathName funkce](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx).

Všimněte si, že můžete cesty více než `MAX_PATH` znaků [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) bez `\\?\`. Podporuje libovolné délky cesty až velikost maximální řetězec, který může zpracovat systému Windows.

## <a name="case-and-the-windows-file-system"></a>Případ a systému souborů

Typickým znakem systému souborů, jiný systém než Windows uživatelů a vývojářů najít matoucí této cesty a názvy adresářů jsou velká a malá písmena. To znamená adresáře a souboru názvy projeví malá a velká písmena řetězce použité při jejich vytváření. Například volání metody

```csharp
Directory.Create(TeStDiReCtOrY);
```
Vytvoří adresář s názvem TeStDiReCtOrY. Pokud přejmenujete adresář nebo soubor změnit jeho případ, adresář nebo soubor název odráží v případě řetězec použitý při přejmenování ho. Následující kód například přejmenuje soubor s názvem test.txt do Test.txt:

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

Porovnání název adresáře a souboru jsou však velká a malá písmena. Pokud dáte vyhledat soubor s názvem "test.txt", systém souborů .NET API ignorovat velká písmena v porovnání. Test.txt, TEST. TXT, test. "Test.txt" bude odpovídat TXT a dalších kombinaci velkých a malých písmen.
