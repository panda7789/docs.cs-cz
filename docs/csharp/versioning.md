---
title: C# Správa verzí – Průvodce v C#
description: Pochopení principu správy verzí v C# a .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: a0c75e2f1397f43fadf91d145e8b63de1d4d90eb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243488"
---
# <a name="versioning-in-c"></a>Správa verzí v jazyce C# #

V tomto kurzu se dozvíte, jaké správy verzí znamená, že v rozhraní .NET. Dozvíte se víc i faktory vzít v úvahu při vytváření verzí knihovny, jakož i upgrade na novou verzi knihovny.

## <a name="authoring-libraries"></a>Vytváření knihovny

Jako vývojář, který byl vytvořen knihovny .NET pro veřejně přístupný, když jste většinu pravděpodobně byl v situacích, kdy máte zavádět nové aktualizace. Jak přejít o tomto procesu hrají podle musíte zajistit, že je jednoduchý přechod z existujícího kódu na novou verzi knihovny. Tady je několik věcí, které je třeba zvážit při vytváření nové vydané verze:

### <a name="semantic-versioning"></a>Semantic Versioning

[Sémantické správy verzí](https://semver.org/) (SemVer zkráceně) je zásady vytváření názvů u verze knihovny místo konkrétní verze události.
V ideálním případě informací o verzi, poskytnete své knihovny by měly pomoci vývojářům zjistit informace o kompatibilitě s jejich projekty, které využívají starší verze, která stejné knihovny.

Nejzákladnější přístup k SemVer je formát 3 komponenty `MAJOR.MINOR.PATCH`, kde:

* `MAJOR` se zvýší, když provedete změny nekompatibilní rozhraní API
* `MINOR` se zvýší, když přidáte funkci způsobem zpětně kompatibilní
* `PATCH` se zvýší, když provedete zpětně kompatibilní opravy chyb

Existují také způsoby, jak určit jiné scénáře, jako jsou předběžné verze atd. při použití informací o verzi na knihovny .NET.

### <a name="backwards-compatibility"></a>Zpětné kompatibility

Jak vydáním nové verze knihovny zpětné kompatibility s předchozími verzemi bude pravděpodobně mezi hlavní priority.
Zdroj kompatibilní s předchozí verzí, pokud kód, který závisí na předchozí verzi, při nové kompilaci neúspěchu v nové verzi je nová verze knihovny. Pokud aplikace, která závisí na předchozí verzi aplikace můžou bez rekompilace, pracovat s novou verzi, je nová verze knihovny binární kompatibilní.

Tady je pár věcí k uvážení při pokusu o zachování zpětné kompatibility se staršími verzemi knihovny:

* Virtuální metody: Když vytvoříte virtuální metody v nové verzi nevirtuální, znamená to, že projekty, které potlačí tuto metodu bude mít aktualizovat. To je obrovská rozbíjející změny a se důrazně nedoporučuje.
* Podpisy metod: Při aktualizaci chování metoda vyžaduje, abyste změňte její signaturu tak dobře, měli byste místo toho přetížení vytvořit tak, aby kód volání do metody budou i nadále fungovat.
Vždy můžete pracovat s starý podpis metody, chcete-li volat nový podpis metody tak, aby zůstala konzistentní implementaci.
* [Zastaralé atribut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Tento atribut v kódu můžete použít k určení, že třídy nebo členy třídy, které jsou zastaralé a pravděpodobně odebrán v budoucích verzích.
Tím se zajistí, že vývojáři využívající knihovnu lépe připraveni rozbíjející změny.
* Metoda volitelné argumenty: Když provedete metoda dříve volitelné argumenty povinné nebo změnit výchozí hodnoty a veškerý kód, který neposkytuje tyto argumenty budou potřeba aktualizovat.
> [!NOTE]
> Provádění povinné argumenty volitelné by měl mít velmi malý vliv, zejména v případě, že ho nedojde ke změně chování metody.

Tím snadněji provedete to pro vaše uživatele pro upgrade na novou verzi knihovny, tím pravděpodobnější, že se bude upgradovat dřív.

### <a name="application-configuration-file"></a>Konfigurační soubor aplikace

Jako vývojář .NET existuje velmi vysoká pravděpodobnost, kterým jste se setkali [ `app.config` soubor](../framework/configure-apps/file-schema/index.md) součástí většinu typů projektu.
Tento jednoduchý konfigurační soubor můžete urazily dlouhou cestu do zlepšení zavedení nové aktualizace. Obecně byste navrhnout svoje knihovny takovým způsobem, že je uložené informace, které jsou pravděpodobně pravidelně měnit v `app.config` souboru tímto způsobem, když dojde k aktualizaci těchto informací právě potřebuje vyměnit s novým konfiguračního souboru starší verze bez nutnosti rekompilace knihovny.

## <a name="consuming-libraries"></a>Použití knihovny

Jako vývojář, který využívá knihovny .NET vytvořených jinými vývojáři vědět pravděpodobně, že nová verze knihovny nemusí být plně kompatibilní s vaším projektem, takže vám často sami s a aktualizujte svůj kód pro práci s těmito změnami.

Šťastná za vás C# a ekosystému .NET obsahuje funkce a techniky, které umožňuje snadno aktualizovat naší aplikace pro práci s novými verzemi nástroje knihovny, které můžou zavést rozbíjející změny.

### <a name="assembly-binding-redirection"></a>Přesměrování vazby sestavení

Můžete použít `app.config` souboru k aktualizaci verze knihovny aplikace používá. Přidáním, co se volá [ *přesměrování vazby* ](../framework/configure-apps/redirect-assembly-versions.md) používáte novou verzi knihovny bez nutnosti znovu kompilovat aplikace. Následující příklad ukazuje, jak by aktualizovat vaše aplikace `app.config` soubor má být použit `1.0.1` oprav verze `ReferencedLibrary` místo `1.0.0` původně byl kompilován s verzí.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Tento postup bude fungovat jenom v případě novou verzi `ReferencedLibrary` binární kompatibilní s vaší aplikací.
> Zobrazit [Backwards Compatibility](#backwards-compatibility) výše uvedené části hledejte při určování kompatibility se změny.

### <a name="new"></a>new

Můžete použít `new` modifikátor ke skrytí zděděné členy základní třídy. Toto je jeden způsob odvozené třídy může reagovat na aktualizací v základních tříd.

Proveďte v následujícím příkladu:

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

**Output**

```
A base method
A derived method
```

V předchozím příkladu můžete zobrazit jak `DerivedClass` skryje `MyMethod` metody, které jsou k dispozici v `BaseClass`.
To znamená, že když základní třídy v nové verzi knihovny přidá člen, který již existuje v odvozené třídě, můžete jednoduše použít `new` modifikátor vaší odvozené třídě člen skrýt člena základní třídy.

Pokud ne `new` modifikátor určena, odvozené třídy ve výchozím nastavení skryje konfliktní členy v základní třídě, i když se vygeneruje upozornění kompilátoru kód se stále zkompiluje. To znamená, že jednoduše přidání nových členů do existující třídy díky tuto novou verzi knihovny zdroje a binární soubor kompatibilní s kódem, který na něm závisí.

### <a name="override"></a>override

`override` Modifikátor znamená, že odvozené implementace rozšiřuje implementaci člena základní třídy místo skrývá ho. Členu základní třídy musí mít `virtual` použit modifikátor.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Output**

```
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` Modifikátor je vyhodnocen v době kompilace a kompilátor vyvolá chybu, pokud se nenajde virtuální člen přepsat.

Svoje znalosti v oblasti popsané technik, jakož i pochopíte jaké situacích k jejich použití bude urazily dlouhou cestu a zvýšit tak snadné přechod mezi verzemi knihovny.
