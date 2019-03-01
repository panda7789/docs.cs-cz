---
title: Event – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Event
- vb.Custom
helpviewer_keywords:
- Event statement [Visual Basic]
- declaring events [Visual Basic], syntax
- Public keyword [Visual Basic], Event statements
- Custom keyword [Visual Basic]
- declarations [Visual Basic], events
- event keyword [Visual Basic]
- WithEvents keyword [Visual Basic], Event statements
- events [Visual Basic], declaring
- ByVal keyword [Visual Basic], Event statements
- events [Visual Basic], custom
- ByRef keyword [Visual Basic], Event statements
- declaring user-defined events
ms.assetid: 306ff8ed-74dd-4b6a-bd2f-e91b17474042
ms.openlocfilehash: 13b1d18592379d7a08e68e84ffba62f1cc977caa
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966070"
---
# <a name="event-statement"></a>Event – příkaz
Deklaruje uživatelem definovanou událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname[(parameterlist)] _  
[ Implements implementslist ]  
' -or-  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname As delegatename _  
[ Implements implementslist ]  
' -or-  
 [ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Custom Event eventname As delegatename _  
[ Implements implementslist ]  
   [ <attrlist> ] AddHandler(ByVal value As delegatename)  
      [ statements ]  
   End AddHandler  
   [ <attrlist> ] RemoveHandler(ByVal value As delegatename)  
      [ statements ]  
   End RemoveHandler  
   [ <attrlist> ] RaiseEvent(delegatesignature)  
      [ statements ]  
   End RaiseEvent  
End Event  
```  
  
## <a name="parts"></a>Součásti  
  
|Část|Popis|  
|---|---|  
|`attrlist`|Volitelné. Seznam atributů, které se vztahují k této události. Více atributů jsou odděleny čárkami. Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").|  
|`accessmodifier`|Volitelné. Určuje, jaký kód může přistupovat k události. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)– jakýkoli kód, který můžete přístup k elementu, který deklaruje se k němu přístup.<br />-   [Chráněné](../../../visual-basic/language-reference/modifiers/protected.md)– pouze pro kód v rámci své třídy nebo z odvozené třídy k němu přístup.<br />-   [Friend –](../../../visual-basic/language-reference/modifiers/friend.md)– pouze pro kód ve stejném sestavení k němu přístup.<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)– pouze kód v elementu, který deklaruje se k němu přístup.<br /> -   [Protected Friend](../../language-reference/modifiers/protected-friend.md)– pouze pro kód v události, třídy odvozené třídy nebo stejného sestavení k němu přístup. <br />- [Privátní chráněné](../../language-reference/modifiers/private-protected.md)– pouze pro kód ve třídě události nebo z odvozené třídy ve stejném sestavení k němu přístup.|  
|`Shared`|Volitelné. Určuje, že tato událost není přidružen k určité instanci třídy nebo struktury.|  
|`Shadows`|Volitelné. Označuje, že tato událost se znovu deklaruje a skryje identicky pojmenovanou programovací prvek, nebo sadu přetížených elementů v základní třídě. Můžete stínové jakýkoli druh element deklarovaný pomocí jakéhokoli druhu.<br /><br /> Stínovaný element je k dispozici v rámci odvozené třídy, která zastiňuje, s výjimkou z kde stínového provozu prvek je přístupný. Například pokud `Private` element zastiňuje prvek základní třídy, kód, který nemá oprávnění k přístupu `Private` element má přístup k elementu základní třídy místo toho.|  
|`eventname`|Povinný parametr. Název události. splňuje standardní zásady vytváření názvů proměnných.|  
|`parameterlist`|Volitelné. Seznam místních proměnných, které představují parametry této události. Je nutné uzavřít [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md) v závorkách.|  
|`Implements`|Volitelné. Označuje, že tato událost implementuje události rozhraní.|  
|`implementslist`|Požadováno pokud `Implements` pochází. Seznam `Sub` postupy se implementuje. Několik procedur se oddělují čárkami:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Každý `implementedprocedure` má následující syntaxi a části:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface` -Vyžaduje. Název rozhraní, třídy nebo struktury obsahující tento postup je implementace.<br />-   `Definedname` -Vyžaduje. Název, podle kterého postupu je definován v `interface`. To nemusí být stejné jako `name`, název, který tento postup používá při implementaci definovaný postupem.|  
|`Custom`|Povinný parametr. Události deklarované jako `Custom` musí definovat vlastní `AddHandler`, `RemoveHandler`, a `RaiseEvent` přistupující objekty.|  
|`delegatename`|Volitelné. Název delegáta, který určuje podpis obslužné rutiny události.|  
|`AddHandler`|Povinný parametr. Deklaruje `AddHandler` přístupový objekt, který určuje příkazy ke spuštění při přidání obslužné rutiny události, buď explicitně pomocí `AddHandler` příkazu nebo implicitně pomocí `Handles` klauzuli.|  
|`End AddHandler`|Povinný parametr. Ukončuje `AddHandler` bloku.|  
|`value`|Povinný parametr. Název parametru.|  
|`RemoveHandler`|Povinný parametr. Deklaruje `RemoveHandler` přístupový objekt, který určuje příkazy ke spuštění při odebrání obslužné rutiny události pomocí `RemoveHandler` příkazu.|  
|`End RemoveHandler`|Povinný parametr. Ukončuje `RemoveHandler` bloku.|  
|`RaiseEvent`|Povinný parametr. Deklaruje `RaiseEvent` přístupový objekt, který určuje příkazy ke spuštění, když se vyvolá událost pomocí `RaiseEvent` příkazu. Tím se obvykle vyvolá seznam delegátů udržuje `AddHandler` a `RemoveHandler` přistupující objekty.|  
|`End RaiseEvent`|Povinný parametr. Ukončuje `RaiseEvent` bloku.|  
|`delegatesignature`|Povinný parametr. Seznam parametrů, která odpovídá parametry vyžadované `delegatename` delegovat. Je nutné uzavřít [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md) v závorkách.|  
|`statements`|Volitelné. Příkazy, které obsahují orgánů `AddHandler`, `RemoveHandler`, a `RaiseEvent` metody.|  
|`End Event`|Povinný parametr. Ukončuje `Event` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Po události je deklarovaná, použijte `RaiseEvent` příkaz pro vyvolání události. Typické události mohou být deklarovány a aktivovaná, jak je znázorněno v následující fragmenty:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
>  Je možné deklarovat argumenty události, stejně jako argumenty procedur, s následujícími výjimkami: události nemůže mít pojmenované argumenty, `ParamArray` argumenty, nebo `Optional` argumenty. Události nemají návratové hodnoty.  
  
 Zpracovat událost, musíte přidružit ho podprogramu obslužné rutiny události pomocí `Handles` nebo `AddHandler` příkazu. Podpisy podprogramu a události se musí shodovat. Zpracování sdílené události, je nutné použít `AddHandler` příkazu.  
  
 Můžete použít `Event` pouze na úrovni modulu. To znamená, *kontextu deklarace* pro událost musí být třída, struktura, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, procedura nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Ve většině případů můžete první syntaxe v oddílu Syntaxe tohoto tématu pro deklarace událostí. Některé scénáře však vyžadují, že máte větší kontrolu nad chováním podrobné události. Poslední syntaxe v oddílu Syntaxe tohoto tématu, který používá `Custom` – klíčové slovo, obsahuje tento ovládací prvek umožňuje definovat vlastní události. Ve vlastní události je zadat přesně co se stane, když kód přidá nebo odebere obslužnou rutinu události do nebo z události nebo když kód vyvolá událost. Příklady najdete v tématu [jak: Deklarování vlastních událostí pro konzervaci paměti](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) a [jak: Deklarování vlastních událostí k zabránění blokování](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá události k počet sekund od 10 do 0. Kód ukazuje několik událostí související metody, vlastnosti a příkazy. Jedná se o `RaiseEvent` příkazu.  
  
 Třída, která vyvolá událost, je zdroj události a metody, které zpracovávají události jsou obslužné rutiny událostí. Zdroj událostí může mít více obslužných rutin událostí, který generuje. Pokud třída vyvolá událost, této události je vyvoláno na každé třídy, která je se rozhodli zpracovávat události pro tuto instanci objektu.  
  
 V příkladu se také používá formuláře (`Form1`) s tlačítkem (`Button1`) a textové pole (`TextBox1`). Když kliknete na tlačítko, prvního textového pole zobrazuje odpočítávání z 10 na 0 sekund. Po uplynutí doby úplné (10 sekund), se zobrazí "Hotovo" prvního textového pole.  
  
 Kód pro `Form1` Určuje počáteční a terminálu stavy formuláře. Také obsahuje kód, spustí se, když jsou vyvolány události.  
  
 Pokud chcete použít tento příklad, otevřením nového projektu Windows Forms. Pak přidejte tlačítko s názvem `Button1` a textové pole s názvem `TextBox1` hlavní formulář s názvem `Form1`. Klikněte pravým tlačítkem myši na formuláři a klikněte na tlačítko **zobrazit kód** otevřete editor kódu.  
  
 Přidat `WithEvents` do části deklarace proměnných `Form1` třídy:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Následující kód přidejte kód pro `Form1`. Nahraďte všechny duplicitní postupy, které mohou existovat, jako například `Form_Load` nebo `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Stisknutím klávesy F5 spusťte z předchozího příkladu a klikněte na tlačítko s popiskem **Start**. Prvního textového pole spustí odpočet sekundy. Po uplynutí doby úplné (10 sekund), se zobrazí "Hotovo" prvního textového pole.  
  
> [!NOTE]
>  `My.Application.DoEvents` Metoda nezpracovává události stejným způsobem jako formulář nemá. Chcete-li povolit tento formulář pro zpracování událostí přímo, můžete použít multithreadingu. Další informace najdete v tématu [dělení na spravovaná vlákna](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Viz také:
- [Příkaz RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Postupy: Deklarování vlastních událostí k zabránění blokování](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
