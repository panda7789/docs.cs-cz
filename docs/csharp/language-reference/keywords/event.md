---
title: "event (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords: event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f7e7f9f96714f8988eb91d77c63cc4f017d040f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="event-c-reference"></a>event (Referenční dokumentace jazyka C#)
`event` – Klíčové slovo se používá k deklaraci událost v třídě vydavatele.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarace a vyvolávání událost, která používá <xref:System.EventHandler> jako nadřazený typ delegáta. Příklad kompletní kód, který také ukazuje, jak používat obecná <xref:System.EventHandler%601> delegovat typu a přihlášení k odběru na událost a vytvořte obslužnou rutinu události naleznete v tématu [postupy: publikování událostí tohoto neproporcionální vyplnění na rozhraní .NET Framework pokyny](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-csharp[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]  
  
 Události jsou zvláštní druh vícesměrového vysílání delegáta, který jde volat jenom z ve třídě nebo struktuře, kde jsou deklarovány (třída vydavatel). Pokud ostatní třídy nebo struktury přihlášení k odběru události své metody obslužné rutiny události bude volat, pokud třída vydavatele vyvolá událost. Další informace a příklady kódu najdete v tématu [události](../../../csharp/programming-guide/events/index.md) a [delegáti](../../../csharp/programming-guide/delegates/index.md).  
  
 Události může být označen jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné interní](../../../csharp/language-reference/keywords/protected-internal.md) nebo [privátní chráněné](../../../csharp/language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definovat třídy pro přístup uživatelů k události. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="keywords-and-events"></a>Klíčová slova a události  
 Následující klíčová slova se vztahují na události.  
  
|– Klíčové slovo|Popis|Další informace|  
|-------------|-----------------|--------------------------|  
|[statické](../../../csharp/language-reference/keywords/static.md)|Zpřístupní události pro volající kdykoli, i v případě, že neexistuje žádná instance třídy.|[Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtuální](../../../csharp/language-reference/keywords/virtual.md)|Umožňuje odvozené třídy k potlačení chování událost pomocí [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo.|[Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[zapečetěná](../../../csharp/language-reference/keywords/sealed.md)|Určuje, že odvozené třídy jej již virtuální.||  
|[abstraktní](../../../csharp/language-reference/keywords/abstract.md)|Kompilátor nevygeneruje `add` a `remove` bloky přístupového objektu události a proto odvozené třídy musí obsahovat vlastní implementaci.||  
  
 Událost může být deklarován jako statické událost pomocí [statické](../../../csharp/language-reference/keywords/static.md) – klíčové slovo. To zpřístupňuje událost pro volající kdykoli, i v případě, že neexistuje žádná instance třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Událost může být označený jako virtuální událost pomocí [virtuální](../../../csharp/language-reference/keywords/virtual.md) – klíčové slovo. To umožňuje odvozené třídy k potlačení chování událost pomocí [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo. Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md). Událost přepisování virtuální události může být také [zapečetěné](../../../csharp/language-reference/keywords/sealed.md), která určuje, že odvozené třídy jej již virtuální. Nakonec lze deklarovat událost [abstraktní](../../../csharp/language-reference/keywords/abstract.md), což znamená, že kompilátor nevygeneruje `add` a `remove` bloky přístupového objektu události. Odvozené třídy proto musíte zadat své vlastní implementaci.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Přidat](../../../csharp/language-reference/keywords/add.md)  
 [odebrat](../../../csharp/language-reference/keywords/remove.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Postupy: kombinování delegátů (vícesměroví delegáti)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
