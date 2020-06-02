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
ms.openlocfilehash: 5327bd70b05bac8970fa9802fb15e94ba5f686c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290055"
---
# <a name="metadata-and-self-describing-components"></a>Metadata a komponenty popisující samy sebe

Součást softwaru (. exe nebo. dll), která byla napsána v jednom jazyce, nemohla snadno použít softwarovou komponentu, která byla napsána v jiném jazyce. Model COM poskytl krok k řešení tohoto problému. .NET Framework umožňuje, aby kompilátory vygenerovaly další deklarativní informace do všech modulů a sestavení, a to ještě snadněji. Tyto informace, nazývané metadata, pomáhají komponentám plynule pracovat.

 Metadata jsou binární informace popisující váš program, který je uložený buď v souboru PE (Common Language Runtime), nebo v paměti. Při kompilaci kódu do souboru PE, jsou metadata vložena do jedné části souboru a váš kód je převeden do jazyka MSIL (Microsoft Intermediate Language) a vložen do jiné části souboru. Všechny typy a členy, které jsou definovány a odkazovány v modulu nebo sestavení, jsou popsány v rámci metadat. Při spuštění kódu modul runtime načte metadata do paměti a odkazuje na ni, aby zjistil informace o třídách kódu, členech, dědičnosti a tak dále.

 Metadata popisují každý typ a člen definovaný v kódu v jazyce neutrálním způsobem. Metadata uchovávají následující informace:

- Popis sestavení

  - Identita (název, verze, jazyková verze, veřejný klíč).

  - Typy, které jsou exportovány.

  - Další sestavení, na kterých je toto sestavení závislé.

  - Oprávnění zabezpečení potřebná ke spuštění.

- Popis typů

  - Je implementováno jméno, viditelnost, základní třída a rozhraní.

  - Členové (metody, pole, vlastnosti, události, vnořené typy).

- Atribut.

  - Další popisné prvky, které upravují typy a členy.

## <a name="benefits-of-metadata"></a>Výhody metadat

Metadata jsou klíč pro jednodušší programovací model a eliminují potřebu souborů IDL (Interface Definition Language), hlavičkových souborů nebo jakékoli externí metody odkazu na součást. Díky metadatům .NET Framework jazyky mohou být automaticky popsány v jazyce neutrálním způsobem, nezávisle na vývojáři i uživateli. Metadata se navíc rozšiřují prostřednictvím použití atributů. Metadata poskytují následující hlavní výhody:

- Soubory popisující samy sebe.

  Moduly společného jazykového modulu runtime a sestavení jsou samo-popisující. Metadata modulu obsahují vše potřebné pro interakci s jiným modulem. Metadata automaticky poskytují funkce IDL v modelu COM, takže můžete použít jeden soubor pro definici i implementaci. Běhové moduly a sestavení dokonce nevyžadují registraci s operačním systémem. V důsledku toho popisy používané modulem runtime vždy odrážejí skutečný kód ve zkompilovaném souboru, který zvyšuje spolehlivost aplikace.

- Interoperabilita jazyků a snazší návrh založený na komponentách.

  Metadata poskytují všechny informace, které jsou požadovány pro zkompilovaný kód, k dědění třídy ze souboru PE napsaného v jiném jazyce. Můžete vytvořit instanci libovolné třídy napsané v jakémkoli spravovaném jazyce (libovolný jazyk, který cílí na modul CLR), aniž byste se museli starat o explicitní zařazování nebo použití vlastního kódu interoperability.

- Atribut.

  .NET Framework umožňuje deklarovat v kompilovaném souboru konkrétní druhy metadat označované jako atributy. Atributy lze najít v rámci .NET Framework a používají se k tomu, aby lépe napracovaly podrobnosti o tom, jak se program chová během běhu. Kromě toho můžete pomocí uživatelsky definovaných uživatelských atributů vygenerovat do souborů .NET Framework vlastní metadata. Další informace najdete v tématu [atributy](attributes/index.md).

## <a name="metadata-and-the-pe-file-structure"></a>Metadata a struktura přenositelného spustitelného souboru

Metadata se ukládají v jednom oddílu .NET Framework přenositelného spustitelného souboru (PE), zatímco jazyk MSIL (Microsoft Intermediate Language) je uložený v jiné části souboru PE. Část s metadaty v souboru obsahuje řadu datových struktur tabulky a haldy. Část MSIL obsahuje MSIL a tokeny metadat, které odkazují na část metadat souboru PE. Je možné, že při použití nástrojů, jako je například [MSIL Disassembler (Ildasm. exe)](../framework/tools/ildasm-exe-il-disassembler.md) , k zobrazení jazyka MSIL kódu, můžete narazit na tokeny metadat.

### <a name="metadata-tables-and-heaps"></a>Tabulky a haldy metadat

Každá tabulka metadat obsahuje informace o prvcích programu. Například jedna tabulka metadat popisuje třídy v kódu, další tabulka popisuje pole a tak dále. Pokud máte ve svém kódu deset tříd, tabulka třídy bude mít desítkové řádky, jednu pro každou třídu. Tabulky metadat odkazují na jiné tabulky a haldy. Například tabulka metadat pro třídy odkazuje na tabulku pro metody.

Metadata také ukládají informace ve čtyřech strukturách haldy: řetězec, objekt blob, uživatelský řetězec a identifikátor GUID. Všechny řetězce použité k pojmenování typů a členů jsou uloženy v haldě řetězců. Například tabulka metody přímo neukládá název konkrétní metody, ale odkazuje na název metody uložený v haldě řetězců.

### <a name="metadata-tokens"></a>Tokeny metadat

Každý řádek každé tabulky metadat je jednoznačně identifikovaný v části MSIL souboru PE pomocí tokenu metadat. Tokeny metadat jsou koncepčně podobné ukazatelům, které jsou trvale v jazyce MSIL, které odkazují na konkrétní tabulku metadat.

Token metadat je číslo se čtyřmi bajty. Horní bajt označuje tabulku metadat, na kterou se vztahuje konkrétní token (metoda, typ a tak dále). Zbývající tři bajty určují řádek v tabulce metadat, který odpovídá programovacímu prvku, který je popsán. Definujete-li metodu v jazyce C# a zkompilujete ji do souboru PE, v části MSIL souboru PE mohou existovat následující tokeny metadat:

`0x06000004`

Horní Byte ( `0x06` ) označuje, že se jedná o token **MethodDef** . Dolní tři bajty ( `000004` ) označují modulu CLR (Common Language Runtime), aby vypadal na čtvrtém řádku tabulky **MethodDef** pro informace, které popisují tuto definici metody.

### <a name="metadata-within-a-pe-file"></a>Metadata v rámci souboru PE

Je-li program kompilován pro modul CLR (Common Language Runtime), je převeden na soubor PE, který se skládá ze tří částí. Následující tabulka popisuje obsah každé části.

|Oddíl PE|Oddíl obsahu PE|
|----------------|----------------------------|
|PE – hlavička|Index hlavních částí souboru PE a adresa vstupního bodu.<br /><br /> Modul runtime používá tyto informace k identifikaci souboru jako souboru PE a k určení, kde se spuštění spouští při načítání programu do paměti.|
|MSIL – instrukce|Instrukce jazyka MSIL (Microsoft Intermediate Language), které tvoří váš kód. Mnoho instrukcí jazyka MSIL je doprovází tokeny metadat.|
|Metadata|Tabulky metadat a haldy. Modul runtime používá tuto část k zaznamenání informací o každém typu a členu v kódu. Tato část také obsahuje vlastní atributy a informace o zabezpečení.|

## <a name="run-time-use-of-metadata"></a>Používání metadat v době běhu

Chcete-li lépe pochopit metadata a její roli v modulu CLR (Common Language Runtime), může být užitečné vytvořit jednoduchý program a Ukázat, jak metadata ovlivňují dobu běhu. Následující příklad kódu ukazuje dvě metody uvnitř třídy s názvem `MyApp` . `Main`Metoda je vstupním bodem programu, zatímco `Add` Metoda jednoduše vrátí součet dvou celočíselných argumentů.

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

Když se kód spustí, modul runtime načte modul do paměti a požádá o metadata pro tuto třídu. Po načtení modul runtime provádí rozsáhlou analýzu datového proudu jazyka MSIL (Microsoft Intermediate Language), který je převede na rychlé instrukce nativního počítače. Modul runtime používá kompilátor JIT (just-in-time) k převedení instrukcí jazyka MSIL do nativního strojového kódu na jednu metodu v čase podle potřeby.

Následující příklad ukazuje část MSIL vytvořenou z funkce předchozího kódu `Main` . Můžete zobrazit jazyk MSIL a metadata z libovolné .NET Framework aplikace pomocí [jazyka MSIL Disassembler (Ildasm. exe)](../framework/tools/ildasm-exe-il-disassembler.md).

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

Kompilátor JIT přečte MSIL pro celou metodu, analyzuje ji důkladně a generuje efektivní nativní instrukce pro metodu. V systému `IL_000d` je k dispozici token metadat pro `Add` metodu ( `/*` `06000003 */` ) a modul runtime používá token ke konzultaci třetího řádku tabulky **MethodDef** .

Následující tabulka ukazuje část tabulky **MethodDef** , na kterou odkazuje token metadat, který popisuje `Add` metodu. I když v tomto sestavení existují jiné tabulky metadat a mají své vlastní jedinečné hodnoty, je diskutována pouze tato tabulka.

|Řádek|Relativní virtuální adresa (RVA)|Příznaky ImplFlags|Příznaky|Name<br /><br /> (Odkazuje na haldu řetězců.)|Podpis (odkazuje na haldu objektů BLOB.)|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1|0x00002050|IL<br /><br /> Spravovaní|Public<br /><br /> ReuseSlot<br /><br /> SpecialName<br /><br /> Znak<br /><br /> . ctor|. ctor (konstruktor)||
|2|0x00002058|IL<br /><br /> Spravovaní|Public<br /><br /> Static<br /><br /> ReuseSlot|Hlavní|Řetězec|
|3|0x0000208c|IL<br /><br /> Spravovaní|Public<br /><br /> Static<br /><br /> ReuseSlot|Přidat|int, int, int|

Každý sloupec tabulky obsahuje důležité informace o vašem kódu. Sloupec **RVA** umožňuje modulu runtime vypočítat počáteční adresu paměti jazyka MSIL, která definuje tuto metodu. Sloupce **příznaky ImplFlags** a **Flags** obsahují vyčíslení, které popisují metodu (například zda je metoda veřejná nebo soukromá). Sloupec **název** indexuje název metody z haldy řetězce. Sloupec **Signatura** indexuje definici signatury metody v haldě objektů BLOB.

Modul runtime vypočítá požadovanou adresu posunu ze sloupce **RVA** ve třetím řádku a vrátí tuto adresu kompilátoru JIT, který pak pokračuje na novou adresu. Kompilátor JIT pokračuje v zpracovávání MSIL na nové adrese, dokud nenalezne jiný token metadat a proces se opakuje.

Pomocí metadat má modul runtime přístup ke všem informacím, které potřebuje k načtení kódu a jeho zpracování na nativní pokyny pro počítače. Tímto způsobem metadata umožňují soubory popisující samy sebe a společně s běžným typem systému, dědičnosti mezi jazyky.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Atributy](attributes/index.md)|Popisuje, jak použít atributy, zapsat vlastní atributy a načíst informace, které jsou uloženy v atributech.|
