---
title: Výjimky a výkon
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: afa4e748599781a5979823320d8913ff5357d415
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741643"
---
# <a name="exceptions-and-performance"></a>Výjimky a výkon
Jedním z běžných obav souvisejících s výjimkou je, že pokud jsou výjimky používány pro kód, který rutinně selže, výkon implementace nebude možné přijmout. Toto je platný problém. Když člen vyvolá výjimku, může jeho výkon pomalejit pořadí. Je však možné dosáhnout dobrého výkonu v rámci striktního dodržování pokynů pro výjimky, které zakazují použití kódů chyb. Tento postup popisují dva vzory popsané v této části.

 ❌ nepoužívejte kódy chyb z důvodu obav, že výjimky mohou negativně ovlivnit výkon.

 Chcete-li zvýšit výkon, je možné použít buď vzorek test-Doer, nebo vzor try-Parse, který je popsán v následujících dvou částech.

## <a name="tester-doer-pattern"></a>Tester – vzor Doer
 V některých případech je možné zvýšit výkon člena s aktivačními výjimkami, a to rozdělením členu na dva. Pojďme se podívat na metodu <xref:System.Collections.Generic.ICollection%601.Add%2A> rozhraní <xref:System.Collections.Generic.ICollection%601>.

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 Metoda `Add` vyvolá, pokud je kolekce jen pro čtení. Může se jednat o problém s výkonem ve scénářích, kdy se očekává, že volání metody bude často neúspěšné. Jedním ze způsobů, jak zmírnit problém, je otestovat, jestli je kolekce zapisovatelná, než se pokusíte přidat hodnotu.

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 Člen použitý k otestování podmínky, která v našem příkladu je vlastnost `IsReadOnly`, se označuje jako tester. Člen použitý k provedení potenciálně vyvolání operace, `Add` metoda v našem příkladu, se označuje jako Doer.

 ✔️ Představte si vzor Tester-Doer pro členy, které mohou vyvolat výjimky v běžných scénářích, aby nedocházelo k problémům s výkonem souvisejícím s výjimkami.

## <a name="try-parse-pattern"></a>Vzor try-Parse
 Pro vysoce výkonná rozhraní API je vhodné použít ještě rychlejší model, než je vzor testovacího Doeru popsaný v předchozí části. Vzor volá pro úpravu názvu člena k vytvoření dobře definovaného testovacího případu, který je součástí sémantiky členů. Například <xref:System.DateTime> definuje metodu <xref:System.DateTime.Parse%2A>, která vyvolá výjimku, pokud se analýza řetězce nezdařila. Definuje také odpovídající metodu <xref:System.DateTime.TryParse%2A>, která se pokusí analyzovat, ale vrátí hodnotu false, pokud je analýza neúspěšná a vrátí výsledek úspěšné analýzy pomocí parametru `out`.

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 Při použití tohoto modelu je důležité definovat funkci try na základě striktních podmínek. Pokud se člen z jiného důvodu než jasně definovaného try nedaří, člen musí stále vyvolat odpovídající výjimku.

 ✔️ Představte vzor try-Parse pro členy, kteří mohou vyvolat výjimky v běžných scénářích, aby se předešlo problémům s výkonem souvisejícím s výjimkami.

 pro metody, které implementují tento model, ✔️ použít předponu try a logický návratový typ.

 pro každého člena pomocí vzoru try-Parse ✔️ poskytněte člena vyvolání výjimky.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
