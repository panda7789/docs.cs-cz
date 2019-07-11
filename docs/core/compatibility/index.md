---
title: Vyhodnotit změny způsobující chyby – .NET Core
description: Další informace o způsobech, ve kterém pokouší zachovat kompatibilitu mezi verzemi rozhraní .NET pro vývojáře v .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: c68a19b8b98a98bb9c64f5b9fa60b378935e6e93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736555"
---
# <a name="evaluate-breaking-changes-in-net-core"></a>Vyzkoušejte nejnovější změny v rozhraní .NET Core

V průběhu jeho historie se pokusil .NET udržují vysokou úroveň kompatibility z verze na verzi a mezi verzí rozhraní .NET. Tento postup se opakuje na hodnotu true pro .NET Core. I když novou technologii, která je nezávislá rozhraní .NET Framework lze považovat za .NET Core, dvou hlavních faktorech omezit schopnost .NET Core odchýlení od rozhraní .NET Framework:

- Velký počet vývojáři původně vyvinutý nebo pokračovat ve vývoji aplikací využívajících rozhraní .NET Framework. Očekávají konzistentní chování napříč implementace .NET.

- Projekty .NET standard knihovny umožňují vývojářům vytvářet knihovny, které se zaměřují společné rozhraní API, které sdílí .NET Core a .NET Framework. Vývojáři očekávat, že knihovny použít v aplikaci .NET Core by se chovají stejně jako stejnou knihovnu použít v aplikaci .NET Framework.

Vývojáři a informace o kompatibilitě mezi implementace .NET očekávat vysoké úrovně kompatibility ve verzích .NET Core. Zejména by měl kód napsaný pro starší verzi .NET Core běžely na novější verzi .NET Core. Celá řada vývojářů ve skutečnosti očekávají, že nová rozhraní API v .NET Core nově vydané verze by měl být také kompatibilní s předběžnou verzí, ve kterých byly zavedeny těchto rozhraní API.

Tento článek popisuje kategorie kompatibility změny (nebo změny způsobující chyby) a způsob, ve kterém tým .NET vyhodnotí změny v každém z těchto kategorií. Vysvětlení, jak tým .NET blíží možných nejnovějších změn je zvláště užitečné pro vývojáře, kteří jsou otevření žádosti o přijetí změn v [dotnet/corefx](https://github.com/dotnet/corefx) úložiště GitHub, které upravují chování stávajících rozhraní API.

> [!NOTE]
> Definice kategorií kompatibility, jako je například binární kompatibilitu a zpětnou kompatibilitu, naleznete v tématu [narušující změně kategorií](categories.md).

Následující části popisuje kategorie změny provedené v rozhraní API pro .NET Core a jejich dopad na kompatibilitu aplikací. Ikona ✔️ naznačuje, že konkrétní druh změn je povoleno, ❌ označuje, že je zakázané a ❓ označuje změnu, která můžou nebo nemusí být povolený. Změny v této poslední kategorii vyžadují posouzení a vyhodnocení jak předvídatelné, jasné a konzistentní předchozí chování byla.

> [!NOTE]
> Kromě slouží jako vodítko, jak vyhodnotit změny knihovny .NET Core, vývojáře knihovny můžete také tato kritéria použít k vyhodnocení, změny v jejich knihovny cílené na více verzí a implementace .NET.

## <a name="modifications-to-the-public-contract"></a>Úpravy veřejný kontrakt

Změny v této kategorii *upravit* veřejnou oblast typu. Většina změn v této kategorii nejsou povoleny, protože porušují *zpětné kompatibility* (možnost aplikace, která byla vytvořena pomocí předchozí verze rozhraní API spouštět bez nutnosti rekompilace na novější verzi).

### <a name="types"></a>Typy

- **✔️ Odebrání implementaci rozhraní z typu, pokud rozhraní je již implementováno prostřednictvím základní typ**

- **Přidání nové implementace rozhraní na typ ❓**

  To je přijatelné změnit, protože nepříznivě neovlivní stávající klienty. Všechny změny na typ musí pracovat v rámci hranic přijatelné změny, které jsou zde definovány pro novou implementaci zůstat přijatelné. Při přidávání rozhraní, které mají bezprostřední vliv na schopnost návrháře je nutné extrémně opatrní nebo spotřebovanými serializátor pro generování kódu nebo data, která nemůže být nižší úrovně. Příkladem je <xref:System.Runtime.Serialization.ISerializable> rozhraní.

- **❓ Představujeme novou základní třídu**

  Typ může být zavedeno v hierarchii mezi dva existující typy, pokud ji nemá žádné zavést nové [abstraktní](../../csharp/language-reference/keywords/abstract.md) členy nebo měnit sémantiku nebo chování existující typy. Například v rozhraní .NET Framework 2.0 <xref:System.Data.Common.DbConnection> stal nové základní třída pro třídy <xref:System.Data.SqlClient.SqlConnection>, které dříve měly odvozena přímo z <xref:System.ComponentModel.Component>.

- **✔️ Přesunutí typu z jednoho sestavení do druhého**

  Všimněte si, že *staré* sestavení musí být označeny pomocí <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> , která odkazuje na nové sestavení.

- **✔️ Změna [struktura](../../csharp/language-reference/keywords/struct.md) typ, který `readonly struct` typu**

  Všimněte si, že změna `readonly struct` typ, který `struct` typ není povolený.
  
- **✔️ Přidání [zapečetěné](../../csharp/language-reference/keywords/sealed.md) nebo [abstraktní](../../csharp/language-reference/keywords/abstract.md) – klíčové slovo do typu, pokud nejsou žádné *přístupné* konstruktory (veřejné nebo chráněné)**

- **✔️ Rozbalení viditelnosti typu**

- **❌ Změna oboru názvů nebo název typu**

- **❌ Přejmenování nebo odstranění veřejného typu**

   Tím je prolomen veškerý kód, který používá typ přejmenovaných nebo odebrané.

- **Změna základního typu výčtu ❌**

   Toto je za kompilace a chování rozbíjející změny, stejně jako binární zásadní změnu, která může být argumenty atributu nelze analyzovat.

- **Typ, který byl dříve nezapečetěné zapečetění ❌**

- **Přidání rozhraní ke sadu základních typů rozhraní ❌**

   Pokud rozhraní implementuje rozhraní, které dříve neimplementovala, všechny typy, které implementované původní verzi rozhraní jsou přerušená.

- **❓ Odebrání sady základní třídy nebo rozhraní ze sady implementovaných rozhraní třídy**

  Existuje jedna výjimka z pravidla pro odebrání rozhraní: můžete přidat implementaci rozhraní, který je odvozen z rozhraní odebrané. Například můžete odebrat <xref:System.IDisposable> Pokud tento typ nebo rozhraní nyní implementuje <xref:System.ComponentModel.IComponent>, která implementuje <xref:System.IDisposable>.

- **❌ Změna `readonly struct` typ, který [struktura](../../csharp/language-reference/keywords/struct.md) typu**

  Všimněte si, že změna `struct` typ, který `readonly struct` typ je povolený.

- **❌ Změna [struktura](../../csharp/language-reference/keywords/struct.md) typ, který `ref struct` typ a naopak**

- **❌ Snižuje viditelnost typu**

   Viditelnost typu je však povoleno.

### <a name="members"></a>Členové

- **Rozbalení viditelnost člena, který není ✔️ [virtuální](../../csharp/language-reference/keywords/sealed.md)**

- **✔️ Přidání abstraktní člen veřejný typ, který nemá žádné *přístupné* konstruktory (veřejné nebo chráněné), nebo typ je [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**

  Ale přidání abstraktní člen na typ, který má přístupné konstruktory (veřejné nebo chráněné) a není `sealed` není povolený.

- **✔️ Omezení viditelnost [chráněné](../../csharp/language-reference/keywords/protected.md) členský typ nemá žádné přístupné konstruktory (veřejné nebo chráněné), nebo je typ [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**

- **✔️ Přesunutí člena do výše v hierarchii než ze kterého byla odebrána typ třídy**

- **✔️ Přidání nebo odebrání přepsání**

  Mějte na paměti, Představujeme přepsání může způsobit předchozí spotřebitele mají přeskočit při volání metody přepsání [základní](../../csharp/language-reference/keywords/base.md).

- **✔️ Přidáním konstruktoru do třídy, spolu s výchozí (bezparametrový) konstruktor, pokud třída již dříve měli žádné konstruktory**

   Ale přidáním konstruktoru do třídy, které dříve měly žádné konstruktory *bez* přidání konstruktor bez parametrů není povoleno.

- **✔️ Změna člena z [abstraktní](../../csharp/language-reference/keywords/abstract.md) k [virtuální](../../csharp/language-reference/keywords/virtual.md)**

- **✔️ Změny z `ref readonly` k `ref` návratovou hodnotu (s výjimkou virtuální metody nebo rozhraní)**

- **✔️ Odebrání [jen pro čtení](../../csharp/language-reference/keywords/readonly.md) z pole, pokud typ statického pole je typu proměnlivé hodnoty**

- **Volání nové události, která nebyla dříve definovali ✔️**

- **Přidání nového pole instance na typ ❓**

   Tato změna má vliv na serializace.

- **❌ Přejmenování nebo odstranění veřejný člen nebo parametr**

   Tím je prolomen veškerý kód, který používá přejmenovaných nebo odebraný člen nebo parametr.

   Všimněte si, že to zahrnuje odebrání nebo přejmenování getter nebo setter z vlastnosti, jakož i přejmenování nebo odstranění výčet členů.

- **Přidání člena do rozhraní ❌**

- **Změna hodnoty veřejný člen nebo konstanta výčtu ❌**

- **❌ Změnou typu vlastnosti, pole, parametr nebo návratovou hodnotu**

- **❌ Přidání, odebrání nebo změně pořadí parametrů**

- **❌ Přidání nebo odebrání [v](../../csharp/language-reference/keywords/in.md), [si](../../csharp/language-reference/keywords/out.md) , nebo [ref](../../csharp/language-reference/keywords/ref.md) – klíčové slovo z parametru**

- **❌ Přejmenování parametru (včetně změna jeho velikosti písmen)**

  To je považováno za rozbíjející dva důvody:
  
  - To naruší s pozdní vazbou scénářů, jako je pozdní vazba funkce v jazyce Visual Basic a [dynamické](../../csharp/language-reference/keywords/dynamic.md) v C#.
  
  - To naruší [zdroje kompatibility](categories.md#source-compatibility) když vývojáři [pojmenované argumenty](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- **❌ Změny z `ref` vracet hodnotu `ref readonly` návratová hodnota**

- **❌️ Změny z `ref readonly` k `ref` návratová hodnota na virtuální metody nebo rozhraní**

- **❌ Přidání nebo odebrání [abstraktní](../../csharp/language-reference/keywords/abstract.md) od člena**

- **❌ Odebírá [virtuální](../../csharp/language-reference/keywords/virtual.md) – klíčové slovo z člena**

  To často není k zásadní změně protože C# kompilátor může vygenerovat [Call, callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) pokyny k volání nevirtuální metody (`callvirt` provádí kontrolu hodnot null, zatímco nebude normální volání ), toto chování není konstantní z několika důvodů:
  - C#není pouze jazyk, který cílí na .NET.
  
  - C# Kompilátoru stále pokusí optimalizovat `callvirt` normální volání pokaždé, když se do cílové metody je nevirtuální a není pravděpodobně null (například pro metodu prostřednictvím [?. operátor šíření hodnoty null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).
  
  Provádění virtuální metoda znamená, že uživatelský kód často skončili byste volání bez prakticky.

- **❌ Přidání [virtuální](../../csharp/language-reference/keywords/virtual.md) – klíčové slovo ke členovi**

- **❌, že virtuální člen abstraktní**

  A [virtuální člen](../../csharp/language-reference/keywords/virtual.md) obsahuje implementace metody, které *může být* přepsána odvozenou třídou. [Abstraktní člen](../../csharp/language-reference/keywords/abstract.md) poskytuje implementaci a *musí být* přepsat.

- **❌ Přidání abstraktní člen veřejný typ, který má přístupné konstruktory (veřejné nebo chráněné) a že není [zapečetěné](../../csharp/language-reference/keywords/sealed.md)**

- **❌ Přidání nebo odebrání [statické](../../csharp/language-reference/keywords/static.md) – klíčové slovo z člena**

- **Přidání přetížení, které vylučuje existující přetížení a definuje různé chování ❌**

  Tím je prolomen existující klienti, kteří byly vázána na předchozí přetížení. Například pokud třída má jednu verzi metody, která přijímá <xref:System.UInt32>, stávající příjemce se úspěšně vytvořit vazbu tohoto přetížení při předávání <xref:System.Int32> hodnotu. Ale pokud přidáte přetížení, která přijímá <xref:System.Int32>při opětovné kompilaci nebo pomocí pozdní vazby, kompilátor nyní vytvoří vazbu nové přetížení. Pokud různé chování vyplývá, je to zásadní změnu.

- **❌ Přidáním konstruktoru do třídy, které dříve měly žádný konstruktor bez přidání konstruktor bez parametrů**

- **❌️ Přidání [jen pro čtení](../../csharp/language-reference/keywords/readonly.md) na pole**

- **❌ Snižuje viditelnost člena**

   Jedná se o snižuje viditelnost [chráněné](../../csharp/language-reference/keywords/protected.md) člen, když nejsou *přístupné* konstruktory (veřejné nebo chráněné) a typ je *není* [ zapečetěné](../../csharp/language-reference/keywords/sealed.md). Pokud to není tento případ, snižuje viditelnost chráněný člen je povolený.

   Všimněte si, že není povoleno zvýšení viditelnosti člena.

- **❌ Změnu typu člena**

   Návratová hodnota metody nebo typ pole nebo vlastnost nelze upravovat. Například podpis metody, která se vrátí <xref:System.Object> nelze změnit na vrácení <xref:System.String>, nebo naopak.

- **❌ Přidání pole do struktury, které dříve měly žádný stav**

  Pravidla jednoznačného přiřazení umožňují použití neinicializované proměnné tak dlouho, dokud bezstavové struktura je typ proměnné. Pokud struktura stavové, kód může skončit s neinicializovaná data. Toto je potenciálně zdroj dopadem na dřívější kód a binární narušující změna.

- **❌ Ohlásí, existující událost v případě, že se nikdy vyvolala před**

## <a name="behavioral-changes"></a>Změny chování

### <a name="assemblies"></a>Sestavení

- **✔️ Zajištění přenositelnosti sestavení, když stejných platformách jsou stále podporovány.**

- **Změna názvu sestavení ❌**
- **❌ Změna veřejný klíč sestavení**

### <a name="properties-fields-parameters-and-return-values"></a>Vlastnosti, pole, parametry a návratové hodnoty

- **✔️ Změnou hodnoty vlastnosti, pole, návratová hodnota nebo [si](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr více odvozený typ**

  Například metoda, která vrací typ <xref:System.Object> můžete vrátit <xref:System.String> instance. (Však podpis metody nelze změnit.)

- **✔️ Zvýšení rozsahu přijaté hodnoty pro vlastnost nebo parametr, pokud člen není [virtuální](../../csharp/language-reference/keywords/virtual.md)**

  Všimněte si, že při rozsah hodnot, které může být předán metodě nebo člen vrací můžete rozšířit, nelze typ parametru nebo člen. Například když hodnoty předané metodě můžete rozšířit z 0-124 na 0 – 255, typ parametru nelze změnit z <xref:System.Byte> k <xref:System.Int32>.

- **❌ Zvýšení rozsahu přijaté hodnoty pro vlastnost nebo parametr, pokud je člen [virtuální](../../csharp/language-reference/keywords/virtual.md)**

   Tato změna přeruší stávající přepsaného členy, které nebude fungovat správně pro delší rozsah hodnot.

- **❌ Snížení rozsah platných hodnot pro vlastnost nebo parametr**

- **Zvýšení rozsahu ❌ vrácené hodnoty pro vlastnosti, pole, návratová hodnota nebo [si](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**

- **❌ Změna vrácených hodnot pro vlastnosti, pole, metoda návratovou hodnotu, nebo [si](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr**

- **Změna výchozí hodnoty vlastnosti, pole nebo parametr ❌**

- **❌ Změna přesnosti číselná návratová hodnota**

- **Změna ❓ A parsování vstupu a vyvolání nové výjimky (i v případě, že analýza chování není uveden v dokumentaci**

### <a name="exceptions"></a>Výjimky

- **✔️ Vyvolání výjimky více odvozený než existující výjimky**

  Protože nová výjimka je podtřídou existující výjimky, pokračuje v předchozí kód zpracování výjimek pro zpracování výjimky. Metody vytváření a načítání jazykové verze v rozhraní .NET Framework 4, například začal vyvolávat <xref:System.Globalization.CultureNotFoundException> místo <xref:System.ArgumentException> Pokud jazykové verze se nenašla. Protože <xref:System.Globalization.CultureNotFoundException> je odvozena z <xref:System.ArgumentException>, to je přijatelné změnit.

- **Vyvolání více specifické výjimky než ✔️ <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**

- **Došlo k výjimce, která se považuje za neopravitelné ✔️**

  Neopravitelné výjimky by neměly být zachycovány, ale místo toho by měla být zpracovány vysoké úrovně obslužné rutiny catch – to všechno. Uživatelé se tedy, že kód, který zachytává tyto explicitní výjimky. Neopravitelné výjimky jsou:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **✔️ Vyvolání nové výjimky novou cestu kódu**

  Výjimka musíte použít pouze pro nový kód – cestu, který je proveden pomocí nové hodnoty parametru nebo stav, a existující kód, který nemůže provést, který cílí na předchozí verzi.

- **Odebrání výjimky umožňující robustnější chování nebo nové scénáře ✔️**

  Například `Divide` metodu, která dříve pouze kladné hodnoty zpracovat a došlo <xref:System.ArgumentOutOfRangeException> jinak je změnit, aby bez vyvolání výjimky nepodporuje záporné i kladné hodnoty.

- **✔️ Změnu textu chybovou zprávu**

  Vývojáři, neměli byste tedy spoléhat na textu chybové zprávy, které také změní na základě jazykové verze uživatele.

- **❌ Došlo k výjimce ve všech ostatních případech není uvedené výš**

- **Odebrání výjimky ve všech ostatních případech není uvedené výš ❌**

### <a name="attributes"></a>Atributy

- **Změna hodnoty atributu, který je ✔️ *není* pozorovat**

- **❌ Změnit hodnotu atributu, který *je* pozorovat**

- **❓ Odebrat atribut**

  Ve většině případů odebrání atributu (například <xref:System.NonSerializedAttribute>) je zásadní změnu.

## <a name="platform-support"></a>Podpora platforem

- **Podporuje operace na platformě, která se dříve podporovaly ✔️**

- **❌ Není podpory nebo nyní vyžadování konkrétního service pack pro operace, který byl dříve podporován na platformě**

## <a name="internal-implementation-changes"></a>Vnitřní implementace změny

- **❓ Změna útoku na vnitřní typ**

   Tyto změny jsou obecně povoleny, i když jsou přerušit privátní reflexe. V některých případech, kdy Oblíbené knihovny třetích stran nebo velký počet vývojáře závisí na interních rozhraních API, nemusí být povolený tyto změny.

- **❓ Změna vnitřní implementace členu**

  Tyto změny jsou obecně povoleny, i když jsou přerušit privátní reflexe. V některých případech, pokud kód zákazníka často závisí na reflexi privátní nebo kde změna představuje nežádoucí vedlejší účinky, nemusí být povolený tyto změny.

- **Zlepšení výkonu operace ✔️**

   Schopnost upravovat výkonu operace je nezbytné, ale tyto změny může dojít k narušení kódu, která závisí na aktuální rychlost operace. To platí zejména pro kód, který závisí na načasování asynchronních operací. Všimněte si, že změna výkonu by neměla mít žádný vliv na jiné chování rozhraní API dotyčný; v opačném případě se zásadní změnu.

- **✔️ Nepřímo (a často nepříznivě) Změna výkonu operace**

  Pokud se dané změny není kategorizována jako zásadní nějakého jiného důvodu, je to přijatelné. Často akce nezbytné mají být provedeny, který může obsahovat další operace nebo přidá nové funkce. To bude téměř vždy mít vliv na výkon, ale může být nezbytné, aby rozhraní API ve funkci dotaz podle očekávání.

- **❌ Změna synchronního rozhraní API na asynchronní (a naopak)**

## <a name="code-changes"></a>Změny kódu

- **✔️ Přidání [params](../../csharp/language-reference/keywords/params.md) na parametr**

- **❌ Změna [struktura](../../csharp/language-reference/keywords/struct.md) k [třídy](../../csharp/language-reference/keywords/class.md) a naopak**

- **❌ Přidání [zaškrtnutí](../../csharp/language-reference/keywords/virtual.md) – klíčové slovo k bloku kódu**

   Tato změna může způsobit, že kód, který dříve provedený vyvolání <xref:System.OverflowException> a nemůže být přijata.

- **❌ Odebrání [params](../../csharp/language-reference/keywords/params.md) z parametru**

- **Změna pořadí, ve kterém jsou vyvolávány události ❌**

  Vývojáři můžou očekávat rozumně události, která se aktivuje ve stejném pořadí a kód vývojáře často závisí na pořadí, ve kterém jsou vyvolávány události.

- **❌ Odebrání vyvolání události pro danou akci**

- **Jsou volány ❌ změna počet, kolikrát daný události**

- **❌ Přidání <xref:System.FlagsAttribute> na typ výčtu**
