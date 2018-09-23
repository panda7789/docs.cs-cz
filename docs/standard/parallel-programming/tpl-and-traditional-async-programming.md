---
title: TPL a tradiční asynchronní programování v .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8024fe6673b39a611c55eb55742bcfd981300e7e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46702943"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL a tradiční asynchronní programování v .NET Framework
Rozhraní .NET Framework poskytuje následující dva standardní vzory pro provádění vstupně-výstupní a výpočetní asynchronních operací:  
  
-   Asynchronní Programovací Model (APM), ve kterém asynchronní operace reprezentovány dvojice metody Begin/End, jako <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
-   Událost asynchronní vzor založený (EAP), ve kterém jsou asynchronní operace reprezentovány dvojicí metoda/událost, která se nazývá *OperationName*asynchronní a *OperationName*dokončeno, například <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> a <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (EAP byla zavedena v rozhraní .NET Framework verze 2.0).  
  
 Task Parallel Library (TPL) lze použít různými způsoby ve spojení s jedním z asynchronní zpracování. Operace APM a EAP mohou vystavit jako úlohy knihovny spotřebitelům nebo vystavit tyto vzory se dají APM, ale implementace je interně pomocí objekty úloh. V obou případech pomocí objektů úloh můžete zjednodušit kód a využijte užitečné následující funkce:  
  
-   Registrace zpětných volání, ve formuláři pokračování úlohy, kdykoli po spuštění úlohy.  
  
-   Koordinace více operací, které jsou spuštěny v reakci na `Begin_` metodu, pomocí <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody, nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> – metoda nebo <xref:System.Threading.Tasks.Task.WaitAny%2A> metoda.  
  
-   Zapouzdření asynchronní vstupně-výstupní a výpočetní operace ve stejném objektu úlohy.  
  
-   Monitorujte stav objektu Task.  
  
-   Zařazování stav operace pro objekt úlohy s použitím <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Zabalení APM v rámci úlohy  
 Jak <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> a <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> třídy poskytují několik přetížení <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody, které umožňují zapouzdřit páru APM začátek/konec metody v jednom <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> instance. Různé přetížení pojmout všechny dvojice metody Begin/End, který jste od nuly do tří vstupní parametry.  
  
 Dvojice, které mají pro `End` metody, které vracejí hodnotu (`Function` v jazyce Visual Basic), použijte metody v <xref:System.Threading.Tasks.TaskFactory%601> , vytvořit <xref:System.Threading.Tasks.Task%601>. Pro `End` metody, které vracejí void (`Sub` v jazyce Visual Basic), použijte metody v <xref:System.Threading.Tasks.TaskFactory> , vytvořit <xref:System.Threading.Tasks.Task>.  
  
 Pro několik případů, ve kterém `Begin` metoda má více než tři parametry, nebo obsahuje `ref` nebo `out` parametry, další `FromAsync` přetížení, které provádí zapouzdření pouze `End` metody jsou k dispozici.  
  
 Následující příklad ukazuje podpis pro `FromAsync` přetížení, které odpovídá <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> metody. Toto přetížení má tři vstupní parametry, následujícím způsobem.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 První parametr <xref:System.Func%606> delegáta, který se shoduje se signaturou <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metoda. Druhý parametr je <xref:System.Func%602> delegáta, který přebírá <xref:System.IAsyncResult> a vrátí `TResult`. Protože <xref:System.IO.FileStream.EndRead%2A> vrátí celé číslo, kompilátor odvodí typ `TResult` jako <xref:System.Int32> a typ úlohy jako <xref:System.Threading.Tasks.Task>. Poslední čtyři parametry jsou stejné jako ty v <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metody:  
  
-   Vyrovnávací paměť, ve kterém k ukládání dat souborů.  
  
-   Posunutí ve vyrovnávací paměti, ve kterém se má začít zapisovat data.  
  
-   Maximální množství dat ke čtení ze souboru.  
  
-   Volitelný objekt, který ukládá data o stavu na definovaný uživatelem k předání do zpětného volání.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Použití ContinueWith pro funkci zpětného volání  
 Pokud budete potřebovat přístup k datům v souboru, na rozdíl od jenom počet bajtů, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metoda není dostatečná. Místo toho použijte <xref:System.Threading.Tasks.Task>, jehož `Result` vlastnost obsahuje datový soubor. Můžete to provést tak, že přidáte na původním úkolu pokračování. Pokračování práce, které by se obvykle provádí pomocí provádí <xref:System.AsyncCallback> delegovat. Vyvolá se, když je předchůdce dokončen a vyrovnávací paměť dat bylo vyplněno. ( <xref:System.IO.FileStream> Objekt by měl být zavřený před vrácením.)  
  
 Následující příklad ukazuje, jak vrátit <xref:System.Threading.Tasks.Task> , který zapouzdřuje BeginRead/EndRead dvojici <xref:System.IO.FileStream> třídy.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Metoda může pak být volána, následujícím způsobem.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Poskytuje Data o stavu vlastního  
 V typické <xref:System.IAsyncResult> operace, pokud vaše <xref:System.AsyncCallback> delegáta vyžaduje některé vlastní stavová data, budete muset projít ji v posledním parametrem v `Begin` metody tak, aby data můžou být zabaleny do <xref:System.IAsyncResult> objekt, který se nakonec předaný metodě zpětného volání. To není obvykle potřeba při `FromAsync` metody se používají. Pokud vlastní data se ví, že pokračování, pak lze ji zachytit přímo v delegátovi pokračování. Následující příklad je podobný předchozímu příkladu, ale místo zkoumání `Result` vlastnosti předchůdce, pokračování zkontroluje stav vlastní data, která jsou přímo přístupné specialistům uživatelskému delegátovi pokračování.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Synchronizaci více úkolů FromAsync  
 Statické <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody poskytují vyšší flexibilitu při použití ve spojení s `FromAsync` metody. Následující příklad ukazuje, jak spustit několik asynchronních vstupně-výstupních operací a potom počkat na jejich dokončení ještě před spuštěním pokračování.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Úlohy FromAsync pouze v případě metody End  
 Pro několik případů, ve kterém `Begin` metoda vyžaduje víc než tři vstupní parametry nebo má `ref` nebo `out` parametry, můžete použít `FromAsync` přetížení, například <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, které představují pouze `End`metody. Tyto metody lze také ve všech scénářích, ve kterém jsou předány <xref:System.IAsyncResult> a chcete zapouzdřit v rámci úlohy.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Spuštění a zrušení úloh FromAsync  
 Úloha vrácená `FromAsync` metoda je ve stavu WaitingForActivation a bude spuštěna v systému v určitém okamžiku po vytvoření úlohy. Při pokusu o kontaktování Start na takového úkolu, bude vyvolána výjimka.  
  
 Nelze zrušit `FromAsync` úloh, protože základní rozhraní .NET Framework API aktuálně podporují zrušení v průběhu souboru ani / v sítě. Můžete přidat metody, která zapouzdřuje funkce zrušení `FromAsync` volání, ale můžete reagovat jen na zrušení před `FromAsync` volání a po jeho dokončení (například v úloze pokračování).  
  
 Některé třídy, které podporují protokol EAP, například <xref:System.Net.WebClient>podporují zrušení a, které tuto funkci nativní zrušení můžete integrovat s použitím tokenů zrušení.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Vystavení komplexní EAP operace jako úlohy  
 TPL neposkytuje žádné metody, které jsou vytvořené speciálně pro zapouzdření založený na událostech asynchronní operace ve stejné způsobu, jakým `FromAsync` řady metod kolem <xref:System.IAsyncResult> vzor. Poskytuje však TPL <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> třídu, která slouží k reprezentaci jakékoli sady operací, jako <xref:System.Threading.Tasks.Task%601>. Operace může být synchronní nebo asynchronní a může být vázaný vstupně-výstupních operací nebo výpočetní.  
  
 Následující příklad ukazuje způsob použití <xref:System.Threading.Tasks.TaskCompletionSource%601> k vystavení sady asynchronním <xref:System.Net.WebClient> operací pro klientský kód jako základní <xref:System.Threading.Tasks.Task%601>. Metoda vám umožňuje zadat pole adresy URL webových a termín nebo název pro hledání a potom vrátí počet pokusů, které se vyvolá hledaný termín v každé lokalitě.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Kompletní příklad, který obsahuje další zpracování výjimek a ukazuje, jak volat metodu z klientského kódu, naleznete v tématu [postupy: zalomení vzorů EAP v úloze](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Mějte na paměti, že každá úloha, která vytvoří <xref:System.Threading.Tasks.TaskCompletionSource%601> TaskCompletionSource se spustí, a proto by neměl volat metodu Start pro tento úkol uživatelského kódu.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementace vzoru APM pomocí úloh  
 V některých případech může být žádoucí zveřejnit přímo <xref:System.IAsyncResult> vzor pomocí dvojice metody Begin/End v rozhraní API. Například můžete chtít zachovat konzistenci pomocí stávajících rozhraní API, nebo jste automatizovali nástroje, které vyžadují tento model. V takovém případě můžete použít úkoly pro zjednodušení, jak je vzorek APM implementována interně.  
  
 Následující příklad ukazuje, jak použít úlohy k implementaci páru APM začátek/konec metody pro dlouho běžící výpočetní metodu.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Pomocí StreamExtensions ukázkového kódu  
 Soubor v Streamextensions.cs, [ukázky pro paralelní programování pomocí rozhraní .NET Framework 4](https://code.msdn.microsoft.com/ParExtSamples), obsahuje několik referenční implementace, které používají objekty úloh pro asynchronní soubory a vstupně-výstupní operace sítě.  
  
## <a name="see-also"></a>Viz také:

- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
