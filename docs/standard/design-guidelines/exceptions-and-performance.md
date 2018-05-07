---
title: Výjimky a výkonu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfffc2a1c0f607541194a7f51717d5bf8a8537f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-and-performance"></a>Výjimky a výkonu
Jeden běžný problém související s výjimkami je, že pokud se výjimky použijí pro kód, který pravidelně selže, výkon implementace nepřijatelné. Jde o platný problém. Pokud člen, vyvolá výjimku, může být jeho výkon pořadí podle velikosti pomalejší. Je však možné, abyste dosáhli dobrého výkonu při zachování výhradně výjimka pokyny, které zakáže použití kódy chyb. Dva vzory popsaných v této části zjistíte, jak to udělat.  
  
 **X nesmí** z důvodu obavy, že výjimky může ovlivnit výkon negativně používat kódy chyb.  
  
 Pokud chcete zvýšit výkon, je možné použít vzor Tester Doer nebo vzoru zkuste analýzy popsané v následujících dvou částech.  
  
## <a name="tester-doer-pattern"></a>Vzor Tester Doer  
 V některých případech je možné zlepšit výkon člena vyvolávání výjimek porušením člena do dvou. Podívejme se na <xref:System.Collections.Generic.ICollection%601.Add%2A> metodu <xref:System.Collections.Generic.ICollection%601> rozhraní.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 Metoda `Add` způsobí výjimku, pokud kolekce je jen pro čtení. Může se jednat o problém s výkonem ve scénářích, kde je očekávána volání metody, které k selhání často. Jedním ze způsobů zmírnit problém je k ověření, zda kolekce lze zapisovat, než se pokusíte přidat hodnotu.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 Člen používá k testování podmínku, která v našem příkladu je vlastnost `IsReadOnly`, se označuje jako zkušební zařízení. Člen používá k provádění potenciálně aktivační operace, `Add` metoda v našem příkladu se označuje jako doer.  
  
 **✓ ZVAŽTE** Tester Doer vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.  
  
## <a name="try-parse-pattern"></a>Try analýzy vzor  
 Pro rozhraní API velmi náročné na výkon je třeba použít vzor ještě rychlejší než vzoru Tester Doer popsané v předchozí části. Vzor volání pro přizpůsobení název člena, aby dobře definované testovací případ součástí sémantiku člen. Například <xref:System.DateTime> definuje <xref:System.DateTime.Parse%2A> metoda, která vyvolá výjimku, pokud analýza řetězce nezdaří. Také definuje odpovídající <xref:System.DateTime.TryParse%2A> metoda, která se pokusí analyzovat, ale vrací hodnotu false Pokud analýza neúspěšná a vrátí výsledek úspěšné analýzy pomocí `out` parametr.  
  
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
  
 Pokud používáte tento vzor, je důležité určit, zkuste funkce v striktní podmínky. Pokud z nějakého důvodu než dobře definovaný zkuste selže člen, musí člen stále odpovídající výjimku vyvolat.  
  
 **✓ ZVAŽTE** zkuste analýzy vzor pro členy, které může vyvolat výjimky společné scénáře, aby se zabránilo problémům s výkonem souvisejících s výjimkami.  
  
 **PROVEĎTE ✓** použijte předponu "Zkuste" a logickou hodnotu návratový typ pro metody implementace tohoto vzoru.  
  
 **PROVEĎTE ✓** zadejte člena vyvolávání výjimek pro každého člena pomocí vzoru zkuste analýzy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
