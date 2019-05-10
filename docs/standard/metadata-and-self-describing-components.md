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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ccfb0dee0eb6380d48498ba61f763eb777bded1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754941"
---
# <a name="metadata-and-self-describing-components"></a>Metadata a komponenty popisující samy sebe

V minulosti součást softwaru (.exe nebo .dll), která byla zapsána v jednom jazyce nelze použít snadno softwarová součást, která byla zapsána v jiném jazyce. COM poskytuje krok k řešení tohoto problému. Rozhraní .NET Framework usnadňuje spolupráci komponenty i tím, že kompilátory pro generování dalších deklarativní informace do všech modulů a sestavení. Tyto informace nazývané metadata, pomáhá součásti komunikovat bez problémů.

 Metadata jsou binární informace, které popisují program, který je uložený v běžných soubor (PE portable executable) modulu runtime jazyka nebo v paměti. Při kompilaci kódu do souboru PE metadata se vloží do jedné části souboru, a je převeden na jazyk Microsoft intermediate language (MSIL) a vložen do jiné části souboru kódu. Každý typ nebo člen, který je definován a odkazuje na modul nebo sestavení, jsou popsány v metadatech. Pokud je kód spuštěn, modul runtime načte metadata do paměti a odkazuje na zjišťování informací o váš kód tříd, členů, dědičnosti a tak dále.

 Metadata popisují každou typů a členů, které jsou definované ve vašem kódu v jazykově neutrální způsob. Metadata se ukládají následující informace:

- Popis sestavení.

  - Identita (název, verze, jazykové verze, veřejného klíče).

  - Typy, které jsou exportovány.

  - Jiná sestavení, na kterých závisí tato sestavení.

  - Oprávnění zabezpečení potřebné ke spuštění.

- Popis typů.

  - Název, viditelnost, základní třídu a implementovaná rozhraní.

  - Členy (metody, pole, vlastnosti, události, vnořené typy).

- Atributy.

  - Další popisný prvky, které upravují typy a členy.

## <a name="benefits-of-metadata"></a>Výhody metadat

Metadata je klíčem k jednodušší programovací model a eliminuje potřebu soubory, soubory hlaviček nebo všechny externí metoda odkaz na komponentu rozhraní Definition Language (IDL). Metadata umožňují jazycích rozhraní .NET Framework k podrobnému popisu, sami automaticky způsobem jazykově neutrální, neviditelný vývojáře a uživatele. Kromě toho je rozšiřitelný prostřednictvím použití atributů metadat. Metadata poskytují následující hlavní výhody:

- Soubory popisující samy sebe.

  Common language runtime modulů a sestavení jsou popisující samy sebe. Metadata modulu obsahuje vše potřebné k interakci s jiný modul. Metadata automaticky poskytuje funkce pro IDL v modelu COM, abyste mohli používat jeden soubor pro definici i implementaci. Moduly runtime a sestavení i nevyžadují registraci s operačním systémem. V důsledku toho popisů používaných modulem runtime vždy odráží skutečný kód zkompilovaný soubor, což zvyšuje spolehlivost aplikace.

- Vzájemná funkční spolupráce jazyka a jednodušší návrh založených na komponentách.

  Metadata poskytují všechny požadované informace o zkompilovaný kód si můžete dědit třídy ze souboru PE napsané v jiném jazyce. Můžete vytvořit instance libovolné třídy napsané v libovolném jazyce spravované (libovolný jazyk, který se zaměřuje na modul common language runtime) bez starostí o explicitní zařazování nebo pomocí kódu vlastní vzájemná funkční spolupráce.

- Atributy.

  Rozhraní .NET Framework umožňuje deklarovat konkrétní typy metadat v zkompilovaný soubor jako atributy. Atributy lze nalézt v celém rozhraní .NET Framework a slouží k řízení podrobněji chování vašeho programu za běhu. Kromě toho můžete vysílat vlastní metadata do soubory rozhraní .NET Framework pomocí uživatelsky definované vlastní atributy. Další informace najdete v tématu [atributy](../../docs/standard/attributes/index.md).

## <a name="metadata-and-the-pe-file-structure"></a>Metadata a struktura přenositelného spustitelného souboru

Metadata jsou uložena v jedné části souboru rozhraní .NET Framework přenosné spustitelné (PE), při Microsoft intermediate language (MSIL) je uložen v jiném oddíle souboru PE. Část metadata souboru obsahuje řadu tabulku a haldu datové struktury. Část jazyk MSIL obsahuje jazyk MSIL a metadata tokeny, které odkazují na metadata část souboru PE. Tokeny metadat může dojít, když pomocí nástrojů, jako [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) Chcete-li zobrazit kód uživatele jazyk MSIL, třeba.

### <a name="metadata-tables-and-heaps"></a>Metadata tabulky a haldy

Každá tabulka metadat obsahuje informace o prvky programu. Například jedna tabulka metadata popisuje třídy v kódu, jiné tabulka popisuje pole a tak dále. Pokud máte deset tříd ve vašem kódu, třída tabulka bude mít desítky řádků, jeden pro každou třídu. Metadata tabulky odkazují jiné tabulky a haldy. Například tabulku metadat pro třídy odkazuje na tabulku pro metody.

Metadata také ukládá informace o čtyři struktury haldy: řetězec, objekt blob, uživatel string a GUID. Všechny řetězce pro název typy a členy jsou uloženy v haldě řetězce. Například metoda tabulky přímo neukládá název konkrétní metody, ale odkazuje na název metody uložený v haldě řetězce.

### <a name="metadata-tokens"></a>Tokeny metadat

Každý řádek každé metadat tabulky je jedinečně identifikovaný MSIL část souboru PE token metadat. Tokeny metadat se koncepčně podobá ukazatelů trvalý do jazyka MSIL, odkazující na konkrétní tabulku metadat.

Token metadat je číslo čtyř bajtů. Horní byte označuje metadata tabulky, na který odkazuje konkrétní token (metoda, typ a tak dále). Zbývající bajty tři určení řádku v tabulce metadata, která odpovídá na programovací prvek popisovaný. Pokud definujete metodu v C# a zkompilovat ji do souboru PE, může existovat následující token metadat v části jazyk MSIL přenositelného Spustitelného souboru:

```
0x06000004
```

Horní byte (`0x06`) označuje, že se jedná **MethodDef** token. Nižší třech bajtech (`000004`) říká modul common language runtime podívat na čtvrtém řádku **MethodDef** tabulku informace popisující definici této metody.

### <a name="metadata-within-a-pe-file"></a>Metadata v rámci přenositelný Spustitelný soubor

Při kompilaci programu pro modul common language runtime, je převeden na soubor PE, která se skládá ze tří částí. Následující tabulka popisuje obsah jednotlivých částí.

|PE oddíl|Obsah PE oddíl|
|----------------|----------------------------|
|Záhlaví PE|Index hlavní části souboru PE a adresa vstupního bodu.<br /><br /> Modul runtime používá tyto informace k identifikaci souboru jako přenositelný Spustitelný soubor a k určení, kde provádění začne při načítání program do paměti.|
|MSIL – instrukce|Microsoft intermediate language pokynů (MSIL), které tvoří kódu. Počet instrukcí jazyka MSIL jsou doplněny tokeny metadat.|
|Metadata|Metadata tabulky a haldy. Modul runtime používá k zaznamenání informací o všech typů a členů ve vašem kódu v této části. Tato část také obsahuje informace o zabezpečení a vlastní atributy.|

## <a name="run-time-use-of-metadata"></a>Používání metadat v době běhu

Abyste lépe pochopili metadata a jejich rolí v modulu common language runtime, může být užitečné vytvořit jednoduchý program a ukazují, jak metadata ovlivňuje jeho život v době běhu. Následující příklad kódu ukazuje dvě metody uvnitř třídy nazvané `MyApp`. `Main` Metoda je vstupní bod programu, zatímco `Add` metoda jednoduše vrací součet dvou argumentů celé číslo.

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

Při spuštění kódu, modul runtime modul načítá do paměti a bere v úvahu metadata pro tuto třídu. Po načtení, modul runtime provádí rozsáhlé analýzy metody Microsoft intermediate language (MSIL) datového proudu pro převod na rychlé nativních strojové instrukce. Modul runtime používá kompilátor just-in-time (JIT) pro převod instrukce jazyka MSIL do nativního strojového kódu v době podle potřeby.

Následující příklad ukazuje část MSIL vytvořené z předchozího kódu `Main` funkce. Můžete zobrazit jazyk MSIL a metadata z libovolné aplikace rozhraní .NET Framework pomocí [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md).

```
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

Kompilátor JIT přečte MSIL pro celou metodu, důkladně analyzuje je a generuje efektivní nativní pokyny pro metodu. Na `IL_000d`, token metadat pro `Add` – metoda (`/*` `06000003 */`) dochází a modul runtime používá token poradit třetí řádek **MethodDef** tabulky.

Následující tabulka ukazuje část **MethodDef** tabulka odkazovaná metadat tokenu, který popisuje `Add` metody. Zatímco jiné tabulky metadat existovat v tomto sestavení a mají své vlastní jedinečné hodnoty, jsou popsány pouze v této tabulce.

|Řádek|Relativní virtuální adresu (RVA)|Příznaky ImplFlags|Příznaky|Name<br /><br /> (Odkazuje na řetězec haldy.)|Podpis (bodů do objektu blob haldy.)|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1|0x00002050|IL<br /><br /> Spravovaní|Public<br /><br /> ReuseSlot<br /><br /> SpecialName<br /><br /> RTSpecialName<br /><br /> konstruktoru (.ctor)|konstruktoru (.ctor) (konstruktor)||
|2|0x00002058|IL<br /><br /> Spravovaní|Public<br /><br /> Static<br /><br /> ReuseSlot|Hlavní|String|
|3|0x0000208c|IL<br /><br /> Spravovaní|Public<br /><br /> Static<br /><br /> ReuseSlot|Přidejte|int, int, int|

Každý sloupec v tabulce obsahuje důležité informace o svém kódu. **RVA** sloupec umožňuje modulu runtime pro výpočet adresu paměti MSIL, která definuje tuto metodu. **ImplFlags** a **příznaky** sloupce obsahují vyčíslení, které popisují metody (například, jestli metoda je veřejné nebo soukromé). **Název** sloupec indexuje název metody z haldy řetězce. **Podpis** sloupec indexuje definice podpis metody v haldě objektů blob.

Modul runtime vypočítá požadovanou adresu posunu od **RVA** sloupce ve třetím řádku a vrátí tuto adresu kompilátoru JIT, který pak pokračuje na novou adresu. Kompilátor JIT pokračuje ve zpracování jazyka MSIL na novou adresu, dokud nenarazí na další token metadat a proces se opakuje.

Modul runtime pomocí metadat, má přístup ke všem informacím, které potřebuje načíst kód a zpracovat je do nativních strojové instrukce. Tímto způsobem umožňuje metadat soubory popisující samy sebe a společně s obecný systém typů, dědičnost mezi jazyky.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Atributy](../../docs/standard/attributes/index.md)|Popisuje způsob použití atributů, zápis vlastních atributů a načítání informací uložených v atributech.|
