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
ms.openlocfilehash: f9fe3045d8bd8b4d625c5cd49bc18574ebb740de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026429"
---
# <a name="exceptions-and-performance"></a>Výjimky a výkon
Jeden společný problém související s výjimkami je, že pokud se výjimky použijí pro kód, který pravidelně selže, výkon implementace nepřijatelná. Toto je platný žádný problém. Pokud člen vyvolá výjimku, jeho výkon a může být řádů pomalejší. Je však možné dosáhnout dobrý výkon při výhradně týkajícími se výjimka pokyny, které zakáže použití se kódy chyb. Dva způsoby, které jsou popsané v této části navrhujeme způsoby, jak to provést.  
  
 **X DO NOT** z důvodu obavy, že výjimky může ovlivnit výkon negativně používat kódy chyb.  
  
 Ke zlepšení výkonu, je možné použít vzor Tester Doer nebo zkuste analýzy vzor, je popsáno v následujících dvou částech.  
  
## <a name="tester-doer-pattern"></a>Vzor Tester Doer  
 Výkon člena vyvolání výjimek v některých případech lze zvýšit tím, že rozkládají člena na dva. Podívejme se <xref:System.Collections.Generic.ICollection%601.Add%2A> metodu <xref:System.Collections.Generic.ICollection%601> rozhraní.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 Metoda `Add` vyvolá výjimku, pokud je kolekce určena jen pro čtení. To může být problém s výkonem ve scénářích, kde je očekávána volání metody, které k selhání často. Jedním ze způsobů pro zmírnění těchto potíží je k ověření, zda kolekce je zapisovatelný, než se pokusíte přidat hodnotu.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 Člen použily k testování podmínku, která je v našem příkladu vlastnost `IsReadOnly`, se označuje jako tester. Člen použil k potenciálně aktivační operaci `Add` metoda v našem příkladu se označuje jako doer.  
  
 **✓ CONSIDER** Tester Doer vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.  
  
## <a name="try-parse-pattern"></a>Try-Parse vzor  
 Pro velmi citlivé na výkon rozhraní API je třeba použít ještě rychlejší vzor než Tester Doer vzor je popsáno v předchozí části. Vzor se volá pro úpravu názvu členu a proveďte jasně definované testovací malá a velká část sémantiku člena. Například <xref:System.DateTime> definuje <xref:System.DateTime.Parse%2A> metodu, která vyvolá výjimku, pokud analýza řetězce selže. Definuje také odpovídající <xref:System.DateTime.TryParse%2A> metodu, která se pokusí analyzovat, ale vrátí false, pokud analýza neúspěšná a vrátí výsledek úspěšné analýzy pomocí `out` parametru.  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 Při použití tohoto modelu, je potřeba definovat funkci zkuste v striktní podmínky. Pokud člen selže z nějakého důvodu než je dobře definovaný try, musí člen stále vyvolat odpovídající výjimky.  
  
 **✓ CONSIDER** zkuste analýzy vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.  
  
 **✓ DO** použijte předponu "Zkuste" a logickou hodnotu návratový typ pro metody implementace tohoto vzoru.  
  
 **✓ DO** zadejte člena vyvolávání výjimek pro každého člena pomocí vzoru zkuste analýzy.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
