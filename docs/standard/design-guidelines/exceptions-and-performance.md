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
author: KrzysztofCwalina
ms.openlocfilehash: 967692092186b81802a7ab635ea8fe4dbacd49ed
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611514"
---
# <a name="exceptions-and-performance"></a>Výjimky a výkon
Jedním z běžných obav souvisejících s výjimkou je, že pokud jsou výjimky používány pro kód, který rutinně selže, výkon implementace nebude možné přijmout. Toto je platný problém. Když člen vyvolá výjimku, může jeho výkon pomalejit pořadí. Je však možné dosáhnout dobrého výkonu v rámci striktního dodržování pokynů pro výjimky, které zakazují použití kódů chyb. Tento postup popisují dva vzory popsané v této části.

 **X DO NOT** z důvodu obavy, že výjimky může ovlivnit výkon negativně používat kódy chyb.

 Chcete-li zvýšit výkon, je možné použít buď vzorek test-Doer, nebo vzor try-Parse, který je popsán v následujících dvou částech.

## <a name="tester-doer-pattern"></a>Tester – vzor Doer
 V některých případech je možné zvýšit výkon člena s aktivačními výjimkami, a to rozdělením členu na dva. Pojďme se <xref:System.Collections.Generic.ICollection%601.Add%2A> podívat na metodu <xref:System.Collections.Generic.ICollection%601> rozhraní.

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 Metoda `Add` vyvolá, je-li kolekce určena pouze pro čtení. Může se jednat o problém s výkonem ve scénářích, kdy se očekává, že volání metody bude často neúspěšné. Jedním ze způsobů, jak zmírnit problém, je otestovat, jestli je kolekce zapisovatelná, než se pokusíte přidat hodnotu.

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 Člen použitý k otestování podmínky, která v našem příkladu je vlastnost `IsReadOnly`, je označována jako tester. Člen, který se používá k provedení potenciálně vyvolání operace, `Add` metoda v našem příkladu je označována jako Doer.

 **✓ CONSIDER** Tester Doer vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.

## <a name="try-parse-pattern"></a>Vzor try-Parse
 Pro vysoce výkonná rozhraní API je vhodné použít ještě rychlejší model, než je vzor testovacího Doeru popsaný v předchozí části. Vzor volá pro úpravu názvu člena k vytvoření dobře definovaného testovacího případu, který je součástí sémantiky členů. <xref:System.DateTime> Například<xref:System.DateTime.Parse%2A> definuje metodu, která vyvolá výjimku, pokud se analýza řetězce nezdařila. Definuje také odpovídající <xref:System.DateTime.TryParse%2A> metodu, která se pokusí analyzovat, ale vrátí hodnotu false, pokud je analýza neúspěšná a vrátí výsledek úspěšné analýzy `out` pomocí parametru.

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

 **✓ CONSIDER** zkuste analýzy vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.

 **✓ DO** použijte předponu "Zkuste" a logickou hodnotu návratový typ pro metody implementace tohoto vzoru.

 **✓ DO** zadejte člena vyvolávání výjimek pro každého člena pomocí vzoru zkuste analýzy.

 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. pomocí [pokynů pro návrh rozhraní: Konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
