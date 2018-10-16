---
title: Použití WorkflowInvoker a WorkflowApplication
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: cc315013ce50539eb4b72d26848a99164bb6b2d0
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347978"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Použití WorkflowInvoker a WorkflowApplication
Windows Workflow Foundation (WF) poskytuje několik způsobů hostování pracovních postupů. <xref:System.Activities.WorkflowInvoker> poskytuje jednoduchý způsob pro volání pracovního postupu, jako kdyby byly volání metody a lze použít pouze pro pracovní postupy, které nepoužívají trvalosti. <xref:System.Activities.WorkflowApplication> poskytuje širší model pro spouštění pracovních postupů, které obsahuje oznámení o události životního cyklu, řízení provádění, záložku obnovení a trvalost. <xref:System.ServiceModel.Activities.WorkflowServiceHost> poskytuje podporu pro zasílání zpráv aktivity a se primárně používají služby pracovního postupu. Toto téma vás seznámí s hostování pracovního postupu se <xref:System.Activities.WorkflowInvoker> a <xref:System.Activities.WorkflowApplication>. Další informace o hostování pracovních postupů pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, naleznete v tématu [služeb pracovních postupů](../../../docs/framework/wcf/feature-details/workflow-services.md) a [přehled hostování služeb pracovních postupů](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Použití WorkflowInvoker  
 <xref:System.Activities.WorkflowInvoker> poskytuje model pro provádění pracovního postupu, jako by šlo volání metody. K vyvolání pracovního postupu pomocí <xref:System.Activities.WorkflowInvoker>, zavolejte <xref:System.Activities.WorkflowInvoker.Invoke%2A> a předáte v definici pracovního postupu pracovního postupu, který má být vyvolán. V tomto příkladu <xref:System.Activities.Statements.WriteLine> aktivity je vyvolán pomocí <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Když pracovní postup je vyvolán pomocí <xref:System.Activities.WorkflowInvoker>, pracovní postup spustí na volajícím vlákně a <xref:System.Activities.WorkflowInvoker.Invoke%2A> metoda blokuje, dokud se nedokončí, včetně kdykoli nečinného pracovního postupu. Pokud chcete nakonfigurovat interval časového limitu, ve kterém musíte dokončit pracovní postup, použijte jednu z <xref:System.Activities.WorkflowInvoker.Invoke%2A> přetížení, která přijímá <xref:System.TimeSpan> parametr. V tomto příkladu je pracovní postup volána dvakrát s dva intervaly různých časového limitu. První pracovní postup skončí, ale druhá ne.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
>  <xref:System.TimeoutException> Je vyvolána pouze když uplyne časový limit a pracovního postupu změní nečinnosti během provádění. Pracovní postup, který trvá déle než interval zadaný časový limit na dokončení se úspěšně dokončí, pokud pracovní postup nečinný.  
  
 <xref:System.Activities.WorkflowInvoker> také poskytuje asynchronní verze metody invoke. Další informace naleznete v tématu <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> a <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Vstupní argumenty nastavení pracovního postupu  
 Data mohou být předány do pracovního postupu pomocí slovníku vstupních parametrů, s klíči název argumentu, které se mapují na vstupní argumenty pracovního postupu. V tomto příkladu <xref:System.Activities.Statements.WriteLine> je vyvolána a hodnotu pro jeho <xref:System.Activities.Statements.WriteLine.Text%2A> je zadán argument pomocí slovníku vstupní parametry.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Načítání výstupní argumenty pracovního postupu  
 Výstupní parametry pracovního postupu lze zjistit pomocí slovníku výstupy vrácené z volání <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Následující příklad vyvolá pracovní postup, který se skládá z jedné `Divide` aktivitu, má dva vstupní argumenty a výstupu dva argumenty. Když uživatel vyvolá pracovní postup, `arguments` slovník je předán, který obsahuje hodnoty pro každý vstupní argument, s klíči název argumentu. Při volání `Invoke` vrátí, každý argument výstup se vrátí v `outputs` slovníku. Tím se také s klíči název argumentu.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 Pokud pracovní postup je odvozena z <xref:System.Activities.ActivityWithResult>, jako například `CodeActivity<TResult>` nebo `Activity<TResult>`, a výstupní argumenty kromě jasně definovaných <xref:System.Activities.Activity%601.Result%2A> výstupní argument obecné přetížení `Invoke` nutné použít k načtení Další argumenty. K tomuto účelu definice pracovního postupu předané do `Invoke` musí být typu <xref:System.Activities.Activity>. V tomto příkladu `Divide` aktivity je odvozena z `CodeActivity<int>`, ale je deklarováno jako <xref:System.Activities.Activity> tak, aby obecné přetížení `Invoke` je používá, která vrací slovník argumentů místo jednoho návratovou hodnotu.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>Pomocí aplikace WorkflowApplication  
 <xref:System.Activities.WorkflowApplication> poskytuje bohatou sadu funkcí pro správu instance pracovního postupu. <xref:System.Activities.WorkflowApplication> funguje jako proxy vlákna bezpečné a skutečnou <xref:System.Activities.Hosting.WorkflowInstance>, který zapouzdřuje modul runtime a poskytuje metody pro vytváření a načítání instance pracovního postupu, pozastavení a obnovení, ukončení a oznámení o události životního cyklu. Pro spuštění pracovního postupu pomocí <xref:System.Activities.WorkflowApplication> vytvoříte <xref:System.Activities.WorkflowApplication>, přihlášení k odběru událostí všechny požadované životního cyklu, spuštění pracovního postupu a potom počkejte na její dokončení. V tomto příkladu definice pracovního postupu, který se skládá z <xref:System.Activities.Statements.WriteLine> vytvoření aktivity a <xref:System.Activities.WorkflowApplication> je vytvořený pomocí definici zadaného pracovního postupu. <xref:System.Activities.WorkflowApplication.Completed%2A> je zpracována, tak hostitele je upozorněni na dokončení pracovního postupu, pracovní postup se spustí s volání <xref:System.Activities.WorkflowApplication.Run%2A>, a pak hostitele čeká na dokončení pracovního postupu. Po dokončení pracovního postupu <xref:System.Threading.AutoResetEvent> a Hostitel aplikace může obnovit spuštění, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>Události životního cyklu aplikace WorkflowApplication  
 Kromě <xref:System.Activities.WorkflowApplication.Completed%2A>, autoři hostitelů můžete být upozorněni, když pracovní postup bude uvolněna (<xref:System.Activities.WorkflowApplication.Unloaded%2A>), bylo přerušeno (<xref:System.Activities.WorkflowApplication.Aborted%2A>), změní na nečinnosti (<xref:System.Activities.WorkflowApplication.Idle%2A> a <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>), nebo dojde k neošetřené výjimce (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>). Vývojáři aplikace pracovního postupu můžete zpracovat tato oznámení a proveďte příslušné akce, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Vstupní argumenty nastavení pracovního postupu  
 Data mohou být předány do pracovního postupu, jako je spuštěno pomocí slovník parametrů, podobně jako způsob, jak se předávají při použití <xref:System.Activities.WorkflowInvoker>. Každá položka ve slovníku se mapuje na vstupní argument zadaného pracovního postupu. V tomto příkladu pracovního postupu, který se skládá z <xref:System.Activities.Statements.WriteLine> vyvolání aktivity a jeho <xref:System.Activities.Statements.WriteLine.Text%2A> je zadán argument pomocí slovníku vstupní parametry.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Načítání výstupní argumenty pracovního postupu  
 Po dokončení pracovního postupu argumentů výstup můžete získat <xref:System.Activities.WorkflowApplication.Completed%2A> obslužná rutina díky přístupu do <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> slovníku. V následujícím příkladu je hostitelem pracovního postupu pomocí <xref:System.Activities.WorkflowApplication>. A <xref:System.Activities.WorkflowApplication> instance se vytváří pomocí definice pracovního postupu, který se skládá z jedné `DiceRoll` aktivity. `DiceRoll` Aktivita má dvě výstupní argumenty, které reprezentují výsledky operace vrácení dice. Po dokončení pracovního postupu, se načtou výstupy <xref:System.Activities.WorkflowApplication.Completed%2A> obslužné rutiny.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
>  <xref:System.Activities.WorkflowApplication> a <xref:System.Activities.WorkflowInvoker> používají slovník vstupní argumenty a vrací slovník `out` argumenty. Tyto parametry slovníku, vlastnosti a návratové hodnoty jsou typu `IDictionary<string, object>`. Skutečné instance třídy slovník, který je předán může být libovolná třída, která implementuje `IDictionary<string, object>`. V těchto příkladech `Dictionary<string, object>` se používá. Další informace o slovníky, naleznete v tématu <xref:System.Collections.Generic.IDictionary%602> a <xref:System.Collections.Generic.Dictionary%602>.  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Předání dat do spuštění pracovního postupu pomocí záložky  
 Záložky jsou mechanismus, pomocí kterého aktivita pasivně počkat, obnovení a slouží jako mechanismus pro předávání dat do běžící instance pracovního postupu. Pokud aktivita čeká na data, můžete vytvořit <xref:System.Activities.Bookmark> a registrace metody zpětného volání, která se má volat při <xref:System.Activities.Bookmark> obnovení, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Při spuštění `ReadLine` aktivita vytvoří <xref:System.Activities.Bookmark>, zaregistruje zpětné volání a potom počká <xref:System.Activities.Bookmark> obnovení. Po obnovení, `ReadLine` aktivity přiřadí data, která byla předána s <xref:System.Activities.Bookmark> k jeho <xref:System.Activities.Activity%601.Result%2A> argument. V tomto příkladu se vytvoří pracovní postup, který používá `ReadLine` aktivity získat uživatelské jméno a zobrazit je v okně konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Když `ReadLine` provádění aktivity, vytvoří <xref:System.Activities.Bookmark> s názvem `UserName` a potom počká na záložku obnovení. Hostitel shromažďuje požadovaná data a potom obnoví <xref:System.Activities.Bookmark>. Pracovní postup bude pokračovat, zobrazí název a potom dokončí.  
  
 Hostitelská aplikace, můžete si prohlédnout pracovní postup určí, jestli jsou všechny aktivní záložky. To lze provést voláním <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> metodu <xref:System.Activities.WorkflowApplication> instanci a tím zkontrolujete <xref:System.Activities.WorkflowApplicationIdleEventArgs> v <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutiny.  
  
 Následující příklad kódu je jako předchozí příklad s tím rozdílem, že aktivní záložky výčtu předtím, než se obnoví na záložku. Spuštění pracovního postupu a jednou <xref:System.Activities.Bookmark> se vytvoří a pracovního postupu přejde nečinný, <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> je volána. Po dokončení pracovního postupu se zobrazí následující výstup do konzoly.  
  
 **Jak se jmenuješ?**  
**BookmarkName: Uživatelské jméno - OwnerDisplayName: ReadLine**   
**Steve**   
**Dobrý den, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Následující příklad kódu zkontroluje <xref:System.Activities.WorkflowApplicationIdleEventArgs> předán <xref:System.Activities.WorkflowApplication.Idle%2A> obslužná rutina <xref:System.Activities.WorkflowApplication> instance. V tomto příkladu obsahuje pracovní postup přepnutí do režimu nečinnosti <xref:System.Activities.Bookmark> s názvem `EnterGuess`, vlastněné uživatelem aktivita s názvem `ReadInt`. Tento příklad kódu je na základě odhlásit z [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md), který je součástí [kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md). Pokud <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutiny v tomto kroku je upravit tak, aby obsahovala jedinečný kód z tohoto příkladu, se zobrazí následující výstup.  
  
 **BookmarkName: EnterGuess - OwnerDisplayName: readint –**
 
 [!code-csharp[CFX_WorkflowApplicationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Souhrn  
 <xref:System.Activities.WorkflowInvoker> poskytuje jednoduchý způsob, jak vyvolat pracovních postupů, a přestože poskytuje metody pro předávání dat v při spuštění pracovního postupu a extrahování dat z dokončený pracovní postup, neposkytuje pro složitější scénáře, který je tam, kde <xref:System.Activities.WorkflowApplication> lze použít.
