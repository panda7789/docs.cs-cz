---
title: Typy přerušujících změn
description: Přečtěte si, jak se .NET Core pokusí zachovat kompatibilitu pro vývojáře napříč verzemi .NET a jaký druh změny se považuje za zásadní změnu.
ms.date: 06/10/2019
ms.openlocfilehash: bc93316141ae99d8cfedc5e6d88a9e91216f9c6e
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415742"
---
# <a name="changes-that-affect-compatibility"></a>Změny ovlivňující kompatibilitu

V průběhu své historie se .NET pokusilo udržet vysokou úroveň kompatibility z verze na verzi a v různých charakterech rozhraní .NET. To platí i pro .NET Core. I když .NET Core se dá považovat za novou technologii, která je nezávislá na .NET Framework, dva hlavní faktory omezují schopnost .NET Core odchýlit se od .NET Framework:

- Velký počet vývojářů byl buď původně vyvinutý, nebo pokračoval v vývoji .NET Frameworkch aplikací. Očekávají konzistentní chování napříč implementacemi rozhraní .NET.

- Projekty knihovny .NET Standard umožňují vývojářům vytvářet knihovny, které cílí na společná rozhraní API sdílená pomocí .NET Core a .NET Framework. Vývojáři očekávají, že se knihovna používaná v aplikaci .NET Core musí chovat stejně jako stejná knihovna, jakou používá aplikace .NET Framework.

Společně s kompatibilitou mezi implementacemi .NET očekávají vývojáři vysokou úroveň kompatibility napříč verzemi .NET Core. Konkrétně kód napsaný pro starší verzi rozhraní .NET Core by měl běžet plynule v novější verzi .NET Core. Mnoho vývojářů předpokládá, že nová rozhraní API nalezená v nově vydaných verzích rozhraní .NET Core by měla být také kompatibilní s předběžnými verzemi, ve kterých byla tato rozhraní API zavedena.

Tento článek popisuje změny ovlivňující kompatibilitu a způsob, jakým tým .NET vyhodnocuje každý typ změny. Porozumění způsobu, jakým tým .NET získává možné nepotřebné změny, jsou zvláště užitečné pro vývojáře, kteří otevřou žádosti o přijetí změn, které mění chování [existujících rozhraní API .NET](https://github.com/dotnet/runtime).

Následující části popisují kategorie změn provedených v rozhraních API .NET Core a jejich dopad na kompatibilitu aplikací. Změny jsou buď povolené ✔️, Nepovoleno ❌ nebo vyžadovat rozhodnutí a vyhodnocení toho, jak bylo předchozí chování ❓ předvídatelné, zjevné a konzistentní.

> [!NOTE]
>
> - Kromě toho, že slouží jako vodítko k tomu, jak jsou vyhodnocovány změny knihoven .NET, mohou vývojáři knihovny použít také k vyhodnocení změn ve svých knihovnách, které cílí na více implementací a verzí rozhraní .NET.
> - Informace o kategoriích kompatibility, například o dopředné a zpětné kompatibilitě, najdete v tématu [Kompatibilita](categories.md).

## <a name="modifications-to-the-public-contract"></a>Úpravy veřejné smlouvy

Změny v této kategorii upravují oblast veřejného povrchu typu. Většina změn v této kategorii není povolená, protože narušují *zpětnou kompatibilitu* (schopnost aplikace, která byla vyvinutá pomocí předchozí verze rozhraní API, aby se spustila bez překompilace na novější verzi).

### <a name="types"></a>Typy

- ✔️ **povoleno: odebrání implementace rozhraní z typu, když je rozhraní již implementováno pomocí základního typu**

- ❓ **Vyžaduje rozhodnutí: Přidání nové implementace rozhraní do typu**

  Jedná se o přijatelnou změnu, protože nepříznivě neovlivní stávající klienty. Všechny změny typu musí fungovat v rámci hranic přijatelných změn, které jsou zde definovány, aby nová implementace zůstala přijatelná. Při přidávání rozhraní, která přímo ovlivňují schopnost návrháře nebo serializátoru vytvořit kód nebo data, která nelze spotřebovat na nižší úroveň, je nezbytné extrémní opatrnost. Příkladem je <xref:System.Runtime.Serialization.ISerializable> rozhraní.

- ❓ **Vyžaduje rozhodnutí: Představujeme novou základní třídu.**

  Typ lze začlenit do hierarchie mezi dvěma existujícími typy, pokud nezavádí žádné nové [abstraktní](../../csharp/language-reference/keywords/abstract.md) členy nebo nemění sémantiku nebo chování stávajících typů. Například v .NET Framework 2,0 se <xref:System.Data.Common.DbConnection> Třída stala novou základní třídou pro <xref:System.Data.SqlClient.SqlConnection> , která byla dříve odvozena přímo z <xref:System.ComponentModel.Component> .

- ✔️ **povoleno: přesunutí typu z jednoho sestavení do druhého**

  *Původní* sestavení musí být označeno s <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> bodem, který odkazuje na nové sestavení.

- ✔️ **povoleno: Změna typu [struktury](../../csharp/language-reference/builtin-types/struct.md) na `readonly struct` typ**

  Změna `readonly struct` typu na `struct` typ není povolená.

- ✔️ **povoleno: přidání [zapečetěného](../../csharp/language-reference/keywords/sealed.md) nebo [abstraktního](../../csharp/language-reference/keywords/abstract.md) klíčového slova do typu, pokud nejsou k *dispozici* žádné (veřejné nebo chráněné) konstruktory**

- ✔️ **povoleno: rozšíření viditelnosti typu**

- ❌**Nepovoleno: Změna oboru názvů nebo názvu typu**

- ❌**Nepovoleno: přejmenování nebo odebrání veřejného typu**

   Tím dojde k zalomení veškerého kódu, který používá přejmenovaný nebo odebraný typ.

- ❌**Nepovoleno: Změna základního typu výčtu**

   Toto je zásadní změna v době kompilace a chování a také binární zásadní změna, která může nastavit argumenty atributu jako neanalyzovatelné.

- ❌**Nepovoleno: uzavření typu, který byl dříve nezapečetěný**

- ❌**Nepovoleno: Přidání rozhraní do sady základních typů rozhraní**

   Pokud rozhraní implementuje rozhraní, které dříve neimplementovalo, všechny typy, které implementují původní verzi rozhraní, jsou přerušeny.

- ❓ **Vyžaduje rozhodnutí: odebrání třídy ze sady základních tříd nebo rozhraní ze sady implementovaných rozhraní.**

  Pravidlo pro odebrání rozhraní obsahuje jednu výjimku: můžete přidat implementaci rozhraní, které je odvozeno z odebraného rozhraní. Například můžete odebrat, <xref:System.IDisposable> Pokud typ nebo rozhraní nyní implementuje <xref:System.ComponentModel.IComponent> , které implementuje <xref:System.IDisposable> .

- ❌**Nepovoleno: Změna `readonly struct` typu na typ [struktury](../../csharp/language-reference/builtin-types/struct.md) **

  Změna `struct` typu na `readonly struct` typ je povolena, ale.

- ❌**Zakázáno: Změna typu [struktury](../../csharp/language-reference/builtin-types/struct.md) na `ref struct` typ a naopak**

- ❌**Nepovoleno: zmenšení viditelnosti typu**

   Nicméně zvýšení viditelnosti typu je povoleno.

### <a name="members"></a>Členové

- ✔️ **povoleno: rozšíření viditelnosti člena, který není [virtuální](../../csharp/language-reference/keywords/sealed.md) **

- ✔️ **povoleno: Přidání abstraktního člena do veřejného typu, který nemá žádné *přístupné* (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěn](../../csharp/language-reference/keywords/sealed.md) **

  Nicméně přidání abstraktního člena do typu, který má přístupné (veřejné nebo chráněné) konstruktory a není `sealed` povoleno.

- ✔️ **povoleno: omezení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, když typ nemá žádné přístupné (veřejné nebo chráněné) konstruktory nebo je typ [zapečetěn](../../csharp/language-reference/keywords/sealed.md) **

- ✔️ **povoleno: přesun člena do třídy vyšší v hierarchii, než je typ, ze kterého byl odebrán**

- ✔️ **povoleno: Přidání nebo odebrání přepsání**

  Představení přepsání může způsobit, že předchozí příjemci přeskočí přepsání při volání [základny](../../csharp/language-reference/keywords/base.md).

- ✔️ **povoleno: Přidání konstruktoru do třídy spolu s konstruktorem bez parametrů, pokud třída předtím neměla žádné konstruktory**

   Nicméně přidání konstruktoru do třídy, která dříve neměla žádné konstruktory bez přidání konstruktoru *bez* parametrů, není povoleno.

- ✔️ **povoleno: Změna člena z [abstract](../../csharp/language-reference/keywords/abstract.md) na [Virtual](../../csharp/language-reference/keywords/virtual.md) **

- ✔️ **povoleno: Změna z `ref readonly` na `ref` návratovou hodnotu (s výjimkou virtuálních metod nebo rozhraní)**

- ✔️ **povoleno: odebrání [jen pro čtení](../../csharp/language-reference/keywords/readonly.md) z pole, pokud statický typ pole není proměnlivý typ hodnoty**

- ✔️ **povoleno: volání nové události, která nebyla dříve definována.**

- ❓ **Vyžaduje rozhodnutí: Přidání nového pole instance do typu**

   Tato změna ovlivňuje serializaci.

- ❌**Nepovoleno: přejmenování nebo odebrání veřejného členu nebo parametru**

   Tím dojde k rozdělení veškerého kódu, který používá přejmenovaný nebo odebraný člen nebo parametr.

   To zahrnuje odebrání nebo přejmenování metody getter nebo setter z vlastnosti a také přejmenování nebo odebrání členů výčtu.

- ❌**Nepovoleno: Přidání člena do rozhraní**

- ❌**Nepovoleno: Změna hodnoty veřejné konstanty nebo člena výčtu**

- ❌**Nepovoleno: Změna typu vlastnosti, pole, parametru nebo návratové hodnoty**

- ❌**Nepovoleno: Přidání, odebrání nebo změna pořadí parametrů**

- ❌**Nepovoleno: Přidání nebo odebrání klíčového slova [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) nebo [ref](../../csharp/language-reference/keywords/ref.md) z parametru**

- ❌**Nepovoleno: Přejmenování parametru (včetně změny jeho velikosti)**

  To se považuje za porušení dvou důvodů:

  - Dojde k přerušení scénářů s pozdní vazbou, jako je funkce pozdní vazby v Visual Basic a [Dynamická](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) v jazyce C#.

  - Pokud vývojáři používají [pojmenované argumenty](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments), dojde k přerušení [kompatibility zdrojů](categories.md#source-compatibility) .

- ❌**Nepovoleno: Změna `ref` návratové hodnoty na `ref readonly` návratovou hodnotu**

- ❌️**Nepovoleno: Změna z na `ref readonly` `ref` návratovou hodnotu u virtuální metody nebo rozhraní**

- ❌**Nepovoleno: Přidání nebo odebrání [abstraktního](../../csharp/language-reference/keywords/abstract.md) ze člena**

- ❌**Nepovoleno: odebrání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) ze člena**

  I když se tato často nejedná o zásadní změnu, protože kompilátor jazyka C# chce [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) volat nevirtuální metody pro volání nevirtuálních metod ( `callvirt` provede kontrolu null, zatímco normální volání ne), toto chování není pro několik důvodů neproměnné:
  - Jazyk C# není jediným jazykem, který cílí na .NET.

  - Kompilátor jazyka C# se stále častěji snaží optimalizovat `callvirt` na normální volání, kdykoli je cílová metoda nevirtuální a pravděpodobně není null (například metoda, kterou lze použít prostřednictvím [operátoru šíření?. null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).

  Vytvořením metody Virtual by kód příjemce často ukončil volání, které není prakticky.

- ❌**Nepovoleno: přidání klíčového slova [Virtual](../../csharp/language-reference/keywords/virtual.md) do člena**

- ❌**Nepovoleno: vytváření abstraktních virtuálních členů**

  [Virtuální člen](../../csharp/language-reference/keywords/virtual.md) poskytuje implementaci metody, kterou *lze* přepsat odvozenou třídou. [Abstraktní člen](../../csharp/language-reference/keywords/abstract.md) neposkytuje žádnou implementaci a *musí být* přepsán.

- ❌**Nepovoleno: Přidání abstraktního člena k veřejnému typu, který má přístupné (veřejné nebo chráněné) konstruktory, které nejsou [zapečetěné](../../csharp/language-reference/keywords/sealed.md) **

- ❌**Nepovoleno: Přidání nebo odebrání klíčového slova [static](../../csharp/language-reference/keywords/static.md) ze člena**

- ❌**Nepovoleno: Přidání přetížení, které vylučuje existující přetížení a definuje jiné chování**

  Tím dojde k přerušení stávajících klientů vázaných na předchozí přetížení. Například pokud má třída jedinou verzi metody, která přijímá <xref:System.UInt32> , existující příjemce se úspěšně připojí k tomuto přetížení při předání <xref:System.Int32> hodnoty. Nicméně pokud přidáte přetížení, které přijímá <xref:System.Int32> , při opětovném kompilování nebo použití pozdní vazby, kompilátor nyní váže k novému přetížení. Pokud dojde k různým výsledkům chování, jedná se o zásadní změnu.

- ❌**Nepovoleno: Přidání konstruktoru do třídy, která dříve neměla žádný konstruktor bez přidání konstruktoru bez parametrů**

- ❌️**Nepovoleno: přidání [ReadOnly](../../csharp/language-reference/keywords/readonly.md) do pole**

- ❌**Nepovoleno: zmenšení viditelnosti člena**

   To zahrnuje snížení viditelnosti [chráněného](../../csharp/language-reference/keywords/protected.md) člena, pokud jsou *přístupné* `public` `protected` konstruktory (nebo) a typ *není* [zapečetěn](../../csharp/language-reference/keywords/sealed.md). V takovém případě se omezení viditelnosti chráněného člena povoluje.

   Zvýšení viditelnosti člena je povoleno.

- ❌**Nepovoleno: Změna typu člena**

   Vrácenou hodnotu metody nebo typu pole nelze změnit. Například signatura metody, která vrací hodnotu <xref:System.Object> , nemůže být změněna, aby vracela <xref:System.String> , nebo naopak.

- ❌**Nepovoleno: Přidání pole do struktury, která dřív neměla žádný stav**

  Pravidla pro jednoznačné přiřazení umožňují použití neinicializovaných proměnných, pokud typ proměnné je Bezstavová struktura. Pokud je struktura nastavená jako stavová, může kód končit neinicializovanými daty. To může být i poškození zdroje a binární změna.

- ❌**Nepovoleno: vyvolává se existující událost, pokud nebyla nikdy aktivována.**

## <a name="behavioral-changes"></a>Změny chování

### <a name="assemblies"></a>Sestavení

- ✔️ **povoleno: sestavení přenositelného přenosného, pokud jsou stejné platformy stále podporovány**

- ❌**Nepovoleno: Změna názvu sestavení**
- ❌**Nepovoleno: Změna veřejného klíče sestavení**

### <a name="properties-fields-parameters-and-return-values"></a>Vlastnosti, pole, parametry a návratové hodnoty

- ✔️ **povoleno: Změna hodnoty vlastnosti, pole, návratové hodnoty nebo parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na více odvozený typ**

  Například metoda, která vrací typ, <xref:System.Object> může vracet <xref:System.String> instanci. (Signatura metody se ale nemůže změnit.)

- ✔️ **povoleno: zvýšení rozsahu přípustných hodnot pro vlastnost nebo parametr, pokud člen není [virtuální](../../csharp/language-reference/keywords/virtual.md) ** .

  I když rozsah hodnot, které lze předat metodě nebo které mohou být vráceny členem, lze rozšířit, parametr nebo typ člena nemůže. Například zatímco hodnoty předané metodě lze rozšířit z 0-124 na 0-255, typ parametru nemůže být změněn z <xref:System.Byte> na <xref:System.Int32> .

- ❌**Nepovoleno: zvýšení rozsahu přípustných hodnot pro vlastnost nebo parametr, pokud je člen [virtuální](../../csharp/language-reference/keywords/virtual.md) **

   Tato změna rozdělí existující přepsané členy, které nebudou správně fungovat pro rozšířený rozsah hodnot.

- ❌**Nepovoleno: zmenšení rozsahu přípustných hodnot pro vlastnost nebo parametr**

- ❌**Nepovoleno: zvýšení rozsahu vrácených hodnot pro vlastnost, pole, návratovou hodnotu nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**

- ❌**Nepovoleno: Změna vrácených hodnot pro vlastnost, pole, návratovou hodnotu metody nebo [výstupní](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**

- ❌**Nepovoleno: Změna výchozí hodnoty vlastnosti, pole nebo parametru**

- ❌**Nepovoleno: Změna přesnosti číselné návratové hodnoty**

- ❓ **Vyžaduje rozhodnutí: Změna v analýze vstupu a vyvolání nových výjimek (i v případě, že se v dokumentaci nezadá chování při analýze).**

### <a name="exceptions"></a>Výjimky

- ✔️ **povoleno: vyvolání více odvozené výjimky, než je stávající výjimka**

  Vzhledem k tomu, že nová výjimka je podtřídou existující výjimky, pokračuje zpracování předchozí kódu zpracováním výjimky. Například v .NET Framework 4, metody vytváření a načítání jazykové verze začaly vyvolat namísto, <xref:System.Globalization.CultureNotFoundException> <xref:System.ArgumentException> Pokud nebyla nalezena jazyková verze. Vzhledem <xref:System.Globalization.CultureNotFoundException> <xref:System.ArgumentException> k tomu, že je odvozen z, jedná se o přijatelnou změnu.

- ✔️ **povoleno: byla aktivována konkrétnější výjimka než <xref:System.NotSupportedException> , <xref:System.NotImplementedException> , <xref:System.NullReferenceException> **

- ✔️ **povoleno: probíhá vyvolání výjimky, která je považována za neodstranitelnou.**

  Neodstranitelné výjimky by neměly být zachyceny, ale místo toho by měly být zpracovány pomocí obslužné rutiny catch na vysoké úrovni. Proto se neočekává, že uživatelé budou mít kód, který tyto explicitní výjimky zachytí. Neobnovitelné výjimky jsou:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- ✔️ **povoleno: probíhá vyvolání nové výjimky v nové cestě kódu.**

  Výjimka se musí vztahovat jenom k nové cestě kódu, která se spustí s novými hodnotami parametrů nebo stavem a kterou nejde spustit pomocí stávajícího kódu, který cílí na předchozí verzi.

- ✔️ **povoleno: odebrání výjimky pro povolení robustnějšího chování nebo nových scénářů**

  Například `Divide` metoda, která dříve zpracovala pouze kladné hodnoty a vyvolala <xref:System.ArgumentOutOfRangeException> jinak, může být změněna tak, aby podporovala záporné i kladné hodnoty bez vyvolání výjimky.

- ✔️ **povoleno: Změna textu chybové zprávy**

  Vývojáři by neměli spoléhat na text chybových zpráv, které se také mění v závislosti na jazykové verzi uživatele.

- ❌**Nepovoleno: vyvolává se výjimka v jakémkoli jiném případě, který není uveden výše.**

- ❌**Nepovoleno: odebrání výjimky v jiném případě, než je uvedeno výše**

### <a name="attributes"></a>Atributy

- ✔️ **povoleno: Změna hodnoty atributu, který není *možné* pozorovat**

- ❌**Nepovoleno: Změna hodnoty atributu, který *je* možné pozorovatelit**

- ❓ **Vyžaduje rozhodnutí: odebrání atributu**

  Ve většině případů je odebrání atributu (například) zásadní <xref:System.NonSerializedAttribute> změnou.

## <a name="platform-support"></a>Podpora platformy

- ✔️ **povoleno: podpora operace na platformě, která nebyla dříve podporována**

- ❌**Nepovoleno: Nepodporováno nebo nyní nevyžaduje konkrétní aktualizaci Service Pack pro operaci, která byla dříve podporovaná na platformě.**

## <a name="internal-implementation-changes"></a>Změny interní implementace

- ❓ **Vyžaduje rozhodnutí: Změna oblasti povrchu interního typu**

   Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz. V některých případech, kde jsou oblíbené knihovny třetích stran nebo velký počet vývojářů závislé na interních rozhraních API, nemusí být tyto změny povolené.

- ❓ **Vyžaduje rozhodnutí: Změna interní implementace členu.**

  Tyto změny jsou obecně povoleny, i když přeruší soukromý odraz. V některých případech, kde kód zákazníka často závisí na soukromé reflexi nebo kde změna zavádí nezamýšlené vedlejší účinky, nemusí být tyto změny povoleny.

- ✔️ **povoleno: zlepšení výkonu operace**

   Možnost upravit výkon operace je zásadní, ale tyto změny mohou přerušit kód, který spoléhá na aktuální rychlost operace. To platí zejména pro kód, který závisí na časování asynchronních operací. Změna výkonu by neměla mít žádný vliv na jiné chování rozhraní API. v opačném případě bude změna zálomena.

- ✔️ **povoleno: nepřímo (a často nepříznivě) měnit výkon operace**

  Pokud se změna nedělí z nějakého jiného důvodu jako porušení, je to přijatelné. Často je potřeba provést akce, které mohou zahrnovat dodatečné operace nebo které přidávají nové funkce. To bude téměř vždy mít vliv na výkon, ale může být nezbytné, aby rozhraní API fungovalo podle očekávání.

- ❌**Nepovoleno: Změna synchronního rozhraní API na asynchronní (a naopak)**

## <a name="code-changes"></a>Změny kódu

- ✔️ **povoleno: přidání [parametrů](../../csharp/language-reference/keywords/params.md) do parametru**

- ❌**Zakázáno: Změna [struktury](../../csharp/language-reference/builtin-types/struct.md) na [třídu](../../csharp/language-reference/keywords/class.md) a naopak**

- ❌**Nepovoleno: přidání klíčového slova [checked](../../csharp/language-reference/keywords/virtual.md) do bloku kódu**

   Tato změna může způsobit, že kód, který dřív provedl k vyvolání <xref:System.OverflowException> a, je nepřijatelný.

- ❌**Nepovoleno: odebírání [parametrů](../../csharp/language-reference/keywords/params.md) z parametru**

- ❌**Nepovoleno: Změna pořadí, ve kterém jsou události aktivovány**

  Vývojáři mohou rozumně očekávat, že události budou aktivovány ve stejném pořadí a kód pro vývojáře často závisí na pořadí, ve kterém jsou události vyvolány.

- ❌**Nepovoleno: odebrání vyvolání události v dané akci**

- ❌**Nepovoleno: Změna počtu volání daných událostí**

- ❌**Nepovoleno: přidání <xref:System.FlagsAttribute> do výčtového typu**
