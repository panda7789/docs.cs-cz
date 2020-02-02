---
title: Zápis jednoduchého paralelního programu pomocí Parallel. ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 528e22d6b54179181d1479f4feaedfbf82933c58
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921220"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Postupy: zápis jednoduché smyčky Parallel. ForEach

Tento příklad ukazuje, jak použít smyčku <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> k povolení datových paralelismu přes libovolný <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroj dat.

> [!NOTE]
> Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ. Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Příklad

V tomto příkladu se předpokládá, že máte ve složce *C:\Users\Public\Pictures\Sample obrázky* několik souborů. jpg a vytvoříme novou podsložku s názvem *Modified*. Když spustíte příklad, otáčí se každý obrázek. jpg ve *vzorových obrázcích* a uloží se do *upraveného*. V případě potřeby můžete tyto dvě cesty upravit.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>ová smyčka funguje jako smyčka <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>. Smyčka rozdělí zdrojovou kolekci a naplánuje práci na více vláknech na základě prostředí systému. Čím více procesorů v systému, tím rychleji se spustí paralelní metoda. U některých zdrojových kolekcí může být sekvenční smyčka rychlejší v závislosti na velikosti zdroje a druhu práce, kterou smyčka provádí. Další informace o výkonu najdete v tématu [potenciální nástrah v datech a paralelismuch Tasks](potential-pitfalls-in-data-and-task-parallelism.md).

Další informace o paralelních smyčkách naleznete v tématu [How to: Write a Simple Parallel. for Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Chcete-li použít <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> s neobecnou kolekcí, můžete použít metodu rozšíření <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> k převedení kolekce do obecné kolekce, jak je znázorněno v následujícím příkladu:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Můžete také použít Paralelní LINQ (PLINQ) k paralelizovat zpracování zdrojů dat <xref:System.Collections.Generic.IEnumerable%601>. PLINQ umožňuje použít syntax deklarativního dotazu k vyjádření chování smyčky. Další informace naleznete v tématu [PARALLEL LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).

## <a name="compile-and-run-the-code"></a>Zkompilovat a spustit kód

Kód můžete zkompilovat jako konzolovou aplikaci pro .NET Framework nebo jako konzolovou aplikaci pro .NET Core.

V aplikaci Visual Studio jsou k dispozici C# šablony pro Visual Basic a konzolové aplikace pro Windows Desktop a .NET Core.

Z příkazového řádku můžete použít buď příkazy .NET Core CLI (například `dotnet new console` nebo `dotnet new console -lang vb`), nebo můžete vytvořit soubor a použít kompilátor příkazového řádku pro aplikaci .NET Framework.

V případě projektu .NET Core musíte odkazovat na balíček NuGet **System. Drawing. Common** . V aplikaci Visual Studio použijte Správce balíčků NuGet k instalaci balíčku. Alternativně můžete do souboru \*. csproj nebo \*. vbproj přidat odkaz na balíček:
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Chcete-li spustit konzolovou aplikaci .NET Core z příkazového řádku, použijte `dotnet run` ze složky, která obsahuje vaši aplikaci.

Chcete-li spustit konzolovou aplikaci ze sady Visual Studio, stiskněte klávesu **F5**.

## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
