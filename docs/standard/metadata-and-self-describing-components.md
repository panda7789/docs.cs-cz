---
title: Metadata a komponenty popisující samy sebe
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET Framework], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
ms.openlocfilehash: a4f4c0e1af379d31c5b478472780d5c7de813bf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121937"
---
# <a name="metadata-and-self-describing-components"></a>Metadata a komponenty popisující samy sebe

V minulosti softwarová součást (.exe nebo .dll), která byla napsána v jednom jazyce, nemohla snadno použít softwarovou součást, která byla napsána v jiném jazyce. COM poskytla krok k vyřešení tohoto problému. Rozhraní .NET Framework usnadňuje spolupráci komponent tím, že umožňuje kompilátorům vyzařovat další deklarativní informace do všech modulů a sestavení. Tyto informace, nazývané metadata, pomáhají komponentám bezproblémovou interakci.

 Metadata jsou binární informace popisující váš program, který je uložen buď v souboru přenosného spustitelného souboru (PE) s běžným jazykem, nebo v paměti. Při kompilaci kódu do souboru PE metadata je vložen do jedné části souboru a váš kód je převeden na zprostředkující jazyk Společnosti Microsoft (MSIL) a vložen do jiné části souboru. Každý typ a člen, který je definován a odkazován v modulu nebo sestavení je popsán v metadatech. Při spuštění kódu modul runtime načte metadata do paměti a odkazuje na něj, aby zjistil informace o třídách kódu, členech, dědičnosti a tak dále.

 Metadata popisují každý typ a člen definovaný v kódu jazykově neutrálním způsobem. Metadata ukládá následující informace:

- Popis sestavení.

  - Identita (název, verze, jazyková verze, veřejný klíč).

  - Typy, které jsou exportovány.

  - Další sestavení, na kterých závisí toto sestavení.

  - Oprávnění zabezpečení potřebná ke spuštění.

- Popis typů.

  - Název, viditelnost, základní třída a rozhraní implementována.

  - Členové (metody, pole, vlastnosti, události, vnořené typy).

- Atributy.

  - Další popisné prvky, které upravují typy a členy.

## <a name="benefits-of-metadata"></a>Výhody metadat

Metadata jsou klíčem k jednoduššímu programovacímu modelu a eliminují potřebu souborů IDL (Interface Definition Language), souborů hlaviček nebo jakékoli externí metody odkazu na komponenty. Metadata umožňuje jazyky rozhraní .NET Framework popsat sami automaticky jazykově neutrálním způsobem, který vývojář i uživatel nevidí. Metadata je navíc rozšiřitelná pomocí atributů. Metadata poskytují následující hlavní výhody:

- Samopopisné soubory.

  Moduly a sestavení modulů a sestavení modulů společného jazyka jsou samopopisující. Metadata modulu obsahují vše potřebné pro interakci s jiným modulem. Metadata automaticky poskytuje funkce IDL v com, takže můžete použít jeden soubor pro definici i implementaci. Moduly a sestavy runtime ani nevyžadují registraci u operačního systému. V důsledku toho popisy používané za běhu vždy odrážet skutečný kód v kompilovaném souboru, což zvyšuje spolehlivost aplikace.

- Jazyková interoperabilita a snadnější návrh založený na komponentách.

  Metadata poskytuje všechny informace potřebné o zkompilovaný kód pro vás zdědit třídu ze souboru PE napsané v jiném jazyce. Můžete vytvořit instanci libovolné třídy napsané v libovolném spravovaném jazyce (libovolný jazyk, který se zaměřuje na běžný jazyk runtime) bez obav o explicitní zařazování nebo pomocí vlastního kódu interoperability.

- Atributy.

  Rozhraní .NET Framework umožňuje deklarovat určité druhy metadat, nazývaných atributy, v kompilovaném souboru. Atributy lze nalézt v rámci rozhraní .NET Framework a slouží k podrobnějšímu řízení, jak se program chová za běhu. Kromě toho můžete vyzařovat vlastní metadata do souborů rozhraní .NET Framework prostřednictvím vlastních atributů definovaných uživatelem. Další informace naleznete v [tématu Atributy](../../docs/standard/attributes/index.md).

## <a name="metadata-and-the-pe-file-structure"></a>Metadata a struktura přenositelného spustitelného souboru

Metadata jsou uložena v jedné části přenosného spustitelného souboru rozhraní .NET Framework (PE), zatímco zprostředkující jazyk Společnosti Microsoft (MSIL) je uložen v jiné části souboru PE. Část metadat souboru obsahuje řadu datových struktur tabulky a haldy. Část MSIL obsahuje msil a tokeny metadat, které odkazují na část metadat souboru PE. Tokeny metadat se mohou vyskytnou, když používáte nástroje, jako je například [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení MSIL kódu, například.

### <a name="metadata-tables-and-heaps"></a>Tabulky metadat a hromady metadat

V každé tabulce metadat jsou uvedeny informace o prvcích programu. Například jedna tabulka metadat popisuje třídy v kódu, jiná tabulka popisuje pole a tak dále. Pokud máte deset tříd v kódu, tabulka tříd bude mít desítky řádků, jeden pro každou třídu. Tabulky metadat odkazují na jiné tabulky a hromady. Například tabulka metadat pro třídy odkazuje na tabulku metod.

Metadata také ukládá informace ve čtyřech strukturách haldy: řetězec, objekt blob, uživatelský řetězec a GUID. Všechny řetězce používané k pojmenování typů a členů jsou uloženy v haldě řetězce. Například tabulka metody neukládá přímo název určité metody, ale odkazuje na název metody uložený v haldě řetězce.

### <a name="metadata-tokens"></a>Tokeny metadat

Každý řádek každé tabulky metadat je jednoznačně identifikován v části MSIL souboru PE tokenem metadat. Tokeny metadat jsou koncepčně podobné ukazatele, trvalé v MSIL, které odkazují na konkrétní tabulky metadat.

Token metadat je čtyřbajtové číslo. Horní bajt označuje tabulku metadat, na kterou odkazuje konkrétní token (metoda, typ a tak dále). Zbývající tři bajty určují řádek v tabulce metadat, který odpovídá popsanému programovacímu prvku. Pokud definujete metodu v c# a zkompilujete ji do souboru PE, může existovat následující token metadat v části MSIL souboru PE:

`0x06000004`

Horní bajt`0x06`( ) označuje, že se jedná o token **MethodDef.** Nižší tři bajty`000004`( ) říká za běhu běžného jazyka hledat ve čtvrtém řádku tabulky **MethodDef** informace, které popisují tuto definici metody.

### <a name="metadata-within-a-pe-file"></a>Metadata v souboru PE

Když je program kompilován pro běžný jazyk runtime, je převeden na soubor PE, který se skládá ze tří částí. Následující tabulka popisuje obsah každé části.

|Sekce PE|Obsah sekce PE|
|----------------|----------------------------|
|Hlavička PE|Index hlavních částí souboru PE a adresa vstupního bodu.<br /><br /> Runtime používá tyto informace k identifikaci souboru jako soubor pe a určit, kde spuštění spustí při načítání programu do paměti.|
|MSIL – instrukce|Pokyny pro zprostředkující jazyk společnosti Microsoft (MSIL), které tvoří váš kód. Mnoho msil pokyny jsou doprovázeny tokeny metadat.|
|Metadata|Tabulky metadat a hromady. Runtime používá tuto část k zaznamenání informací o každém typu a členu ve vašem kódu. Tato část také obsahuje vlastní atributy a informace o zabezpečení.|

## <a name="run-time-use-of-metadata"></a>Používání metadat v době běhu

Chcete-li lépe porozumět metadatům a jejich roli v modulu runtime společného jazyka, může být užitečné vytvořit jednoduchý program a ilustrovat, jak metadata ovlivňují jeho životnost za běhu. Následující příklad kódu ukazuje dvě metody `MyApp`uvnitř třídy s názvem . Metoda `Main` je vstupní bod programu, `Add` zatímco metoda jednoduše vrátí součet dvou celé ho argumenty.

```vb
Public Class MyApp
   Public Shared Sub Main()
      Dim ValueOne As Integer = 10
      Dim ValueTwo As Integer = 20
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo))
   End Sub

   Public Shared Function Add(One As Integer, Two As Integer) As Integer
      Return (One + Two)
   End Function
End Class
```

```csharp
using System;
public class MyApp
{
   public static int Main()
   {
      int ValueOne = 10;
      int ValueTwo = 20;
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo));
      return 0;
   }
   public static int Add(int One, int Two)
   {
      return (One + Two);
   }
}
```

Při spuštění kódu modul runtime načte modul do paměti a nahlíží metadata pro tuto třídu. Po načtení provede runtime rozsáhlou analýzu datového proudu zprostředkujícího jazyka Microsoft (MSIL) metody a převede jej na rychlé nativní pokyny počítače. Runtime používá kompilátor just-in-time (JIT) k převodu pokynů MSIL na nativní strojový kód jednu metodu najednou podle potřeby.

Následující příklad ukazuje část MSIL vyrobené z funkce `Main` předchozího kódu. MSIL a metadata můžete zobrazit z libovolné aplikace rozhraní .NET Framework pomocí [disassembleru MSIL (Ildasm.exe).](../../docs/framework/tools/ildasm-exe-il-disassembler.md)

```console
.entrypoint
.maxstack  3
.locals ([0] int32 ValueOne,
         [1] int32 ValueTwo,
         [2] int32 V_2,
         [3] int32 V_3)
IL_0000:  ldc.i4.s   10
IL_0002:  stloc.0
IL_0003:  ldc.i4.s   20
IL_0005:  stloc.1
IL_0006:  ldstr      "The Value is: {0}"
IL_000b:  ldloc.0
IL_000c:  ldloc.1
IL_000d:  call int32 ConsoleApplication.MyApp::Add(int32,int32) /* 06000003 */
```

Kompilátor JIT přečte MSIL pro celou metodu, důkladně analyzuje a generuje efektivní nativní pokyny pro metodu. Na `IL_000d`, metadata token `Add` pro`/*` `06000003 */`metodu ( ) je zjištěna a modul runtime používá token ke konzultaci třetí řádek **Tabulky MethodDef.**

V následující tabulce je uvedena část tabulky **MethodDef** odkazovaná tokenem metadat, který popisuje metodu. `Add` Zatímco ostatní tabulky metadat existují v tomto sestavení a mají své vlastní jedinečné hodnoty, je popsána pouze tato tabulka.

|Řádek|Relativní virtuální adresa (RVA)|Příznaky ImplFlags|Příznaky|Name (Název)<br /><br /> (Odkazuje na haldu řetězce.)|Podpis (odkazuje na haldu objektu blob.)|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1|0x00002050|IL<br /><br /> Spravovaní|Public<br /><br /> Znovu použítSlot<br /><br /> SpecialName<br /><br /> Název RTSpecialName<br /><br /> .ctor|.ctor (konstruktor)||
|2|0x00002058|IL<br /><br /> Spravovaní|Public<br /><br /> Statická<br /><br /> Znovu použítSlot|Hlavní|Řetězec|
|3|0x0000208c|IL<br /><br /> Spravovaní|Public<br /><br /> Statická<br /><br /> Znovu použítSlot|Přidat|int, int, int|

Každý sloupec tabulky obsahuje důležité informace o kódu. Sloupec **RVA** umožňuje za běhu vypočítat počáteční adresu paměti MSIL, která definuje tuto metodu. **ImplFlags** a **Flags** sloupce obsahují bitové masky, které popisují metodu (například zda je metoda veřejné nebo soukromé). Název **Name** sloupec indexuje název metody z haldy řetězce. Sloupec **Podpis** indexuje definici podpisu metody v haldě objektu blob.

Za běhu vypočítá požadovanou adresu posunu ze sloupce **RVA** ve třetím řádku a vrátí tuto adresu kompilátoru JIT, který pak pokračuje na novou adresu. Kompilátor JIT pokračuje ve zpracování jazyka MSIL na nové adrese, dokud nenarazí na jiný token metadat a proces se opakuje.

Pomocí metadat má modul runtime přístup ke všem informacím, které potřebuje k načtení kódu a jeho zpracování do nativních pokynů počítače. Tímto způsobem metadata umožňuje vlastní popis souborů a spolu s běžným systémem typu dědičnost mezi jazyky.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Atributy](../../docs/standard/attributes/index.md)|Popisuje, jak použít atributy, psát vlastní atributy a načítat informace, které jsou uloženy v atributech.|
