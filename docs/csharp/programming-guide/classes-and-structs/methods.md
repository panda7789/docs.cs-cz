---
title: Metody (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: d3fc4107c10d098d40e4021bef9f6acd06311fab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="methods-c-programming-guide"></a>Metody (Průvodce programováním v C#)
Metoda je blok kódu, který obsahuje řadu příkazů. Program způsobí, že příkazy provádět volání metody a zadání argumentů požadovaná metoda. V jazyce C# každé spuštění instrukce se provádí v kontextu metody. Hlavní metoda je vstupní bod pro každou aplikaci C# a je volána metodou common language runtime (CLR) při spuštění programu.  
  
> [!NOTE]
>  Toto téma popisuje pojmenované metody. Informace o anonymní funkce najdete v tématu [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Podpisy – metoda  
 Metody, které jsou deklarované v [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) zadáním úroveň přístupu, jako `public` nebo `private`, volitelné modifikátory jako `abstract` nebo `sealed`, návratový hodnota, název metody a všechny parametry metody. Následující části jsou společně podpis metody.  
  
> [!NOTE]
>  Návratový typ metody není součástí podpis metody pro účely přetěžování metody. Je však součástí podpis metody při určování kompatibilitu mezi delegáta a metodu, která odkazuje na.  
  
 Parametry metody jsou uzavřené v závorkách a jsou odděleny čárkami. Závorky, jinak znamenat, že metoda nevyžaduje žádné parametry. Tato třída obsahuje tři metody:  
  
 [!code-csharp[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]  
  
## <a name="method-access"></a>Přístup k metodě  
 Volání metody objektu je jako přístup k poli. Po názvu objektu přidáte období, název metody, a kulaté závorky. Argumenty jsou uvedeny v závorkách a jsou odděleny čárkami. Metody `Motorcycle` třída proto nelze volat jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]  
  
## <a name="method-parameters-vs-arguments"></a>Parametry metody vs. Arguments  
 Definice metoda určuje názvy a typy parametrů, které jsou požadovány. Při volání metody kód zavolá metodu, poskytuje konkrétní hodnoty nazývaných argumenty pro jednotlivé parametry. Argumenty, které musí být kompatibilní s typem parametru ale argument jméno (pokud existuje) použité v kód volání nemusí být stejný jako parametr s názvem definované v metodě. Příklad:  
  
 [!code-csharp[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Předání odkaz vs. Předání hodnotou  
 Ve výchozím nastavení když typ hodnoty je předána metodě, je kopie předán místo samotného objektu. Změny argument tedy mít žádný vliv na původní kopie v metodě volání. Typ hodnoty odkazem můžete předat pomocí ref – klíčové slovo. Další informace najdete v tématu [předávání parametrů typu hodnoty](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md). Seznam typů předdefinovaných hodnot najdete v tématu [Tabulka typů hodnot](../../../csharp/language-reference/keywords/value-types-table.md).  
  
 Když metoda předána objekt typu odkazu, odkaz na objekt je předán. To znamená metoda obdrží, ale ne samotný objekt argument, který určuje umístění objektu. Pokud změníte členem objektu pomocí tohoto odkazu, změny se v argumentu v metodě volání, i když tento objekt předat hodnotu.  
  
 Vytvoření typu odkazu pomocí `class` – klíčové slovo, jak ukazuje následující příklad.  
  
 [!code-csharp[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]  
  
 Nyní Pokud předáte objekt, který je založen na tento typ a metodu, je předaná odkaz na objekt. Následující příklad předá objekt typu `SampleRefType` metodě `ModifyObject`.  
  
 [!code-csharp[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]  
  
 V příkladu nemá v podstatě má stejnou funkci jako předchozí příklad, předá argumentu podle hodnoty metodu. Ale protože odkaz na typ se používá, výsledek se liší. Změna, která se provádí v `ModifyObject` k `value` pole parametru, `obj`, také změní `value` pole argumentu, `rt`v `TestRefType` metoda. `TestRefType` Metoda zobrazí 33 jako výstup.  
  
 Další informace o tom, jak předat odkazové typy odkazem a hodnotou najdete v tématu [předávání parametrů typu odkazu](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) a [odkazové typy](../../../csharp/language-reference/keywords/reference-types.md).  
  
## <a name="return-values"></a>Návratové hodnoty  
Metody můžete vrátit hodnotu volajícímu. Pokud je návratový typ, není typu uvedené před název metody `void`, metoda může vrátit hodnotu pomocí `return` – klíčové slovo. Příkaz s `return` – klíčové slovo, za nímž následuje hodnotu, která odpovídá návratový typ, vrátí tuto hodnotu Metoda volajícímu. 

Hodnota může být vrácen volajícímu hodnotu nebo, počínaje C# 7.0, [odkazem](ref-returns.md). Hodnoty jsou vráceny volajícímu odkazem, pokud `ref` – klíčové slovo se používá v podpis metody a postupuje každý `return` – klíčové slovo. Například následující příkaz podpisu a vraťte se metoda znamenat, že metoda vrátí názvy proměnných `estDistance` odkazem na volajícího.

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

`return` – Klíčové slovo také zastaví provádění metody. Pokud je návratový typ `void`, `return` je stále užitečné zastavit provádění metody příkaz bez hodnoty. Bez `return` – klíčové slovo, metoda skončí při ukončení bloku kódu. Metody s není void vrací typ jsou nutné k použití `return` – klíčové slovo bude vrácena hodnota. Například použít tyto dvě metody `return` – klíčové slovo vrátit celá čísla:  
  
 [!code-csharp[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]  
  
 Pokud chcete použít hodnotu, vrátí metoda, můžete použít metodu volání volání metody samotné kdekoli hodnota stejného typu by být dostatečná. Můžete také přiřadit návratovou hodnotu proměnné. Například následující příklady kódu dvě dosažení stejné cíle:  
  
 [!code-csharp[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]  
  
 [!code-csharp[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]  
  
 Použití místní proměnné, v takovém případě `result`, ukládat hodnota je volitelná. Dobře čitelnost kódu, nebo může být nutné, pokud je třeba uložit původní hodnota argumentu pro celý rozsah metodu.  

Na používání hodnoty vrácené odkaz z metody, je třeba deklarovat [ref místní](ref-returns.md#ref-locals) proměnná, pokud chcete upravit její hodnotu. Například pokud `Planet.GetEstimatedDistance` metoda vrátí <xref:System.Double> hodnotu odkazem, můžete ji definovat jako místní proměnné ref kódem takto:

```csharp
ref int distance = plant 
```

Vrácení vícerozměrné z metody, `M`, která mění tohoto pole obsah není nutné v případě, že pole do předána volání funkce `M`.  Může vrátit výsledné pole z `M` pro dobrý styl nebo funkční toku hodnoty, ale není nutné, protože C# předá všechny odkazové typy podle hodnoty a odkaz na pole hodnotu má ukazatel na pole. V metodě `M`, všechny změny do tohoto pole obsahu, jsou lze zobrazit pomocí kód, který obsahuje odkaz na pole, jak je znázorněno v následujícím příkladu.  
  
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
 Pomocí funkce asynchronní můžete vyvolat asynchronních metod bez použití explicitní zpětná volání nebo Ruční rozdělení kódu mezi více metod nebo výrazy lambda. 
  
 Pokud označíte metodu s [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor, můžete použít [await](../../../csharp/language-reference/keywords/await.md) operátor v metodě. Když řízení dosáhne výraz await v asynchronní metody, řízení vrátí volajícímu a průběh v metodě je pozastaveno, dokud dokončení awaited úlohy. Po dokončení úlohy provádění může pokračovat v metodě.  
  
> [!NOTE]
>  Asynchronní metody vrátí volající, pokud zjistí první awaited objekt, který ještě není dokončena nebo získá na konec asynchronní metody, cokoliv nastane dříve.  
  
 Asynchronní metody může mít návratový typ <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, nebo void. Typ vrácené hodnoty void slouží především k definování obslužné rutiny událostí, kdy je potřeba typ vrácené hodnoty void. Asynchronní metody, který vrátí prázdnou hodnotu nemůže být očekáváno a volající metody vrácení void nelze catch výjimky, které vyvolá metoda.  
  
 V následujícím příkladu `DelayAsync` je asynchronní metody, který má návratový typ <xref:System.Threading.Tasks.Task%601>. `DelayAsync` má `return` příkaz, který vrátí celé číslo. Proto metoda deklaraci `DelayAsync` musí mít návratový typ `Task<int>`. Vzhledem k tomu, že je návratový typ `Task<int>`, vyhodnocení `await` výrazu v `DoSomethingAsync` vytváří celé číslo, jak ukazuje následující příkaz: `int result = await delayTask`.  
  
 `startButton_Click` Metoda je příkladem asynchronní metody, který má návratový typ void. Protože `DoSomethingAsync` je asynchronní metody, úlohy pro volání `DoSomethingAsync` musí být očekáváno, jak ukazuje následující příkaz: `await DoSomethingAsync();`. `startButton_Click` Metoda musí být definovány se `async` modifikátor vzhledem k tomu, že metoda má `await` výrazu.  
  
 [!code-csharp[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]  
  
 Asynchronní metody nelze deklarovat všechny [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, ale můžete volat metody, které mají tyto parametry.  
  
 Další informace o asynchronní metody najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md), [řízení toku v asynchronních programech](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), a [asynchronní vrátit typy](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>Výraz definice textu  
 Je běžné metoda definicemi, jednoduše okamžitě vrátí s výsledkem výrazu nebo které mají jediný příkaz jako text metody.  Je syntaxe zástupce pro definování těchto metod, pomocí `=>`:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Pokud metoda vrátí `void` nebo asynchronní metody, pak těla metody musí být příkaz výraz (stejné jako u lambdas).  Pro vlastnostmi a indexery, se musí být jen pro čtení, a nepoužíváte `get` – klíčové slovo přistupujícího objektu.  
  
## <a name="iterators"></a>Iterátory  
 Iterátor provede vlastní iterace nad kolekcí, jako je například seznam nebo pole. Iterátor používá [yield vrátit](../../../csharp/language-reference/keywords/yield.md) příkaz vrátit každý element, jeden v čase. Když [yield vrátit](../../../csharp/language-reference/keywords/yield.md) příkaz je dosaženo, uloží je aktuální umístění v kódu. Při iteraci volání při příštím spuštění restartování z tohoto umístění.  
  
 Volání iterovat z kódu klienta pomocí [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz.  
  
 Návratový typ iterovat může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Další informace najdete v tématu [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](index.md)  
 [Modifikátory přístupu](access-modifiers.md)  
 [Statické třídy a jejich členové](static-classes-and-static-class-members.md)  
 [Dědičnost](inheritance.md)  
 [Abstraktní a uzavřené třídy a jejich členové](abstract-and-sealed-classes-and-class-members.md)  
 [params](../../../csharp/language-reference/keywords/params.md)  
 [return](../../../csharp/language-reference/keywords/return.md)  
 [out](../../../csharp/language-reference/keywords/out.md)  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [Předávání parametrů](passing-parameters.md)
