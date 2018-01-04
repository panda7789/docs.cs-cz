---
title: "TPL a tradiční asynchronní programování v .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 50c4f9cfeb135f1046fbb427585897ca99248afd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL a tradiční asynchronní programování v .NET Framework
Rozhraní .NET Framework poskytuje následující dva standardní vzory pro provádění I/čítači a výpočetních asynchronní operace:  
  
-   Asynchronní programování modelu (APM), ve kterém asynchronní operace jsou reprezentované pomocí pár začátek/konec metody, jako <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
-   Na základě událostí asynchronního vzoru (EAP), ve kterém jsou asynchronní operace reprezentována pár metoda/událost, která jsou pojmenované *OperationName*asynchronní a *OperationName*dokončit, například <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> a <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (EAP byla zavedena v rozhraní .NET Framework verze 2.0).  
  
 Task Parallel Library (TPL) lze použít v různých způsobů ve spojení s buď asynchronní zpracování. Operace APM a EAP jako úlohy můžou zpřístupnit k příjemce knihovny, nebo můžete vystavit vzory amp ale použít objekty úloh pro jejich implementaci interně. V obou případech pomocí úlohy objektů můžete zjednodušit kód a využít užitečné následující funkce:  
  
-   Registrace zpětných volání, ve formě pokračování úlohy, kdykoli po spuštění úlohy.  
  
-   Koordinaci více operací, které jsou spouštěny v reakci na `Begin_` metodu, pomocí <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody, nebo <xref:System.Threading.Tasks.Task.WaitAll%2A> metoda nebo <xref:System.Threading.Tasks.Task.WaitAny%2A> metoda.  
  
-   Zapouzdření asynchronních I/čítači a výpočetních operací ve stejném objektu úlohy.  
  
-   Monitorování stavu objekt úlohy.  
  
-   Zařazování stav operace pro objekt úlohy pomocí <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Úloha zabalení APM  
 Jak <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> a <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> třídy poskytují několik přetížení <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody, které umožňují zapouzdření dvojici APM začátek/konec metoda v jednom <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> instance. Různé přetížení pojmout všechny dvojice začátek/konec metoda, která mají od nuly do tří vstupní parametry.  
  
 Pro dvojice, které mají `End` metody, které vrací hodnotu (`Function` v jazyce Visual Basic), pomocí metod v nástroji <xref:System.Threading.Tasks.TaskFactory%601> , vytvoření <xref:System.Threading.Tasks.Task%601>. Pro `End` metody, které vracet typ void (`Sub` v jazyce Visual Basic), pomocí metod v nástroji <xref:System.Threading.Tasks.TaskFactory> , vytvoření <xref:System.Threading.Tasks.Task>.  
  
 Pro několik případů, ve kterém `Begin` metoda má víc než třemi parametry, nebo obsahuje `ref` nebo `out` parametry, další `FromAsync` přetížení, které zapouzdřuje pouze `End` metoda jsou k dispozici.  
  
 Následující příklad ukazuje podpis pro `FromAsync` přetížení, které odpovídá <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> metody. Toto přetížení přijímá tři vstupní parametry, následujícím způsobem.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 První parametr je <xref:System.Func%606> delegáta, který odpovídá podpis <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metoda. Druhý parametr je <xref:System.Func%602> delegáta, který přebírá <xref:System.IAsyncResult> a vrátí `TResult`. Protože <xref:System.IO.FileStream.EndRead%2A> vrátí celé číslo, kompilátor odvodí typ `TResult` jako <xref:System.Int32> a typ úlohy, jako <xref:System.Threading.Tasks.Task>. Poslední čtyři parametry jsou stejné jako v <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metoda:  
  
-   Vyrovnávací paměť, do které chcete uložit datové soubory.  
  
-   Posunutí ve vyrovnávací paměti, pro kterou chcete zahájit zápis dat.  
  
-   Maximální množství dat ke čtení ze souboru.  
  
-   Volitelný objekt, který ukládá data o stavu uživatelem definované předat zpětné volání.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Použití ContinueWith pro funkci zpětného volání  
 Pokud budete potřebovat přístup k datům v souboru oproti právě počet bajtů, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metoda není dostatečná. Místo toho použijte <xref:System.Threading.Tasks.Task>, jejichž `Result` vlastnost obsahuje datový soubor. Můžete provést přidáním pokračování do původního úkolu. Pokračování provede práci, které by obvykle provádí pomocí <xref:System.AsyncCallback> delegovat. Vyvolání při dokončení předchůdce a naplní datová vyrovnávací paměť. ( <xref:System.IO.FileStream> Objekt by měly být ukončeny před vrácením.)  
  
 Následující příklad ukazuje, jak vrátit <xref:System.Threading.Tasks.Task> který zapouzdřuje dvojici BeginRead/EndRead <xref:System.IO.FileStream> třídy.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Metoda pak jde volat, následujícím způsobem.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Poskytuje stav vlastní Data  
 V typické <xref:System.IAsyncResult> operace, pokud vaše <xref:System.AsyncCallback> delegáta vyžaduje některá vlastní stavová data, budete muset v předání poslední parametr v `Begin` metoda, tak, aby mohla být zabalena data do <xref:System.IAsyncResult> objekt, který se nakonec byl předán metoda zpětného volání. Toto není obvykle nutné při `FromAsync` metody se používají. Pokud je k pokračování je znám vlastních dat, potom ji můžete zachytit přímo v delegát pokračování. V následujícím příkladu vypadá takto: na předchozí příklad, ale místo zkoumání `Result` vlastnost předchůdce pokračování prozkoumá stav vlastní data, která je přímo přístupný uživatelskému delegátovi pokračování.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Synchronizace více FromAsync úloh  
 Statické <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody poskytují přidané flexibilitu při použití ve spojení s `FromAsync` metody. Následující příklad ukazuje, jak zahájit více asynchronní vstupně-výstupních operací, a pak počkat na jejich dokončení před spuštěním pokračování.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>FromAsync úlohy pouze End – metoda  
 Pro několik případů, ve kterém `Begin` metoda vyžaduje víc než třemi vstupní parametry, nebo má `ref` nebo `out` parametry, můžete použít `FromAsync` přetížení, například <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, které představují pouze `End`metoda. Tyto metody lze také v žádném scénáři, ve kterém jsou předány <xref:System.IAsyncResult> a chcete zapouzdření v úloze.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Spuštění a zrušení FromAsync úlohy  
 Úloha vrácená `FromAsync` metoda má stav WaitingForActivation a bude spuštěna v systému v určitém okamžiku po vytvoření úlohy. Pokud se pokusíte volání začátku u takových úloh, bude vyvolána výjimka.  
  
 Nelze zrušit `FromAsync` úloh, protože základní rozhraní .NET Framework API aktuálně nepodporují Probíhá zrušení souboru nebo sítě vstupně-výstupní operace. Můžete přidat funkcionalitu zrušení metodě, který zapouzdřuje `FromAsync` volání, ale nemůže reagovat na zrušení před `FromAsync` voláním nebo po jeho dokončení (například v úloze pokračování).  
  
 Některé třídy, které podporují protokol EAP, například <xref:System.Net.WebClient>, podporují zrušení a tuto funkci nativního zrušení můžete integrovat pomocí zrušení tokenů.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Vystavení složité EAP operace jako úlohy  
 TPL neposkytuje žádné metody, které jsou vytvořené speciálně pro zapouzdření na základě událostí asynchronní operace ve stejné způsobem, jako `FromAsync` rodině metod kolem <xref:System.IAsyncResult> vzor. Však poskytuje TPL <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> třídy, která slouží k reprezentaci jakékoli sady operací, jako <xref:System.Threading.Tasks.Task%601>. Operace může být synchronní nebo asynchronní a může být vázána vstupně-výstupních operací nebo výpočetních nebo obojí.  
  
 Následující příklad ukazuje, jak používat <xref:System.Threading.Tasks.TaskCompletionSource%601> vystavit sadu asynchronní <xref:System.Net.WebClient> operací pro klientský kód jako základní <xref:System.Threading.Tasks.Task%601>. Metoda slouží k zadání pole webové adresy URL a termín nebo název pro vyhledávání a vrátí počet k hledaný termín dochází v každé lokalitě.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Úplnější příklad, který obsahuje další zpracování výjimek a ukazuje, jak volat metodu z kódu klienta, najdete v části [postupy: zalomení vzoru EAP v úloze](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Mějte na paměti, že žádné úloha, která byla vytvořena ve <xref:System.Threading.Tasks.TaskCompletionSource%601> bude zahájena v TaskCompletionSource, a proto by nemělo uživatelského kódu volat metodu Start na úlohu.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementace vzoru APM pomocí úloh  
 V některých případech může být žádoucí přímo vystavit <xref:System.IAsyncResult> vzor pomocí dvojice začátek/konec metoda v rozhraní API. Například můžete chtít zachovat konzistenci s stávajících rozhraní API, nebo máte automatizované nástroje, které vyžadují tento vzor. V takových případech můžete úlohy ke zjednodušení tom, jak interně implementují vzoru APM.  
  
 Následující příklad ukazuje, jak použít k implementaci dvojici APM začátek/konec metoda pro výpočetní metody dlouho běžící úlohy.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Pomocí StreamExtensions ukázkový kód  
 V Streamextensions.cs soubor v [ukázky pro paralelní programování v rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=165717) na webu MSDN, obsahuje několik odkaz implementace, které objekty úlohy použít pro asynchronní soubor a síťový vstupně-výstupních operací.  
  
## <a name="see-also"></a>Viz také  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
