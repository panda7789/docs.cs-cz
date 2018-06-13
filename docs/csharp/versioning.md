---
title: C# Správa verzí – Průvodce v C#
description: Pochopit, jak funguje správa verzí v C# a rozhraní .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 4dc8e7e521bf209d6ca69a84534d277fb8a93ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351781"
---
# <a name="versioning-in-c"></a>Správa verzí v jazyce C# #

V tomto kurzu se dozvíte, jaké verze znamená v rozhraní .NET. Taky poznáte faktory vzít v úvahu při Správa verzí knihovnu, jakož i upgrade na novou verzi knihovnu.

## <a name="authoring-libraries"></a>Vytváření knihovny

Jako vývojář, který vytvořil knihovny .NET pro veřejné použijte, když jste většinu pravděpodobně byla v situacích, kdy máte zavádět nové aktualizace. Jak přejdete o tomto procesu otázkách mnoho, je potřeba zajistit, že je snadný přechod z existujícího kódu na novou verzi své knihovny. Tady je několik zvážit při vytváření nové verze:

### <a name="semantic-versioning"></a>Sémantické verze

[Sémantické verze](http://semver.org/) (SemVer pro zkrácení) je použita pro verze knihovny a označují konkrétní verze události zásady vytváření názvů.
V ideálním případě informace o verzi, poskytnete své knihovny by měly pomoci vývojářům určete kompatibilitu s jejich projektů, které používá starší verzí této stejné knihovny.

Nejzákladnější přístup k SemVer je formát 3 součást `MAJOR.MINOR.PATCH`, kde:
 
* `MAJOR` se zvýší, když provedete změny nekompatibilní rozhraní API
* `MINOR` se zvýší, když přidáte funkci způsobem zpětně kompatibilní
* `PATCH` se zvýší, když provedete zpětně kompatibilní opravy chyb

Existují také způsobů určení scénáře jako předprodejní verze atd. při použití informací o verzi do knihovny .NET.

### <a name="backwards-compatibility"></a>Zpětné kompatibility

Jak můžete vydání nové verze knihovny, zpětné kompatibility s předchozími verzemi bude pravděpodobně jednou z hlavních věcí.
Nová verze knihovny je zdrojem kompatibilní s předchozí verze, pokud kód, který závisí na předchozí verzi můžete, pokud překompilovat, pracovat s novou verzí. Pokud aplikace, která závisí na předchozí verzi můžete, bez rekompilace pracovat s novou verzí, je nová verze knihovny binární kompatibilní.

Zde jsou některé věci, které je třeba zvážit při zachování zpětné kompatibility s starší verze knihovny:

* Virtuální metody: Pokud vytvoříte virtuální metoda nevirtuálních v nové verzi znamená, že bude muset aktualizovat projekty, které potlačí tuto metodu. Toto je velký narušující změně a se důrazně nedoporučuje.
* Metoda podpisů: při aktualizaci chování metoda vyžaduje, abyste změnit také jeho podpis, měli byste místo toho vytvořit přetížení tak, aby kód volání do dané metody budou i nadále fungovat.
Vždy můžete upravit původní podpis metody provést volání do nové podpis metody tak, aby implementace konzistentní.
* [Zastaralé atribut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Tento atribut v kódu můžete použít k určení třídy nebo členy třídy, které jsou zastaralé a mohou být odebrány v budoucích verzích.
Tím se zajistí, že vývojáři využitím knihovnu lépe připravené pro nejnovější změny.
* Nepovinné argumenty metoda: Když provedete metoda dříve volitelné argumenty povinné nebo změnit jejich výchozí hodnoty a všechen kód, který neposkytuje těchto argumentů bude potřeba aktualizovat.
> [!NOTE]
> Provedení povinné argumenty nepovinné by měl mít velmi malý vliv, zejména v případě, že se nezmění, metoda chování.

Tím snadnější provedete ji pro uživatele k upgradu na novou verzi knihovny, je pravděpodobnější, že se provede upgrade dřív.

### <a name="application-configuration-file"></a>Konfigurační soubor aplikace

Jako vývojář .NET existuje velmi vysoká pravděpodobnost byla zjištěna [ `app.config` souboru](https://msdn.microsoft.com/library/1fk1t1t0(v=vs.110).aspx) ve většině typy projektů.
Tento jednoduchý konfigurační soubor můžete vyhledat celou do zlepšení zavedení nových aktualizací. Měli byste obecně navrhnout knihovnách tak, že jsou informace, které pravděpodobně se změní pravidelně uložena v `app.config` souboru, tak při aktualizaci tyto informace do konfiguračního souboru starší verze právě je nutné vyměnit novým bez nutnosti rekompilace knihovny.

## <a name="consuming-libraries"></a>Použití knihovny

Jako vývojář, který využívá knihovny .NET vytvořené jinými vývojáři jste s největší pravděpodobností vědět, že novou verzi knihovny nemusí být plně kompatibilní s projektem a může najít často sami nutnosti aktualizujte kód a pracovat s těmito změnami.

Šťastná pro vás C# a ekosystému .NET obsahuje funkce a techniky, které umožňují snadno aktualizovat vaší aplikace pro práci s novými verzemi nástroje knihovny, které může způsobit dodatečné změny.

### <a name="assembly-binding-redirection"></a>Sestavení – přesměrování vazby

Můžete použít `app.config` soubor aktualizovat verzi knihovny vaše aplikace používá. Přidáním, co se nazývá [ *přesměrování vazby* ](https://msdn.microsoft.com/library/7wd6ex19(v=vs.110).aspx) vaše můžete použít na novou verzi knihovny bez nutnosti její kompilace aplikace. Následující příklad ukazuje, jak by aktualizovat vaše aplikace `app.config` soubor se má použít `1.0.1` oprav verze `ReferencedLibrary` místo `1.0.0` verze byla původně kompilovat s.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Tento postup bude fungovat pouze v případě novou verzi `ReferencedLibrary` je binární kompatibilní s vaší aplikací.
> Najdete v článku [zpětné kompatibility](#backwards-compatibility) část výše změny hledání při určování kompatibility.

### <a name="new"></a>new

Můžete použít `new` modifikátor skrytí zděděné členy základní třídy. To je jedním způsobem odvozené třídy mohou reagovat na aktualizace v základní třídy.

Proveďte v následujícím příkladu:

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

**Output**

```
A base method
A derived method
```

Z výše uvedeném příkladu uvidíte jak `DerivedClass` skryje `MyMethod` metoda součástí `BaseClass`.
To znamená, že pokud základní třídu v nové verzi knihovny přidá člena, který již existuje v odvozené třídě, můžete jednoduše použít `new` modifikátor na vaše člen odvozené třídy ke skrytí člen základní třídy.

Pokud ne `new` Modifikátor je zadán, bude ve výchozím nastavení do odvozené třídy skrýt konfliktní členy v základní třídě, i když se vygeneruje upozornění kompilátoru stále kompilací kódu. To znamená, že jednoduše přidáním nové členy do existující třídy díky nové verze nástroje knihovnu zdrojový i binární kompatibilní s kódem, který na něm závisí.

### <a name="override"></a>override

`override` Modifikátor znamená odvozené implementace rozšiřuje implementace člena základní třídy místo skryje ho. Základní třída člen musí mít `virtual` modifikátor použije na ni.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Output**

```
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` Modifikátor je vyhodnocován v době kompilace a kompilátor vyvolá chybu, pokud se nenajde člena virtuální přepsat.

Vašich znalostí technik popsaných i pochopení jaké situacích používat přejde dlouho způsob, jak zvýšit snadný přechod mezi verzemi knihovny.
