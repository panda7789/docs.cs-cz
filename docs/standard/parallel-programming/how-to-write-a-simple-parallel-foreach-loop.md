---
title: Zápis paralelního jednoduchý program pomocí paralelní ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 599432af178031a85dea4155a8fd2923f879a600
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427354"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Postupy: Zápis jednoduché smyčky Parallel.ForEach

Tento příklad ukazuje způsob použití <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčky umožňující datový paralelismus nad <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroj dat.

> [!NOTE]
> Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ. Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, naleznete v tématu [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Příklad

Tento příklad předpokládá, že máte několik jpg soubory *C:\Users\Public\Pictures\Sample obrázky* složku a vytvoří novou podsložku s názvem *změněné*. Při spuštění v příkladu se otočí každý obrázek JPG v *vzorové obrázky* a ukládá ji do *změněné*. Můžete upravit podle potřeby tyto dvě cesty.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčky funguje stejně jako <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčky. Smyčky oddílů zdrojové kolekce a plánuje práci z více vláken, které jsou založené na prostředí systému. Více procesorů v systému, tím rychleji paralelní metoda pracuje. Pro některé zdroje kolekce může být rychlejší, v závislosti na velikosti zdroje a na druhu práce, kterou provádí smyčky sekvenční smyčka. Další informace o výkonu, naleznete v tématu [Potenciální nástrahy paralelismu dat a úloh](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)

Další informace o paralelních smyček, naleznete v tématu [jak: Zápis jednoduché smyčky Parallel.for](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Chcete-li použít <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> v obecné kolekci, můžete použít <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> metodu rozšíření k převodu kolekce na obecné kolekce, jak je znázorněno v následujícím příkladu:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Paralelní LINQ (PLINQ) můžete také použít pro paralelní zpracování <xref:System.Collections.Generic.IEnumerable%601> zdrojů. PLINQ umožňuje používat deklarativní syntaxe vyjádřit chování smyčky. Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).

## <a name="compile-and-run-the-code"></a>Kompilace a spuštění kódu

Kód lze zkompilovat jako konzolovou aplikaci pro rozhraní .NET Framework nebo konzolové aplikace pro .NET Core.

V sadě Visual Studio jsou jazyka Visual Basic a C# konzole šablony aplikací pro stolní počítače Windows a .NET Core.

Z příkazového řádku, můžete použít .NET Core a jeho nástrojů rozhraní příkazového řádku (například `dotnet new console` nebo `dotnet new console -lang vb`), nebo můžete vytvořit soubor a pomocí příkazového řádku kompilátoru pro aplikace rozhraní .NET Framework.

Pro projekt .NET Core, musí odkazovat **System.Drawing.Common** balíček NuGet. V sadě Visual Studio pomocí Správce balíčků NuGet nainstalujte balíček. Alternativně můžete přidat odkaz na balíček ve vaší \*.csproj nebo \*souboru .vbproj:
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Chcete-li spustit konzolovou aplikaci .NET Core z příkazového řádku, použijte `dotnet run` ze složky, která obsahuje vaši aplikaci.

Chcete-li spustit konzolovou aplikaci v sadě Visual Studio, stiskněte **F5**.

## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
