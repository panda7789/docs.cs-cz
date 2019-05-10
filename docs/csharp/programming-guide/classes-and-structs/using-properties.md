---
title: Použití vlastnosti - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: 6a929957a0bb512ae4af503ad4b80c9d081764dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582967"
---
# <a name="using-properties-c-programming-guide"></a>Použití vlastností (Průvodce programováním v C#)
Vlastnosti zkombinovat prvky pole a metody. Uživateli objekt vlastnost se zobrazí jako pole, přístup k vlastnosti vyžaduje podle stejné syntaxe. Implementátor třídy, vlastnosti je jeden nebo dva bloky kódu představují [získat](../../../csharp/language-reference/keywords/get.md) přístupového objektu a/nebo [nastavit](../../../csharp/language-reference/keywords/set.md) přistupujícího objektu. Blok kódu pro `get` přístupový objekt se spouští při čtení vlastnosti; kód zablokuje `set` přístupový objekt se spouští při vlastnost je přiřazena nová hodnota. Vlastnost bez `set` přístupový objekt je považován za jen pro čtení. Vlastnost bez `get` přístupový objekt je považován za jen pro zápis. Vlastnost, která má oba přístupové objekty je pro čtení i zápis.  
  
 Na rozdíl od pole vlastnosti nejsou klasifikovaná jako proměnné. Proto nelze předat vlastnost jako [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru.  
  
 Vlastnosti mají celou řadu uplatnění: se může ověřovat data předtím, než změnu; zveřejňovaly můžete transparentně data ve třídě, kterých se tato data ve skutečnosti načítají z nějakého jiného zdroje, jako je například databázi. Při změně dat, jako je například vyvolání události nebo změna hodnoty ostatních polí, můžete provedení akce.  
  
 Vlastnosti jsou deklarované v bloku třídy tak, že zadáte úroveň přístupu pole, za nímž následuje typu vlastnosti, za nímž následuje název vlastnosti a za nímž následuje blok kódu, který deklaruje `get`-přistupujícího objektu a/nebo `set` přistupujícího objektu. Příklad:  
  
 [!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]  
  
 V tomto příkladu `Month` je deklarován jako vlastnost tak, která `set` přístupového objektu můžete Ujistěte se, že `Month` hodnotu od 1 do 12. `Month` Vlastnost používá soukromé pole ke sledování skutečnou hodnotu. Skutečné umístění dat vlastnost se často označuje jako vlastnosti "záložního úložiště." Je běžné, že vlastnosti, které chcete použít privátní pole jako záložního úložiště. Pole je označeno privátní, pokud chcete mít jistotu, že ho můžete změnit jenom pomocí volání vlastnost. Další informace o omezeních veřejné a privátní přístup, najdete v části [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Automaticky implementované vlastnosti poskytují zjednodušenou syntaxi pro jednoduchou vlastnost deklarace. Další informace najdete v tématu [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>Přístupový objekt get  
 Text `get` přistupující objekt podobná signatuře metody. Musí vracet hodnotu typu vlastnosti. Provedení příkazu `get` přístupový objekt je ekvivalentní k čtení hodnoty pole. Například když vracíte soukromé proměnné z `get` přístupového objektu a optimalizace povolena, volání `get` přístupové metody je vložená v kompilátoru, takže neexistuje žádný režijní náklady na volání metody. Nicméně virtuální `get` přístupové metody nemůže být vložená, protože kompilátor nezná v době kompilace, která metoda může být volána ve skutečnosti v době běhu. Tady je `get` přístupový objekt, který vrací hodnotu soukromé pole `name`:  
  
 [!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]  
  
 Při odkazování na vlastnost, s výjimkou jako cílem přiřazení, `get` přístupového objektu je vyvolán načíst hodnotu vlastnosti. Příklad:  
  
 [!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]  
  
 `get` Přístupového objektu musí končit [vrátit](../../../csharp/language-reference/keywords/return.md) nebo [throw](../../../csharp/language-reference/keywords/throw.md) příkazu a ovládací prvek nelze flow mimo tělo přístupového objektu.  
  
 Je špatný styl programování ke změně stavu objektu pomocí `get` přistupujícího objektu. Například následující přístupový objekt vytváří vedlejším účinkem změna pokaždé, když se stav objektu, který `number` pole je přístupné.  
  
 [!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]  
  
 `get` Přístupového objektu lze vrátit hodnotu pole nebo ho compute a vrácení. Příklad:  
  
 [!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]  
  
 V předchozí segment kódu, pokud nelze přiřadit hodnotu `Name` vlastnosti, vrátí hodnotu NA.  
  
## <a name="the-set-accessor"></a>Sada přístupového objektu  
 `set` Přístupový objekt se podobá metodou, jejíž návratový typ je [void](../../../csharp/language-reference/keywords/void.md). Používá implicitní parametr s názvem `value`, jehož typ je typ proměnné. V následujícím příkladu `set` přístupový objekt se přidá do `Name` vlastnost:  
  
 [!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]  
  
 Když přiřadíte hodnotu k vlastnosti, `set` přístupového objektu je vyvolán pomocí argument, který obsahuje novou hodnotu. Příklad:  
  
 [!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]  
  
 Jedná se o chybu použít implicitní parametr název `value`, pro místní deklarace proměnné v `set` přistupujícího objektu.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnosti může být označený jako `public`, `private`, `protected`, `internal`, `protected internal` nebo `private protected`. Tyto modifikátory přístupu definují, jak se uživatelé třídy můžete přistupovat k vlastnosti. `get` a `set` přístupové objekty pro stejnou vlastnost může mít různé přístupu modifikátory přístupu. Například `get` může být `public` povolit přístup jen pro čtení z mimo typ a `set` může být `private` nebo `protected`. Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Vlastnosti mohou být deklarovány jako statická vlastnost s použitím `static` – klíčové slovo. To zpřístupňuje vlastnost volajícím v okamžiku, i v případě, že neexistuje žádná instance třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Vlastnost může být označena jako virtuální vlastnost s použitím [virtuální](../../../csharp/language-reference/keywords/virtual.md) – klíčové slovo. To umožňuje odvozeným třídám přepsat vlastnost chování pomocí [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo. Další informace o těchto možnostech najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Vlastnost přepisování virtuální vlastnosti může být také [zapečetěné](../../../csharp/language-reference/keywords/sealed.md), určení, že odvozené třídy jej již není virtuální. A konečně, lze deklarovat vlastnost [abstraktní](../../../csharp/language-reference/keywords/abstract.md). To znamená, že neexistuje žádná implementace třídy a odvozené třídy musí zapsat vlastní implementaci. Další informace o těchto možnostech najdete v tématu [abstraktní a zapečetěné třídy a členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  Jedná se o chybu použití [virtuální](../../../csharp/language-reference/keywords/virtual.md), [abstraktní](../../../csharp/language-reference/keywords/abstract.md), nebo [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor přistupující objekt z [statické](../../../csharp/language-reference/keywords/static.md) vlastnost.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vlastnosti instance, statické a jen pro čtení. Přijímá název zaměstnance z klávesnice, přírůstky `NumberOfEmployees` 1 a zobrazí zaměstnanec název a číslo.  
  
 [!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak získat přístup k vlastnosti v základní třídě, který je skryt další vlastnost, která má stejný název v odvozené třídě.  
  
 [!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]  
  
 Tady jsou důležité body v předchozím příkladu:  
  
- Vlastnost `Name` odvozené třídy skryje vlastnost `Name` v základní třídě. V takovém případě `new` modifikátor se používá v deklarace vlastností v odvozené třídě:  
  
     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  
  
- Přetypování `(Employee)` slouží k přístupu k skrytá vlastnost v základní třídě:  
  
     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]  
  
     Další informace o skrývání členů, najdete v článku [new – modifikátor](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu dvě třídy `Cube` a `Square`, implementace abstraktní třídy `Shape`a přepsat její abstraktní `Area` vlastnost. Všimněte si, [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor ve vlastnostech. Program přijímá jako vstup na straně a vypočítá oblasti pro hranaté a datové krychle. Také přijímá jako vstup oblasti a vypočítá odpovídající na straně pro hranaté a datové krychle.  
  
 [!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Vlastnosti rozhraní](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)
- [Automaticky implementované vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
