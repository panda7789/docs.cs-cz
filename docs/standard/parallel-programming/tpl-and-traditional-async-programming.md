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
ms.openlocfilehash: 7db031c655980dd800de77cbbd6a07a0ba94b33b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284881"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL a tradiční asynchronní programování v .NET Framework
.NET Framework poskytuje následující dva standardní vzory pro provádění asynchronních operací vstupně-výstupních operací a výpočtů vázaných na výpočetní prostředky:  
  
- Asynchronní programovací model (APM), ve kterém jsou asynchronní operace reprezentovány dvojicí metod begin/end, jako jsou <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType> .  
  
- Asynchronní vzor založený na událostech (EAP), ve kterém jsou asynchronní operace reprezentované dvojicí metoda/událost, která má název *OperationName*Async a *operace*dokončena, například <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> a <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType> . (Protokol EAP byl představený v .NET Framework verze 2,0.)  
  
 Task Parallel Library (TPL) lze použít různými způsoby ve spojení s jedním z asynchronních vzorů. Můžete vystavit operace APM i EAP jako úlohy pro příjemce knihovny, nebo můžete vystavit vzory APM, ale použít objekty úlohy k jejich implementaci interně. V obou případech pomocí objektů úkolů můžete zjednodušit kód a využít následující užitečné funkce:  
  
- Zaregistrujte zpětná volání ve formě pokračování úlohy, kdykoli po spuštění úlohy.  
  
- Koordinovat více operací, které jsou spouštěny v reakci na `Begin_` metodu, pomocí <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> metod a nebo metody <xref:System.Threading.Tasks.Task.WaitAll%2A> nebo <xref:System.Threading.Tasks.Task.WaitAny%2A> metody.  
  
- Zapouzdřit asynchronní operace vázané na vstupně-výstupní operace a výpočetní operace v rámci stejného objektu Task.  
  
- Monitoruje stav objektu úlohy.  
  
- Zařazení stavu operace do objektu úlohy pomocí <xref:System.Threading.Tasks.TaskCompletionSource%601> .  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Zabalení operací APM do úlohy  
 <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> Třídy i poskytují několik přetížení <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metod a, které umožňují zapouzdřit dvojici metod begin/end APM v jednom <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> instanci. Různá přetížení přibývají libovolné dvojici metod begin/end, které mají od nuly až tří vstupních parametrů.  
  
 Pro páry, které mají `End` metody, které vracejí hodnotu ( `Function` v Visual Basic), použijte metody v <xref:System.Threading.Tasks.TaskFactory%601> , které vytvoří <xref:System.Threading.Tasks.Task%601> . Pro `End` metody, které vracejí typ void ( `Sub` v Visual Basic), použijte metody v <xref:System.Threading.Tasks.TaskFactory> , které vytvoří <xref:System.Threading.Tasks.Task> .  
  
 V několika případech, ve kterých `Begin` má metoda více než tři parametry nebo obsahuje `ref` parametry nebo `out` , jsou k `FromAsync` dispozici další přetížení, která zapouzdřuje pouze `End` metodu.  
  
 Následující příklad ukazuje signaturu pro `FromAsync` přetížení, která odpovídá <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> metodám a. Toto přetížení používá tři vstupní parametry, a to následujícím způsobem.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 První parametr je <xref:System.Func%606> delegát, který se shoduje s signaturou <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metody. Druhý parametr je <xref:System.Func%602> delegát, který přebírá <xref:System.IAsyncResult> a vrátí `TResult` . Vzhledem <xref:System.IO.FileStream.EndRead%2A> k tomu, že vrací celé číslo, kompilátor odvodí typ `TResult` jako <xref:System.Int32> a typ úlohy <xref:System.Threading.Tasks.Task> . Poslední čtyři parametry jsou stejné jako v <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> metodě:  
  
- Vyrovnávací paměť, do které se mají ukládat data souboru  
  
- Posun ve vyrovnávací paměti, kdy začít zapisovat data.  
  
- Maximální množství dat, které se má načíst ze souboru.  
  
- Volitelný objekt, který ukládá uživatelem definovaná data o stavu, která budou předána zpětnému volání.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Použití ContinueWith pro funkci zpětného volání  
 Pokud budete vyžadovat přístup k datům v souboru, nikoli pouze k počtu bajtů, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> metoda není dostačující. Místo toho použijte <xref:System.Threading.Tasks.Task> , jehož `Result` vlastnost obsahuje data souboru. To lze provést přidáním pokračování do původní úlohy. Pokračování provede práci, kterou by obvykle prováděl <xref:System.AsyncCallback> delegát. Vyvolá se po dokončení předchůdce a vyrovnávací paměť dat byla vyplněna. ( <xref:System.IO.FileStream> Objekt by měl být před vrácením zavřen.)  
  
 Následující příklad ukazuje, jak vrátit <xref:System.Threading.Tasks.Task> , který zapouzdřuje dvojici BeginRead/funkci EndRead <xref:System.IO.FileStream> třídy.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Metodu lze následně volat následujícím způsobem.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Poskytování vlastních dat o stavu  
 V typických <xref:System.IAsyncResult> operacích, pokud váš <xref:System.AsyncCallback> delegát požaduje některá vlastní data stavu, je nutné jej předat prostřednictvím posledního parametru v `Begin` metodě, aby bylo možné data zabalit do <xref:System.IAsyncResult> objektu, který je nakonec předán metodě zpětného volání. To obvykle není nutné při `FromAsync` použití metod. Pokud jsou pro pokračování známa vlastní data, lze ji zachytit přímo v delegátu pokračování. Následující příklad je podobný předchozímu příkladu, ale místo prověření `Result` vlastnosti předchůdce kontroluje pokračování vlastní data stavu, která jsou přímo přístupná uživatelskému delegátu pokračování.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Synchronizace více FromAsync úloh  
 Statické <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> metody a <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> poskytují zvýšení flexibility při použití ve spojení s `FromAsync` metodami. Následující příklad ukazuje, jak spustit více asynchronních vstupně-výstupních operací a pak počkat na jejich dokončení před provedením pokračování.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>FromAsync úlohy pouze pro metodu end  
 Pro několik případů, ve kterých `Begin` metoda vyžaduje více než tři vstupní parametry, nebo má `ref` parametry nebo `out` , můžete použít `FromAsync` přetížení, například, <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType> která představuje pouze `End` metodu. Tyto metody lze také použít v jakémkoli scénáři, ve kterém jste předali <xref:System.IAsyncResult> a chcete ji zapouzdřit do úlohy.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Spuštění a zrušení FromAsync úlohy  
 Úloha vrácená `FromAsync` metodou má stav WaitingForActivation a bude systémem spuštěna v určitém okamžiku po vytvoření úkolu. Při pokusu o volání metody Start na takovou úlohu bude vyvolána výjimka.  
  
 Úlohu nelze zrušit `FromAsync` , protože podkladová rozhraní API pro .NET Framework aktuálně nepodporují zrušení probíhajícího rušení souboru nebo síťové vstupně-výstupních operací. Můžete přidat funkci zrušení do metody, která zapouzdřuje `FromAsync` volání, ale můžete pouze reagovat na zrušení před `FromAsync` voláním nebo po dokončení (například v úloze pokračování).  
  
 Některé třídy, které podporují protokol EAP, například podporují <xref:System.Net.WebClient> zrušení a můžete integrovat tuto nativní funkci zrušení pomocí tokenů zrušení.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Vystavení složitých operací EAP jako úloh  
 TPL neposkytuje žádné metody, které jsou určeny konkrétně k zapouzdření asynchronní operace založené na událostech stejným způsobem, jakým `FromAsync` rodina metod zabalí <xref:System.IAsyncResult> vzor. TPL však poskytuje <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> třídu, kterou lze použít k reprezentaci libovolné sady operací jako <xref:System.Threading.Tasks.Task%601> . Operace můžou být synchronní nebo asynchronní a můžou být vázané na vstupně-výstupní operace nebo výpočetní výkon nebo obojí.  
  
 Následující příklad ukazuje, jak použít <xref:System.Threading.Tasks.TaskCompletionSource%601> k vystavení sady asynchronních <xref:System.Net.WebClient> operací pro klientský kód jako základní <xref:System.Threading.Tasks.Task%601> . Metoda umožňuje zadat pole webových adres URL a termín nebo název, který se má vyhledat, a potom vrátí počet výskytů hledaného termínu v každé lokalitě.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Pro úplnější příklad, který obsahuje další zpracování výjimek a ukazuje, jak volat metodu z klientského kódu, naleznete v tématu [How to: Wrap Patterns EAP in a Task](how-to-wrap-eap-patterns-in-a-task.md).  
  
 Mějte na paměti, že každý úkol, který je vytvořen pomocí <xref:System.Threading.Tasks.TaskCompletionSource%601> , bude spuštěn tímto TaskCompletionSource, a proto by kód uživatele neměl volat metodu Start tohoto úkolu.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementace vzoru APM pomocí úloh  
 V některých scénářích může být vhodné přímo vystavit <xref:System.IAsyncResult> vzor pomocí párů begin/end metod v rozhraní API. Můžete například chtít zachovat konzistenci se stávajícími rozhraními API nebo můžete mít automatizované nástroje, které vyžadují tento model. V takových případech můžete pomocí úloh zjednodušit způsob, jakým se model APM implementuje interně.  
  
 Následující příklad ukazuje, jak použít úlohy pro implementaci páru APM begin/end Method pro dlouhou běžící výpočetní metodu.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Použití ukázkového kódu StreamExtensions  
 Soubor *Streamextensions.cs* v úložišti [extra rozšíření .NET Standard Parallel Extensions](/samples/dotnet/samples/parallel-programming-extensions-extras-cs/) obsahuje několik referenčních implementací, které používají `Task` objekty pro asynchronní soubory a vstupně-výstupní operace sítě.
  
## <a name="see-also"></a>Viz také

- [Task Parallel Library (TPL)](task-parallel-library-tpl.md)
