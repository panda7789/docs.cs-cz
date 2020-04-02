---
title: Napsat jednoduchý paralelní program pomocí Parallel.ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 0300f8900cd18159ba3a2170cfba96f302f282a0
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588145"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Postup: Napište jednoduchou smyčku Parallel.ForEach

Tento příklad ukazuje, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> jak použít smyčku k <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> povolení paralelismu dat přes všechny nebo zdroj dat.

> [!NOTE]
> Tato dokumentace používá lambda výrazy definovat delegáty v PLINQ. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Příklad

Tento příklad předpokládá, že máte několik souborů JPG ve složce *C:\Users\Public\Pictures\Sample Pictures* a vytvoří tenovou podsložku s názvem *Změněno*. Při spuštění příkladu otočí každý .jpg obraz v *ukázkové obrázky* a uloží jej *do změnit*. Podle potřeby můžete upravit dvě cesty.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

Smyčka <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> funguje jako <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčka. Smyčka rozdělí zdrojovou kolekci a naplánuje práci na více vláknech na základě systémového prostředí. Čím více procesorů v systému, tím rychlejší paralelní metoda běží. Pro některé zdrojové kolekce může být sekvenční smyčka rychlejší, v závislosti na velikosti zdroje a druhu práce, kterou smyčka provádí. Další informace o výkonu naleznete [v tématu Potenciální úskalí v datech a paralelismu úloh](potential-pitfalls-in-data-and-task-parallelism.md).

Další informace o paralelních smyčkách naleznete v [tématu How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Chcete-li použít <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> s neobecnou kolekci, můžete použít metodu <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> rozšíření převést kolekci na obecnou kolekci, jak je znázorněno v následujícím příkladu:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Paralelní LINQ (PLINQ) můžete také použít k <xref:System.Collections.Generic.IEnumerable%601> paralelizaci zpracování zdrojů dat. PLINQ umožňuje použít syntaxi deklarativního dotazu k vyjádření chování smyčky. Další informace naleznete [v tématu Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).

## <a name="compile-and-run-the-code"></a>Kompilace a spuštění kódu

Kód můžete zkompilovat jako konzolovou aplikaci pro rozhraní .NET Framework nebo jako konzolovou aplikaci pro rozhraní .NET Core.

V sadě Visual Studio existují šablony aplikací visual basic a c# konzoly pro Windows Desktop a .NET Core.

Z příkazového řádku můžete použít příkazy rozhraní PŘÍKAZU .NET `dotnet new console` `dotnet new console -lang vb`Core (například nebo ) nebo můžete vytvořit soubor a použít kompilátor příkazového řádku pro aplikaci rozhraní .NET Framework.

Pro projekt .NET Core je nutné odkazovat na balíček **System.Drawing.Common** NuGet. V sadě Visual Studio použijte K instalaci balíčku Správce balíčků NuGet. Případně můžete přidat odkaz na balíček \*v souboru \*.csproj nebo .vbproj:

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Chcete-li spustit aplikaci konzoly .NET `dotnet run` Core z příkazového řádku, použijte ze složky, která obsahuje vaši aplikaci.

Chcete-li spustit konzolovou aplikaci z aplikace Visual Studio, stiskněte **klávesu F5**.

## <a name="see-also"></a>Viz také

- [Paralelismus dat](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
