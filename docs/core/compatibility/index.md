---
title: Typy přerušovatých změn
description: Zjistěte, jak se rozhraní .NET Core pokouší zachovat kompatibilitu pro vývojáře ve verzích rozhraní .NET a jaký druh změny je považován za narušující změnu.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628589"
---
# <a name="changes-that-affect-compatibility"></a>Změny, které ovlivňují kompatibilitu

V průběhu své historie .NET se pokusil a udržovat vysokou úroveň kompatibility z verze na verzi a napříč variantami .NET. To platí i nadále pro .NET Core. Přestože .NET Core lze považovat za novou technologii, která je nezávislá na rozhraní .NET Framework, dva hlavní faktory omezují schopnost .NET Core odchýlit se od rozhraní .NET Framework:

- Velký počet vývojářů původně vyvinutý nebo pokračovat ve vývoji aplikací rozhraní .NET Framework. Očekávají konzistentní chování napříč implementacemi rozhraní .NET.

- Projekty knihovny .NET Standard umožňují vývojářům vytvářet knihovny, které cílí na běžná rozhraní API sdílená rozhraními .NET Core a .NET Framework. Vývojáři očekávají, že knihovna použitá v aplikaci .NET Core by se měla chovat stejně jako stejná knihovna používaná v aplikaci rozhraní .NET Framework.

Spolu s kompatibilitou napříč implementacemi rozhraní .NET vývojáři očekávají vysokou úroveň kompatibility napříč verzemi .NET Core. Zejména kód napsaný pro starší verzi rozhraní .NET Core by měl běžet bez problémů v novější verzi rozhraní .NET Core. Ve skutečnosti mnoho vývojářů očekává, že nová rozhraní API nalezená v nově vydaných verzích rozhraní .NET Core by měla být také kompatibilní s předběžnými verzemi, ve kterých byla tato rozhraní API zavedena.

Tento článek popisuje kategorie změny kompatibility (nebo narušující změny) a způsob, jakým tým .NET vyhodnocuje změny v každé z těchto kategorií. Pochopení toho, jak tým .NET přistupuje k možným narušujícím změnám, je užitečné zejména pro vývojáře, kteří otevírají žádosti o přijetí změn v úložišti GitHub [dotnet/runtime,](https://github.com/dotnet/runtime) které mění chování existujících rozhraní API.

> [!NOTE]
> Definice kategorií kompatibility, jako je například binární kompatibilita a zpětná kompatibilita, naleznete [v tématu Breaking change categories](categories.md).

Následující části popisují kategorie změn provedených rozhraní API .NET Core a jejich dopad na kompatibilitu aplikací. Změny jsou buď povoleny ❌✔️, zakázáno , nebo vyžadují úsudek a hodnocení toho, jak předvídatelné, zřejmé a konzistentní předchozí chování bylo ❓.

> [!NOTE]
> Kromě toho, že slouží jako vodítko pro vyhodnocování změn v knihovnách .NET Core, mohou vývojáři knihovny také použít tato kritéria k vyhodnocení změn v jejich knihovnách, které cílí na více implementací a verzí rozhraní .NET.

## <a name="modifications-to-the-public-contract"></a>Změny veřejné zakázky

Změny v této kategorii upravují veřejnou plochu typu. Většina změn v této kategorii jsou zakázány, protože porušují *zpětnou kompatibilitu* (schopnost aplikace, která byla vyvinuta s předchozí verzí rozhraní API spustit bez rekompilace v novější verzi).

### <a name="types"></a>Typy

- ✔️ **povoleno: Odebrání implementace rozhraní z typu, když je rozhraní již implementováno základním typem**

- ❓ **vyžaduje úsudek: Přidání nové implementace rozhraní typu**

  Jedná se o přijatelnou změnu, protože nemá nepříznivý vliv na stávající klienty. Všechny změny typu musí fungovat v rámci hranic přijatelné změny definované zde pro nové implementace zůstat přijatelné. Extrémní opatrnost je nutná při přidávání rozhraní, které přímo ovlivňují schopnost návrháře nebo serializátoru generovat kód nebo data, která nelze spotřebovat na nižší úrovni. Příkladem je <xref:System.Runtime.Serialization.ISerializable> rozhraní.

- ❓ **vyžaduje úsudek: Zavedení nové základní třídy**

  Typ může být zaveden do hierarchie mezi dvěma existujícími typy, pokud nezavádí žádné nové [abstraktní](../../csharp/language-reference/keywords/abstract.md) členy nebo nemění sémantiku nebo chování existujících typů. Například v rozhraní .NET Framework <xref:System.Data.Common.DbConnection> 2.0 se třída <xref:System.Data.SqlClient.SqlConnection>stala novou základní třídou pro , která byla dříve odvozena přímo z . <xref:System.ComponentModel.Component>

- ✔️ **povoleno: Přesunutí typu z jedné sestavy do druhé**

  *Staré* sestavení musí být <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> označeno, které odkazuje na nové sestavení.

- ✔️ **povoleno: [struct](../../csharp/language-reference/builtin-types/struct.md) Změna typu struktury `readonly struct` na typ**

  Změna `readonly struct` typu na `struct` typ není povolena.

- ✔️ **povoleno: Přidání [zapečetěného](../../csharp/language-reference/keywords/sealed.md) nebo [abstraktního](../../csharp/language-reference/keywords/abstract.md) klíčového slova k typu, pokud neexistují žádné *přístupné* (veřejné nebo chráněné) konstruktory**

- ✔️ **povoleno: Rozšíření viditelnosti typu**

- ❌**Zakázáno: Změna oboru názvů nebo názvu typu**

- ❌**Zakázáno: Přejmenování nebo odebrání veřejného typu**

   Tím se rozdělí veškerý kód, který používá přejmenovaný nebo odebraný typ.

- ❌**Zakázáno: Změna základního typu výčtu**

   Toto je změna kompilace a chování lámání, stejně jako binární zalomení změny, které mohou atribut argumenty neopravitelné.

- ❌**Zakázáno: Zapečetění typu, který byl dříve nezapečetěný**

- ❌**Zakázáno: Přidání rozhraní do sady základních typů rozhraní**

   Pokud rozhraní implementuje rozhraní, které dříve neimplementoval, jsou poškozeny všechny typy, které implementovaly původní verzi rozhraní.

- ❓ **vyžaduje úsudek: Odebrání třídy ze sady základních tříd nebo rozhraní ze sady implementovaných rozhraní**

  Existuje jedna výjimka z pravidla pro odebrání rozhraní: můžete přidat implementaci rozhraní, které je odvozeno z odebraného rozhraní. Můžete například odebrat, <xref:System.IDisposable> pokud typ nebo <xref:System.ComponentModel.IComponent>rozhraní nyní <xref:System.IDisposable>implementuje , který implementuje .

- ❌**Zakázáno: Změna `readonly struct` typu [na](../../csharp/language-reference/builtin-types/struct.md) typ struktury**

  Změna `struct` typu typu `readonly struct` je však povolena.

- ❌**Zakázáno: Změna typu [struktury](../../csharp/language-reference/builtin-types/struct.md) na `ref struct` typ a naopak.**

- ❌**Zakázáno: Snížení viditelnosti typu**

   Zvýšení viditelnosti typu je však povoleno.

### <a name="members"></a>Členové

- ✔️ **povoleno: Rozšíření viditelnosti člena, který není [virtuální](../../csharp/language-reference/keywords/sealed.md) **

- ✔️ **povoleno: Přidání abstraktního člena do veřejného typu, který nemá žádné *přístupné* (veřejné nebo chráněné) konstruktory, nebo je [zapečetěný typ.](../../csharp/language-reference/keywords/sealed.md) **

  Přidání abstraktního člena do typu, který má přístupné (veřejné nebo `sealed` chráněné) konstruktory a není povoleno.

- ✔️ **povoleno: Omezení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, pokud typ nemá přístupné (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěný](../../csharp/language-reference/keywords/sealed.md) **

- ✔️ **povoleno: Přesunutí člena do třídy vyšší v hierarchii, než je typ, ze kterého byl odebrán**

- ✔️ **povoleno: Přidání nebo odebrání přepsání**

  Zavedení přepsání může způsobit, že předchozí spotřebitelé přeskočí přepsání při volání [base](../../csharp/language-reference/keywords/base.md).

- ✔️ **povoleno: Přidání konstruktoru do třídy, spolu s konstruktorem bez parametrů, pokud třída dříve neměla žádné konstruktory**

   Přidání konstruktoru do třídy, která dříve neměla žádné konstruktory *bez* přidání konstruktoru bez parametrů, však není povoleno.

- ✔️ **povoleno: Změna člena z [abstraktního](../../csharp/language-reference/keywords/abstract.md) na [virtuální](../../csharp/language-reference/keywords/virtual.md) **

- ✔️ **povoleno: Přechod `ref readonly` z `ref` a na vrácenou hodnotu (s výjimkou virtuálních metod nebo rozhraní)**

- ✔️ **povoleno: Odebrání [pouze pro čtení](../../csharp/language-reference/keywords/readonly.md) z pole, pokud statický typ pole není proměnlivý typ hodnoty**

- ✔️ **povoleno: Volání nové události, která nebyla dříve definována**

- ❓ **vyžaduje úsudek: Přidání pole nové instance k typu**

   Tato změna má vliv na serializaci.

- ❌**Zakázáno: Přejmenování nebo odebrání veřejného člena nebo parametru**

   Tím se rozdělí veškerý kód, který používá přejmenovaný nebo odebraný člen nebo parametr.

   To zahrnuje odebrání nebo přejmenování getter nebo setter z vlastnosti, jakož i přejmenování nebo odebrání členů výčtu.

- ❌**Zakázáno: Přidání člena do rozhraní**

- ❌**Zakázáno: Změna hodnoty veřejné konstanty nebo člena výčtu**

- ❌**Zakázáno: Změna typu vlastnosti, pole, parametru nebo vrácené hodnoty**

- ❌**Zakázáno: Přidání, odebrání nebo změna pořadí parametrů**

- ❌**Zakázáno: Přidání nebo odebrání klíčového slova [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) nebo [ref](../../csharp/language-reference/keywords/ref.md) z parametru**

- ❌**Zakázáno: Přejmenování parametru (včetně změny jeho případu)**

  To je považováno za porušení ze dvou důvodů:

  - Přeruší scénáře s pozdní vazbou, jako je například funkce pozdní vazby v jazyce Visual Basic a [dynamické](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) v jazyce C#.

  - Přeruší [kompatibilitu zdroje,](categories.md#source-compatibility) když vývojáři používají [pojmenované argumenty](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- ❌**Zakázáno: Změna z `ref` vrácené `ref readonly` hodnoty na vrácenou hodnotu**

- ❌️**Zakázáno: Přechod z `ref readonly` a `ref` na vrácenou hodnotu na virtuální metodu nebo rozhraní**

- ❌**Zakázáno: Přidání nebo odebrání [abstraktu](../../csharp/language-reference/keywords/abstract.md) z člena**

- ❌**Zakázáno: Odebrání [virtuálního](../../csharp/language-reference/keywords/virtual.md) klíčového slova z člena**

  I když to často není narušující změna, protože kompilátor Jazyka C# má tendenci vyzařovat pokyny`callvirt` pro volání zprostředkujícího jazyka [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) (IL) pro volání nevirtuálních metod (provádí kontrolu null, zatímco normální volání není), toto chování není neměnné z několika důvodů:
  - C# není jediný jazyk, který .NET cíle.

  - Kompilátor Jazyka C# `callvirt` se stále více pokouší optimalizovat na normální volání vždy, když je metoda target nevirtuální a pravděpodobně není null (například metoda přístupná prostřednictvím [operátoru šíření null ).](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)

  Vytvoření virtuální metody znamená, že kód příjemce by často skončí volání mj.

- ❌**Zakázáno: Přidání [virtuálního](../../csharp/language-reference/keywords/virtual.md) klíčového slova do člena**

- ❌**Zakázáno: Vytvoření abstraktního virtuálního člena**

  [Virtuální člen](../../csharp/language-reference/keywords/virtual.md) poskytuje implementaci metody, která *může být* přepsána odvozenou třídou. [Abstraktní člen](../../csharp/language-reference/keywords/abstract.md) poskytuje žádnou implementaci a *musí být* přepsán.

- ❌**Zakázáno: Přidání abstraktního člena do veřejného typu, který má přístupné (veřejné nebo chráněné) konstruktory a který není [zapečetěný](../../csharp/language-reference/keywords/sealed.md) **

- ❌**Zakázáno: Přidání nebo odebrání [statického](../../csharp/language-reference/keywords/static.md) klíčového slova z člena**

- ❌**Zakázáno: Přidání přetížení, které vylučuje existující přetížení a definuje jiné chování**

  Tím se přeruší existující klienti, kteří byli vázáni na předchozí přetížení. Například pokud třída má jednu verzi metody, <xref:System.UInt32>která přijímá , existující příjemce bude úspěšně <xref:System.Int32> vázat na toto přetížení při předávání hodnoty. Však pokud přidáte přetížení, které <xref:System.Int32>přijímá , při rekompilaci nebo pomocí pozdní vazby, kompilátor nyní váže na nové přetížení. Pokud dojde k odlišnému chování, jedná se o narušující změnu.

- ❌**Zakázáno: Přidání konstruktoru do třídy, která dříve neměla žádný konstruktor bez přidání konstruktoru bez parametrů**

- ❌️**Zakázáno: Přidání [pouze pro čtení](../../csharp/language-reference/keywords/readonly.md) do pole**

- ❌**Zakázáno: Snížení viditelnosti člena**

   To zahrnuje snížení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) prvku, pokud`public` `protected`jsou *přístupné* ( nebo ) konstruktory a typ *není* [zapečetěn .](../../csharp/language-reference/keywords/sealed.md) Pokud tomu tak není, je povoleno snížení viditelnosti chráněného člena.

   Zvýšení viditelnosti člena je povoleno.

- ❌**Zakázáno: Změna typu člena**

   Vrácenou hodnotu metody nebo typu vlastnosti nebo pole nelze změnit. Například podpis metody, která vrací <xref:System.Object> nelze změnit vrátit <xref:System.String>, nebo naopak.

- ❌**Zakázáno: Přidání pole do struktury, která dříve neměla žádný stav**

  Pravidla jednoznačného přiřazení umožňují použití neinicializovaných proměnných, pokud je typ proměnné strukturou bez stavů. Pokud je struktura provedena stavové, kód může skončit s neinicializovaných dat. Toto je potenciálně zdroj rozdělení a binární rozdělení změny.

- ❌**Zakázáno: Spuštění existující události, když nebyla nikdy předtím aktivována**

## <a name="behavioral-changes"></a>Změny chování

### <a name="assemblies"></a>Sestavení

- ✔️ **povoleno: Vytvoření přenosné sestavy, pokud jsou stále podporovány stejné platformy**

- ❌**Zakázáno: Změna názvu sestavení**
- ❌**Zakázáno: Změna veřejného klíče sestavení**

### <a name="properties-fields-parameters-and-return-values"></a>Vlastnosti, pole, parametry a vrácené hodnoty

- ✔️ **povoleno: Změna hodnoty vlastnosti, pole, vrácené hodnoty nebo parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na odvozenější typ**

  Například metoda, která vrací <xref:System.Object> typ může <xref:System.String> vrátit instanci. (Podpis metody se však nemůže změnit.)

- ✔️ **povoleno: Zvýšení rozsahu přijatých hodnot pro vlastnost nebo parametr, pokud člen není [virtuální](../../csharp/language-reference/keywords/virtual.md) **

  Zatímco rozsah hodnot, které mohou být předány metodě nebo jsou vráceny členem lze rozšířit, parametr nebo typ člena nelze. Například zatímco hodnoty předané metodě lze rozšířit z 0-124 na 0-255, typ parametru nelze změnit z na <xref:System.Byte> <xref:System.Int32>.

- ❌**Zakázáno: Zvýšení rozsahu přijatých hodnot pro vlastnost nebo parametr, pokud je člen [virtuální](../../csharp/language-reference/keywords/virtual.md) **

   Tato změna přeruší existující přepsané členy, které nebudou fungovat správně pro rozšířený rozsah hodnot.

- ❌**Zakázáno: Snížení rozsahu přijatých hodnot pro vlastnost nebo parametr**

- ❌**Zakázáno: Zvýšení rozsahu vrácených hodnot pro parametr vlastnost, [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) pole, vrácenou hodnotu nebo out parametr**

- ❌**Zakázáno: Změna vrácených hodnot pro vlastnost, pole, vrácenou hodnotu metody nebo parametr [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) **

- ❌**Zakázáno: Změna výchozí hodnoty vlastnosti, pole nebo parametru**

- ❌**Zakázáno: Změna přesnosti číselné vrácené hodnoty**

- ❓ **vyžaduje úsudek: Změna analýzy vstupu a vyvolání nových výjimek (i když chování analýzy není specifikováno v dokumentaci**

### <a name="exceptions"></a>Výjimky

- ✔️ **povoleno: Vyvolání více odvozené výjimky než existující výjimky**

  Vzhledem k tomu, že nová výjimka je podtřídou existující výjimky, předchozí kód zpracování výjimek pokračuje ve zpracování výjimky. Například v rozhraní .NET Framework 4 metody vytváření a <xref:System.Globalization.CultureNotFoundException> načítání <xref:System.ArgumentException> jazykové verze začaly vyvolávat místo, pokud nelze nalézt jazykovou verzi. Protože <xref:System.Globalization.CultureNotFoundException> pochází <xref:System.ArgumentException>z , jedná se o přijatelnou změnu.

- ✔️ **povoleno: Vyvolání konkrétnější <xref:System.NotSupportedException>výjimky <xref:System.NullReferenceException> než , <xref:System.NotImplementedException>**

- ✔️ **povoleno: Vyvolání výjimky, která je považována za neopravitelnou**

  Neopravitelné výjimky by neměly být zachyceny, ale místo toho by měly být zpracovány obslužnou rutinou catch-all na vysoké úrovni. Proto se neočekává, že uživatelé mají kód, který zachycuje tyto explicitní výjimky. Neopravitelné výjimky jsou:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- ✔️ **povoleno: Vyvolání nové výjimky v nové cestě kódu**

  Výjimka se musí vztahovat pouze na novou cestu kódu, která je spuštěna s novými hodnotami parametrů nebo stavem a kterou nelze provést existujícím kódem, který cílí na předchozí verzi.

- ✔️ **povoleno: Odebrání výjimky pro povolení robustnějšího chování nebo nových scénářů**

  Například `Divide` metoda, která dříve zpracovávala pouze <xref:System.ArgumentOutOfRangeException> kladné hodnoty a jinak vyvolala jinak, může být změněna tak, aby podporovala záporné i kladné hodnoty bez vyvolání výjimky.

- ✔️ **povoleno: Změna textu chybové zprávy**

  Vývojáři by neměli spoléhat na text chybových zpráv, které se také mění na základě jazykové verze uživatele.

- ❌**Zakázáno: Vyvolání výjimky v jakémkoli jiném případě, který není uveden výše**

- ❌**Zakázáno: Odebrání výjimky v jakémkoli jiném případě, který není uveden výše.**

### <a name="attributes"></a>Atributy

- ✔️ **povoleno: Změna hodnoty atributu, který *není* pozorovatelný**

- ❌**Zakázáno: Změna hodnoty atributu, který *je* pozorovatelný**

- ❓ **vyžaduje úsudek: Odebrání atributu**

  Ve většině případů je odebrání <xref:System.NonSerializedAttribute>atributu (například) narušující změnou.

## <a name="platform-support"></a>Podpora platformy

- ✔️ **povoleno: Podpora operace na platformě, která dříve nebyla podporována**

- ❌**Zakázáno: Nepodporuje nebo nyní vyžaduje konkrétní aktualizaci Service Pack pro operaci, která byla dříve podporována na platformě**

## <a name="internal-implementation-changes"></a>Změny interní implementace

- ❓ **vyžaduje úsudek: Změna plochy vnitřního typu**

   Takové změny jsou obecně povoleny, i když porušují soukromé reflexe. V některých případech, kdy populární knihovny třetích stran nebo velký počet vývojářů závisí na interní rozhraní API, tyto změny nemusí být povoleny.

- ❓ **vyžaduje úsudek: Změna vnitřní implementace členského**

  Tyto změny jsou obecně povoleny, i když porušují soukromé reflexe. V některých případech, kde kód zákazníka často závisí na soukromé reflexe nebo kde změna zavádí nežádoucí vedlejší účinky, tyto změny nemusí být povolena.

- ✔️ **povoleno: Zlepšení výkonu operace**

   Schopnost změnit výkon operace je nezbytná, ale tyto změny mohou přerušit kód, který závisí na aktuální rychlosti operace. To platí zejména pro kód, který závisí na časování asynchronní operace. Změna výkonu by neměla mít žádný vliv na jiné chování daného rozhraní API; v opačném případě bude změna prolomena.

- ✔️ **povoleno: Nepřímo (a často nepříznivě) mění výkon operace**

  Není-li dotyčná změna z nějakého jiného důvodu kvalifikována jako porušení, je to přijatelné. Často je třeba provést akce, které mohou zahrnovat další operace nebo které přidávají nové funkce. To bude téměř vždy ovlivnit výkon, ale může být nezbytné, aby rozhraní API v otázce fungovat podle očekávání.

- ❌**Zakázáno: Změna synchronního rozhraní API na asynchronní (a naopak)**

## <a name="code-changes"></a>Změny kódu

- ✔️ **povoleno: Přidání [paramů](../../csharp/language-reference/keywords/params.md) do parametru**

- ❌**Zakázáno: Změna [struktury](../../csharp/language-reference/builtin-types/struct.md) na [třídu](../../csharp/language-reference/keywords/class.md) a naopak**

- ❌**Zakázáno: Přidání [zaškrtnutého](../../csharp/language-reference/keywords/virtual.md) klíčového slova do bloku kódu**

   Tato změna může způsobit kód, který <xref:System.OverflowException> byl dříve spuštěn vyvolat a je nepřijatelné.

- ❌**Zakázáno: Odebrání [paramů](../../csharp/language-reference/keywords/params.md) z parametru**

- ❌**Zakázáno: Změna pořadí, ve kterém jsou aktivovány události**

  Vývojáři mohou rozumně očekávat, že události se spálí ve stejném pořadí a kód vývojáře často závisí na pořadí, ve kterém jsou události aktivovány.

- ❌**Zakázáno: Odebrání vyvolání události u dané akce**

- ❌**Zakázáno: Změna počtu, kolikrát se nazývají dané události.**

- ❌**Zakázáno: Přidání <xref:System.FlagsAttribute> do typu výčtu**
