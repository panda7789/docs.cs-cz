---
title: Kontrola stromu aktivit
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 014795b79b3536b387096e4de64266e26649da21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774111"
---
# <a name="activity-tree-inspection"></a>Kontrola stromu aktivit
Kontrola stromu aktivit používá ke kontrole pracovních postupů hostitelem aplikace autoři aplikace pracovního postupu. S použitím <xref:System.Activities.WorkflowInspectionServices>, pracovní postupy lze vyhledávat konkrétní podřízené aktivity, jednotlivé aktivity a jejich vlastností můžete vytvořit výčet a mezipaměti metadat runtime aktivit v určitém čase. Toto téma obsahuje přehled <xref:System.Activities.WorkflowInspectionServices> a jak ho použít ke kontrole strom aktivity.  
  
## <a name="using-workflowinspectionservices"></a>Pomocí WorkflowInspectionServices  
 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Metoda se používá k vytvoření výčtu všech aktivit ve stromové struktuře zadané aktivita. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Vrátí Výčtový objekt, který se dotýká všechny aktivity v rámci stromu, včetně podřízené položky, obslužné rutiny delegáta, výchozí hodnoty proměnné a výrazy argumentu. V následujícím příkladu se vytvoří definice pracovního postupu pomocí <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.WriteLine>a výrazy. Po vytvoření definice pracovního postupu, je vyvolána a pak `InspectActivity` metoda je volána.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Výčet aktivit, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> je volán na kořenovou aktivitu a znovu rekurzivně pro každý vrácený aktivitu. V následujícím příkladu <xref:System.Activities.Activity.DisplayName%2A> jednotlivých aktivit a výrazů v aktivitě stromu zapsána do konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Tento vzorový kód obsahuje následující výstup.  
  
 **Položka 1**  
**Položka 2**   
**Položky seznamu 3**   
**Položky seznamu 4**   
**Položky seznamu 5**   
**Přidat do kolekce položek.**   
**Pořadí**   
 **Literál < seznam\<řetězec >>**  
 **While**  
 **AddToCollection\<String>**  
 **VariableValue<ICollection\<String>>**  
 **LambdaValue\<String>**  
 **LocationReferenceValue<List\<String>>**  
 **LambdaValue\<logická >**  
 **LocationReferenceValue<List\<String>>**  
 **ForEach\<řetězec >**  
 **VariableValue < IEnumerable\<řetězec >>**  
 **WriteLine**  
 **DelegateArgumentValue\<String>**  
 **Sequence**  
 **WriteLine**  
 **Literál\<řetězec >** načíst konkrétní aktivity místo vytvoření výčtu všech aktivit, <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> se používá. Obě <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> a <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> provést, pokud ukládání do mezipaměti metadat `WorkflowInspectionServices.CacheMetadata` dříve nebyla volána. Pokud <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> byla volána poté <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> vychází ze stávajících metadat. Proto pokud stromu se změnily od posledního volání <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> může vrátit neočekávané výsledky. Pokud byly provedeny změny do pracovního postupu po volání <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>, metadata můžete znovu uložit do mezipaměti pomocí volání <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metody. Ukládání do mezipaměti metadat je popsáno v další části.  
  
### <a name="caching-metadata"></a>Ukládání do mezipaměti metadat  
 Ukládání do mezipaměti metadat pro aktivitu sestavení a ověří popis aktivity argumenty proměnných, podřízené aktivity a delegátů aktivit. Metadata, ve výchozím nastavení, je uložit do mezipaměti modulem runtime tehdy, pokud je pro spuštění aktivity. Pokud chce, aby se Autor hostitele pracovního postupu pro ukládání do mezipaměti metadat pro aktivitu nebo stromu aktivit před tím, třeba když chcete provést všechny náklady na předem, pak <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> slouží k ukládání do mezipaměti metadat na požadovanou dobu.
