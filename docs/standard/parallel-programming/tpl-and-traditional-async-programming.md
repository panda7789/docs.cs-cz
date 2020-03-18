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
ms.openlocfilehash: 27766c10d0624b5eda8256a3211662036a1b16b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139947"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL a tradiční asynchronní programování v .NET Framework
Rozhraní .NET Framework poskytuje následující dva standardní vzory pro provádění vstupně-výstupních a výpočetních asynchronních operací:  
  
- Asynchronní programovací model (APM), ve kterém jsou asynchronní operace reprezentovány <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> dvojicí metod Begin/End, například a <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
- Asynchronní vzor založený na událostech (EAP), ve kterém jsou asynchronní operace reprezentovány dvojicí metod nebo událostí <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> s <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>názvem *OperationName*Async a *OperationName*Completed, například a . (EAP byl zaveden v rozhraní .NET Framework verze 2.0.)  
  
 Paralelní knihovna úloh (TPL) lze použít různými způsoby ve spojení s některou z asynchronních vzorů. Můžete vystavit apm a EAP operace jako úkoly pro spotřebitele knihovny nebo můžete vystavit vzorky APM, ale použít Task objekty k jejich implementaci interně. V obou scénářích můžete pomocí task objekty, můžete zjednodušit kód a využít následující užitečné funkce:  
  
- Zaregistrujte zpětná volání ve formě pokračování úkolu kdykoli po zahájení úkolu.  
  
- Koordinujte více operací, které se provádějí v <xref:System.Threading.Tasks.Task.WaitAll%2A> reakci na <xref:System.Threading.Tasks.Task.WaitAny%2A> metodu `Begin_` pomocí metody <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> nebo metody nebo metody.  
  
- Zapouzdření asynchronních operací vázaných na vstupně-výstupníoperace a výpočetních operací ve stejném objektu Task.  
  
- Sledujte stav objektu Task.  
  
- Zařazování stavu operace na <xref:System.Threading.Tasks.TaskCompletionSource%601>objekt Task pomocí .  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Zabalení operací APM do úlohy  
 <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> A <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> třídy poskytují několik přetížení <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> a metody, které umožňují zapouzdřit dvojice <xref:System.Threading.Tasks.Task> metody <xref:System.Threading.Tasks.Task%601> APM Begin/End v jedné nebo instanci. Různé přetížení ubytovat všechny Begin/End dvojice metod, které mají od nuly do tří vstupních parametrů.  
  
 Pro dvojice, `End` které mají metody,`Function` které vracejí hodnotu <xref:System.Threading.Tasks.TaskFactory%601> (v <xref:System.Threading.Tasks.Task%601>jazyce Visual Basic), použijte metody v tomto vytvořit . Pro `End` metody, které`Sub` vrátí void ( v <xref:System.Threading.Tasks.TaskFactory> jazyce <xref:System.Threading.Tasks.Task>Visual Basic), použijte metody v tomto vytvořit .  
  
 Pro těch několik případů, `Begin` ve kterých má `ref` metoda `out` více než `FromAsync` tři parametry nebo obsahuje `End` nebo parametry, další přetížení, které zapouzdřují pouze metodu jsou k dispozici.  
  
 Následující příklad ukazuje podpis `FromAsync` pro přetížení, <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> které odpovídá a metody. Toto přetížení trvá tři vstupní parametry, takto.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 První parametr je <xref:System.Func%606> delegát, který odpovídá <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> podpisu metody. Druhý parametr je <xref:System.Func%602> delegát, <xref:System.IAsyncResult> který trvá `TResult`a vrátí . Protože <xref:System.IO.FileStream.EndRead%2A> vrátí celé číslo, kompilátor odvodí typ `TResult` as <xref:System.Int32> a <xref:System.Threading.Tasks.Task>typ úkolu jako . Poslední čtyři parametry jsou shodné <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> s parametry v metodě:  
  
- Vyrovnávací paměť, do které chcete uložit data souboru.  
  
- Posun ve vyrovnávací paměti, ve kterém chcete začít zápis dat.  
  
- Maximální množství dat pro čtení ze souboru.  
  
- Volitelný objekt, který ukládá uživatelem definovaná data stavu pro předání zpětnému volání.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Použití funkce continuewith pro funkce zpětného volání  
 Pokud požadujete přístup k datům v souboru, na rozdíl od <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> pouze počet bajtů, metoda není dostatečná. Místo toho <xref:System.Threading.Tasks.Task>použijte `Result` , jehož vlastnost obsahuje data souboru. To lze provést přidáním pokračování původní úlohy. Pokračování provádí práci, která by obvykle <xref:System.AsyncCallback> provádí delegát. Je vyvolána po dokončení předchůdce a vyrovnávací paměť dat byla vyplněna. (Objekt <xref:System.IO.FileStream> by měl být uzavřen před návratem.)  
  
 Následující příklad ukazuje, jak <xref:System.Threading.Tasks.Task> vrátit, který zapouzdřuje BeginRead/EndRead pár <xref:System.IO.FileStream> třídy.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Metoda pak může být volána následujícím způsobem.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Poskytování vlastních dat stavu  
 V <xref:System.IAsyncResult> typické operace, <xref:System.AsyncCallback> pokud váš delegát vyžaduje některá vlastní data stavu, `Begin` je nutné předat prostřednictvím poslední parametr <xref:System.IAsyncResult> v metodě, tak, aby data mohou být zabaleny do objektu, který je nakonec předán metodě zpětného volání. To obvykle není vyžadováno `FromAsync` při použití metod. Pokud vlastní data je známo, že pokračování, pak může být zachycena přímo v delegáta pokračování. Následující příklad se podobá předchozímu příkladu, `Result` ale namísto zkoumání vlastnosti předchůdce, pokračování zkoumá vlastní stav dat, která je přímo přístupná pro delegáta uživatele pokračování.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Synchronizace více úloh FromAsync  
 Statické <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metody poskytují větší flexibilitu při `FromAsync` použití ve spojení s metodami. Následující příklad ukazuje, jak zahájit více asynchronních vstupně-va operací a potom čekat na dokončení všech z nich před spuštěním pokračování.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>FromAsync úlohy pouze end metoda  
 `Begin` Pro těch několik případů, `ref` `out` `FromAsync` <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>ve kterých metoda vyžaduje více než tři vstupní parametry nebo má nebo parametry, můžete použít přetížení, například , které představují pouze metodu. `End` Tyto metody lze také použít v libovolném <xref:System.IAsyncResult> scénáři, ve kterém jsou předány a chcete zapouzdřit do Task.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Spuštění a zrušení úloh fromAsync  
 Úloha vrácená `FromAsync` metodou má stav WaitingForActivation a bude spuštěna systémem v určitém okamžiku po vytvoření úlohy. Pokud se pokusíte volat Start na takový úkol, bude vyvolána výjimka.  
  
 `FromAsync` Úkol nelze zrušit, protože základní rozhraní API rozhraní .NET Framework aktuálně nepodporují probíhající zrušení vstupně-nevstupně-videa. Můžete přidat funkce zrušení metody, která zapouzdřuje `FromAsync` volání, ale můžete `FromAsync` odpovědět pouze na zrušení před je volána nebo po jeho dokončení (například v pokračování úkolu).  
  
 Některé třídy, které podporují <xref:System.Net.WebClient>EAP, například , podporují zrušení a můžete integrovat tuto nativní funkci zrušení pomocí tokenů zrušení.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Vystavení složitých operací EAP jako úkolů  
 TPL neposkytuje žádné metody, které jsou speciálně navrženy tak, aby zapouzdřit `FromAsync` asynchronní <xref:System.IAsyncResult> operace založené na událostech stejným způsobem, že rodina metod zabalit vzor. TPL však poskytuje <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> třídu, kterou lze použít k reprezentaci <xref:System.Threading.Tasks.Task%601>libovolné sady operací jako . Operace mohou být synchronní nebo asynchronní a mohou být vázány vstupně-výstupními operacemi nebo vázány na výpočetní prostředky nebo obojí.  
  
 Následující příklad ukazuje, jak <xref:System.Threading.Tasks.TaskCompletionSource%601> použít sadu asynchronních <xref:System.Net.WebClient> operací do klientského <xref:System.Threading.Tasks.Task%601>kódu jako základní . Tato metoda umožňuje zadat pole webových adres URL a termín nebo název, který chcete vyhledat, a potom vrátí počet výskytů hledaného výrazu na jednotlivých webech.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Pro úplnější příklad, který zahrnuje další zpracování výjimek a ukazuje, jak volat metodu z kódu klienta, naleznete v [tématu How to: Wrap EAP Patterns in a Task](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Nezapomeňte, že všechny úkoly, které jsou vytvořeny <xref:System.Threading.Tasks.TaskCompletionSource%601> bude spuštěn a to TaskCompletionSource a proto uživatelský kód by neměl volat Start metoda na tento úkol.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementace vzoru APM pomocí úloh  
 V některých scénářích může být <xref:System.IAsyncResult> žádoucí přímo vystavit vzor pomocí begin/end dvojice metod v rozhraní API. Můžete například chtít zachovat konzistenci s existujícími api nebo můžete mít automatizované nástroje, které vyžadují tento vzor. V takových případech můžete pomocí tasks zjednodušit, jak je interně implementován vzor APM.  
  
 Následující příklad ukazuje, jak pomocí úloh implementovat dvojici metod APM Begin/End pro dlouho běžící metodu vázanou na výpočetní výkon.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Použití ukázkového kódu StreamExtensions  
 Soubor Streamextensions.cs v [ukázkách pro paralelní programování s rozhraním .NET Framework 4](https://code.msdn.microsoft.com/ParExtSamples)obsahuje několik referenčních implementací, které používají objekty Task pro asynchronní soubor a vstupně-v.  
  
## <a name="see-also"></a>Viz také

- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
