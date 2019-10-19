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
ms.openlocfilehash: ab4ff31cbc7b16e1d0ad8defed18e523c237e10d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583360"
---
# <a name="event-statement"></a>Event – příkaz
Deklaruje uživatelsky definovanou událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
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
  
|Částí|Popis|  
|---|---|  
|`attrlist`|Volitelné. Seznam atributů, které se vztahují na tuto událost. Více atributů je odděleno čárkami. [Seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) je nutné uzavřít do lomených závorek ("`<`" a "`>`").|  
|`accessmodifier`|Volitelné. Určuje, jaký kód má mít přístup k události. Může to být jedna z následujících:<br /><br /> -   [veřejné](../../../visual-basic/language-reference/modifiers/public.md)– jakýkoliv kód, který má přístup k prvku, který ho deklaruje, má k němu přístup.<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)– k němu má přístup jenom kód v rámci své třídy nebo odvozené třídy.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)– k němu má přístup jenom kód ve stejném sestavení.<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)– pouze kód v prvku, který ho deklaruje, má k němu přístup.<br /> -   [chráněný](../../language-reference/modifiers/protected-friend.md)kód jenom pro přítele ve třídě události, odvozená třída nebo stejné sestavení k němu má přístup. <br />- [soukromým chráněným](../../language-reference/modifiers/private-protected.md)kódem ve třídě události nebo v odvozené třídě ve stejném sestavení má k němu přístup.|  
|`Shared`|Volitelné. Určuje, že tato událost není přidružena ke konkrétní instanci třídy nebo struktury.|  
|`Shadows`|Volitelné. Označuje, že tato událost znovu deklaruje a skryje identicky pojmenovaný programový prvek nebo sadu přetížených prvků v základní třídě. Můžete vystínovat jakýkoliv druh deklarovaného prvku s jakýmkoli jiným druhem.<br /><br /> Stínovaný element není k dispozici v odvozené třídě, která ho nastínuje, s výjimkou, kde není k dispozici stínový element. Například pokud `Private` element stínování elementu základní třídy, kód, který nemá oprávnění pro přístup k `Private` elementu, přistupuje k elementu základní třídy namísto.|  
|`eventname`|Požadováno. Název události; Následují standardní zásady vytváření názvů proměnných.|  
|`parameterlist`|Volitelné. Seznam místních proměnných, které reprezentují parametry této události. [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md) musí být uzavřen v závorkách.|  
|`Implements`|Volitelné. Označuje, že tato událost implementuje událost rozhraní.|  
|`implementslist`|Vyžaduje se, pokud je dodána `Implements`. Seznam `Sub`ch procedur, které jsou implementovány. Více postupů je odděleno čárkami:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Každý `implementedprocedure` má následující syntaxi a části:<br /><br /> `interface`. `definedname`<br /><br /> `interface` -    – povinné. Název rozhraní, které tato procedura obsahuje, implementuje třídu nebo strukturu.<br />`Definedname` -    – povinné. Název, podle kterého je procedura definovaná v `interface`. To nemusí být stejné jako `name`, název, který tento postup používá k implementaci definované procedury.|  
|`Custom`|Požadováno. Události deklarované jako `Custom` musí definovat vlastní přístupové objekty `AddHandler`, `RemoveHandler` a `RaiseEvent`.|  
|`delegatename`|Volitelné. Název delegáta, který určuje signaturu obslužné rutiny události.|  
|`AddHandler`|Požadováno. Deklaruje přistupující objekt `AddHandler`, který určuje příkazy, které mají být provedeny při přidání obslužné rutiny události, buď explicitně pomocí příkazu `AddHandler` nebo implicitně pomocí klauzule `Handles`.|  
|`End AddHandler`|Požadováno. Ukončí blok `AddHandler`.|  
|`value`|Požadováno. Název parametru|  
|`RemoveHandler`|Požadováno. Deklaruje přistupující objekt `RemoveHandler`, který určuje příkazy, které mají být provedeny při odebrání obslužné rutiny události pomocí příkazu `RemoveHandler`.|  
|`End RemoveHandler`|Požadováno. Ukončí blok `RemoveHandler`.|  
|`RaiseEvent`|Požadováno. Deklaruje přistupující objekt `RaiseEvent`, který určuje příkazy, které mají být provedeny při vyvolání události pomocí příkazu `RaiseEvent`. Obvykle to vyvolá seznam delegátů udržovaných `AddHandler` a přístupových objektů `RemoveHandler`.|  
|`End RaiseEvent`|Požadováno. Ukončí blok `RaiseEvent`.|  
|`delegatesignature`|Požadováno. Seznam parametrů, které odpovídají parametrům vyžadovaným delegátem `delegatename`. [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md) musí být uzavřen v závorkách.|  
|`statements`|Volitelné. Příkazy, které obsahují těla metod `AddHandler`, `RemoveHandler` a `RaiseEvent`.|  
|`End Event`|Požadováno. Ukončí blok `Event`.|  
  
## <a name="remarks"></a>Poznámky  
 Po deklaraci události použijte příkaz `RaiseEvent` k vyvolání události. Typickou událost může být deklarována a vyvolána, jak je znázorněno v následujících fragmentech:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
> Argumenty události lze deklarovat stejně jako argumenty procedur, s následujícími výjimkami: události nemohou mít pojmenované argumenty, `ParamArray` argumenty nebo `Optional` argumenty. Události neobsahují návratové hodnoty.  
  
 Chcete-li zpracovat událost, je nutné ji přidružit k podrutině obslužné rutiny události pomocí příkazu `Handles` nebo `AddHandler`. Signatury subrutiny a události se musí shodovat. Chcete-li zpracovat sdílenou událost, je nutné použít příkaz `AddHandler`.  
  
 @No__t_0 můžete použít jenom na úrovni modulu. To znamená, že *kontext deklarace* pro událost musí být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Ve většině případů můžete použít první syntaxi v oddílu syntax tohoto tématu pro deklarování událostí. Některé scénáře ale vyžadují, abyste měli větší kontrolu nad podrobná chování události. Poslední syntaxe v oddílu syntax tohoto tématu, která používá klíčové slovo `Custom`, poskytuje tento ovládací prvek tak, že vám umožní definovat vlastní události. Ve vlastní události přesně určíte, co se stane, když kód přidá nebo odebere obslužnou rutinu události nebo z události nebo když kód vyvolá událost. Příklady naleznete v tématu [How to: deklarovat vlastní události pro zachování paměti](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) a [Postupy: deklarování vlastních událostí, aby se zabránilo zablokování](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá události pro počítání sekund od 10 do 0. Kód ilustruje několik metod, vlastností a příkazů souvisejících s událostmi. To zahrnuje příkaz `RaiseEvent`.  
  
 Třída, která vyvolá událost, je zdrojem události a metody, které zpracovávají události, jsou obslužné rutiny událostí. Zdroj události může mít několik obslužných rutin pro události, které generuje. Když třída vyvolá událost, tato událost je vyvolána na každé třídě, která se rozhodla zpracovávat události pro tuto instanci objektu.  
  
 Příklad také používá formulář (`Form1`) s tlačítkem (`Button1`) a textovým polem (`TextBox1`). Když kliknete na tlačítko, zobrazí se v prvním textovém poli odpočítávání od 10 do 0 sekund. Když uplyne celý čas (10 sekund), zobrazí se v prvním textovém poli "Hotovo".  
  
 Kód pro `Form1` Určuje počáteční a koncovou stavy formuláře. Obsahuje také kód spuštěný při vyvolání události.  
  
 Chcete-li použít tento příklad, otevřete nový projekt model Windows Forms. Pak přidejte tlačítko s názvem `Button1` a textové pole s názvem `TextBox1` do hlavního formuláře s názvem `Form1`. Potom klikněte pravým tlačítkem myši na formulář a kliknutím na **Zobrazit kód** otevřete Editor kódu.  
  
 Přidejte `WithEvents` proměnnou do oddílu deklarace `Form1` třídy:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Do kódu pro `Form1` přidejte následující kód. Nahraďte všechny duplicitní procedury, které mohou existovat, například `Form_Load` nebo `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Stisknutím klávesy F5 spusťte předchozí příklad a klikněte na tlačítko s názvem **Spustit**. V prvním textovém poli se začne počítat sekundy. Když uplyne celý čas (10 sekund), zobrazí se v prvním textovém poli "Hotovo".  
  
> [!NOTE]
> Metoda `My.Application.DoEvents` nezpracovává události stejným způsobem jako formulář. Chcete-li povolit, aby formulář zpracovával události přímo, můžete použít multithreading. Další informace najdete v tématu [spravovaná vlákna](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Příkaz RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Řeší](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Postupy: Deklarování vlastních událostí k zabránění blokování](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
