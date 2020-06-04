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
ms.openlocfilehash: a136a517c7ce865b4e1d349270696e2704d61592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404664"
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
  
|Část|Description|  
|---|---|  
|`attrlist`|Nepovinný parametr. Seznam atributů, které se vztahují na tuto událost. Více atributů je odděleno čárkami. [Seznam atributů](attribute-list.md) musíte uzavřít do lomených závorek (" `<` " a " `>` ").|  
|`accessmodifier`|Nepovinný parametr. Určuje, jaký kód má mít přístup k události. Může to být jedna z následujících:<br /><br /> -   [Public](../modifiers/public.md)– jakýkoliv kód, který má přístup k prvku, který ho deklaruje, má k němu přístup.<br />-   [Protected](../modifiers/protected.md)– k němu má přístup jenom kód v rámci své třídy nebo odvozené třídy.<br />-   [Friend](../modifiers/friend.md)– k němu má přístup jenom kód ve stejném sestavení.<br />-   [Private](../modifiers/private.md)– pouze kód v prvku, který ho deklaruje, má k němu přístup.<br /> -   [Chráněný](../modifiers/protected-friend.md)kód jenom pro přítele ve třídě události, odvozená třída nebo stejné sestavení k němu má přístup. <br />- [Soukromý chráněný](../modifiers/private-protected.md)– kód pouze ve třídě události nebo v odvozené třídě ve stejném sestavení má k němu přístup.|  
|`Shared`|Nepovinný parametr. Určuje, že tato událost není přidružena ke konkrétní instanci třídy nebo struktury.|  
|`Shadows`|Nepovinný parametr. Označuje, že tato událost znovu deklaruje a skryje identicky pojmenovaný programový prvek nebo sadu přetížených prvků v základní třídě. Můžete vystínovat jakýkoliv druh deklarovaného prvku s jakýmkoli jiným druhem.<br /><br /> Stínovaný element není k dispozici v odvozené třídě, která ho nastínuje, s výjimkou, kde není k dispozici stínový element. Například pokud `Private` prvek nastínuje element základní třídy, kód, který nemá oprávnění pro přístup k elementu, přistupuje k `Private` elementu základní třídy.|  
|`eventname`|Povinná hodnota. Název události; Následují standardní zásady vytváření názvů proměnných.|  
|`parameterlist`|Nepovinný parametr. Seznam místních proměnných, které reprezentují parametry této události. [Seznam parametrů](parameter-list.md) musí být uzavřen v závorkách.|  
|`Implements`|Nepovinný parametr. Označuje, že tato událost implementuje událost rozhraní.|  
|`implementslist`|Vyžaduje `Implements` se, pokud je zadaný. Seznam `Sub` implementovaných procedur. Více postupů je odděleno čárkami:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Každá `implementedprocedure` z nich má následující syntaxi a části:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`Požadovanou. Název rozhraní, které tato procedura obsahuje, implementuje třídu nebo strukturu.<br />-   `Definedname`Požadovanou. Název, podle kterého je procedura definovaná `interface` . To nemusí být stejné jako `name` název, který tento postup používá k implementaci definované procedury.|  
|`Custom`|Povinná hodnota. Události deklarované jako `Custom` musí definovat vlastní `AddHandler` , `RemoveHandler` a `RaiseEvent` přistupující objekty.|  
|`delegatename`|Nepovinný parametr. Název delegáta, který určuje signaturu obslužné rutiny události.|  
|`AddHandler`|Povinná hodnota. Deklaruje `AddHandler` přistupující objekt, který určuje příkazy, které mají být provedeny při přidání obslužné rutiny události, buď explicitně pomocí `AddHandler` příkazu nebo implicitně pomocí `Handles` klauzule.|  
|`End AddHandler`|Povinná hodnota. Ukončí `AddHandler` blok.|  
|`value`|Povinná hodnota. Názvy parametrů.|  
|`RemoveHandler`|Povinná hodnota. Deklaruje `RemoveHandler` přistupující objekt, který určuje příkazy, které mají být provedeny při odebrání obslužné rutiny události pomocí `RemoveHandler` příkazu.|  
|`End RemoveHandler`|Povinná hodnota. Ukončí `RemoveHandler` blok.|  
|`RaiseEvent`|Povinná hodnota. Deklaruje `RaiseEvent` přistupující objekt, který určuje příkazy, které mají být provedeny při vyvolání události pomocí `RaiseEvent` příkazu. Obvykle vyvolá seznam delegátů udržovaných pomocí `AddHandler` `RemoveHandler` přístupových objektů a.|  
|`End RaiseEvent`|Povinná hodnota. Ukončí `RaiseEvent` blok.|  
|`delegatesignature`|Povinná hodnota. Seznam parametrů, které odpovídají parametrům vyžadovaným `delegatename` delegátem. [Seznam parametrů](parameter-list.md) musí být uzavřen v závorkách.|  
|`statements`|Nepovinný parametr. Příkazy, které obsahují těla `AddHandler` `RemoveHandler` metod, a `RaiseEvent` .|  
|`End Event`|Povinná hodnota. Ukončí `Event` blok.|  
  
## <a name="remarks"></a>Poznámky  
 Po deklaraci události použijte `RaiseEvent` příkaz k vyvolání události. Typickou událost může být deklarována a vyvolána, jak je znázorněno v následujících fragmentech:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
> Argumenty události lze deklarovat stejně jako argumenty procedur, s následujícími výjimkami: události nemohou mít pojmenované argumenty, `ParamArray` argumenty nebo `Optional` argumenty. Události neobsahují návratové hodnoty.  
  
 Chcete-li zpracovat událost, je nutné ji přidružit k podrutině obslužné rutiny události pomocí `Handles` `AddHandler` příkazu nebo. Signatury subrutiny a události se musí shodovat. Chcete-li zpracovat sdílenou událost, musíte použít `AddHandler` příkaz.  
  
 Můžete použít `Event` pouze na úrovni modulu. To znamená, že *kontext deklarace* pro událost musí být třída, struktura, modul nebo rozhraní a nemůže se jednat o zdrojový soubor, obor názvů, proceduru nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).  
  
 Ve většině případů můžete použít první syntaxi v oddílu syntax tohoto tématu pro deklarování událostí. Některé scénáře ale vyžadují, abyste měli větší kontrolu nad podrobná chování události. Poslední syntaxe v oddílu syntax tohoto tématu, která používá `Custom` klíčové slovo, poskytuje tento ovládací prvek, který umožňuje definovat vlastní události. Ve vlastní události přesně určíte, co se stane, když kód přidá nebo odebere obslužnou rutinu události nebo z události nebo když kód vyvolá událost. Příklady naleznete v tématu [How to: deklarovat vlastní události pro zachování paměti](../../programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) a [Postupy: deklarování vlastních událostí, aby se zabránilo zablokování](../../programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá události pro počítání sekund od 10 do 0. Kód ilustruje několik metod, vlastností a příkazů souvisejících s událostmi. To zahrnuje `RaiseEvent` příkaz.  
  
 Třída, která vyvolá událost, je zdrojem události a metody, které zpracovávají události, jsou obslužné rutiny událostí. Zdroj události může mít několik obslužných rutin pro události, které generuje. Když třída vyvolá událost, tato událost je vyvolána na každé třídě, která se rozhodla zpracovávat události pro tuto instanci objektu.  
  
 V příkladu se používá také formulář ( `Form1` ) s tlačítkem ( `Button1` ) a textovým polem ( `TextBox1` ). Když kliknete na tlačítko, zobrazí se v prvním textovém poli odpočítávání od 10 do 0 sekund. Když uplyne celý čas (10 sekund), zobrazí se v prvním textovém poli "Hotovo".  
  
 Kód pro `Form1` Určuje počáteční a koncovou stavy formuláře. Obsahuje také kód spuštěný při vyvolání události.  
  
 Chcete-li použít tento příklad, otevřete nový projekt model Windows Forms. Pak přidejte tlačítko s názvem `Button1` a textové pole s názvem `TextBox1` do hlavního formuláře s názvem `Form1` . Potom klikněte pravým tlačítkem myši na formulář a kliknutím na **Zobrazit kód** otevřete Editor kódu.  
  
 Přidejte `WithEvents` proměnnou do oddílu deklarace `Form1` třídy:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Přidejte následující kód do kódu pro `Form1` . Nahraďte všechny duplicitní procedury, které mohou existovat, například `Form_Load` nebo `Button_Click` .  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Stisknutím klávesy F5 spusťte předchozí příklad a klikněte na tlačítko s názvem **Spustit**. V prvním textovém poli se začne počítat sekundy. Když uplyne celý čas (10 sekund), zobrazí se v prvním textovém poli "Hotovo".  
  
> [!NOTE]
> `My.Application.DoEvents`Metoda nezpracovává události stejným způsobem jako formulář. Chcete-li povolit, aby formulář zpracovával události přímo, můžete použít multithreading. Další informace najdete v tématu [spravovaná vlákna](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Viz také

- [RaiseEvent – příkaz](raiseevent-statement.md)
- [Implements – Příkaz](implements-statement.md)
- [Události](../../programming-guide/language-features/events/index.md)
- [AddHandler – příkaz](addhandler-statement.md)
- [RemoveHandler – příkaz](removehandler-statement.md)
- [Handles](handles-clause.md)
- [Delegate – příkaz](delegate-statement.md)
- [Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Postupy: Deklarování vlastních událostí k zabránění blokování](../../programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Shared](../modifiers/shared.md)
- [Shadows](../modifiers/shadows.md)
