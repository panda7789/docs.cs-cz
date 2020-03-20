---
title: Použití WorkflowInvoker a WorkflowApplication
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 5d09fc3c902b1993b32edf3e9f92393433281636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182707"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Použití WorkflowInvoker a WorkflowApplication
Windows Workflow Foundation (WF) poskytuje několik metod hostování pracovních postupů. <xref:System.Activities.WorkflowInvoker>poskytuje jednoduchý způsob, jak vyvolat pracovní postup, jako by se jednalo o volání metody a lze jej použít pouze pro pracovní postupy, které nepoužívají trvalost. <xref:System.Activities.WorkflowApplication>poskytuje bohatší model pro provádění pracovních postupů, který zahrnuje oznámení událostí životního cyklu, řízení provádění, obnovení záložky a trvalost. <xref:System.ServiceModel.Activities.WorkflowServiceHost>poskytuje podporu pro zasílání zpráv a používá se především se službami pracovního postupu. Toto téma vás seznámí <xref:System.Activities.WorkflowInvoker> <xref:System.Activities.WorkflowApplication>s hostováním pracovních postupů s a . Další informace o hostování <xref:System.ServiceModel.Activities.WorkflowServiceHost>pracovních postupů pomocí najdete [v tématu Pracovní postupy a](../wcf/feature-details/workflow-services.md) Přehled služeb hostování [pracovních postupů](../wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Použití workflowinvokeru  
 <xref:System.Activities.WorkflowInvoker>poskytuje model pro provádění pracovního postupu, jako by se jednalo o volání metody. Chcete-li vyvolat <xref:System.Activities.WorkflowInvoker>pracovní <xref:System.Activities.WorkflowInvoker.Invoke%2A> postup pomocí , volání metody a předat v definici pracovního postupu pracovního postupu vyvolat. V tomto příkladu je aktivita <xref:System.Activities.Statements.WriteLine> vyvolána pomocí <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Pokud je pracovní postup <xref:System.Activities.WorkflowInvoker>vyvolán pomocí , pracovní postup <xref:System.Activities.WorkflowInvoker.Invoke%2A> se spustí v volajícím vlákně a metoda se zablokuje, dokud nebude pracovní postup dokončen, včetně doby nečinnosti. Chcete-li nakonfigurovat časový interval, ve kterém musí <xref:System.Activities.WorkflowInvoker.Invoke%2A> být dokončen pracovní <xref:System.TimeSpan> postup, použijte jedno z přetížení, které přebírá parametr. V tomto příkladu je pracovní postup vyvolán dvakrát se dvěma různými časovými intervaly. První pracovní postup se zkompletuje, ale druhý nikoli.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
> Je <xref:System.TimeoutException> vyvolána pouze v případě, že časový limit interval uplyne a pracovní postup se stane nečinný během provádění. Pracovní postup, jehož dokončení trvá déle než zadaný časový limit, bude úspěšně dokončen, pokud se pracovní postup neprojeví nečinnosti.  
  
 <xref:System.Activities.WorkflowInvoker>poskytuje také asynchronní verze metody invoke. Další informace naleznete v tématech <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> a <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Nastavení vstupních argumentů pracovního postupu  
 Data mohou být předána do pracovního postupu pomocí slovníku vstupních parametrů, který je zaklávesový podle názvu argumentu a který se mapuje na vstupní argumenty pracovního postupu. V tomto příkladu je vyvolána <xref:System.Activities.Statements.WriteLine> a <xref:System.Activities.Statements.WriteLine.Text%2A> hodnota pro jeho argument je určena pomocí slovníku vstupních parametrů.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Načítání výstupních argumentů pracovního postupu  
 Výstupní parametry pracovního postupu lze získat pomocí slovníku výstupů, <xref:System.Activities.WorkflowInvoker.Invoke%2A>který je vrácen z volání do . Následující příklad vyvolá pracovní postup skládající `Divide` se z jedné aktivity, která má dva vstupní argumenty a dva výstupní argumenty. Při vyvolání pracovního `arguments` postupu je předán slovník, který obsahuje hodnoty pro každý vstupní argument, zadávaný názvem argumentu. Při volání `Invoke` vrátí, každý výstupní argument `outputs` je vrácena ve slovníku, také zadali podle názvu argumentu.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 Pokud pracovní postup <xref:System.Activities.ActivityWithResult>pochází z `CodeActivity<TResult>` `Activity<TResult>`, například nebo , a existují výstupní <xref:System.Activities.Activity%601.Result%2A> argumenty kromě dobře definovaný `Invoke` výstupní argument, musí být použita neobecné přetížení musí být použitk načíst další argumenty. Chcete-li to provést, `Invoke` musí být <xref:System.Activities.Activity>předaná definice pracovního postupu typu . V tomto `Divide` příkladu je `CodeActivity<int>`aktivita odvozena z , ale je deklarována tak, <xref:System.Activities.Activity> aby se použilo neobecné přetížení, `Invoke` které vrací slovník argumentů namísto jedné vrácené hodnoty.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>Použití aplikace WorkflowApplication  
 <xref:System.Activities.WorkflowApplication>poskytuje bohatou sadu funkcí pro správu instancí pracovního postupu. <xref:System.Activities.WorkflowApplication>funguje jako proxy pro bezpečné <xref:System.Activities.Hosting.WorkflowInstance>přístupy k vláknu ke skutečnému , který zapouzdřuje dobu runtime a poskytuje metody pro vytváření a načítání instancí pracovního postupu, pozastavení a obnovení, ukončení a oznámení událostí životního cyklu. Chcete-li spustit <xref:System.Activities.WorkflowApplication> pracovní <xref:System.Activities.WorkflowApplication>postup pomocí vytvoření , přihlaste se k odběru všech požadovaných událostí životního cyklu, spusťte pracovní postup a počkejte na jeho dokončení. V tomto příkladu je vytvořena definice <xref:System.Activities.Statements.WriteLine> pracovního postupu, která se skládá z aktivity, a <xref:System.Activities.WorkflowApplication> je vytvořena pomocí zadané definice pracovního postupu. <xref:System.Activities.WorkflowApplication.Completed%2A>je zpracována tak, aby byl hostitel upozorněn po dokončení pracovního <xref:System.Activities.WorkflowApplication.Run%2A>postupu, pracovní postup je spuštěn s voláním a hostitel čeká na dokončení pracovního postupu. Po dokončení pracovního <xref:System.Threading.AutoResetEvent> postupu je nastavena a hostitelská aplikace může pokračovat v provádění, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>Události životního cyklu aplikace WorkflowApplication  
 Kromě <xref:System.Activities.WorkflowApplication.Completed%2A>aplikace mohou být autoři hostitele upozorněni, když<xref:System.Activities.WorkflowApplication.Unloaded%2A>je pracovní<xref:System.Activities.WorkflowApplication.Aborted%2A>postup uvolněn<xref:System.Activities.WorkflowApplication.Idle%2A> <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>( ), přerušeno (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>), se stane nečinným ( a ) nebo dojde k neošetřené výjimce ( ). Vývojáři aplikací pracovního postupu mohou zpracovávat tato oznámení a přijmout vhodná opatření, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Nastavení vstupních argumentů pracovního postupu  
 Data mohou být předána do pracovního postupu při spuštění pomocí slovníku parametrů, podobně <xref:System.Activities.WorkflowInvoker>jako jsou data při použití . Každá položka ve slovníku se mapuje na vstupní argument zadaného pracovního postupu. V tomto příkladu je vyvolán <xref:System.Activities.Statements.WriteLine> pracovní postup, který <xref:System.Activities.Statements.WriteLine.Text%2A> se skládá z aktivity a jeho argument je určen pomocí slovníku vstupních parametrů.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Načítání výstupních argumentů pracovního postupu  
 Po dokončení pracovního postupu lze všechny výstupní argumenty načíst v <xref:System.Activities.WorkflowApplication.Completed%2A> obslužné rutině přístupem ke slovníku. <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> Následující příklad hostuje <xref:System.Activities.WorkflowApplication>pracovní postup pomocí aplikace . Instance <xref:System.Activities.WorkflowApplication> je vytvořena pomocí definice pracovního postupu, která se skládá z jedné `DiceRoll` aktivity. Aktivita `DiceRoll` má dva výstupní argumenty, které představují výsledky operace kostky. Po dokončení pracovního postupu jsou výstupy <xref:System.Activities.WorkflowApplication.Completed%2A> načteny v obslužné rutině.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
> <xref:System.Activities.WorkflowApplication>a <xref:System.Activities.WorkflowInvoker> vzít slovník vstupní ch argumentů a `out` vrátit slovník argumentů. Tyto parametry slovníku, vlastnosti a `IDictionary<string, object>`vrácené hodnoty jsou typu . Skutečná instance třídy slovníku, která je předána v `IDictionary<string, object>`může být libovolná třída, která implementuje . V těchto příkladech se `Dictionary<string, object>` používá. Další informace o slovnících <xref:System.Collections.Generic.IDictionary%602> <xref:System.Collections.Generic.Dictionary%602>naleznete v tématech a .  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Předávání dat do spuštěného pracovního postupu pomocí záložek  
 Záložky jsou mechanismus, kterým aktivita může pasivně čekat na obnovení a jsou mechanismem pro předávání dat do spuštěné instance pracovního postupu. Pokud aktivita čeká na data, <xref:System.Activities.Bookmark> může vytvořit a zaregistrovat metodu <xref:System.Activities.Bookmark> zpětného volání, která má být volána při obnovení, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Při spuštění aktivity `ReadLine` vytvoří <xref:System.Activities.Bookmark>, zaregistruje zpětné volání a potom <xref:System.Activities.Bookmark> čeká na obnovení. Po obnovení aktivita `ReadLine` přiřadí data, která byla <xref:System.Activities.Bookmark> předána <xref:System.Activities.Activity%601.Result%2A> s jeho argument. V tomto příkladu je vytvořen `ReadLine` pracovní postup, který používá aktivitu ke shromáždění jména uživatele a jeho zobrazení v okně konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Když `ReadLine` je aktivita spuštěna, <xref:System.Activities.Bookmark> `UserName` vytvoří pojmenovaný a pak čeká na záložku, která má být obnovena. Hostitel shromažďuje požadovaná data a potom <xref:System.Activities.Bookmark>obnoví . Pracovní postup se obnoví, zobrazí název a potom se dokončí.  
  
 Hostitelská aplikace může zkontrolovat pracovní postup a zjistit, zda existují nějaké aktivní záložky. To lze provést <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> voláním metody <xref:System.Activities.WorkflowApplication> instance nebo kontrolou <xref:System.Activities.WorkflowApplicationIdleEventArgs> v <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutině.  
  
 Následující příklad kódu je jako v předchozím příkladu s tím rozdílem, že aktivní záložky jsou uvedeny před obnovením záložky. Pracovní postup je spuštěn <xref:System.Activities.Bookmark> a jakmile je vytvořen <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> a pracovní postup přejde nečinnosti, je volána. Po dokončení pracovního postupu se do konzoly zobrazí následující výstup.  
  
 **Jak se jmenuješ?**  
**Název záložky: UserName - OwnerDisplayName: ReadLine**
**Steve**
**Hello, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Následující příklad kódu kontroluje <xref:System.Activities.WorkflowApplicationIdleEventArgs> předány <xref:System.Activities.WorkflowApplication.Idle%2A> do <xref:System.Activities.WorkflowApplication> obslužné rutiny instance. V tomto příkladu má <xref:System.Activities.Bookmark> nečinný pracovní `EnterGuess`postup jeden s `ReadInt`názvem , vlastněný aktivitou s názvem . Tento příklad kódu je založen mimo [How to: Run a Workflow](how-to-run-a-workflow.md), který je součástí kurzu [Začínáme](getting-started-tutorial.md). Pokud <xref:System.Activities.WorkflowApplication.Idle%2A> obslužná rutina v tomto kroku je upravena tak, aby obsahovala kód z tohoto příkladu, zobrazí se následující výstup.  
  
 **Název záložky: EnterGuess - OwnerDisplayName: ReadInt**

 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Souhrn  
 <xref:System.Activities.WorkflowInvoker>poskytuje lehký způsob vyvolání pracovních postupů a přestože poskytuje metody pro předávání dat na začátku pracovního postupu a extrahování <xref:System.Activities.WorkflowApplication> dat z dokončeného pracovního postupu, neposkytuje složitější scénáře, které je místo, kde lze použít.
