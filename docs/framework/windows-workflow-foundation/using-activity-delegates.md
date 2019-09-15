---
title: Používání delegátů aktivit
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 63f550549456404b237067c98afdb18a8758dd7a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989084"
---
# <a name="using-activity-delegates"></a>Používání delegátů aktivit
Delegáti aktivity umožňují autorům aktivity vystavovat zpětná volání s konkrétními podpisy, pro které mohou uživatelé aktivity poskytovat obslužné rutiny založené na aktivitách. K dispozici jsou dva typy delegátů <xref:System.Activities.ActivityAction%601> aktivit: slouží k definování delegátů aktivity, které nemají návratovou hodnotu, <xref:System.Activities.ActivityFunc%601> a slouží k definování delegátů aktivity, které mají vrácenou hodnotu.

Delegáty aktivity jsou užitečné ve scénářích, kdy musí být podřízená aktivita omezená na určitý podpis. <xref:System.Activities.Statements.While> Aktivita může například obsahovat libovolný typ podřízené aktivity bez omezení, ale tělo <xref:System.Activities.Statements.ForEach%601> aktivity je <xref:System.Activities.ActivityAction%601>a podřízená aktivita, <xref:System.Activities.InArgument%601> která je nakonec vykonávána <xref:System.Activities.Statements.ForEach%601> , musí mít je stejný typ členů kolekce, které jsou <xref:System.Activities.Statements.ForEach%601> výčty.

## <a name="using-activityaction"></a>Použití ActivityAction

Několik [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] aktivit používá akce aktivity, například <xref:System.Activities.Statements.Catch> aktivity a <xref:System.Activities.Statements.ForEach%601> aktivity. V každém případě akce aktivity představuje umístění, kde Autor pracovního postupu určuje aktivitu, která poskytne požadované chování při vytváření pracovního postupu pomocí jedné z těchto aktivit. V následujícím příkladu <xref:System.Activities.Statements.ForEach%601> se aktivita používá k zobrazení textu v okně konzoly. Tělo <xref:System.Activities.Statements.ForEach%601> je určeno pomocí objektu <xref:System.Activities.ActivityAction%601> , který <xref:System.Activities.Statements.ForEach%601> odpovídá typu řetězce, který je řetězec. Aktivita zadaná <xref:System.Activities.Statements.WriteLine.Text%2A> <xref:System.Activities.Statements.ForEach%601> v argumentu <xref:System.Activities.ActivityDelegate.Handler%2A> má svůj argument svázaný s řetězcovými hodnotami v kolekci, kterou aktivita <xref:System.Activities.Statements.WriteLine> prochází.

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

ActionArgument se používá k flowování jednotlivých položek v kolekci do WriteLine. Po vyvolání pracovního postupu se do konzoly zobrazí následující výstup.

```console
HelloWorld.
```

Příklady v tomto tématu používají syntaxi inicializace objektu. Syntaxe inicializace objektu může být užitečný způsob, jak vytvořit definice pracovních postupů v kódu, protože poskytuje hierarchické zobrazení aktivit v pracovním postupu a znázorňuje vztah mezi aktivitami. Při vytváření pracovních postupů prostřednictvím kódu programu není nutné používat syntaxi inicializace objektu. Následující příklad je funkčně ekvivalentní k předchozímu příkladu.

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

Další informace o inicializátorech objektů naleznete v tématu [How to: Inicializujte objekty bez volání konstruktoru (C# Průvodce programováním](https://go.microsoft.com/fwlink/?LinkId=161015) ) [a postupy: Deklarujte objekt pomocí inicializátoru](https://go.microsoft.com/fwlink/?LinkId=161016)objektu.

V následujícím příkladu <xref:System.Activities.Statements.TryCatch> se aktivita používá v pracovním postupu. Pracovní <xref:System.ApplicationException> postup vyvolá výjimku, která je zpracována <xref:System.Activities.Statements.Catch%601> aktivitou. Obslužná rutina <xref:System.Activities.Statements.Catch%601> akce aktivity aktivity <xref:System.Activities.Statements.WriteLine> je aktivita a podrobnosti o výjimce jsou předávány do ní pomocí `ex`. <xref:System.Activities.DelegateInArgument%601>

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

Při vytváření vlastní aktivity, která definuje <xref:System.Activities.ActivityAction%601>, <xref:System.Activities.Statements.InvokeAction%601> použijte k modelování vyvolání <xref:System.Activities.ActivityAction%601>. V tomto příkladu je definována vlastní `WriteLineWithNotification` aktivita. Tato aktivita se skládá z typu <xref:System.Activities.Statements.Sequence> , který <xref:System.Activities.Statements.WriteLine> obsahuje aktivitu následovanou <xref:System.Activities.Statements.InvokeAction%601> , která vyvolá <xref:System.Activities.ActivityAction%601> jeden řetězcový argument.

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

Když je pracovní postup vytvořen pomocí `WriteLineWithNotification` aktivity, Autor pracovního postupu Určuje požadovanou vlastní logiku v <xref:System.Activities.ActivityDelegate.Handler%2A>akci aktivity. V tomto příkladu je vytvořen pracovní postup, který `WriteLineWithNotification` aktivitu používá, <xref:System.Activities.Statements.WriteLine> a <xref:System.Activities.ActivityDelegate.Handler%2A>aktivita se používá jako.

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

K předání jednoho nebo více argumentů <xref:System.Activities.Statements.InvokeAction%601> je <xref:System.Activities.ActivityAction%601> k dispozici několik obecných verzí a.

## <a name="using-activityfunc"></a>Použití ActivityFunc

<xref:System.Activities.ActivityAction%601>je užitečné v případě, že aktivita neobsahuje výsledek hodnoty a <xref:System.Activities.ActivityFunc%601> používá se při vrácení hodnoty výsledku. Při vytváření vlastní aktivity, která definuje <xref:System.Activities.ActivityFunc%601>, <xref:System.Activities.Expressions.InvokeFunc%601> použijte k modelování vyvolání <xref:System.Activities.ActivityFunc%601>. V následujícím příkladu `WriteFillerText` je definována aktivita. Chcete-li zadat text výplně, <xref:System.Activities.Expressions.InvokeFunc%601> je zadána hodnota, která přijímá celočíselný argument a má výsledek řetězce. Po načtení textu výplně se zobrazí v konzole s použitím <xref:System.Activities.Statements.WriteLine> aktivity.

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

Chcete-li text dodat, je nutné použít aktivitu, která přijímá `int` jeden argument a má výsledek řetězce. V tomto příkladu se `TextGenerator` zobrazuje aktivita, která splňuje tyto požadavky.

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

Chcete-li `TextGenerator` aktivitu použít `WriteFillerText` s aktivitou <xref:System.Activities.ActivityDelegate.Handler%2A>, zadejte ji jako.

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
