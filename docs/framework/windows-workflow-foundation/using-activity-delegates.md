---
title: Používání delegátů aktivit
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: cbcc8f8e498be4f79f8fed5af7cd3557d7c55981
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837568"
---
# <a name="using-activity-delegates"></a>Používání delegátů aktivit
Delegáti aktivity umožňují autorům aktivity vystavovat zpětná volání s konkrétními podpisy, pro které mohou uživatelé aktivity poskytovat obslužné rutiny založené na aktivitách. K dispozici jsou dva typy delegátů aktivit: <xref:System.Activities.ActivityAction%601> slouží k definování delegátů aktivity, které nemají návratovou hodnotu, a <xref:System.Activities.ActivityFunc%601> slouží k definování delegátů aktivity, které mají návratovou hodnotu.

Delegáty aktivity jsou užitečné ve scénářích, kdy musí být podřízená aktivita omezená na určitý podpis. Například aktivita <xref:System.Activities.Statements.While> může obsahovat jakýkoli typ podřízené aktivity bez omezení, ale tělo aktivity <xref:System.Activities.Statements.ForEach%601> je <xref:System.Activities.ActivityAction%601>a podřízená aktivita, která je nakonec spouštěna <xref:System.Activities.Statements.ForEach%601>, musí mít <xref:System.Activities.InArgument%601>, který je stejný jako stejný typ členů kolekce, které <xref:System.Activities.Statements.ForEach%601> výčet.

## <a name="using-activityaction"></a>Použití ActivityAction

Několik aktivit [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] používá akce aktivity, jako je aktivita <xref:System.Activities.Statements.Catch> a aktivita <xref:System.Activities.Statements.ForEach%601>. V každém případě akce aktivity představuje umístění, kde Autor pracovního postupu určuje aktivitu, která poskytne požadované chování při vytváření pracovního postupu pomocí jedné z těchto aktivit. V následujícím příkladu se <xref:System.Activities.Statements.ForEach%601> aktivita používá k zobrazení textu v okně konzoly. Tělo <xref:System.Activities.Statements.ForEach%601> je určeno pomocí <xref:System.Activities.ActivityAction%601>, která odpovídá typu <xref:System.Activities.Statements.ForEach%601> což je řetězec. U <xref:System.Activities.Statements.WriteLine> aktivity zadané v <xref:System.Activities.ActivityDelegate.Handler%2A> je jeho argument <xref:System.Activities.Statements.WriteLine.Text%2A> svázán s hodnotami řetězce v kolekci, kterou aktivita <xref:System.Activities.Statements.ForEach%601> prochází.

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

ActionArgument se používá k flowování jednotlivých položek v kolekci do WriteLine. Po vyvolání pracovního postupu se do konzoly zobrazí následující výstup.

```console
HelloWorld.
```

Příklady v tomto tématu používají syntaxi inicializace objektu. Syntaxe inicializace objektu může být užitečný způsob, jak vytvořit definice pracovních postupů v kódu, protože poskytuje hierarchické zobrazení aktivit v pracovním postupu a znázorňuje vztah mezi aktivitami. Při vytváření pracovních postupů prostřednictvím kódu programu není nutné používat syntaxi inicializace objektu. Následující příklad je funkčně ekvivalentní k předchozímu příkladu.

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

Další informace o inicializátorech objektů naleznete v tématu [How to: Initialize Objects bez volání konstruktoru (C# Průvodce programováním)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) a [Postupy: deklarace objektu pomocí inicializátoru objektu (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md).

V následujícím příkladu se v pracovním postupu používá <xref:System.Activities.Statements.TryCatch> aktivita. Pracovní postup vyvolal <xref:System.ApplicationException> a je zpracováván aktivitou <xref:System.Activities.Statements.Catch%601>. Obslužná rutina akce aktivity <xref:System.Activities.Statements.Catch%601> aktivity je <xref:System.Activities.Statements.WriteLine> aktivita a podrobnosti o výjimce se do ní přesměrují pomocí `ex` <xref:System.Activities.DelegateInArgument%601>.

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

Při vytváření vlastní aktivity definující <xref:System.Activities.ActivityAction%601>použijte k modelování vyvolání tohoto <xref:System.Activities.ActivityAction%601><xref:System.Activities.Statements.InvokeAction%601>. V tomto příkladu je definována vlastní aktivita `WriteLineWithNotification`. Tato aktivita se skládá z <xref:System.Activities.Statements.Sequence>, která obsahuje aktivitu <xref:System.Activities.Statements.WriteLine> následovanou <xref:System.Activities.Statements.InvokeAction%601>, která vyvolá <xref:System.Activities.ActivityAction%601>, který přijímá jeden řetězcový argument.

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

Když je pracovní postup vytvořen pomocí aktivity `WriteLineWithNotification`, Autor pracovního postupu Určuje požadovanou vlastní logiku v <xref:System.Activities.ActivityDelegate.Handler%2A>akce aktivity. V tomto příkladu je vytvořen pracovní postup, který používá aktivitu `WriteLineWithNotification` a <xref:System.Activities.Statements.WriteLine> aktivita se používá jako <xref:System.Activities.ActivityDelegate.Handler%2A>.

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

Existuje několik obecných verzí <xref:System.Activities.Statements.InvokeAction%601> a <xref:System.Activities.ActivityAction%601> poskytuje pro předávání jednoho nebo více argumentů.

## <a name="using-activityfunc"></a>Použití ActivityFunc

<xref:System.Activities.ActivityAction%601> je užitečné, pokud neexistují žádné hodnoty výsledku z aktivity a <xref:System.Activities.ActivityFunc%601> se používá při vrácení hodnoty výsledku. Při vytváření vlastní aktivity definující <xref:System.Activities.ActivityFunc%601>použijte k modelování vyvolání tohoto <xref:System.Activities.ActivityFunc%601><xref:System.Activities.Expressions.InvokeFunc%601>. V následujícím příkladu je definována aktivita `WriteFillerText`. Chcete-li zadat text výplně, je zadána <xref:System.Activities.Expressions.InvokeFunc%601>, která přebírá celočíselný argument a má výsledek řetězce. Jakmile se načte text výplně, zobrazí se v konzole nástroje s použitím aktivity <xref:System.Activities.Statements.WriteLine>.

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

K zadávání textu je nutné použít aktivitu, která přijímá jeden `int` argument a má výsledek řetězce. Tento příklad ukazuje aktivitu `TextGenerator`, která splňuje tyto požadavky.

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

Chcete-li použít aktivitu `TextGenerator` s aktivitou `WriteFillerText`, zadejte ji jako <xref:System.Activities.ActivityDelegate.Handler%2A>.

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
