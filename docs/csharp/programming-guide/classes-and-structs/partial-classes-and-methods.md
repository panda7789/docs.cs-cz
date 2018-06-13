---
title: Částečné třídy a metody (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: d257846821f14a377c505099e38971dd5d8a297a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172435"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Částečné třídy a metody (Průvodce programováním v C#)
Je možné rozdělit definice [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md), [rozhraní](../../../csharp/language-reference/keywords/interface.md) nebo metoda přes dvě nebo více zdrojových souborů. Každý zdrojový soubor obsahuje oddíl definice typ nebo metoda a všechny části spojují během kompilace aplikace.  
  
## <a name="partial-classes"></a>Částečné třídy  
 Při rozdělování definice třídy je žádoucí existuje několik situací:  
  
-   Při práci na velkých projektech, šíří třídu po samostatné soubory umožňuje více programátorům práci ve stejnou dobu.  
  
-   Při práci se zdrojem automaticky generované, kód můžete přidat do třídy bez nutnosti opětného vytváření zdrojový soubor. Visual Studio použije tento přístup při vytváření Windows Forms, kódu obálky webové služby a tak dále. Můžete vytvořit kód, který používá tyto třídy, aniž by bylo nutné upravit soubor vytvořený pomocí sady Visual Studio.  
  
-   Rozdělení definice třídy, použijte [částečné](../../../csharp/language-reference/keywords/partial-type.md) – klíčové slovo modifikátoru, jak je vidět tady:  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 `partial` – Klíčové slovo označuje, že dalších částí třída, struktura, nebo rozhraní lze definovat v oboru názvů. Musíte použít všechny části `partial` – klíčové slovo. Všechny části musí být k dispozici v kompilaci čas poslední typ formuláře. Všechny části musí mít stejné usnadnění jako `public`, `private`a tak dále.  
  
 Libovolnou část je deklarovaná abstraktní, celý typ se považuje abstraktní. Pokud některou část deklarována zapečetěné, pak celý typ je považován za zapečetěná. Pokud některou část deklaruje základní typ, dědí celou typ třídy.  
  
 Všechny součásti, které zadejte základní třídu, musíte souhlasit, ale částí, které vynechejte základní třídu stále dědění základního typu. Části můžete zadat různé základní rozhraní a typ konečné implementuje všechna rozhraní uvedené podle částečné deklarace. Všechny třída, struktura nebo členové rozhraní, které jsou deklarované v definici částečné jsou k dispozici pro všechny ostatní části. Poslední typ je kombinace všechny části v době kompilace.  
  
> [!NOTE]
>  `partial` Modifikátor není k dispozici v deklaracích delegáta nebo výčet.  
  
 Následující příklad ukazuje, že vnořené typy mohou být částečné, i když není zadaný typ, že jsou vnořené do částečné sám sebe.  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 Při kompilaci jsou sloučeny atributy definicí partial-type. Zvažte například následující deklarace:  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 Jsou ekvivalentní následující deklarace:  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 Toto jsou slučovány z všech definic partial-type:  
  
-   XML – komentáře  
  
-   rozhraní  
  
-   Parametr obecného typu atributy  
  
-   class – atributy  
  
-   členové  
  
 Zvažte například následující deklarace:  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 Jsou ekvivalentní následující deklarace:  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a>Omezení  
 Existuje několik pravidla při práci se definice pro třídu:  
  
-   Všechny definice typu partial určené jako součásti stejného typu musí být upravena se `partial`. Například následující deklarace třídy vygenerovat chybu:  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   `partial` Modifikátoru může vyskytovat pouze bezprostředně před klíčová slova `class`, `struct`, nebo `interface`.  
  
-   Vnořené částečné typy jsou povoleny v definicích partial-type, jak je znázorněno v následujícím příkladu:  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   Všechny definice typu partial určené jako součásti stejného typu musí být definovaný ve stejném sestavení a stejné modul (soubor .exe nebo .dll). Částečné definice nemůžou zahrnovat více modulů.  
  
-   Název třídy a parametry obecného typu musí odpovídat na všechny definice partial-type. Obecné typy může být částečné. Každá částečné deklarace, musíte použít stejné názvy parametrů ve stejném pořadí.  
  
-   Následující klíčová slova v definici typu partial jsou nepovinné, ale pokud je k dispozici na jednu definici partial typu, nelze v konfliktu s klíčová slova v jiné definici částečné pro stejný typ zadaný:  
  
    -   [public](../../../csharp/language-reference/keywords/public.md)  
  
    -   [private](../../../csharp/language-reference/keywords/private.md)  
  
    -   [protected](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [internal](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   base – třída  
  
    -   [nové](../../../csharp/language-reference/keywords/new.md) – modifikátor (vnořené částí)  
  
    -   Obecná omezení  
  
         Další informace najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="example-1"></a>Příklad 1  
  
### <a name="description"></a>Popis  
 V následujícím příkladu, pole a konstruktoru třídy `CoOrds`, jsou deklarované v jedné definice částečné třídy a člen, `PrintCoOrds`, je v jiné definici třídu deklarovat.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a>Příklad 2  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje, že můžete také vyvíjet částečné struktury a rozhraní.  
  
### <a name="code"></a>Kód  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a>Částečné metody  
 Částečné metody mohou obsahovat částečné třídě nebo struktuře. Jeden součástí třídy obsahuje podpis metody. Volitelné implementace může být definovány v části stejné nebo jiné části. Pokud je implementace není zadaný, poté metoda a všechna volání do metody odstraněny při kompilaci.  
  
 Částečné metody povolit implementátor jednou ze součástí sady třídu definovat metodu, podobné události. Implementátor na straně druhé třídy se můžete rozhodnout, zda implementovat metodu, nebo ne. Pokud metoda není implementována, pak kompilátor odebere metodu podpisu a všechna volání do metody. Volání metody, včetně všechny výsledky, které by tomu bylo ze zkušební verze argumentů ve voláních, nemají žádný vliv za běhu. Proto žádný kód v třídu můžete volně použít částečné metodu, i v případě, že není součástí implementace. Žádné chyby kompilace nebo běhu dojde, pokud metoda je volána, ale není implementováno.  
  
 Částečné metody jsou užitečné zejména jako způsob, jak přizpůsobit generovaného kódu. Povolí pro název metody a podpis jako vyhrazené, tak, aby generovaného kódu můžete volat metodu ale vývojář může rozhodnout, zda chcete implementovat metodu. Částečné třídy, jako je mnohem částečné metody povolit kód vytvořený generátor kódu a kód vytvořený vývojářem, který spolupracovat bez běhové náklady na lidské.  
  
 Deklarace částečné metody se skládá ze dvou částí: definice a implementaci. To může být v samostatné části částečné třídy, nebo ve stejné části. Pokud není k dispozici žádná deklarace implementace, pak kompilátor optimalizuje rychle i definování deklarace a všechna volání do metody.  
  
```csharp  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   Částečné metody deklarace musí začínat kontextové klíčové slovo [částečné](../../../csharp/language-reference/keywords/partial-type.md) a musí vracet metodu [void](../../../csharp/language-reference/keywords/void.md).  
  
-   Částečné metody může mít [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md) nebo [ref](../../../csharp/language-reference/keywords/ref.md) ale ne [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry.  
  
-   Částečné metody jsou implicitně [privátní](../../../csharp/language-reference/keywords/private.md), a proto nemůže být [virtuální](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Částečné metody nemůže být [extern](../../../csharp/language-reference/keywords/extern.md), protože přítomnost text určuje, zda jsou definování nebo implementace.  
  
-   Částečné metody může mít [statické](../../../csharp/language-reference/keywords/static.md) a [unsafe](../../../csharp/language-reference/keywords/unsafe.md) modifikátory.  
  
-   Částečné metody mohou být obecný. Omezení se umístí definující deklarace částečné metody a může volitelně opakována na implementující jeden. Parametr a zadejte názvy parametrů nemusí být stejný v implementující deklaraci jako definující jeden.  
  
-   Můžete provést [delegovat](../../../csharp/language-reference/keywords/delegate.md) částečné metodu, která byla definována a implementována, ale není částečné metodu, která pouze byla definována.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)  
 [partial (typ)](../../../csharp/language-reference/keywords/partial-type.md)
