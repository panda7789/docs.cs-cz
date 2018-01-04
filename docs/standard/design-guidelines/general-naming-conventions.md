---
title: "Obecné zásady vytváření názvů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5e5c09c4db8e65d836c7afc7cb78c1f9e32bab65
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="general-naming-conventions"></a>Obecné zásady vytváření názvů
Tato část popisuje obecné zásady vytváření názvů vztahující se k výběru word pokyny k používání zkratky a zkratky a doporučení na tom, jak zamezit pomocí názvů konkrétní jazyk.  
  
## <a name="word-choice"></a>Výběr aplikace Word  
 **PROVEĎTE ✓** zvolte snadno čitelné identifikátor názvy.  
  
 Například vlastnost s názvem `HorizontalAlignment` je angličtina srozumitelnější než `AlignmentHorizontal`.  
  
 **PROVEĎTE ✓** upřednostnit čitelnost přes jako stručný výtah.  
  
 Název vlastnosti `CanScrollHorizontally` je lepší, než `ScrollableX` (skrytého odkaz na ose x).  
  
 **X nesmí** použít podtržítka, pomlčky nebo jiné nealfanumerické znaky.  
  
 **X nesmí** použijte Maďarská zápis.  
  
 **X nepoužívejte** pomocí identifikátorů, které je v konfliktu s slov široce používá programovací jazyky.  
  
 Podle pravidla 4 z specifikace CLS (Common Language) musíte zadat všechny jazyky kompatibilní mechanismus, který umožňuje přístup k pojmenované položky, které používají klíčové slovo daného jazyka jako identifikátor. C#, například používá znak jako mechanismus řídicí v tomto případě @. Je však stále vhodné se vyhnout běžné klíčová slova, protože je mnohem obtížnější pro použití metody s řídicí sekvence než jeden bez ní.  
  
## <a name="using-abbreviations-and-acronyms"></a>Pomocí zkratky a zkratky  
 **X nesmí** použít zkratky nebo staženiny jako součást identifikátoru názvy.  
  
 Například použít `GetWindow` místo `GetWin`.  
  
 **X nesmí** žádné režim, které nejsou široce používaný a to i v případě, že jsou pouze v případě, že je nutné použít.  
  
## <a name="avoiding-language-specific-names"></a>Zamezení názvy konkrétní jazyk  
 **PROVEĎTE ✓** používá sémanticky zajímavé názvy namísto klíčová slova specifická pro jazyk pro názvy typů.  
  
 Například `GetLength` je lepší název než `GetInt`.  
  
 **PROVEĎTE ✓** použít obecný název typu CLR, nikoli název konkrétní jazyk, ve výjimečných případech, pokud identifikátor nemá význam sémantického nad rámec jeho typu.  
  
 Například metoda převodu na <xref:System.Int64> by měl být pojmenován `ToInt64`, nikoli `ToLong` (protože <xref:System.Int64> je název CLR jazyka C# – konkrétní alias `long`). Následující tabulka představuje několik základních datových typů pomocí názvy typů CLR (stejně jako odpovídající názvy typů pro C#, Visual Basic a C++).  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte –**|**char**|**SByte –**|  
|**byte**|**Bajtů**|**unsigned char**|**Bajtů**|  
|**short**|**Krátký**|**short**|**Int16**|  
|**ushort**|**UInt16**|**short bez znaménka**|**UInt16**|  
|**int**|**Celé číslo**|**int**|**Int32**|  
|**uint**|**UInt32**|**int bez znaménka**|**UInt32**|  
|**long**|**Dlouhá**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**__int64 bez znaménka**|**UInt64**|  
|**float**|**Jeden**|**float**|**Jeden**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Logická hodnota**|**bool**|**Logická hodnota**|  
|**char**|**Char –**|**wchar_t**|**Char –**|  
|**string**|**Řetězec**|**Řetězec**|**Řetězec**|  
|**object**|**Objekt**|**Objekt**|**Objekt**|  
  
 **PROVEĎTE ✓** použít běžný název, například `value` nebo `item`, místo opakování název typu ve výjimečných případech, pokud identifikátor nemá žádný význam sémantického a typ parametru není důležité.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Pojmenování nové verze stávajících rozhraní API  
 **PROVEĎTE ✓** použijte název podobná staré rozhraní API, při vytváření nové verze existujícího rozhraní API.  
  
 To pomůže zvýrazněte vztah mezi rozhraní API.  
  
 **PROVEĎTE ✓** přednost přidání příponu místo předpony označující novou verzi existujícího rozhraní API.  
  
 To vám pomůže zjišťování při procházení dokumentace, nebo pomocí Intellisense. Stará verze rozhraní API se uspořádají blízko nových rozhraní API, protože většina prohlížečů a Intellisense zobrazí identifikátory v abecedním pořadí.  
  
 **✓ ZVAŽTE** pomocí identifikátor úplně nový, ale smysluplný místo přidávání příponu nebo předponu.  
  
 **PROVEĎTE ✓** používá číselnou příponou se k označení novou verzi existujícího rozhraní API, zvlášť pokud existující název rozhraní API je pouze název, který dává smysl (tj. Pokud je oborový standard) a Pokud Přidání všechny smysluplný přípony (nebo změna názvu) není aplikace možnost ropriate.  
  
 **X nesmí** "Ex" (nebo podobná) používat příponu pro identifikátor ho odlišuje od dřívější verzi rozhraní API stejné.  
  
 **PROVEĎTE ✓** používají "64" příponu zaváděné verze rozhraní API, která pracovat 64bitové celé číslo (dlouhých celých čísel) namísto 32bitové celé číslo. Potřebujete použít tuto metodu, pokud existuje existujícího rozhraní API 32-bit; nedělají nic pro nové rozhraní API s 64bitovou verzi.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
