---
title: Použití delegátů aktivity
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 96a412a066342fb9c459e1388c5b58847ebac390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-activity-delegates"></a>Použití delegátů aktivity
Delegáti aktivity povolit aktivity autorům vystavit zpětná volání s konkrétní podpisy, pro které uživatelé aktivity zadat na základě aktivity obslužné rutiny. K dispozici jsou dva typy aktivity delegáti: <xref:System.Activities.ActivityAction%601> se používá k definování delegáti aktivity, které nemají návratovou hodnotu, a <xref:System.Activities.ActivityFunc%601> se používá k definování delegáti aktivity, které mají návratovou hodnotu.  
  
 Delegáti aktivity jsou užitečný ve scénářích, kde podřízené aktivity musí být omezen na situaci, kdy určité podpis. Například <xref:System.Activities.Statements.While> aktivita může obsahovat jakýkoli typ podřízené aktivity s žádná omezení, ale text <xref:System.Activities.Statements.ForEach%601> aktivita <xref:System.Activities.ActivityAction%601>a podřízené aktivity, které se nakonec provedený <xref:System.Activities.Statements.ForEach%601> musí mít <xref:System.Activities.InArgument%601> , je stejný typ členy kolekce, <xref:System.Activities.Statements.ForEach%601> zobrazí.  
  
## <a name="using-activityaction"></a>Pomocí ActivityAction  
 Několik [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] aktivity pomocí aktivity akcí, například <xref:System.Activities.Statements.Catch> aktivity a <xref:System.Activities.Statements.ForEach%601> aktivity. V každém případě aktivity akce představuje umístění Určuje, kde Autor pracovního postupu aktivitu k poskytnutí požadované chování při sestavování pomocí jedné z těchto aktivit pracovního postupu. V následujícím příkladu <xref:System.Activities.Statements.ForEach%601> aktivita se používá k zobrazení textu v okně konzoly. Text <xref:System.Activities.Statements.ForEach%601> zadané pomocí <xref:System.Activities.ActivityAction%601> odpovídající typ <xref:System.Activities.Statements.ForEach%601> tedy řetězec. <xref:System.Activities.Statements.WriteLine> Aktivity zadaný v <xref:System.Activities.ActivityDelegate.Handler%2A> má jeho <xref:System.Activities.Statements.WriteLine.Text%2A> argument vázána na řetězcové hodnoty v kolekci, <xref:System.Activities.Statements.ForEach%601> opakuje aktivity.  
  
 [!code-csharp[CFX_ActivityExample#6](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]  
  
 ActionArgument se používá k toku jednotlivé položky v kolekci WriteLine. Po vyvolání pracovního postupu se zobrazí následující výstup do konzoly.  
 ``` 
 HelloWorld.
 ```  
V příkladech v tomto tématu použijte syntaxi inicializace objektu. Syntaxe inicializace objektu může být užitečný způsob, jak vytvořit definice pracovního postupu v kódu, protože poskytuje hierarchické zobrazení aktivity v pracovním postupu a znázorňuje vztah mezi aktivitami. Neexistuje žádný požadavek na použití syntaxe inicializace objektu při prostřednictvím kódu programu vytváření pracovních postupů. V následujícím příkladu je funkčně srovnatelný předchozí příklad.  
  
 [!code-csharp[CFX_ActivityExample#7](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]  
  
 Další informace o inicializátory objektů najdete v tématu [postupy: Inicializace objektů bez volání konstruktoru (C# Průvodce programováním)](http://go.microsoft.com/fwlink/?LinkId=161015) a [postupy: Deklarace objektu pomocí inicializátoru objektu](http://go.microsoft.com/fwlink/?LinkId=161016).  
  
 V následujícím příkladu <xref:System.Activities.Statements.TryCatch> aktivita se používá v pracovním postupu. <xref:System.ApplicationException> Je vyvolána v tomto pracovním postupu a jsou zpracována <xref:System.Activities.Statements.Catch%601> aktivity. Obslužná rutina pro <xref:System.Activities.Statements.Catch%601> aktivity aktivity akce je <xref:System.Activities.Statements.WriteLine> aktivity a podrobnosti výjimky je plynoucích prostřednictvím se pomocí `ex` <xref:System.Activities.DelegateInArgument%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Při vytváření vlastních aktivit, které definuje <xref:System.Activities.ActivityAction%601>, použijte <xref:System.Activities.Statements.InvokeAction%601> modelování volání této <xref:System.Activities.ActivityAction%601>. V tomto příkladu vlastní `WriteLineWithNotification` aktivity je definována. Tato aktivita se skládá z <xref:System.Activities.Statements.Sequence> obsahující <xref:System.Activities.Statements.WriteLine> následuje aktivity <xref:System.Activities.Statements.InvokeAction%601> , který spustí <xref:System.Activities.ActivityAction%601> , která má jeden argument řetězec.  
  
 [!code-csharp[CFX_ActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]  
  
 Vytvoření pracovního postupu pomocí `WriteLineWithNotification` aktivity, Autor pracovního postupu určuje požadovanou vlastní logiky v akci aktivity <xref:System.Activities.ActivityDelegate.Handler%2A>. V tomto příkladu se vytvoří pracovní postup využívající `WriteLineWithNotification` aktivitu a <xref:System.Activities.Statements.WriteLine> aktivita se používá jako <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]  
  
 Existuje více obecné verzí <xref:System.Activities.Statements.InvokeAction%601> a <xref:System.Activities.ActivityAction%601> zadaná pro předání jeden nebo více argumentů.  
  
## <a name="using-activityfunc"></a>Pomocí ActivityFunc  
 <xref:System.Activities.ActivityAction%601> je užitečné, když není žádná hodnota výsledek z aktivity, a <xref:System.Activities.ActivityFunc%601> se používá, pokud je vrácena hodnota výsledek. Při vytváření vlastních aktivit, které definuje <xref:System.Activities.ActivityFunc%601>, použijte <xref:System.Activities.Expressions.InvokeFunc%601> modelování volání této <xref:System.Activities.ActivityFunc%601>. V následujícím příkladu `WriteFillerText` aktivity je definována. K poskytování Výplň textu, <xref:System.Activities.Expressions.InvokeFunc%601> je zadán, který používá argument celé číslo a má výsledném řetězci. Jakmile se načte text výplň, se zobrazí na pomocí konzoly <xref:System.Activities.Statements.WriteLine> aktivity.  
  
 [!code-csharp[CFX_ActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]  
  
 Zadat text, musí být použita aktivity, který přijímá jeden `int` argument a výsledek řetězec obsahuje. Tento příklad ukazuje `TextGenerator` aktivity, která splňuje tyto požadavky.  
  
 [!code-csharp[CFX_ActivityExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]  
  
 Použít `TextGenerator` aktivitu `WriteFillerText` aktivity, je zadat jako <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#5](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]  
  
## <a name="see-also"></a>Viz také  
 [Zveřejnění a vyvolání akcí aktivit](../../../docs/framework/windows-workflow-foundation/samples/exposing-and-invoking-activityactions.md)
