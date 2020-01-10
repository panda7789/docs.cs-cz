---
title: Typy přerušujících změn – .NET Core
description: Přečtěte si, jak se .NET Core pokusí zachovat kompatibilitu pro vývojáře napříč verzemi .NET a jaký druh změny se považuje za zásadní změnu.
ms.date: 06/10/2019
ms.openlocfilehash: a84468c0c0e04f367dc7e89ce806ac01b2b49b48
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740892"
---
# <a name="changes-that-affect-compatibility"></a>Změny ovlivňující kompatibilitu

V průběhu své historie se .NET pokusilo udržet vysokou úroveň kompatibility z verze na verzi a v různých charakterech rozhraní .NET. To platí i pro .NET Core. I když .NET Core se dá považovat za novou technologii, která je nezávislá na .NET Framework, dva hlavní faktory omezují schopnost .NET Core odchýlit se od .NET Framework:

- Velký počet vývojářů byl buď původně vyvinutý, nebo pokračoval v vývoji .NET Frameworkch aplikací. Očekávají konzistentní chování napříč implementacemi rozhraní .NET.

- Projekty knihovny .NET Standard umožňují vývojářům vytvářet knihovny, které cílí na společná rozhraní API sdílená pomocí .NET Core a .NET Framework. Vývojáři očekávají, že se knihovna používaná v aplikaci .NET Core musí chovat stejně jako stejná knihovna, jakou používá aplikace .NET Framework.

Společně s kompatibilitou mezi implementacemi .NET očekávají vývojáři vysokou úroveň kompatibility napříč verzemi .NET Core. Konkrétně kód napsaný pro starší verzi rozhraní .NET Core by měl běžet plynule v novější verzi .NET Core. Mnoho vývojářů předpokládá, že nová rozhraní API nalezená v nově vydaných verzích rozhraní .NET Core by měla být také kompatibilní s předběžnými verzemi, ve kterých byla tato rozhraní API zavedena.

Tento článek popisuje kategorie změn kompatibility (nebo zásadní změny) a způsob, jakým tým .NET vyhodnocuje změny v každé z těchto kategorií. Porozumění způsobu, jakým tým .NET přistupuje k možným nepřípadným změnám, je zvláště užitečné pro vývojáře, kteří otevřou žádosti o přijetí změn v úložišti GitHubu [a modulu runtime](https://github.com/dotnet/runtime) , které upravují chování existujících rozhraní API.

> [!NOTE]
> Definici kategorií kompatibility, jako je binární kompatibilita a zpětná kompatibilita, najdete v tématu [přerušující kategorie změn](categories.md).

Následující části popisují kategorie změn provedených v rozhraních API .NET Core a jejich dopad na kompatibilitu aplikací. Ikona ✔️ označuje, že je povolen určitý druh změny, ❌ indikuje, že není povolený, a ❓ indikuje změnu, která může nebo nemusí být povolená. Změny v této poslední kategorii vyžadují posouzení a vyhodnocení toho, jak by bylo předchozí chování předvídatelné, zjevné a konzistentní.

> [!NOTE]
> Kromě toho, že slouží jako vodítko, jak jsou vyhodnocovány změny knihoven .NET Core, mohou vývojáři knihovny použít také k vyhodnocení změn ve svých knihovnách, které cílí na více implementací a verzí rozhraní .NET.

## <a name="modifications-to-the-public-contract"></a>Úpravy veřejné smlouvy

Změny v této kategorii upravují oblast veřejného povrchu typu. Většina změn v této kategorii není povolená, protože narušují *zpětnou kompatibilitu* (schopnost aplikace, která byla vyvinutá pomocí předchozí verze rozhraní API, aby se spustila bez překompilace na novější verzi).

### <a name="types"></a>Typy

- **✔️ odebrání implementace rozhraní z typu, když je rozhraní už implementované základním typem.**

- **❓ Přidání nové implementace rozhraní do typu**

  Jedná se o přijatelnou změnu, protože nepříznivě neovlivní stávající klienty. Všechny změny typu musí fungovat v rámci hranic přijatelných změn, které jsou zde definovány, aby nová implementace zůstala přijatelná. Při přidávání rozhraní, která přímo ovlivňují schopnost návrháře nebo serializátoru vytvořit kód nebo data, která nelze spotřebovat na nižší úroveň, je nezbytné extrémní opatrnost. Příkladem je <xref:System.Runtime.Serialization.ISerializable> rozhraní.

- **❓ Představení nové základní třídy**

  Typ lze začlenit do hierarchie mezi dvěma existujícími typy, pokud nezavádí žádné nové [abstraktní](../../csharp/language-reference/keywords/abstract.md) členy nebo nemění sémantiku nebo chování stávajících typů. Například v .NET Framework 2,0 se <xref:System.Data.Common.DbConnection> třída stala novou základní třídou pro <xref:System.Data.SqlClient.SqlConnection>, která byla dříve odvozena přímo od <xref:System.ComponentModel.Component>.

- **✔️ Přesunutí typu z jednoho sestavení na jiný**

  Všimněte si, že *staré* sestavení musí být označeno <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>, které odkazuje na nové sestavení.

- **✔️ Změna typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `readonly struct`**

  Všimněte si, že změna typu `readonly struct` na typ `struct` není povolená.

- **✔️ přidání klíčového slova [sealed](../../csharp/language-reference/keywords/sealed.md) nebo [abstract](../../csharp/language-reference/keywords/abstract.md) do typu, *Pokud nejsou k dispozici žádné (* veřejné nebo chráněné) konstruktory**

- **✔️ rozšíření viditelnosti typu**

- **❌ Změna oboru názvů nebo názvu typu**

- **❌ přejmenování nebo odebrání veřejného typu**

   Tím dojde k zalomení veškerého kódu, který používá přejmenovaný nebo odebraný typ.

- **❌ Změna základního typu výčtu**

   Toto je zásadní změna v době kompilace a chování a také binární zásadní změna, která může nastavit argumenty atributu jako neanalyzovatelné.

- **❌ zapečetění typu, který se dřív nezapečetěný**

- **❌ přidání rozhraní do sady základních typů rozhraní**

   Pokud rozhraní implementuje rozhraní, které dříve neimplementovalo, všechny typy, které implementují původní verzi rozhraní, jsou přerušeny.

- **❓ Odebrání třídy ze sady základních tříd nebo z rozhraní ze sady implementovaných rozhraní**

  Pravidlo pro odebrání rozhraní obsahuje jednu výjimku: můžete přidat implementaci rozhraní, které je odvozeno z odebraného rozhraní. Můžete například odebrat <xref:System.IDisposable>, pokud typ nebo rozhraní nyní implementuje <xref:System.ComponentModel.IComponent>, které implementuje <xref:System.IDisposable>.

- **❌ Změna typu `readonly struct` na typ [struktury](../../csharp/language-reference/keywords/struct.md)**

  Všimněte si, že změna typu `struct` na typ `readonly struct` je povolena.

- **❌ Změna typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `ref struct` a naopak**

- **❌ snížení viditelnosti typu**

   Nicméně zvýšení viditelnosti typu je povoleno.

### <a name="members"></a>Členové

- **✔️ rozšíření viditelnosti členu, který není [virtuální](../../csharp/language-reference/keywords/sealed.md)**

- **✔️ Přidání abstraktního člena k veřejnému typu, který nemá žádné *přístupné* (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěný](../../csharp/language-reference/keywords/sealed.md)**

  Nicméně přidání abstraktního člena do typu, který má přístupné (veřejné nebo chráněné) konstruktory a není `sealed` není povoleno.

- **✔️ omezit viditelnost [chráněného](../../csharp/language-reference/keywords/protected.md) člena, když typ nemá žádné přístupné (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěný](../../csharp/language-reference/keywords/sealed.md) .**

- **✔️ přesunu člena do třídy vyšší v hierarchii, než je typ, ze kterého byl odebrán**

- **✔️ Přidání nebo odebrání přepsání**

  Všimněte si, že zavedení přepsání může způsobit, že předchozí příjemci přeskočí přepsání při volání [základny](../../csharp/language-reference/keywords/base.md).

- **✔️ Přidání konstruktoru do třídy spolu s konstruktorem bez parametrů, pokud třída předtím neměla žádné konstruktory**

   Nicméně přidání konstruktoru do třídy, která dříve neměla žádné konstruktory bez přidání konstruktoru *bez* parametrů, není povoleno.

- **✔️ Změna členu z [abstract](../../csharp/language-reference/keywords/abstract.md) na [Virtual](../../csharp/language-reference/keywords/virtual.md)**

- **✔️ Změna hodnoty z `ref readonly` na `ref` návratovou hodnotu (s výjimkou virtuálních metod nebo rozhraní)**

- **✔️ odstranění [jen pro čtení](../../csharp/language-reference/keywords/readonly.md) z pole, pokud statický typ pole není proměnlivý typ hodnoty.**

- **✔️ volání nové události, která nebyla dříve definovaná.**

- **❓ Přidání nového pole instance do typu**

   Tato změna ovlivňuje serializaci.

- **❌ přejmenování nebo odebrání veřejného členu nebo parametru**

   Tím dojde k rozdělení veškerého kódu, který používá přejmenovaný nebo odebraný člen nebo parametr.

   Všimněte si, že to zahrnuje odebrání nebo přejmenování metody getter nebo setter z vlastnosti a také přejmenování nebo odebrání členů výčtu.

- **❌ přidání člena do rozhraní**

- **❌ Změna hodnoty veřejné konstanty nebo člena výčtu**

- **❌ Změna typu vlastnosti, pole, parametru nebo návratové hodnoty**

- **❌ přidání, odebrání nebo změna pořadí parametrů**

- **❌ přidání nebo odebrání klíčového slova [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) nebo [ref](../../csharp/language-reference/keywords/ref.md) z parametru**

- **❌ Přejmenování parametru (včetně změny jeho velikosti)**

  To se považuje za porušení dvou důvodů:

  - Dojde k přerušení scénářů s pozdní vazbou, jako je funkce pozdní vazby [](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) v Visual Basic C#a dynamické v.

  - Pokud vývojáři používají [pojmenované argumenty](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments), dojde k přerušení [kompatibility zdrojů](categories.md#source-compatibility) .

- **❌ změna ze `ref` návratové hodnoty na `ref readonly` návratovou hodnotu**

- **❌️ změna z `ref readonly` na `ref` návratovou hodnotu ve virtuální metodě nebo rozhraní.**

- **❌ přidávání nebo odebírání [abstraktu](../../csharp/language-reference/keywords/abstract.md) ze člena**

- **❌ odebrání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) ze člena**

  I když se často nejedná o zásadní změnu, C# protože kompilátor chce vygenerovat instrukce [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) pro volání nevirtuálních metod (`callvirt` provádí kontrolu null, zatímco normální volání ne), toto chování není pro několik důvodů neproměnné:
  - C#není jediným jazykem, který cílí na .NET.

  - C# Kompilátor stále častěji snaží optimalizovat `callvirt` na normální volání, kdykoli je cílová metoda nevirtuální a pravděpodobně není null (například metoda, ke které se přistupoval prostřednictvím [operátoru rozšíření?. null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).

  Vytvořením metody Virtual by kód příjemce často ukončil volání, které není prakticky.

- **❌ přidání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) do člena**

- **❌ vytvoření abstrakce virtuálního členu**

  [Virtuální člen](../../csharp/language-reference/keywords/virtual.md) poskytuje implementaci metody, kterou *lze* přepsat odvozenou třídou. [Abstraktní člen](../../csharp/language-reference/keywords/abstract.md) neposkytuje žádnou implementaci a *musí být* přepsán.

- **❌ přidání abstraktního člena k veřejnému typu, který má přístupné (veřejné nebo chráněné) konstruktory, které nejsou [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**

- **❌ přidání nebo odebrání klíčového slova [static](../../csharp/language-reference/keywords/static.md) ze člena**

- **❌ přidání přetížení, které vylučuje existující přetížení a definuje jiné chování**

  Tím dojde k přerušení stávajících klientů vázaných na předchozí přetížení. Například pokud má třída jedinou verzi metody, která přijímá <xref:System.UInt32>, existující příjemce se úspěšně připojí k tomuto přetížení při předávání hodnoty <xref:System.Int32>. Nicméně pokud přidáte přetížení, které přijímá <xref:System.Int32>, při rekompilování nebo použití pozdní vazby nyní kompilátor vytvoří vazbu k novému přetížení. Pokud dojde k různým výsledkům chování, jedná se o zásadní změnu.

- **❌ přidání konstruktoru do třídy, která dříve neměla žádný konstruktor bez přidání konstruktoru bez parametrů**

- **❌️ přidání [ReadOnly](../../csharp/language-reference/keywords/readonly.md) do pole**

- **❌ snížení viditelnosti člena**

   To zahrnuje snížení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, pokud jsou *přístupné* (veřejné nebo chráněné) konstruktory a *typ není* [zapečetěný](../../csharp/language-reference/keywords/sealed.md). V takovém případě se omezení viditelnosti chráněného člena povoluje.

   Všimněte si, že zvýšení viditelnosti člena je povoleno.

- **❌ Změna typu člena**

   Vrácenou hodnotu metody nebo typu pole nelze změnit. Například podpis metody, která vrací <xref:System.Object>, nelze změnit tak, aby vracela <xref:System.String>, nebo naopak.

- **❌ přidání pole do struktury, která dřív neměla žádný stav**

  Pravidla pro jednoznačné přiřazení umožňují použití neinicializovaných proměnných, pokud typ proměnné je Bezstavová struktura. Pokud je struktura nastavená jako stavová, může kód končit neinicializovanými daty. To může být i poškození zdroje a binární změna.

- **❌ vypálení existující události, když nebyla nikdy aktivována**

## <a name="behavioral-changes"></a>Změny chování

### <a name="assemblies"></a>Sestavení

- **✔️ přenos sestavení v případě, že jsou stejné platformy stále podporovány**

- **❌ Změna názvu sestavení**
- **❌ změna veřejného klíče sestavení**

### <a name="properties-fields-parameters-and-return-values"></a>Vlastnosti, pole, parametry a návratové hodnoty

- **✔️ Změna hodnoty vlastnosti, pole, návratové hodnoty nebo parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na více odvozený typ**

  Například metoda, která vrací typ <xref:System.Object> může vracet instanci <xref:System.String>. (Signatura metody se ale nemůže změnit.)

- **✔️ zvýšení rozsahu přijatelných hodnot pro vlastnost nebo parametr, pokud člen není [virtuální](../../csharp/language-reference/keywords/virtual.md) .**

  Všimněte si, že zatímco rozsah hodnot, které lze předat metodě nebo které mohou být vráceny členem, lze rozšířit, parametr nebo typ člena nemůže. Například zatímco hodnoty předané metodě lze rozšířit z 0-124 na 0-255, typ parametru nemůže být změněn z <xref:System.Byte> na <xref:System.Int32>.

- **❌ zvýšení rozsahu přijatelných hodnot pro vlastnost nebo parametr, pokud je člen [virtuální](../../csharp/language-reference/keywords/virtual.md)**

   Tato změna rozdělí existující přepsané členy, které nebudou správně fungovat pro rozšířený rozsah hodnot.

- **❌ snížení rozsahu přijatelných hodnot pro vlastnost nebo parametr**

- **❌ zvýšení rozsahu vrácených hodnot pro vlastnost, pole, návratovou hodnotu nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**

- **❌ změnu vrácených hodnot pro vlastnost, pole, návratovou hodnotu metody nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**

- **❌ Změna výchozí hodnoty vlastnosti, pole nebo parametru**

- **❌ měnící přesnost číselné návratové hodnoty**

- **❓ Změnu v analýze vstupu a vyvolání nových výjimek (i v případě, že se v dokumentaci nezadá chování při analýze)**

### <a name="exceptions"></a>Výjimky

- **✔️ vyvolání více odvozené výjimky, než je stávající výjimka**

  Vzhledem k tomu, že nová výjimka je podtřídou existující výjimky, pokračuje zpracování předchozí kódu zpracováním výjimky. Například v .NET Framework 4 začaly metody vytváření a načítání jazykové verze vyvolávat <xref:System.Globalization.CultureNotFoundException> namísto <xref:System.ArgumentException>, pokud nebyla nalezena jazyková verze. Vzhledem k tomu, že <xref:System.Globalization.CultureNotFoundException> jsou odvozeny z <xref:System.ArgumentException>, jedná se o přijatelnou změnu.

- **✔️ vyvolává konkrétnější výjimku než <xref:System.NotSupportedException>, <xref:System.NotImplementedException><xref:System.NullReferenceException>**

- **✔️a se vyvolala výjimka, která je považována za neodstranitelnou.**

  Neodstranitelné výjimky by neměly být zachyceny, ale místo toho by měly být zpracovány pomocí obslužné rutiny catch na vysoké úrovni. Proto se neočekává, že uživatelé budou mít kód, který tyto explicitní výjimky zachytí. Neobnovitelné výjimky jsou:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **✔️ vyvolání nové výjimky v nové cestě kódu**

  Výjimka se musí vztahovat pouze k nové cestě kódu, která je spuštěna s novými hodnotami parametrů nebo stavem, a nelze ji spustit pomocí stávajícího kódu, který cílí na předchozí verzi.

- **✔️ odebrání výjimky pro zajištění robustnějšího chování nebo nových scénářů**

  Například `Divide` metoda, která dříve zpracovala pouze kladné hodnoty a vyvolala <xref:System.ArgumentOutOfRangeException> jinak může být změněna tak, aby podporovala záporné i kladné hodnoty bez vyvolání výjimky.

- **✔️ Změna textu chybové zprávy**

  Vývojáři by neměli spoléhat na text chybových zpráv, které se také mění v závislosti na jazykové verzi uživatele.

- **❌ vyvolání výjimky v jakémkoli jiném případě, který není uveden výše.**

- **❌ odebrání výjimky v jakémkoli jiném případě, který není uvedený výše**

### <a name="attributes"></a>Atributy

- **✔️ Změna hodnoty atributu, který *není pozorovatelný***

- **❌ Změna hodnoty atributu, který *je* pozorovatelný**

- **❓ Odebrání atributu**

  Ve většině případů je odebrání atributu (například <xref:System.NonSerializedAttribute>) zásadní změnou.

## <a name="platform-support"></a>Podpora platformy

- **✔️ podporující operaci na platformě, která nebyla dřív podporovaná**

- **❌ nepodporují nebo ještě nevyžadují konkrétní aktualizaci Service Pack pro operaci, která byla dřív podporovaná na platformě.**

## <a name="internal-implementation-changes"></a>Změny interní implementace

- **❓ Změna oblasti povrchu interního typu**

   Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz. V některých případech, kde jsou oblíbené knihovny třetích stran nebo velký počet vývojářů závislé na interních rozhraních API, nemusí být tyto změny povolené.

- **❓ Změna interní implementace člena**

  Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz. V některých případech, kde kód zákazníka často závisí na soukromé reflexi nebo kde změna zavádí nezamýšlené vedlejší účinky, nemusí být tyto změny povoleny.

- **✔️ zlepšení výkonu operace**

   Možnost upravit výkon operace je zásadní, ale tyto změny mohou přerušit kód, který spoléhá na aktuální rychlost operace. To platí zejména pro kód, který závisí na časování asynchronních operací. Všimněte si, že změna výkonu by neměla mít žádný vliv na jiné chování rozhraní API. v opačném případě bude změna zálomena.

- **✔️ nepřímo (a často nepříznivě) měnit výkon operace.**

  Pokud se změna nedělí z nějakého jiného důvodu jako porušení, je to přijatelné. Často je potřeba provést akce, které mohou zahrnovat dodatečné operace nebo které přidávají nové funkce. To bude téměř vždy mít vliv na výkon, ale může být nezbytné, aby rozhraní API fungovalo podle očekávání.

- **❌ změna synchronního rozhraní API na asynchronní (a naopak)**

## <a name="code-changes"></a>Změny kódu

- **✔️ Přidání [parametrů](../../csharp/language-reference/keywords/params.md) do parametru**

- **❌ změnu [struktury](../../csharp/language-reference/keywords/struct.md) na [třídu](../../csharp/language-reference/keywords/class.md) a naopak**

- **❌ přidání klíčového slova [checked](../../csharp/language-reference/keywords/virtual.md) do bloku kódu**

   Tato změna může způsobit, že kód, který dřív provedl k vyvolání <xref:System.OverflowException> a je nepřijatelný.

- **❌ odebírání [parametrů](../../csharp/language-reference/keywords/params.md) z parametru**

- **❌ Změna pořadí, ve kterém jsou události aktivovány**

  Vývojáři mohou rozumně očekávat, že události budou aktivovány ve stejném pořadí a kód pro vývojáře často závisí na pořadí, ve kterém jsou události vyvolány.

- **❌ odebrání vyvolání události na dané akci**

- **❌ změnu počtu volání daných událostí**

- **❌ přidání <xref:System.FlagsAttribute> do výčtového typu**
