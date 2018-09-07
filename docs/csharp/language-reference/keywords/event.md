---
title: event (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 35a42692bc87da63c69d7ccbce1b49396a84f5a2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068700"
---
# <a name="event-c-reference"></a>event (Referenční dokumentace jazyka C#)
`event` – Klíčové slovo se používá pro deklaraci události ve třídě vydavatele.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat a vyvolat událost, která používá <xref:System.EventHandler> jako nadřazený typ delegáta. Pro příklad úplného kódu, který ukazuje způsob použití obecného <xref:System.EventHandler%601> delegáta typu a jak přihlásit odběr události a vytvořit metodu obslužné rutiny události, najdete v článku [postupy: publikování událostí tohoto neproporcionální vyplnění na .NET Framework – směrnice](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 Události jsou zvláštním druhem vícesměrového vysílání delegát, který lze vyvolat pouze z v rámci třídy nebo struktury, ve kterém jsou deklarovány (třída, vydavatel). Pokud k události registrovat jiné třídy nebo struktury, jejich obslužné rutiny události bude volána po vydavatele třída vyvolá událost. Další informace a příklady kódu naleznete v tématu [události](../../../csharp/programming-guide/events/index.md) a [delegáti](../../../csharp/programming-guide/delegates/index.md).  
  
 Události může být označený jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [interní chráněné](../../../csharp/language-reference/keywords/protected-internal.md) nebo [private, protected](../../../csharp/language-reference/keywords/private-protected.md). Tyto modifikátory přístupu definují, jak se uživatelé třídy mají přístup k události. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="keywords-and-events"></a>Klíčová slova a události  
 Následující klíčová slova se vztahují na události.  
  
|Klíčové slovo|Popis|Další informace|  
|-------------|-----------------|--------------------------|  
|[static](../../../csharp/language-reference/keywords/static.md)|Zpřístupní události volajících v okamžiku, i v případě, že neexistuje žádná instance třídy.|[Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Umožňuje odvozeným třídám přepsat chování události pomocí [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo.|[Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|Určuje, že odvozené třídy, už nejsou virtuální.||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Kompilátor nevygeneruje `add` a `remove` bloky přístupového objektu události a proto odvozené třídy musí poskytovat vlastní implementaci.||  
  
 Události mohou být deklarovány jako statické události pomocí [statické](../../../csharp/language-reference/keywords/static.md) – klíčové slovo. To zpřístupňuje události volajícím v okamžiku, i v případě, že neexistuje žádná instance třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Událost může být označený jako virtuální událost pomocí [virtuální](../../../csharp/language-reference/keywords/virtual.md) – klíčové slovo. To umožňuje odvozeným třídám přepsat chování události pomocí [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo. Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md). Přepisování virtuální událost události může být také [zapečetěné](../../../csharp/language-reference/keywords/sealed.md), která určuje, že odvozené třídy jej již není virtuální. A konečně, lze deklarovat událost [abstraktní](../../../csharp/language-reference/keywords/abstract.md), což znamená, že kompilátor nevygeneruje `add` a `remove` bloky přístupového objektu události. Proto musí zajišťovat odvozené třídy vlastní implementaci.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [add](../../../csharp/language-reference/keywords/add.md)  
- [remove](../../../csharp/language-reference/keywords/remove.md)  
- [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
- [Postupy: kombinování delegátů (vícesměroví delegáti)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
