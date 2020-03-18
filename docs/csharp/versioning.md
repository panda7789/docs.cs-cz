---
title: C# Správa verzí – průvodce C#
description: Zjistěte, jak funguje správa verzí v c# a .NET
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 124cce51865f04a555bc121fb6ce18cc95591bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156464"
---
# <a name="versioning-in-c"></a>Správa verzí v C\#

V tomto kurzu se dozvíte, co znamená správa verzí v rozhraní .NET. Dozvíte se také faktory, které je třeba vzít v úvahu při snímání verzí knihovny a upgradu na novou verzi knihovny.

## <a name="authoring-libraries"></a>Vytváření knihoven

Jako vývojář, který vytvořil knihovny .NET pro veřejné použití, jste s největší pravděpodobností byli v situacích, kdy budete muset zavést nové aktualizace. Jak jít o tomto procesu záleží hodně, jak je třeba zajistit, že je bezproblémový přechod existujícího kódu na novou verzi knihovny. Zde je několik věcí, které je třeba zvážit při vytváření nové verze:

### <a name="semantic-versioning"></a>Sémantická správa verzí

[Sémantická správa verzí](https://semver.org/) (zkráceně SemVer) je konvence pojmenování použitá pro verze knihovny, která označuje konkrétní události milníků.
V ideálním případě by informace o verzi, které poskytujete knihovně, měly vývojářům pomoci určit kompatibilitu s jejich projekty, které využívají starší verze stejné knihovny.

Nejzákladnější přístup k SemVer je `MAJOR.MINOR.PATCH`3 složka formátu , kde:

- `MAJOR`je se zpřísněn, když provedete nekompatibilní změny rozhraní API
- `MINOR`je se zvýší, když přidáte funkce zpětně kompatibilním způsobem
- `PATCH`je se zpřísněn, když provedete opravy chyb kompatibilní se zpětnou kompatibilitou

Existují také způsoby, jak zadat další scénáře, jako jsou předběžné verze atd.

### <a name="backwards-compatibility"></a>Zpětná kompatibilita

Při vydávání nových verzí knihovny bude zpětná kompatibilita s předchozími verzemi s největší pravděpodobností jednou z vašich hlavních obav.
Nová verze knihovny je zdroj kompatibilní s předchozí verzí, pokud kód, který závisí na předchozí verzi může při překompilování pracovat s novou verzí.
Nová verze knihovny je binární kompatibilní, pokud aplikace, která závisela na staré verzi, může bez rekompilace pracovat s novou verzí.

Při pokusu o zachování zpětné kompatibility se staršími verzemi knihovny je třeba zvážit několik věcí:

- Virtuální metody: Pokud vytvoříte virtuální metodu nevirtuální v nové verzi, znamená to, že projekty, které tuto metodu přepíší, budou muset být aktualizovány. Jedná se o obrovskou průlomovou změnu a je silně odrazována.
- Podpisy metody: Při aktualizaci chování metody vyžaduje také změnit jeho podpis, měli byste místo toho vytvořit přetížení tak, aby kód volající do této metody bude i nadále fungovat.
Vždy můžete manipulovat starý podpis metody volat do podpisu nové metody tak, aby implementace zůstává konzistentní.
- [Zastaralý atribut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Tento atribut v kódu můžete použít k určení tříd nebo členů tříd, které jsou zastaralé a pravděpodobně budou odebrány v budoucích verzích. Tím je zajištěno, že vývojáři využívající vaši knihovnu jsou lépe připraveni na nejnovější změny.
- Volitelné argumenty metody: Pokud provedete dříve volitelné argumenty metody povinné nebo změnit jejich výchozí hodnotu pak veškerý kód, který neposkytuje tyto argumenty bude muset být aktualizován.

> [!NOTE]
> Povinné argumenty by měly mít velmi malý účinek, zejména pokud nezmění chování metody.

Čím snadněji provedete upgrade na novou verzi knihovny uživatelům, tím je pravděpodobnější, že budou upgradovat dříve.

### <a name="application-configuration-file"></a>Konfigurační soubor aplikace

Jako vývojář rozhraní .NET je velmi vysoká pravděpodobnost, že jste narazili [na `app.config` soubor](../framework/configure-apps/file-schema/index.md) přítomný ve většině typů projektů.
Tento jednoduchý konfigurační soubor může jít dlouhou cestu do zlepšení zavádění nových aktualizací. Obecně byste měli navrhnout knihovny tak, aby informace, které se `app.config` pravděpodobně pravidelně mění, byly uloženy v souboru, a tak při aktualizaci těchto informací musí být konfigurační soubor starších verzí nahrazen novým bez nutnosti rekompilace knihovny.

## <a name="consuming-libraries"></a>Náročné knihovny

Jako vývojář, který využívá knihovny .NET vytvořené jinými vývojáři, jste si s největší pravděpodobností vědomi toho, že nová verze knihovny nemusí být plně kompatibilní s vaším projektem a často se často ocitnete museli aktualizovat kód pro práci s těmito změnami.

Naštěstí pro vás, C# a .NET ekosystém přichází s funkcemi a technikami, které nám umožňují snadno aktualizovat naši aplikaci pro práci s novými verzemi knihoven, které by mohly zavést nejnovější změny.

### <a name="assembly-binding-redirection"></a>Přesměrování vazeb sestavy

Pomocí souboru *app.config* můžete aktualizovat verzi knihovny, kterou vaše aplikace používá. Přidáním takzvaného [*přesměrování vazby*](../framework/configure-apps/redirect-assembly-versions.md)můžete použít novou verzi knihovny, aniž byste museli znovu kompilovat aplikaci. Následující příklad ukazuje, jak byste aktualizovali soubor *app.config* aplikace `ReferencedLibrary` tak, `1.0.0` aby používal verzi `1.0.1` opravy namísto verze, ve které byl původně zkompilován.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Tento přístup bude fungovat pouze `ReferencedLibrary` v případě, že nová verze je binární kompatibilní s vaší aplikací.
> Změny, na které je třeba dávat pozor při určování kompatibility, najdete v části [Zpětná kompatibilita](#backwards-compatibility) výše.

### <a name="new"></a>new

`new` Modifikátor slouží ke skrytí zděděných členů základní třídy. Toto je jeden způsob, jak odvozené třídy mohou reagovat na aktualizace v základních třídách.

Vezměte v následující příklad:

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

**Výstup**

```console
A base method
A derived method
```

Z výše uvedeného příkladu můžete vidět, jak `DerivedClass` skryje metodu přítomnou `MyMethod` v `BaseClass`.
To znamená, že když základní třída v nové verzi knihovny přidá člen, který již existuje `new` v odvozené třídě, můžete jednoduše použít modifikátor na člen odvozené třídy skrýt člen základní třídy.

Pokud `new` není zadán žádný modifikátor, odvozená třída bude ve výchozím nastavení skrývat konfliktní členy v základní třídě, i když bude generováno upozornění kompilátoru, kód bude stále kompilován. To znamená, že jednoduše přidání nových členů do existující třídy způsobí, že nová verze knihovny zdrojové i binární kompatibilní s kódem, který na něm závisí.

### <a name="override"></a>override

Modifikátor `override` znamená, že odvozená implementace rozšiřuje implementaci člena základní třídy, nikoli jej skryje. Člen základní třídy musí `virtual` mít modifikátor použít.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

**Výstup**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

Modifikátor `override` je vyhodnocen v době kompilace a kompilátor vyvolá chybu, pokud nenajde virtuálního člena přepsat.

Vaše znalosti diskutovaných technik a vaše chápání situací, ve kterých je používat, půjdou dlouhou cestu k usnadnění přechodu mezi verzemi knihovny.
