---
title: Asynchronní přístup k souborům (C#)
description: Naučte se používat funkci Async pro přístup k souborům v C#. Můžete volat na asynchronní metody bez použití zpětných volání nebo rozdělení kódu napříč metodami.
ms.date: 08/19/2020
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 9a8db6004e8fff2cb39f0c350b403b56ea619e54
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812039"
---
# <a name="asynchronous-file-access-c"></a>Asynchronní přístup k souborům (C#)

K přístupu k souborům můžete použít funkci Async. Pomocí asynchronní funkce můžete zavolat do asynchronních metod bez použití zpětných volání nebo rozdělení kódu napříč více metodami nebo lambda výrazy. Chcete-li synchronní asynchronní kód, stačí zavolat asynchronní metodu namísto synchronní metody a přidat k kódu několik klíčových slov.

Při přidávání asynchronii do volání přístupu k souborům můžete zvážit následující důvody:

> [!div class="checklist"]
>
> - Asynchronii umožňuje aplikacím uživatelského rozhraní lépe reagovat, protože vlákno uživatelského rozhraní, které spouští operaci, může provádět i jinou práci. Pokud vlákno uživatelského rozhraní musí spustit kód, který trvá dlouhou dobu (například více než 50 milisekund), může uživatelské rozhraní zablokovat až do dokončení vstupně-výstupních operací a vlákno uživatelského rozhraní může znovu zpracovat vstupy klávesnice a myši a další události.
> - Asynchronii zlepšuje škálovatelnost ASP.NET a dalších serverových aplikací tím, že snižuje nutnost vláken. Pokud aplikace používá vyhrazené vlákno na reakci a tisíce požadavků jsou zpracovávány současně, je zapotřebí tisíce vláken. Asynchronní operace často nepotřebují použít vlákno během čekání. Na konci se krátce používají existující vlákna dokončení v/v.
> - Latence operace přístupu k souboru může být v rámci současných podmínek velmi nízká, ale latence může výrazně zvýšit i v budoucnu. Soubor může být například přesunut na server, který je na celém světě.
> - Přidaná režie použití asynchronní funkce je malá.
> - Asynchronní úlohy lze snadno spustit paralelně.

## <a name="use-appropriate-classes"></a>Použít příslušné třídy

Jednoduché příklady v tomto tématu ukazují <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> a <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType> . Pro omezenou kontrolu nad vstupně-výstupními operacemi souborů použijte <xref:System.IO.FileStream> třídu, která má možnost, která způsobí, že asynchronní vstupně-výstupní operace proběhne na úrovni operačního systému. Pomocí této možnosti se můžete vyhnout blokování vlákna fondu vláken v mnoha případech. Chcete-li povolit tuto možnost, zadejte `useAsync=true` `options=FileOptions.Asynchronous` argument nebo ve volání konstruktoru.

Tuto možnost nemůžete použít s <xref:System.IO.StreamReader> a, <xref:System.IO.StreamWriter> Pokud je otevřete přímo zadáním cesty k souboru. Tuto možnost však můžete použít, pokud jim poskytnete <xref:System.IO.Stream> třídu, kterou <xref:System.IO.FileStream> otevřela. Asynchronní volání jsou rychlejší v aplikacích uživatelského rozhraní i v případě, že je vlákno fondu vláken blokované, protože během čekání není zablokované vlákno uživatelského rozhraní.

## <a name="write-text"></a>Napsat text

Následující příklady zapisují text do souboru. V každém příkazu await se metoda okamžitě ukončí. Po dokončení vstupně-výstupních operací se metoda obnoví v příkazu, který následuje po příkazu await. Modifikátor Async je v definici metod, které používají příkaz await.

### <a name="simple-example"></a>Jednoduchý příklad

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleWrite":::

### <a name="finite-control-example"></a>Příklad omezeného ovládacího prvku

:::code language="csharp" source="snippets/file-access/Program.cs" id="WriteText":::

Původní příklad obsahuje příkaz `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` , který je kontraktem následujících dvou příkazů:

```csharp
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);
await theTask;
```

První příkaz vrátí úlohu a způsobí, že se zpracování souboru spustí. Druhý příkaz s operátorem await způsobí, že metoda okamžitě ukončí a vrátí jiný úkol. Po dokončení zpracování souboru se spuštění vrátí do příkazu, který následuje za operátorem await.

## <a name="read-text"></a>Přečíst text

Následující příklady čtou text ze souboru.

### <a name="simple-example"></a>Jednoduchý příklad

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleRead":::

### <a name="finite-control-example"></a>Příklad omezeného ovládacího prvku

Text je uložen do vyrovnávací paměti a v tomto případě je umístěn do <xref:System.Text.StringBuilder> . Na rozdíl od předchozího příkladu vyhodnocení await vytvoří hodnotu. <xref:System.IO.Stream.ReadAsync%2A>Metoda vrací <xref:System.Threading.Tasks.Task> \<<xref:System.Int32>>, takže vyhodnocení metody await vytvoří `Int32` hodnotu `numRead` po dokončení operace. Další informace naleznete v tématu [Asynchronní návratové typy (C#)](async-return-types.md).

:::code language="csharp" source="snippets/file-access/Program.cs" id="ReadText":::

## <a name="parallel-asynchronous-io"></a>Paralelní asynchronní vstupně-výstupní operace

Následující příklady znázorňují paralelní zpracování zápisem 10 textových souborů.

### <a name="simple-example"></a>Jednoduchý příklad

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleParallelWrite":::

### <a name="finite-control-example"></a>Příklad omezeného ovládacího prvku

Pro každý soubor <xref:System.IO.Stream.WriteAsync%2A> Metoda vrátí úkol, který je poté přidán do seznamu úkolů. `await Task.WhenAll(tasks);`Příkaz ukončí metodu a pokračuje v rámci metody, když je zpracování souborů dokončeno pro všechny úlohy.

Příklad zavře všechny <xref:System.IO.FileStream> instance v `finally` bloku po dokončení úkolů. Pokud byl každý z `FileStream` nich vytvořen v `using` příkazu, `FileStream` může být odstraněn před dokončením úkolu.

Jakékoli zvýšení výkonu je prakticky zcela úplné od paralelního zpracování, nikoli z asynchronního zpracování. Výhody asynchronii jsou, že neodkazují na více vláken a že nevyužívají vlákno uživatelského rozhraní.

:::code language="csharp" source="snippets/file-access/Program.cs" id="ParallelWriteText":::

Při použití <xref:System.IO.Stream.WriteAsync%2A> metod a <xref:System.IO.Stream.ReadAsync%2A> můžete zadat <xref:System.Threading.CancellationToken> , které můžete použít k zrušení operace střední-Stream. Další informace naleznete v tématu [zrušení ve spravovaných vláknech](../../../../standard/threading/cancellation-in-managed-threads.md).

## <a name="see-also"></a>Viz také

- [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](index.md)
- [Asynchronní návratové typy (C#)](async-return-types.md)
