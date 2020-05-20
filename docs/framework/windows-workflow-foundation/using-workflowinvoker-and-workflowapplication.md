---
title: Použití WorkflowInvoker a WorkflowApplication
description: Tento článek popisuje hostování pracovního postupu pomocí WorkflowInvoker a WorkflowApplication v programovací model Windows Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 50ad291bc73818092e7a08d489d6860636f9c379
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421316"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Použití WorkflowInvoker a WorkflowApplication
Programovací model Windows Workflow Foundation (WF) poskytuje několik metod hostování pracovních postupů. <xref:System.Activities.WorkflowInvoker>poskytuje jednoduchý způsob, jak vyvolat pracovní postup, jako by šlo o volání metody a dá se použít jenom pro pracovní postupy, které nepoužívají trvalost. <xref:System.Activities.WorkflowApplication>poskytuje bohatší model pro spouštění pracovních postupů, které obsahují oznámení o událostech životního cyklu, řízení provádění, opětovném obnovení záložek a persistenci. <xref:System.ServiceModel.Activities.WorkflowServiceHost>poskytuje podporu pro aktivity zasílání zpráv a primárně se používá se službami pracovních postupů. V tomto tématu se seznámíte s hostováním pracovních postupů pomocí <xref:System.Activities.WorkflowInvoker> a <xref:System.Activities.WorkflowApplication> . Další informace o hostování pracovních postupů pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost> najdete v tématu Přehled [služeb pracovních](../wcf/feature-details/workflow-services.md) postupů a [hostování pracovních postupů](../wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Použití WorkflowInvoker  
 <xref:System.Activities.WorkflowInvoker>poskytuje model pro spuštění pracovního postupu, jako by šlo o volání metody. Chcete-li vyvolat pracovní postup pomocí <xref:System.Activities.WorkflowInvoker> , zavolejte <xref:System.Activities.WorkflowInvoker.Invoke%2A> metodu a předejte do definice pracovního postupu pracovního postupu, který se má vyvolat. V tomto příkladu <xref:System.Activities.Statements.WriteLine> je aktivita vyvolána pomocí <xref:System.Activities.WorkflowInvoker> .  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Když je pracovní postup vyvolán pomocí <xref:System.Activities.WorkflowInvoker> , pracovní postup se spustí v volajícím vlákně a <xref:System.Activities.WorkflowInvoker.Invoke%2A> Metoda zablokuje až do dokončení pracovního postupu, včetně veškerého času nečinnosti. Chcete-li nakonfigurovat časový limit, ve kterém musí být pracovní postup dokončen, použijte jedno <xref:System.Activities.WorkflowInvoker.Invoke%2A> přetížení, které přijímá <xref:System.TimeSpan> parametr. V tomto příkladu je pracovní postup vyvolán dvakrát se dvěma různými časovými intervaly. První pracovní postup skončí, ale druhý ne.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
> <xref:System.TimeoutException>Je vyvolána pouze v případě, že uplyne časový limit a pracovní postup se v průběhu provádění nečinný. Pracovní postup, který trvá déle, než je zadaný časový limit, se úspěšně dokončí, pokud se pracovní postup nestane nečinným.  
  
 <xref:System.Activities.WorkflowInvoker>poskytuje také asynchronní verze metody Invoke. Další informace naleznete v tématech <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> a <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Nastavení vstupních argumentů pracovního postupu  
 Data je možné předat do pracovního postupu pomocí slovníku vstupních parametrů, s názvem argumentu, který se mapuje na vstupní argumenty pracovního postupu. V tomto příkladu <xref:System.Activities.Statements.WriteLine> je vyvolána a hodnota pro svůj <xref:System.Activities.Statements.WriteLine.Text%2A> argument je určena pomocí slovníku vstupních parametrů.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Načítají se výstupní argumenty pracovního postupu.  
 Výstupní parametry pracovního postupu lze získat pomocí slovníku výstupy, který je vrácen z volání <xref:System.Activities.WorkflowInvoker.Invoke%2A> . Následující příklad vyvolá pracovní postup sestávající z jediné `Divide` aktivity, která má dva vstupní argumenty a dva výstupní argumenty. Když je pracovní postup vyvolán, `arguments` je předán slovník, který obsahuje hodnoty pro každý vstupní argument, s klíčem podle názvu argumentu. Když se volání `Invoke` vrátí, vrátí se každý výstupní argument ve `outputs` slovníku, také se zobrazí jako název argumentu.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 Pokud je pracovní postup odvozen z <xref:System.Activities.ActivityWithResult> , například `CodeActivity<TResult>` nebo `Activity<TResult>` , a existují výstupní argumenty kromě správně definovaného <xref:System.Activities.Activity%601.Result%2A> výstupního argumentu, je nutné použít neobecné přetížení, aby bylo možné `Invoke` načíst další argumenty. K tomu je potřeba, aby definice pracovního postupu, která se předala, `Invoke` měla být typu <xref:System.Activities.Activity> . V tomto příkladu `Divide` je aktivita odvozena z `CodeActivity<int>` , ale je deklarována jako, <xref:System.Activities.Activity> aby bylo použito neobecné přetížení, `Invoke` které vrací slovník argumentů namísto jediné návratové hodnoty.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>Použití aplikace WorkflowApplication  
 <xref:System.Activities.WorkflowApplication>poskytuje bohatou sadu funkcí pro správu instancí pracovního postupu. <xref:System.Activities.WorkflowApplication>slouží jako proxy server bezpečný pro přístup k vláknům <xref:System.Activities.Hosting.WorkflowInstance> , který zapouzdřuje modul runtime a poskytuje metody pro vytváření a načítání instancí pracovního postupu, pozastavení a obnovení, ukončení a oznámení o událostech životního cyklu. Pokud chcete pracovní postup spustit pomocí <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowApplication> , přihlaste se k odběru všech požadovaných událostí životního cyklu, spusťte pracovní postup a počkejte na jeho dokončení. V tomto příkladu se vytvoří definice pracovního postupu, která se skládá z <xref:System.Activities.Statements.WriteLine> aktivity a vytvoří <xref:System.Activities.WorkflowApplication> se pomocí zadané definice pracovního postupu. <xref:System.Activities.WorkflowApplication.Completed%2A>je zpracována, aby byl hostitel upozorněn po dokončení pracovního postupu, byl pracovní postup spuštěn s voláním <xref:System.Activities.WorkflowApplication.Run%2A> a poté hostitel čeká na dokončení pracovního postupu. Po dokončení pracovního postupu <xref:System.Threading.AutoResetEvent> je sada nastavena a hostitelská aplikace může pokračovat v provádění, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>WorkflowApplication – události životního cyklu  
 Kromě <xref:System.Activities.WorkflowApplication.Completed%2A> toho mohou být autoři hostitele upozorněni, když je pracovní postup uvolněn ( <xref:System.Activities.WorkflowApplication.Unloaded%2A> ), přerušen ( <xref:System.Activities.WorkflowApplication.Aborted%2A> ), stane se nečinným ( <xref:System.Activities.WorkflowApplication.Idle%2A> a <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> ), nebo dojde k neošetřené výjimce ( <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ). Vývojáři aplikací pracovních postupů můžou tato oznámení zpracovat a provést příslušné akce, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Nastavení vstupních argumentů pracovního postupu  
 Data je možné předat do pracovního postupu, protože je spouštěno pomocí slovníku parametrů, podobně jako při použití se data předávají <xref:System.Activities.WorkflowInvoker> . Každá položka ve slovníku se mapuje na vstupní argument zadaného pracovního postupu. V tomto příkladu je vyvolán pracovní postup, který se skládá z <xref:System.Activities.Statements.WriteLine> aktivity, a jeho <xref:System.Activities.Statements.WriteLine.Text%2A> argument je zadán pomocí slovníku vstupních parametrů.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Načítají se výstupní argumenty pracovního postupu.  
 Po dokončení pracovního postupu lze v obslužné rutině načíst libovolné výstupní argumenty <xref:System.Activities.WorkflowApplication.Completed%2A> přístupem ke <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> slovníku. Následující příklad hostuje pracovní postup pomocí <xref:System.Activities.WorkflowApplication> . <xref:System.Activities.WorkflowApplication>Instance je vytvořena pomocí definice pracovního postupu, která se skládá z jedné `DiceRoll` aktivity. `DiceRoll`Aktivita má dva argumenty výstupů, které reprezentují výsledky operace obnovení indexy. Po dokončení pracovního postupu se výstupy načtou v <xref:System.Activities.WorkflowApplication.Completed%2A> obslužné rutině.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
> <xref:System.Activities.WorkflowApplication>a <xref:System.Activities.WorkflowInvoker> Využijte slovník vstupních argumentů a vraťte slovník `out` argumentů. Tyto parametry slovníku, vlastnosti a návratové hodnoty jsou typu `IDictionary<string, object>` . Skutečná instance třídy Dictionary, která je předána, může být libovolná třída, která implementuje `IDictionary<string, object>` . V těchto příkladech `Dictionary<string, object>` se používá. Další informace o slovnících najdete v tématech <xref:System.Collections.Generic.IDictionary%602> a <xref:System.Collections.Generic.Dictionary%602> .  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Předávání dat do běžícího pracovního postupu pomocí záložek  
 Záložky jsou mechanismus, podle kterého může aktivita, která se má projít, počkat na obnovení a je mechanismem pro předávání dat do spuštěné instance pracovního postupu. Pokud aktivita čeká na data, může vytvořit <xref:System.Activities.Bookmark> a zaregistrovat metodu zpětného volání, která bude volána <xref:System.Activities.Bookmark> , když je obnoveno, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Po spuštění `ReadLine` aktivita vytvoří <xref:System.Activities.Bookmark> , zaregistruje zpětné volání a potom počká, <xref:System.Activities.Bookmark> až se obnoví. Když je obnovena, `ReadLine` Aktivita přiřadí data, která byla předána <xref:System.Activities.Bookmark> do svého <xref:System.Activities.Activity%601.Result%2A> argumentu. V tomto příkladu je vytvořen pracovní postup, který používá `ReadLine` aktivitu ke shromáždění jména uživatele a jeho zobrazení v okně konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Když se `ReadLine` aktivita spustí, vytvoří se <xref:System.Activities.Bookmark> pojmenovaná `UserName` a potom počká, až se záložka obnoví. Hostitel shromáždí požadovaná data a pak obnoví <xref:System.Activities.Bookmark> . Pracovní postup obnoví, zobrazí název a pak dokončí.  
  
 Hostitelská aplikace může zkontrolovat pracovní postup a zjistit, jestli existují žádné aktivní záložky. To lze provést voláním <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> metody <xref:System.Activities.WorkflowApplication> instance nebo kontrolou <xref:System.Activities.WorkflowApplicationIdleEventArgs> v <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutině.  
  
 Následující příklad kódu je podobný jako předchozí příklad s tím rozdílem, že aktivní záložky jsou vyčísleny před pokračováním záložky. Spustí se pracovní postup a jakmile <xref:System.Activities.Bookmark> se vytvoří a pracovní postup se nečinný, <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> zavolá se. Po dokončení pracovního postupu se v konzole zobrazí následující výstup.  
  
 **Jak se jmenuješ?**  
**Záložka: username-OwnerDisplayName: ReadLine** 
 **Steve** 
 **Hello, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Následující příklad kódu kontroluje <xref:System.Activities.WorkflowApplicationIdleEventArgs> předané <xref:System.Activities.WorkflowApplication.Idle%2A> obslužné rutině <xref:System.Activities.WorkflowApplication> instance. V tomto příkladu pracovní postup, který pronikne nečinný, má jeden <xref:System.Activities.Bookmark> s názvem `EnterGuess` , jehož vlastníkem je aktivita s názvem `ReadInt` . Tento příklad kódu je založený na [postupu: spuštění pracovního postupu](how-to-run-a-workflow.md), který je součástí [kurzu Začínáme](getting-started-tutorial.md). Pokud <xref:System.Activities.WorkflowApplication.Idle%2A> je obslužná rutina v tomto kroku upravena tak, aby obsahovala kód z tohoto příkladu, zobrazí se následující výstup.  
  
 **Bookmark: EnterGuess-OwnerDisplayName: ReadInt**

 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Souhrn  
 <xref:System.Activities.WorkflowInvoker>poskytuje lehký způsob, jak vyvolat pracovní postupy a i když poskytuje metody pro předávání dat na začátku pracovního postupu a extrahování dat z dokončeného pracovního postupu, neposkytuje pro složitější scénáře, které se <xref:System.Activities.WorkflowApplication> dají použít.
