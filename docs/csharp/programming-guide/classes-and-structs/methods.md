---
title: Metody - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: df2d7837217f4267f95ed73948a4eb479cc035c1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244411"
---
# <a name="methods-c-programming-guide"></a>Metody (Průvodce programováním v C#)
Metoda je blok kódu, který obsahuje řadu příkazů. Program způsobí, že příkazů ke spuštění volání metody a zadáním argumentů požadovanou metodu. V jazyce C# se provádí každých provedené instrukce v rámci metody. Metoda Main je vstupním bodem pro každou aplikaci C# a je volána modulem common language runtime (CLR), když se program spustí.  
  
> [!NOTE]
>  Toto téma popisuje pojmenované metody. Informace o anonymní funkce, najdete v části [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Podpisy metod  
 Metody jsou deklarovány v [třídy](../../../csharp/language-reference/keywords/class.md) nebo [– struktura](../../../csharp/language-reference/keywords/struct.md) zadáním úroveň přístupu `public` nebo `private`, volitelné modifikátory jako `abstract` nebo `sealed`, vrácení hodnota, názvu metody a parametry metody. Tyto části jsou společně podpis metody.  
  
> [!NOTE]
>  Návratový typ metody není součástí podpis metody pro účely přetížení metody. Je však součást podpisu metody při určování kompatibility mezi delegáta a, který odkazuje na metodu.  
  
 Parametry metody jsou uzavřeny v závorkách a odděleny čárkami. Prázdných kulatých závorek znamenat, že metoda nevyžaduje žádné parametry. Tato třída obsahuje čtyři metody:  
  
 [!code-csharp[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]  
  
## <a name="method-access"></a>Přístup k metodě  
 Volání metody na objektu je například přístup k poli. Za název objektu přidejte tečku, názvu metody a závorky. Argumenty jsou uvedeny v závorkách a odděleny čárkami. Metody `Motorcycle` třídy proto lze volat jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]  
  
## <a name="method-parameters-vs-arguments"></a>Parametry metody vs. Arguments  
 Definice metody určuje názvy a typy všech parametrů, které jsou požadovány. Při volání kód volá metody, poskytuje konkrétní hodnoty nazývaných argumenty pro každý parametr. Argumenty musí být kompatibilní s typem parametru, ale nebude muset být stejný jako parametr s názvem definovaný v metodě název argumentu (pokud existuje), použít ve volajícím kódu. Příklad:  
  
 [!code-csharp[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Předávání odkaz na vs. Předání hodnotou  
 Ve výchozím nastavení když typ hodnoty se předá metodě, je kopie předán místo samotného objektu. Proto se změny na argument nemají žádný vliv na původní kopii ve volání metody. Můžete předat typ hodnoty podle odkazu s použitím ref – klíčové slovo. Další informace najdete v tématu [předávání parametrů typu hodnoty](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md). Seznam typů předdefinovaných hodnot najdete v tématu [Tabulka typů hodnot](../../../csharp/language-reference/keywords/value-types-table.md).  
  
 Pokud objekt typu odkazu je předán do metody, je předán odkaz na objekt. To znamená metoda přijímá argument, který označuje umístění objektu, ale nikoli samotného objektu. Pokud změníte členem objektu pomocí této reference, změny se projeví v argumentu ve volání metody i v případě, že můžete předat hodnotu v objektu.  
  
 Vytvoříte pomocí typu odkazu `class` – klíčové slovo, jak ukazuje následující příklad.  
  
 [!code-csharp[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]  
  
 Nyní pokud je objekt, který je založen na tomto typu metody, je předán odkaz na objekt. Následující příklad předá objekt typu `SampleRefType` metodě `ModifyObject`.  
  
 [!code-csharp[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]  
  
 V příkladu se v podstatě totéž jako předchozí příklad, předá argumentu podle hodnoty metody. Ale protože odkazový typ se používá, výsledek se liší. Úpravy, které se provádí v `ModifyObject` k `value` pole parametru, `obj`, také změní `value` pole argumentu, `rt`v `TestRefType` metoda. `TestRefType` Metoda zobrazí 33 jako výstup.  
  
 Další informace o tom, jak předat typy odkazů podle odkazu a podle hodnoty, najdete v části [předávání parametrů typu odkazu](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) a [odkazové typy](../../../csharp/language-reference/keywords/reference-types.md).  
  
## <a name="return-values"></a>Návratové hodnoty  
Metody může vrátit hodnotu volajícímu. Pokud návratový typ, typ uveden před název metody není `void`, metoda může vrátit hodnotu pomocí `return` – klíčové slovo. Příkaz s `return` – klíčové slovo následované hodnotu, která odpovídá návratový typ, vrátí tuto hodnotu volajícímu metody. 

Hodnota může být vrácen volajícímu hodnota nebo, počínaje C# 7.0, [odkazem](ref-returns.md). Hodnoty jsou vráceny volajícímu podle odkazu, pokud `ref` – klíčové slovo se používá v podpisu metody a postupuje každý `return` – klíčové slovo. Například následující příkaz podpis a vrátí metodu signalizovat, že metoda vrací názvy proměnných `estDistance` s odkazem na volajícího.

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

`return` – Klíčové slovo také zastaví provádění metody. Pokud je návratový typ `void`, `return` příkaz bez hodnoty je stále užitečná pro zastavení provádění metody. Bez `return` – klíčové slovo, metoda se zastaví provádění dosáhne konce bloku kódu. Metody s jiný než void vrací typ jsou nutné k použití `return` – klíčové slovo vrátit hodnotu. Například tyto dvě metody použít `return` – klíčové slovo do vrací celá čísla:  
  
 [!code-csharp[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]  
  
 Na používání hodnoty vrátil z metody, můžete použít volání metody volání metody samotný kdekoli, že by stačit hodnotu stejného typu. Můžete také přiřadit návratovou hodnotu proměnné. Například následující dva příklady provedení stejného cíle:  
  
 [!code-csharp[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]  
  
 [!code-csharp[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]  
  
 Použití místní proměnné, v tomto případě `result`pro ukládání hodnota je volitelná. To může pomoci čitelnost kódu nebo může být nezbytné, pokud je potřeba uložit původní hodnoty argumentu pro celý rozsah metody.  

Pokud chcete použít hodnotu vrácený odkazem z metody, je třeba deklarovat [lokální proměnná podle odkazu](ref-returns.md#ref-locals) proměnnou, pokud máte v úmyslu změnit jeho hodnotu. Například pokud `Planet.GetEstimatedDistance` metoda vrátí hodnotu <xref:System.Double> hodnota podle odkazu, můžete ji definovat jako místní proměnná ref s kódem, jako je následující:

```csharp
ref int distance = plant 
```

Vícerozměrné pole vrácení z metody, `M`, aplikací, které mění pole obsahu není nutné v případě volání funkce předány do pole `M`.  Může vrátit výsledné pole z `M` pro dobré styl nebo funkční tok hodnoty, ale není nezbytné, protože C# projde všechny typy odkazů podle hodnoty a odkazu na pole má hodnotu ukazatele na pole. V metodě `M`, všechny změny obsahu pole se pozorovat podle veškerý kód, který obsahuje odkaz na pole, jak je znázorněno v následujícím příkladu.  
  
```csharp  
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```  
  
 Další informace najdete v tématu [vrátit](../../../csharp/language-reference/keywords/return.md).  
  
## <a name="async-methods"></a>Asynchronní metody  
 Při použití asynchronní funkce, se dají vyvolat asynchronní metody bez použití explicitní zpětná volání nebo Ruční rozdělení kódu mezi více metodách a výrazech lambda. 
  
 Pokud určíte metodu s [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor, můžete použít [await](../../../csharp/language-reference/keywords/await.md) operátor v metodě. Když ovládací prvek dosáhne výrazu await v asynchronní metodě, ovládací prvek vrátí volajícímu a průběh v metodě je pozastavený, až do dokončení očekávané úlohy. Po dokončení úlohy se provádění může pokračovat v metodě.  
  
> [!NOTE]
>  Asynchronní metoda vrátí řízení volajícímu, když nalezne první očekávaný objekt, který ještě není dokončeno nebo získá konec asynchronní metody podle toho, co nastane dříve.  
  
 Asynchronní metoda může mít návratový typ <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, nebo void. Typ vrácené hodnoty void se používá především k definování obslužných rutin událostí, kde se vyžaduje typ vrácené hodnoty void. Asynchronní metody vracející typ void nemůže být očekávána a volající metody vracející typ void nemůže zachytit výjimky, které metoda vyvolá.  
  
 V následujícím příkladu `DelayAsync` je asynchronní metoda, která má návratový typ <xref:System.Threading.Tasks.Task%601>. `DelayAsync` má `return` příkaz, který vrátí celé číslo. Proto deklarace metody z `DelayAsync` musí mít typ vrácené hodnoty `Task<int>`. Vzhledem k tomu, že je návratový typ `Task<int>`, vyhodnocení `await` výrazu v `DoSomethingAsync` vytváří celé číslo, jak ukazuje následující příkaz: `int result = await delayTask`.  
  
 `startButton_Click` Metoda je příklad asynchronní metody, která má typ vrácené hodnoty void. Protože `DoSomethingAsync` je metodou asynchronní úloha pro volání `DoSomethingAsync` musí ní použít operátor await, jak ukazuje následující příkaz: `await DoSomethingAsync();`. `startButton_Click` Metoda musí být definované s `async` modifikátor vzhledem k tomu, že tato metoda má `await` výrazu.  
  
 [!code-csharp[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]  
  
 Asynchronní metoda nemůže deklarovat všechny [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, ale může volat metody, které mají tyto parametry.  
  
 Další informace o metodách async naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md), [tok řízení v asynchronních programech](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), a [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>Definice textu výrazu  
 Je běžné mít definice metod, které jednoduše okamžitě vrátí výsledek výrazu nebo, které mají jeden příkaz jako tělo metody.  Existuje místní syntaxe pro definování těchto metod pomocí `=>`:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Pokud metoda vrátí `void` nebo je asynchronní metody, výrazu příkazu (stejně jako výrazy lambda) musí být tělo metody.  Pro vlastnostmi a indexery, musí být jen pro čtení a nepoužíváte `get` – klíčové slovo přistupujícího objektu.  
  
## <a name="iterators"></a>Iterátory  
 Iterátor provádí vlastní iterace nad kolekcí, jako je například seznam nebo pole. Iterátor používá [yield return](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit vždy jeden prvek v čase. Když [yield return](../../../csharp/language-reference/keywords/yield.md) je dosažen příkaz, se uloží aktuální umístění v kódu. Provádění je restartováno z tohoto umístění, při příštím volání iterátoru.  
  
 Můžete volat iterátor z klientského kódu s použitím [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkazu.  
  
 Návratový typ iterátor může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Další informace najdete v tématu [iterátory](../../../csharp/programming-guide/concepts/iterators.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](index.md)  
- [Modifikátory přístupu](access-modifiers.md)  
- [Statické třídy a jejich členové](static-classes-and-static-class-members.md)  
- [Dědičnost](inheritance.md)  
- [Abstraktní a uzavřené třídy a jejich členové](abstract-and-sealed-classes-and-class-members.md)  
- [params](../../../csharp/language-reference/keywords/params.md)  
- [return](../../../csharp/language-reference/keywords/return.md)  
- [out](../../../csharp/language-reference/keywords/out.md)  
- [ref](../../../csharp/language-reference/keywords/ref.md)  
- [Předávání parametrů](passing-parameters.md)
