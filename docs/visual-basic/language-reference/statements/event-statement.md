---
title: Event – příkaz
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
ms.openlocfilehash: d59dc8e7b01612af0e4c8f6c1018269580284c46
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233935"
---
# <a name="event-statement"></a>Event – příkaz
Deklaruje uživatelem definované události.  
  
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
|`attrlist`|Volitelné. Seznam atributů, které se vztahují k této události. Více atributů jsou oddělené čárkami. Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").|  
|`accessmodifier`|Volitelné. Určuje, jaký kód můžete přístup k události. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)– kód, který můžete získat přístup k elementu, který deklaruje se k němu přístup.<br />-   [Chráněné](../../../visual-basic/language-reference/modifiers/protected.md)– pouze kód do své třídy nebo odvozené třídy k němu přístup.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)– pouze pro kód ve stejném sestavení k němu přístup.<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)– jenom kód v elementu, který deklaruje se k němu přístup.<br /> -   [Protected Friend](../../language-reference/modifiers/protected-friend.md)-pouze kód v události třídu, odvozené třídě nebo do stejného sestavení k němu přístup. <br />- [Privátní chráněné](../../language-reference/modifiers/private-protected.md)-pouze kód v události nebo odvozená třída ve stejném sestavení k němu přístup.|  
|`Shared`|Volitelné. Určuje, že tato událost není spojen s konkrétní instanci třídu nebo strukturu.|  
|`Shadows`|Volitelné. Označuje, že tato událost redeclares a skryje stejně jako s názvem programovací prvek, nebo sadu přetížené elementů v základní třídě. Můžete stínové jakýkoli druh deklarovaný element s jakéhokoli jiného typu.<br /><br /> Element stíněné je k dispozici v rámci odvozené třídy, stín, s výjimkou z kde element stínového provozu je nedostupná. Například pokud `Private` element shadows element základní třídy, kód, který nemá oprávnění k přístupu `Private` element přistupuje k prvku základní třídy místo.|  
|`eventname`|Požadováno. Název události; dodržovat standardní zásady vytváření názvů proměnných.|  
|`parameterlist`|Volitelné. Seznam lokální proměnné, které představují parametry této události. Je nutné uzavřít [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md) v závorkách.|  
|`Implements`|Volitelné. Označuje, že tato událost implementuje událost rozhraní.|  
|`implementslist`|Požadováno pokud `Implements` pochází. Seznam `Sub` postupy se implementuje. Několik procedur se oddělují čárkami:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Každý `implementedprocedure` má následující syntaxe a částí:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface` -Vyžaduje. Název rozhraní, třídu nebo strukturu obsahující tento postup je implementace.<br />-   `Definedname` -Vyžaduje. Název, podle kterého postupu je definována v `interface`. To nemusí být stejný jako `name`, název, který tento postup používá k implementaci definovaný postupem.|  
|`Custom`|Požadováno. Události deklarované jako `Custom` musí definovat vlastní `AddHandler`, `RemoveHandler`, a `RaiseEvent` přistupující objekty.|  
|`delegatename`|Volitelné. Název delegáta, který určuje podpis obslužných rutin událostí.|  
|`AddHandler`|Požadováno. Deklaruje `AddHandler` přistupujícího objektu, který určuje příkazy provést při přidání obslužné rutiny události, buď explicitně pomocí `AddHandler` příkaz nebo implicitně pomocí `Handles` klauzule.|  
|`End AddHandler`|Požadováno. Ukončí `AddHandler` bloku.|  
|`value`|Požadováno. Název parametru.|  
|`RemoveHandler`|Požadováno. Deklaruje `RemoveHandler` přistupujícího objektu, který určuje příkazy má provést při obslužné rutiny události odebrán pomocí `RemoveHandler` příkaz.|  
|`End RemoveHandler`|Požadováno. Ukončí `RemoveHandler` bloku.|  
|`RaiseEvent`|Požadováno. Deklaruje `RaiseEvent` přistupujícího objektu, který určuje příkazy má provést při vyvolání události pomocí `RaiseEvent` příkaz. Obvykle to vyvolá seznam delegátů udržované `AddHandler` a `RemoveHandler` přistupující objekty.|  
|`End RaiseEvent`|Požadováno. Ukončí `RaiseEvent` bloku.|  
|`delegatesignature`|Požadováno. Seznam parametrů, který odpovídá parametry vyžadované `delegatename` delegovat. Je nutné uzavřít [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md) v závorkách.|  
|`statements`|Volitelné. Příkazy, které obsahují těla z `AddHandler`, `RemoveHandler`, a `RaiseEvent` metody.|  
|`End Event`|Požadováno. Ukončí `Event` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Jakmile bylo deklarováno událost, použijte `RaiseEvent` příkaz k vyvolání události. Typické události mohou být deklarován a vyvolá, jak je znázorněno v následující fragmenty:  
  
 [!code-vb[VbVbalrEvents#13](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_1.vb)]  
  
> [!NOTE]
>  Argumenty událostí můžou deklarovat, stejným způsobem jako argumenty procedur, s následujícími výjimkami: události nemůže mít název argumenty, `ParamArray` argumenty, nebo `Optional` argumenty. Události nemají návratové hodnoty.  
  
 Zpracovat události, je třeba ji přidružit k podprogramu obslužných rutin událostí pomocí `Handles` nebo `AddHandler` příkaz. Podpisy podprogramu a události se musí shodovat. Zpracování sdílené události, je nutné použít `AddHandler` příkaz.  
  
 Můžete použít `Event` jenom na úrovni modulu. To znamená *deklarace kontextu* pro událost musí být třída, struktura, modul nebo rozhraní a nemůže být zdrojový soubor, obor názvů, postup nebo bloku. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Ve většině situací můžete první syntaxe v syntaxi části tohoto tématu pro deklarace událostí. Některé scénáře vyžadují ale, že máte větší kontrolu nad chováním podrobné události. Poslední syntaxe v části Syntaxe Toto téma, které používá `Custom` – klíčové slovo, obsahuje tento ovládací prvek tím, že vám definovat vlastní události. Vlastní události je zadat přesně co se stane, když kód přidá nebo odebere obslužnou rutinu do nebo z události, nebo když kód vyvolá událost. Příklady najdete v tématu [postup: deklarovat vlastní událostí pro konzervaci paměti](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) a [postupy: deklarace vlastních událostí k vyhnout blokování](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá události počítat dolů sekund z 10 na hodnotu 0. Kód ukazuje několik událostí související metody, vlastnosti a příkazy. To zahrnuje `RaiseEvent` příkaz.  
  
 Třída, která vyvolá událost, je zdroj události a jsou metody, které zpracovat událost obslužné rutiny událostí. Zdroje událostí může mít více obslužných rutin pro události, které generuje. Pokud třída vyvolá událost, že událost se vyvolá při každou třídu, která se rozhodl zpracovat události pro tuto instanci objektu.  
  
 V příkladu se rovněž používá formulář (`Form1`) s tlačítkem na (`Button1`) a textového pole (`TextBox1`). Když kliknete na tlačítko, textové pole první zobrazí odpočítávání z 10 na 0 sekund. Po uplynutí doby úplné (10 sekund), zobrazí první textové pole, "Hotovo".  
  
 Kód pro `Form1` Určuje počáteční a terminálu stavy formuláře. Obsahuje taky kód spustit, když jsou vyvolány události.  
  
 Chcete-li použít tento příklad, otevřete nový projekt Windows Forms. Pak přidejte tlačítko s názvem `Button1` a textové pole s názvem `TextBox1` hlavní formulář s názvem `Form1`. Klikněte pravým tlačítkem formuláři a klikněte na tlačítko **kód zobrazení** otevření editoru kódu.  
  
 Přidat `WithEvents` do části deklarace proměnné `Form1` třídy:  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_2.vb)]  
  
 Přidejte následující kód pro kód pro `Form1`. Nahraďte všechny duplicitní postupy, které mohou existovat, jako například `Form_Load` nebo `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_3.vb)]  
  
 Stisknutím klávesy F5 spusťte předchozí příklad a klikněte na tlačítko s názvem bez přípony **spustit**. První textové pole začne počítat dolů sekundách. Po uplynutí doby úplné (10 sekund), zobrazí první textové pole, "Hotovo".  
  
> [!NOTE]
>  `My.Application.DoEvents` Metoda nezpracovává události stejným způsobem, nemá formuláře. Chcete-li povolit tento formulář pro zpracování událostí přímo, můžete použít více vláken. Další informace najdete v tématu [zřetězení](../../programming-guide/concepts/threading/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkaz RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)  
 [Postupy: Deklarování vlastních událostí k zabránění blokování](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
