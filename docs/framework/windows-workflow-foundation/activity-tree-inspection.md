---
title: Kontrola stromu aktivit
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 692f36d993c3f9c27839122b388a24d0698a2b59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183041"
---
# <a name="activity-tree-inspection"></a>Kontrola stromu aktivit
Kontrola stromu aktivit je používána autory aplikací pracovního postupu ke kontrole pracovních postupů hostovaných aplikací. Pomocí <xref:System.Activities.WorkflowInspectionServices>, pracovní postupy lze vyhledávat pro konkrétní podřízené aktivity, jednotlivé aktivity a jejich vlastnosti mohou být výčtu a runtime metadata aktivit y mohou být uloženy do mezipaměti v určitém čase. Toto téma obsahuje <xref:System.Activities.WorkflowInspectionServices> přehled a jak jej použít ke kontrole stromu aktivit.  
  
## <a name="using-workflowinspectionservices"></a>Použití služby WorkflowInspectionServices  
 Metoda <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> se používá k výčetu všech aktivit ve stromu zadané aktivity. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>vrátí výčtový počet, který se dotýká všech aktivit ve stromu, včetně podřízených rutin, obslužných rutin delegáta, výchozích proměnných a výrazů argumentů. V následujícím příkladu je definice pracovního <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.While>postupu <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.WriteLine>vytvořena pomocí výrazů , , , a výrazů. Po vytvoření definice pracovního postupu je vyvolána a `InspectActivity` pak je volána metoda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Chcete-li výčet aktivity, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> je volána na kořenové aktivity a znovu rekurzivně na každou vrácenou aktivitu. V následujícím příkladu <xref:System.Activities.Activity.DisplayName%2A> je každá aktivita a výraz ve stromu aktivit zapsán do konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Tento ukázkový kód poskytuje následující výstup.  
  
 **Položka seznamu 1**  
**Seznam položka 2**
**Seznam Položka 3**
**Seznam Položka 4**
**Seznam Položka 5**
**Položky přidány do sbírky.** 
 **Řetězec** **<\<vsečnatých<>>sekvence**  
 **Zatímco**  
 **Řetězec AddToCollection\<>**  
 **>>řetězec VariableValue<ICollection\<**  
 **Řetězec LambdaValue\<>**  
 **Řetězec<seznamu\<LocationReferenceValue>>**  
 **LambdaValue\<logická>**  
 **Řetězec<seznamu\<LocationReferenceValue>>**  
 **Pro\<každý řetězec>**  
 **>>řetězce IEnumerable Řetězce proměnné<hodnoty ienumerable\<**  
 **WriteLine**  
 **>řetězec\<Delegačního argumentu**  
 **Sequence**  
 **WriteLine**  
 **Literál\<Řetězec>** Chcete-li načíst konkrétní aktivitu namísto výčtu všech aktivit, <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> se používá. Oba <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> a provádět ukládání metadat `WorkflowInspectionServices.CacheMetadata` do mezipaměti, pokud nebyla dříve volána. Pokud <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> byla volána pak <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> je založena na existující metadata. Proto pokud byly provedeny změny stromu <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>od <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> posledního volání do , může poskytnout neočekávané výsledky. Pokud byly provedeny změny v <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>pracovním postupu po volání , metadata <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> lze znovu ukládat do mezipaměti voláním metody. Ukládání metadat do mezipaměti je popsáno v další části.  
  
### <a name="caching-metadata"></a>Metadata ukládání do mezipaměti  
 Ukládání metadat do mezipaměti pro aktivitu vytvoří a ověří popis argumentů, proměnných, podřízených aktivit a delegátů aktivity. Metadata jsou ve výchozím nastavení ukládána do mezipaměti modulu runtime, když je aktivita připravena k provedení. Pokud autor hostitele pracovního postupu chce ukládat metadata pro aktivitu nebo strom aktivity před <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> tímto, například vzít všechny náklady předem, pak lze použít k ukládání metadat do mezipaměti v požadovaném čase.
