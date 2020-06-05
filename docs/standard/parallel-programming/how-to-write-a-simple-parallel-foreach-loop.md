---
title: Zápis jednoduchého paralelního programu pomocí Parallel. ForEach
description: V tomto článku se dozvíte, jak povolit datovou paralelismuy v .NET. Napište smyčku Parallel. ForEach přes libovolný zdroj dat IEnumerable nebo IEnumerable <T> .
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 59c8710a8e3fc878b2ceded8595f7f3319d4c953
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447196"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Postupy: zápis jednoduché smyčky Parallel. ForEach

Tento příklad ukazuje, jak použít <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčku pro povolení datové paralelismuy prostřednictvím libovolného <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroje dat nebo.

> [!NOTE]
> Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Příklad

V tomto příkladu se předpokládá, že máte ve složce *C:\Users\Public\Pictures\Sample obrázky* několik souborů. jpg a vytvoříme novou podsložku s názvem *Modified*. Když spustíte příklad, otáčí se každý obrázek. jpg ve *vzorových obrázcích* a uloží se do *upraveného*. V případě potřeby můžete tyto dvě cesty upravit.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Smyčka funguje jako <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčka. Smyčka rozdělí zdrojovou kolekci a naplánuje práci na více vláknech na základě prostředí systému. Čím více procesorů v systému, tím rychleji se spustí paralelní metoda. U některých zdrojových kolekcí může být sekvenční smyčka rychlejší v závislosti na velikosti zdroje a druhu práce, kterou smyčka provádí. Další informace o výkonu najdete v tématu [potenciální nástrah v datech a paralelismuch Tasks](potential-pitfalls-in-data-and-task-parallelism.md).

Další informace o paralelních smyčkách naleznete v tématu [How to: Write a Simple Parallel. for Loop](how-to-write-a-simple-parallel-for-loop.md).

Pro použití <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> s neobecnou kolekcí můžete použít <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> metodu rozšíření pro převod kolekce na obecnou kolekci, jak je znázorněno v následujícím příkladu:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

K paralelizovat zpracování zdrojů dat můžete také použít Paralelní LINQ (PLINQ) <xref:System.Collections.Generic.IEnumerable%601> . PLINQ umožňuje použít syntax deklarativního dotazu k vyjádření chování smyčky. Další informace naleznete v tématu [PARALLEL LINQ (PLINQ)](introduction-to-plinq.md).

## <a name="compile-and-run-the-code"></a>Zkompilovat a spustit kód

Kód můžete zkompilovat jako konzolovou aplikaci pro .NET Framework nebo jako konzolovou aplikaci pro .NET Core.

V aplikaci Visual Studio jsou k dispozici šablony konzolové aplikace Visual Basic a C# pro Windows Desktop a .NET Core.

Z příkazového řádku můžete použít buď příkazy .NET Core CLI (například `dotnet new console` nebo `dotnet new console -lang vb` ), nebo můžete vytvořit soubor a použít kompilátor příkazového řádku pro .NET Framework aplikace.

V případě projektu .NET Core musíte odkazovat na balíček NuGet **System. Drawing. Common** . V aplikaci Visual Studio použijte Správce balíčků NuGet k instalaci balíčku. Alternativně můžete do \* souboru. csproj nebo. vbproj přidat odkaz na balíček \* :

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Chcete-li spustit konzolovou aplikaci .NET Core z příkazového řádku, použijte `dotnet run` ze složky, která obsahuje vaši aplikaci.

Chcete-li spustit konzolovou aplikaci ze sady Visual Studio, stiskněte klávesu **F5**.

## <a name="see-also"></a>Viz také

- [Datový paralelismus](data-parallelism-task-parallel-library.md)
- [Paralelní programování](index.md)
- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
