---
title: C#C# Průvodce správou verzí
description: Informace o tom, jak funguje C# Správa verzí v prostředí a .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 4c0d5b5c2ac40cb27c90b4908623dc75b26a80cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699922"
---
# <a name="versioning-in-c"></a>Správa verzí v jazyce C @ no__t-0

V tomto kurzu se dozvíte, co znamená Správa verzí v .NET. Dozvíte se také o faktorech, které je potřeba vzít v úvahu při použití verze knihovny a upgradu na novou verzi knihovny.

## <a name="authoring-libraries"></a>Vytváření knihoven

Jako vývojář, který vytvořil knihovny .NET pro veřejné použití, jste pravděpodobně v situacích, kdy je nutné zavést nové aktualizace. Způsob, jakým se dozvíte o tomto procesu, záleží na tom, co potřebujete, abyste zajistili bezproblémové přechody stávajícího kódu na novou verzi vaší knihovny. Při vytváření nové verze je potřeba vzít v úvahu několik věcí:

### <a name="semantic-versioning"></a>Sémantická verze

[Sémantická Správa verzí](https://semver.org/) (SemVer pro krátké verze) je konvence pojmenování, která se používá ve verzích vaší knihovny k označení konkrétních událostí milníku.
V ideálním případě informace o verzi vaší knihovny by vám měly pomáhat vývojářům určit kompatibilitu s jejich projekty, které využívají starší verze stejné knihovny.

Nejzákladnější přístup k SemVer je 3 formát součásti `MAJOR.MINOR.PATCH`, kde:

- `MAJOR` se zvýší, když provedete nekompatibilní změny rozhraní API
- `MINOR` se zvýší, když přidáváte funkce zpětně kompatibilním způsobem.
- @no__t – 0 se zvýší, když provedete zpětně kompatibilní opravy chyb.

Existují také způsoby určení dalších scénářů, jako jsou předběžné verze verzí atd. při použití informací o verzi do knihovny .NET.

### <a name="backwards-compatibility"></a>Zpětná kompatibilita

Při vydávání nových verzí knihovny bude zpětná kompatibilita s předchozími verzemi pravděpodobně jedním z vašich hlavních otázek.
Nová verze knihovny je kompatibilní se zdrojem předchozí verze, pokud kód, který závisí na předchozí verzi, může při rekompilaci fungovat s novou verzí. Nová verze knihovny je binární, kompatibilní, pokud aplikace, která závisí na staré verzi, může bez rekompilace fungovat s novou verzí.

Tady je několik věcí, které je potřeba vzít v úvahu při pokusu o udržení zpětné kompatibility se staršími verzemi vaší knihovny:

- Virtuální metody: když v nové verzi vytvoříte virtuální metodu, která není virtuální, znamená to, že se budou aktualizovat projekty, které tuto metodu přepíší. Jedná se o velmi zásadní změnu a důrazně se nedoporučuje.
- Signatury metod: při aktualizaci chování metody vyžaduje, abyste změnili jeho signaturu. místo toho byste měli vytvořit přetížení, aby kód, který volá tuto metodu, bude i nadále fungovat.
Můžete vždycky manipulovat s podpisem staré metody, aby se volal do nového podpisu metody, takže implementace zůstane konzistentní.
- [Zastaralý atribut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): pomocí tohoto atributu v kódu můžete určit třídy nebo členy třídy, které jsou zastaralé a pravděpodobně budou v budoucích verzích odebrány. Tím je zajištěno, že vývojáři, kteří využívají vaši knihovnu, budou lépe připraveni na zásadní změny.
- Volitelné argumenty metody: Když ponecháte dříve volitelné argumenty metody jako povinné nebo změníte jejich výchozí hodnotu, bude nutné aktualizovat veškerý kód, který tyto argumenty nedodá.

> [!NOTE]
> Volitelná povinná argumenty by měly mít velmi malý účinek, zejména pokud nemění chování metody.

To je snazší, když uživatelům umožníte upgradovat na novou verzi knihovny, což je pravděpodobnější, že budou upgradovat dřív.

### <a name="application-configuration-file"></a>Konfigurační soubor aplikace

Jako vývojář rozhraní .NET existuje velmi vysoká pravděpodobnost, že jste narazili [na soubor `app.config`](../framework/configure-apps/file-schema/index.md) ve většině typů projektů.
Tento jednoduchý konfigurační soubor může být delší způsob, jak zlepšit zavedení nových aktualizací. Obecně byste měli navrhovat knihovny tak, aby se informace, které se pravděpodobně mění pravidelně, ukládaly do souboru `app.config`. tímto způsobem se tyto informace aktualizují, konfigurační soubor starších verzí stačí nahradit novým a bez je potřeba pro rekompilaci knihovny.

## <a name="consuming-libraries"></a>Využívání knihoven

Jako vývojář, který využívá knihovny .NET vytvořené jinými vývojáři, s největší pravděpodobně víte, že nová verze knihovny nemusí být plně kompatibilní s vaším projektem, a je možné, že často budete muset aktualizovat kód pro práci s těmito změnami.

Štěstí za vás C# a ekosystém .NET přináší funkce a techniky, které nám umožňují snadno aktualizovat naši aplikaci tak, aby fungovala s novými verzemi knihoven, které by mohly vést k zásadním změnám.

### <a name="assembly-binding-redirection"></a>Přesměrování vazby sestavení

Soubor *App. config* můžete použít k aktualizaci verze knihovny, kterou vaše aplikace používá. Přidáním toho, co se nazývá [*přesměrování vazby*](../framework/configure-apps/redirect-assembly-versions.md), můžete použít novou verzi knihovny, aniž by bylo nutné aplikaci znovu kompilovat. Následující příklad ukazuje, jak byste aktualizovali soubor *App. config* aplikace tak, aby používal opravu `1.0.1` verze `ReferencedLibrary` namísto verze `1.0.0`, na kterou byl původně zkompilován.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Tento přístup bude fungovat jenom v případě, že je nová verze `ReferencedLibrary` binární kompatibilní s vaší aplikací.
> V části [Zpětná kompatibilita](#backwards-compatibility) výše najdete změny, které je potřeba zobrazit při určování kompatibility.

### <a name="new"></a>new

Pomocí modifikátoru `new` skryjete zděděné členy základní třídy. Toto je jeden ze způsobů, které odvozené třídy mohou reagovat na aktualizace v základních třídách.

Vezměte v úvahu následující příklad:

[!code-csharp[Sample usage of the 'new' modifier](~/samples/csharp/versioning/new/Program.cs#sample)]

**Output**

```console
A base method
A derived method
```

Z výše uvedeného příkladu vidíte, jak `DerivedClass` skrývá metodu `MyMethod`, která je k dispozici v `BaseClass`.
To znamená, že když základní třída v nové verzi knihovny přidá člena, který již existuje v odvozené třídě, můžete jednoduše použít modifikátor `new` na odvozeném členu třídy pro skrytí člena základní třídy.

Pokud není zadán modifikátor `new`, bude ve výchozím nastavení v odvozené třídě automaticky skrývat konfliktní členy v základní třídě, i když bude vygenerováno upozornění kompilátoru, kód bude stále zkompilován. To znamená, že pouhým přidáním nových členů do existující třídy dojde k tomu, že nová verze knihovny je kompatibilní se zdrojovým i binárním kódem, který na něm závisí.

### <a name="override"></a>override

Modifikátor `override` znamená, že odvozená implementace rozšiřuje implementaci člena základní třídy místo jeho skrytí. Pro člena základní třídy musí být použit modifikátor `virtual`.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Output**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

Modifikátor `override` je vyhodnocen v době kompilace a kompilátor vyvolá chybu, pokud nenajde virtuální člen, který se má přepsat.

Vaše znalosti o popisovaných technikách a také porozumění situacím, které se mají použít, budou mít dlouhý způsob, jak zvýšit přehlednost mezi verzemi knihovny.
 
