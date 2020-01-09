---
title: Rozšiřující metody
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 2578fbacecd9fe790f72e828b455e8983b1298d3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709358"
---
# <a name="extension-methods"></a>Rozšiřující metody
Rozšiřující metody jsou funkce jazyka, která umožňuje volání statických metod pomocí syntaxe volání metody instance. Tyto metody musí mít alespoň jeden parametr, který představuje instanci, na které je metoda provozována.  
  
 Třída, která definuje takové metody rozšíření, je označována jako třída "sponzor" a musí být deklarována jako statická. Chcete-li použít rozšiřující metody, musí jedna importovat obor názvů definující třídu sponzor.  
  
 **X AVOID** frivolously definování rozšiřující metody, hlavně na typech nevlastníte.  
  
 Pokud vlastníte zdrojový kód typu, zvažte místo toho použití regulárních metod instance. Pokud nevlastníte a chcete přidat metodu, buďte velmi opatrní. Liberalizace použití rozšiřujících metod má potenciál nepotřebných rozhraní API typů, která nebyla navržena pro tyto metody.  
  
 **✓ CONSIDER** metodami rozšíření v některém z následujících scénářů:  
  
- Pro poskytování pomocných funkcí, které jsou relevantní pro každou implementaci rozhraní, pokud se tyto funkce dají zapsat v rámci základního rozhraní. Důvodem je skutečnost, že konkrétní implementace nemohou být jinak přiřazeny rozhraním. Například operátory `LINQ to Objects` jsou implementovány jako metody rozšíření pro všechny typy <xref:System.Collections.Generic.IEnumerable%601>. Jakékoli implementace `IEnumerable<>` tedy automaticky podporují LINQ.  
  
- Když metoda instance by zavedla závislost na některém typu, ale taková závislost by mohla přerušit pravidla správy závislostí. Například závislost z <xref:System.String> na <xref:System.Uri?displayProperty=nameWithType> není pravděpodobně žádoucí, takže `String.ToUri()` metoda instance vracející `System.Uri` by byl špatným návrhem z perspektivy správy závislostí. Statická rozšiřující metoda `Uri.ToUri(this string str)` vrácení `System.Uri` by byla mnohem lepším návrhem.  
  
 **X AVOID** definování rozšiřující metody na <xref:System.Object?displayProperty=nameWithType>.  
  
 Visual Basic uživatelé nebudou moci volat takové metody pro odkazy na objekty pomocí syntaxe metody rozšíření. Visual Basic nepodporuje volání takových metod, protože v Visual Basic deklarující odkaz jako objekt vynutí, aby všechny vyvolání metod bylo v tomto případě pozdní vazbou (skutečný člen nazvaný je určen za běhu), zatímco vazby na metody rozšíření jsou určeny na čas kompilace (předčasné vázání).  
  
 Všimněte si, že se pravidla vztahují na jiné jazyky, kde se nachází stejné chování vazby, nebo kde nejsou podporované rozšiřující metody.  
  
 **X DO NOT** umístění rozšiřujících metod v jako typ rozšířené o stejný obor názvů, pokud je pro přidání metody do rozhraní nebo správě závislosti.  
  
 **X AVOID** definování dvě nebo více metod rozšíření se stejným podpisem, i v případě, že jsou umístěny v různých oborech názvů.  
  
 **✓ CONSIDER** definování rozšiřující metody v jako typ rozšířené o stejný obor názvů, pokud typ je rozhraní, a pokud rozšiřující metody jsou určené pro použití ve většině nebo všem případů.  
  
 **X DO NOT** definovat rozšiřující metody, které implementují funkce v obory názvů, které jsou obvykle spojené s jinými funkcemi. Místo toho je definujte v oboru názvů přidruženém k funkci, ke které patří.  
  
 **X AVOID** obecné názvy oborů názvů vyhrazený pro metody rozšíření (například "rozšíření"). Místo toho použijte popisný název (například "Routing").  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
