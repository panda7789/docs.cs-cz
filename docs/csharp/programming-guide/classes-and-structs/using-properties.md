---
title: Použití vlastností (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: f0d470d2c38a07db9a936fc645b7a97aa12a7f84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-properties-c-programming-guide"></a>Použití vlastností (Průvodce programováním v C#)
Vlastnosti kombinovat aspektů pole a metody. Uživateli objektu, zdá být pole, vlastnosti přístupu k vlastnosti vyžaduje stejná syntaxe. Implementátor třídy, vlastnosti je jeden nebo dva bloky kódu představující [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu nebo [nastavit](../../../csharp/language-reference/keywords/set.md) přistupujícího objektu. Blok kódu pro `get` přistupujícího objektu je spuštěn, když je vlastnost číst; blokovat kód pro `set` přistupujícího objektu je spuštěn, když vlastnost je přiřazena nová hodnota. Vlastnost bez `set` přistupujícího objektu je považován za jen pro čtení. Vlastnost bez `get` přistupujícího objektu je považován za jen pro zápis. Vlastnost, která má oba přístupových objektů je pro čtení a zápis.  
  
 Na rozdíl od polí a vlastností nejsou klasifikovaný proměnné. Proto nelze předat jako vlastnost [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr.  
  
 Vlastnosti mají mnoho používá: jejich můžete ověřit data před povolením změnu; transparentně se můžou zpřístupnit data pro třídu, pokud je ve skutečnosti načíst data ze jiný zdroj, například do databáze; jejich zajištění může trvat akce při změně dat, jako je například vyvolání události nebo změně hodnoty nebo jiné pole.  
  
 Vlastnosti jsou deklarované v bloku třída zadáním úroveň přístupu tohoto pole, následovaný typem vlastnosti, a název vlastnosti a následuje blok kódu, který deklaruje `get`-přistupujícího objektu nebo `set` přistupujícího objektu. Příklad:  
  
 [!code-csharp[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_1.cs)]  
  
 V tomto příkladu `Month` je deklarován jako vlastnost, která `set` přistupující objekt můžete Ujistěte se, že `Month` hodnota mezi 1 a 12. `Month` Vlastnost používá soukromé pole ke sledování skutečnou hodnotu. Skutečné umístění dat vlastnost se často označuje jako vlastnosti "zálohování úložiště." Je běžné pro vlastnosti, které chcete používat privátní pole jako úložiště zálohování. Pokud chcete mít jistotu, že ho lze změnit pouze voláním vlastnost privátní je označeno pole. Další informace o omezení přístupu veřejné a privátní najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Automaticky implementované vlastnosti poskytují zjednodušenou syntaxi pro jednoduché vlastnosti deklarací. Další informace najdete v tématu [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>Přistupující objekt get  
 Text `get` přistupujícího objektu podobá se metodu. Musí vracet hodnoty typu vlastnost. Provádění `get` přistupujícího objektu je ekvivalentní čtení hodnoty pole. Například když vracíte soukromé proměnné z `get` přistupujícího objektu a optimalizace, které jsou povolené, volání `get` metoda přistupujícího objektu je vložená kompilátorem, takže neexistuje žádný režijní náklady na volání metody. Však virtuální `get` metoda přistupujícího objektu nemůže být vloženou obslužnou, protože kompilátor nebude vědět, v době kompilace, která metoda může být volána ve skutečnosti za běhu. Následuje `get` přistupujícího objektu, která vrátí hodnotu pole private `name`:  
  
 [!code-csharp[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_2.cs)]  
  
 Když odkazujete vlastnost, s výjimkou jako cíl přiřazení, `get` přistupujícího objektu je volána načíst hodnotu vlastnosti. Příklad:  
  
 [!code-csharp[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_3.cs)]  
  
 `get` Přistupujícího objektu musí končit [vrátit](../../../csharp/language-reference/keywords/return.md) nebo [throw](../../../csharp/language-reference/keywords/throw.md) údajů a řízení nelze toku vypnout textu přistupujícího objektu.  
  
 Je chybný stylu programování na změnu stavu objektu pomocí `get` přistupujícího objektu. Například následující přistupujícího objektu vytváří vedlejším účinkem pokaždé, když změny stavu objektu, který `number` pole je přístupné.  
  
 [!code-csharp[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_4.cs)]  
  
 `get` Přistupujícího objektu lze vrátit hodnotu pole nebo ho výpočetní a obnoví v něm. Příklad:  
  
 [!code-csharp[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_5.cs)]  
  
 V předchozí segment kódu, pokud nepřiřadíte hodnota `Name` vlastnost, vrátí hodnotu NA.  
  
## <a name="the-set-accessor"></a>Sada přístupového objektu  
 `set` Přistupujícího objektu vypadá takto: metoda, jejíž návratový typ [void](../../../csharp/language-reference/keywords/void.md). Použije implicitní parametr s názvem `value`, jejichž typ je typ vlastnosti. V následujícím příkladu `set` přistupujícího objektu je přidán do `Name` vlastnost:  
  
 [!code-csharp[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_6.cs)]  
  
 Přiřadíte-li hodnotu pro vlastnost, `set` přistupujícího objektu je vyvolán pomocí argument, který poskytuje novou hodnotu. Příklad:  
  
 [!code-csharp[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_7.cs)]  
  
 Jedná se o chybu pro použití názvu implicitní parametr `value`, pro místní deklarace proměnné v `set` přistupujícího objektu.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnosti může být označen jako `public`, `private`, `protected`, `internal`, `protected internal` nebo `private protected`. Tyto modifikátory přístupu definovat třídy pro přístup uživatelů vlastnost. `get` a `set` přístupových objektů pro stejnou vlastnost může mít jiný přístup modifikátory. Například `get` může být `public` povolit přístup jen pro čtení z mimo typu a `set` může být `private` nebo `protected`. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Vlastnost může být deklarován jako pomocí statické vlastnosti pomocí `static` – klíčové slovo. To zpřístupňuje vlastnost pro volající kdykoli, i v případě, že neexistuje žádná instance třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Vlastnosti mohou být označeny jako virtuální vlastnost pomocí [virtuální](../../../csharp/language-reference/keywords/virtual.md) – klíčové slovo. To umožňuje odvozené třídy k potlačení chování vlastnost pomocí [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo. Další informace o těchto možnostech najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Vlastnost přepisování virtuální vlastnosti může být také [zapečetěné](../../../csharp/language-reference/keywords/sealed.md), určení, že odvozené třídy jej již virtuální. Nakonec lze deklarovat vlastnost [abstraktní](../../../csharp/language-reference/keywords/abstract.md). To znamená, že neexistuje žádná implementace ve třídě a odvozené třídy musíte napsat vlastní implementaci. Další informace o těchto možnostech najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  Jedná se o chybu používat [virtuální](../../../csharp/language-reference/keywords/virtual.md), [abstraktní](../../../csharp/language-reference/keywords/abstract.md), nebo [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor na přistupující objekt služby [statické](../../../csharp/language-reference/keywords/static.md) vlastnost.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vlastnosti instance, statické a jen pro čtení. Přijímá jméno zaměstnance z klávesnice, zvýší `NumberOfEmployees` 1 a zobrazí zaměstnanec název a číslo.  
  
 [!code-csharp[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_8.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak získat přístup k vlastnosti v základní třídu, která je skrytý na základě další vlastnost, která má stejný název v odvozené třídě.  
  
 [!code-csharp[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_9.cs)]  
  
 Tady jsou důležité body v předchozím příkladu:  
  
-   Vlastnost `Name` v odvozené třídě skryje vlastnost `Name` v základní třídě. V takovém případě `new` modifikátor se používá v deklaraci vlastnosti v odvozené třídě:  
  
     [!code-csharp[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_10.cs)]  
  
-   Přetypování `(Employee)` se používá pro přístup k vlastnost skryté v základní třídě:  
  
     [!code-csharp[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_11.cs)]  
  
     Další informace o skrývání členy, najdete v článku [new – modifikátor](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu dvě třídy `Cube` a `Square`, implementovat abstraktní třídu, `Shape`a přepsat její abstraktní `Area` vlastnost. Všimněte si použití [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor ve vlastnostech. Program, přijímá jako vstup na straně a vypočítá oblasti pro hranaté a datové krychle. Také přijímá oblasti jako vstup a vypočítá odpovídající straně hranaté a datové krychle.  
  
 [!code-csharp[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_12.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Vlastnosti rozhraní](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
 [Automaticky implementované vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
