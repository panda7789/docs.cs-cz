---
title: Používání delegátů aktivit
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: bb23f6a79b6f2390952f9aadc1cf08099acb289b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489926"
---
# <a name="using-activity-delegates"></a>Používání delegátů aktivit
Delegátů aktivit umožňují autorům aktivity vystavit zpětná volání s konkrétní podpisy, které mohou uživatelé aktivity zadat na základě aktivity obslužné rutiny. K dispozici jsou dva typy delegátů aktivit: <xref:System.Activities.ActivityAction%601> se používá k definování delegátů aktivit, které nemají návratovou hodnotu a <xref:System.Activities.ActivityFunc%601> se používá k definování delegátů aktivit, které nemají návratovou hodnotu.  
  
 Delegátů aktivit jsou užitečné v situacích, kdy podřízené aktivity musí být omezeny s tím, že některé podpis. Například <xref:System.Activities.Statements.While> aktivita může obsahovat libovolný typ podřízené aktivity bez omezení, ale text <xref:System.Activities.Statements.ForEach%601> aktivita je <xref:System.Activities.ActivityAction%601>a podřízenou aktivitu, takže v konečném důsledku je spuštěn <xref:System.Activities.Statements.ForEach%601> musí mít <xref:System.Activities.InArgument%601> , který je stejného typu jako objekty její členové kolekce, která <xref:System.Activities.Statements.ForEach%601> vytvoří výčet.  
  
## <a name="using-activityaction"></a>Pomocí ActivityAction  
 Několik [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] aktivity pomocí aktivity akce, jako <xref:System.Activities.Statements.Catch> aktivity a <xref:System.Activities.Statements.ForEach%601> aktivity. V obou případech představuje akci aktivity umístění Určuje, kde Autor pracovního postupu aktivity k poskytování požadované chování při vytváření pracovního postupu pomocí jedné z těchto činností. V následujícím příkladu <xref:System.Activities.Statements.ForEach%601> aktivita se používá k zobrazení textu v okně konzoly. Text <xref:System.Activities.Statements.ForEach%601> je určen pomocí <xref:System.Activities.ActivityAction%601> , který odpovídá vašemu typu <xref:System.Activities.Statements.ForEach%601> což je řetězec. <xref:System.Activities.Statements.WriteLine> Aktivity podle <xref:System.Activities.ActivityDelegate.Handler%2A> má jeho <xref:System.Activities.Statements.WriteLine.Text%2A> argument je vázán na řetězcové hodnoty v kolekci, která <xref:System.Activities.Statements.ForEach%601> aktivit iterace.  
  
 [!code-csharp[CFX_ActivityExample#6](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]  
  
 ActionArgument se používá tok jednotlivých položek v kolekci, která se WriteLine. Když uživatel vyvolá pracovní postup, se zobrazí následující výstup do konzoly.  
 ``` 
 HelloWorld.
 ```  
Příklady v tomto tématu pomocí syntaxe inicializace objektu. Syntaxe inicializace objektu může být užitečný způsob, jak vytvořit definice pracovního postupu v kódu, protože obsahuje hierarchické zobrazení aktivity v pracovním postupu a znázorňuje vztah mezi aktivitami. Neexistuje žádný požadavek na pomocí syntaxe inicializace objektu při programově vytvářet pracovní postupy. Následující příklad je funkčně srovnatelný s předchozím příkladu.  
  
 [!code-csharp[CFX_ActivityExample#7](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]  
  
 Další informace o inicializátory objektů najdete v tématu [jak: Inicializace objektů bez volání konstruktoru (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=161015) a [postupy: Deklarace objektu pomocí inicializátoru objektu](https://go.microsoft.com/fwlink/?LinkId=161016).  
  
 V následujícím příkladu <xref:System.Activities.Statements.TryCatch> aktivita se používá v pracovním postupu. <xref:System.ApplicationException> Je vyvolána tímto pracovním postupem a zařizuje služba <xref:System.Activities.Statements.Catch%601> aktivity. Obslužná rutina pro <xref:System.Activities.Statements.Catch%601> je aktivita akce aktivity <xref:System.Activities.Statements.WriteLine> aktivity a podrobnosti o výjimce se prochází přes pomocí `ex` <xref:System.Activities.DelegateInArgument%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Při vytváření vlastní aktivitu, která definuje <xref:System.Activities.ActivityAction%601>, použijte <xref:System.Activities.Statements.InvokeAction%601> modelování volání, která <xref:System.Activities.ActivityAction%601>. V tomto příkladu vlastní `WriteLineWithNotification` aktivity je definována. Tato aktivita se skládá z <xref:System.Activities.Statements.Sequence> , která obsahuje <xref:System.Activities.Statements.WriteLine> aktivity za nímž následuje <xref:System.Activities.Statements.InvokeAction%601> , která vyvolává <xref:System.Activities.ActivityAction%601> , která přijímá jeden argument řetězec.  
  
 [!code-csharp[CFX_ActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]  
  
 Při vytvoření pracovního postupu pomocí `WriteLineWithNotification` aktivity, Autor pracovní postup určuje požadované vlastní logiku v akci aktivity <xref:System.Activities.ActivityDelegate.Handler%2A>. V tomto příkladu se vytvoří pracovní postup, které používají `WriteLineWithNotification` aktivitu a <xref:System.Activities.Statements.WriteLine> aktivita se používá jako <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]  
  
 Existuje několik obecných verzí <xref:System.Activities.Statements.InvokeAction%601> a <xref:System.Activities.ActivityAction%601> k dispozici pro předávání jeden nebo více argumentů.  
  
## <a name="using-activityfunc"></a>Pomocí activityfunc musí  
 <xref:System.Activities.ActivityAction%601> je užitečné, pokud neexistuje žádná hodnota výsledků z aktivity, a <xref:System.Activities.ActivityFunc%601> se používá, když je výsledná hodnota se vrátí. Při vytváření vlastní aktivitu, která definuje <xref:System.Activities.ActivityFunc%601>, použijte <xref:System.Activities.Expressions.InvokeFunc%601> modelování volání, která <xref:System.Activities.ActivityFunc%601>. V následujícím příkladu `WriteFillerText` aktivity je definována. Slouží k poskytování přednastavené text <xref:System.Activities.Expressions.InvokeFunc%601> je zadán, který přebírá celočíselný argument a vrátí výsledek řetězce. Jakmile se načítá přednastavené text, se zobrazí pomocí konzoly <xref:System.Activities.Statements.WriteLine> aktivity.  
  
 [!code-csharp[CFX_ActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]  
  
 Zadat text, aktivita musí být použita, která přijímá jeden `int` argument a vrátí výsledek řetězce. Tento příklad ukazuje `TextGenerator` aktivitu, která splňuje tyto požadavky.  
  
 [!code-csharp[CFX_ActivityExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]  
  
 Použít `TextGenerator` aktivitu `WriteFillerText` aktivity, je zadat jako <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#5](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]  
  
## <a name="see-also"></a>Viz také  
 [Zveřejnění a vyvolání akcí aktivit](../../../docs/framework/windows-workflow-foundation/samples/exposing-and-invoking-activityactions.md)
