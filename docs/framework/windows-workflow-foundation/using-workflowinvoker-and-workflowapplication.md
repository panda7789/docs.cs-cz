---
title: Pomocí WorkflowInvoker a WorkflowApplication
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 6cbfca14eddeb82fc2d88b70703cae0fe59d63ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Pomocí WorkflowInvoker a WorkflowApplication
Windows Workflow Foundation (WF) poskytuje několik metod hostování pracovních postupů. <xref:System.Activities.WorkflowInvoker> poskytuje jednoduchý způsob pro vyvolání pracovního postupu, jako by byly volání metody a lze použít pouze pro pracovní postupy, které nepoužívají trvalost. <xref:System.Activities.WorkflowApplication> poskytuje bohatší model pro spouštění pracovních postupů, které obsahuje oznámení o události životního cyklu, řízení provádění, obnovení záložku a trvalost. <xref:System.ServiceModel.Activities.WorkflowServiceHost> poskytuje podporu pro aktivity zasílání zpráv a používá se především s služeb pracovních postupů. Toto téma vás seznámí s pracovního postupu hostování s <xref:System.Activities.WorkflowInvoker> a <xref:System.Activities.WorkflowApplication>. Další informace o hostování pracovních postupů s <xref:System.ServiceModel.Activities.WorkflowServiceHost>, najdete v části [služeb pracovních postupů](../../../docs/framework/wcf/feature-details/workflow-services.md) a [přehled hostování služeb pracovních postupů](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Pomocí WorkflowInvoker  
 <xref:System.Activities.WorkflowInvoker> poskytuje model pro provádění pracovního postupu, jako by šlo volání metody. K vyvolání pracovního postupu pomocí <xref:System.Activities.WorkflowInvoker>, volání <xref:System.Activities.WorkflowInvoker.Invoke%2A> metoda a předejte jí definice pracovního postupu pracovního postupu k vyvolání. V tomto příkladu <xref:System.Activities.Statements.WriteLine> aktivity vyvolání pomocí <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Při vyvolání pracovního postupu pomocí <xref:System.Activities.WorkflowInvoker>, pracovní postup spustí na volající vlákno a <xref:System.Activities.WorkflowInvoker.Invoke%2A> metoda blokuje až do dokončení v pracovním postupu, včetně všech doby nečinnosti. Pokud chcete nakonfigurovat interval časového limitu, ve kterém musíte dokončit pracovní postup, použijte jednu z <xref:System.Activities.WorkflowInvoker.Invoke%2A> přetížení, která přebírá <xref:System.TimeSpan> parametr. V tomto příkladu pracovní postup vyvolání dvakrát dva intervaly jiný časový limit. První complets pracovní postup, ale druhý není.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
>  <xref:System.TimeoutException> Je vyvolána pouze, pokud uplyne časový limit a pracovní postup bude nečinnosti během provádění. Pracovní postup, který trvá déle než zadaný časový interval pro dokončení se úspěšně dokončena, pokud pracovní postup nečinný.  
  
 <xref:System.Activities.WorkflowInvoker> také poskytuje asynchronní verze metodu invoke. Další informace naleznete v tématu <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> a <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Nastavení vstupní argumenty pracovního postupu  
 Data mohou být předána do pracovního postupu pomocí slovník vstupních parametrů klíčovány pomocí názvu argument, které jsou mapovány na vstupní argumenty pracovního postupu. V tomto příkladu <xref:System.Activities.Statements.WriteLine> je volána a hodnota jeho <xref:System.Activities.Statements.WriteLine.Text%2A> je zadán argument pomocí slovníku vstupní parametry.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Načítání výstupu argumenty pracovního postupu  
 Výstupní parametry pracovního postupu můžete získat pomocí výstupy slovník, který je vrácená z volání <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Následující příklad popisuje vyvolání pracovního postupu, který se skládá z jedné `Divide` aktivitu, že má dva vstupní argumenty a dva argumenty výstup. Po vyvolání pracovního postupu `arguments` byla předána slovník, který obsahuje hodnoty pro každý vstupní argument, klíčovány pomocí názvu argument. Při volání `Invoke` vrátí všechny argumenty výstup se vrátí v `outputs` slovník také klíčovány pomocí názvu argument.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 Pokud pracovní postup je odvozena z <xref:System.Activities.ActivityWithResult>, například `CodeActivity<TResult>` nebo `Activity<TResult>`, a výstup argumenty kromě dobře definovaný <xref:System.Activities.Activity%601.Result%2A> výstup argument, neobecnou přetížení `Invoke` musí být použit při načtení Další argumenty. K tomuto účelu definice pracovního postupu předané do `Invoke` musí být typu <xref:System.Activities.Activity>. V tomto příkladu `Divide` aktivity je odvozena z `CodeActivity<int>`, ale je deklarován jako <xref:System.Activities.Activity> tak, aby není obecný přetížení z `Invoke` je používá, která vrací slovníku argumentů místo jedné návratovou hodnotu.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>Pomocí WorkflowApplication  
 <xref:System.Activities.WorkflowApplication> poskytuje bohatou sadu funkcí pro správu instance pracovního postupu. <xref:System.Activities.WorkflowApplication> funguje jako proxy bezpečný přístup z více vláken na aktuálně <xref:System.Activities.Hosting.WorkflowInstance>, který zapouzdřuje modul runtime a poskytuje metody pro vytvoření a načtení instance pracovního postupu, pozastavení a obnovení, se ukončuje oznámení o události životního cyklu. Ke spuštění pracovního postupu pomocí <xref:System.Activities.WorkflowApplication> vytvoříte <xref:System.Activities.WorkflowApplication>, přihlásit k odběru událostí všechny požadované životního cyklu, spustit workflow a potom počkejte na její dokončení. V tomto příkladu definice pracovního postupu, se skládá z <xref:System.Activities.Statements.WriteLine> vytvoření aktivity a <xref:System.Activities.WorkflowApplication> je vytvořený pomocí definice pracovního postupu zadané. <xref:System.Activities.WorkflowApplication.Completed%2A> je zpracovat tak, že hostitel obdrží oznámení při dokončení pracovního postupu, pracovní postup je spuštěn s volání <xref:System.Activities.WorkflowApplication.Run%2A>, a potom hostitele čeká na dokončení pracovního postupu. Po dokončení pracovního postupu <xref:System.Threading.AutoResetEvent> je sada a hostiteli aplikace můžete pokračovat v provádění, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>Události životního cyklu WorkflowApplication  
 Kromě <xref:System.Activities.WorkflowApplication.Completed%2A>, autoři hostitele může být upozorněni, když pracovní postup je odpojen (<xref:System.Activities.WorkflowApplication.Unloaded%2A>), přerušených (<xref:System.Activities.WorkflowApplication.Aborted%2A>), stane nečinnosti (<xref:System.Activities.WorkflowApplication.Idle%2A> a <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>), nebo dojde k neošetřené výjimce (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>). Vývojáři aplikace pracovního postupu můžete zpracovat tato oznámení a proveďte příslušné akce, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Nastavení vstupní argumenty pracovního postupu  
 Data mohou být předána do pracovního postupu, jako je spuštěno pomocí slovník parametrů, podobně jako způsob data předaná při použití <xref:System.Activities.WorkflowInvoker>. Každá položka ve slovníku mapuje vstupní argument zadaný pracovního postupu. V tomto příkladu pracovní postup, se skládá z <xref:System.Activities.Statements.WriteLine> aktivity vyvolání a jeho <xref:System.Activities.Statements.WriteLine.Text%2A> je zadán argument pomocí slovníku vstupní parametry.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Načítání výstupu argumenty pracovního postupu  
 Po dokončení pracovního postupu, dá se načíst všechny argumenty výstup v <xref:System.Activities.WorkflowApplication.Completed%2A> obslužná rutina přímým přístupem <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> slovníku. V následujícím příkladu je hostitelem pracovního postupu pomocí <xref:System.Activities.WorkflowApplication>. A <xref:System.Activities.WorkflowApplication> instance je vytvořený pomocí definice pracovního postupu, který se skládá z jedné `DiceRoll` aktivity. `DiceRoll` Aktivita má dva argumenty výstup, které reprezentují výsledky operace vrácení rozčlenění. Po dokončení pracovního postupu výstupy jsou načteny v <xref:System.Activities.WorkflowApplication.Completed%2A> obslužné rutiny.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
>  <xref:System.Activities.WorkflowApplication> a <xref:System.Activities.WorkflowInvoker> trvat slovník vstupní argumenty a vrátí slovník `out` argumenty. Tyto slovník parametrů, vlastnosti a návratové hodnoty jsou typu `IDictionary<string, object>`. Skutečné instance třídy slovník, který se předává v může být jakákoli třída, která implementuje `IDictionary<string, object>`. V těchto příkladech `Dictionary<string, object>` se používá. Další informace o slovnících najdete v tématu <xref:System.Collections.Generic.IDictionary%602> a <xref:System.Collections.Generic.Dictionary%602>.  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Předávání dat do pracovního postupu spuštění použití záložek  
 Záložky jsou mechanismus, pomocí kterého aktivity může být obnoven pasivně čekat a jsou mechanismus pro předávání dat do spuštěné instance pracovního postupu. Pokud aktivita čeká na data, můžete vytvořit <xref:System.Activities.Bookmark> a metody zpětného volání, která se má volat při registraci <xref:System.Activities.Bookmark> obnovena, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Po provedení `ReadLine` vytvoří aktivity <xref:System.Activities.Bookmark>, zaregistruje zpětné volání a potom počká, než <xref:System.Activities.Bookmark> být obnoven. Při obnovení, `ReadLine` aktivity přiřadí data, která byla předána s <xref:System.Activities.Bookmark> k jeho <xref:System.Activities.Activity%601.Result%2A> argument. V tomto příkladu se vytvoří pracovní postup používající `ReadLine` aktivity shromažďovat uživatelské jméno a zobrazit ji do okna konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Když `ReadLine` aktivita se spustí, vytvoří <xref:System.Activities.Bookmark> s názvem `UserName` a potom počká, než záložku být obnoven. Hostitel shromažďuje k požadovaným datům a potom obnoví <xref:System.Activities.Bookmark>. Pracovní postup obnoví, zobrazí název a potom dokončí.  
  
 Hostitelskou aplikaci můžete prohlédnout v pracovním postupu určí, jestli jsou všechny aktivní záložky. Voláním ho můžete to provést <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> metodu <xref:System.Activities.WorkflowApplication> instanci, nebo pomocí kontroly <xref:System.Activities.WorkflowApplicationIdleEventArgs> v <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutiny.  
  
 Následující příklad kódu je jako předchozí příklad, s tím rozdílem, že aktivní záložky jsou uvedené předtím, než je obnoveno záložky. Spuštění pracovního postupu a jednou <xref:System.Activities.Bookmark> je vytvořena a pracovní postup přejde nečinnosti, <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> je volána. Po dokončení pracovního postupu se zobrazí následující výstup do konzoly.  
  
 **Jak se jmenuješ?**  
**NázevZáložky: Uživatelské jméno - OwnerDisplayName: ReadLine**   
**Steve**   
**Hello, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Následující příklad kódu zkontroluje <xref:System.Activities.WorkflowApplicationIdleEventArgs> předaný do <xref:System.Activities.WorkflowApplication.Idle%2A> obslužnou rutinu <xref:System.Activities.WorkflowApplication> instance. V tomto příkladu budete nečinnosti pracovní postup obsahuje jednu <xref:System.Activities.Bookmark> s názvem `EnterGuess`, která aktivitou s názvem `ReadInt`. Tento příklad kódu je na základě odhlásit z [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md), který je součástí [kurzu Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md). Pokud <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutiny v tomto kroku se mění tak, aby obsahovala kód z tohoto příkladu, zobrazí se následující výstup.  
  
 **NázevZáložky: EnterGuess - OwnerDisplayName: readint –**
 
 [!code-csharp[CFX_WorkflowApplicationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Souhrn  
 <xref:System.Activities.WorkflowInvoker> poskytuje jednoduché způsob, jak volat pracovní postupy, a sice poskytuje metody pro předávání dat v při spuštění pracovního postupu a extrahování dat z dokončené pracovního postupu, neposkytuje pro složitější scénáře tedy kde <xref:System.Activities.WorkflowApplication> lze použít.
