---
title: Použití vlastní aktivity
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 6ca67ef7a8c4330d0182e960fc3fdcce656976a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962225"
---
# <a name="using-a-custom-activity"></a>Použití vlastní aktivity
Aktivity, které jsou <xref:System.Activities.Activity> odvozeny z nebo jejich podtříd, mohou být tvořeny většími pracovními postupy nebo přímo v kódu. V tomto tématu se dozvíte, jak používat vlastní aktivity v pracovních postupech vytvořených buď v kódu, nebo v návrháři.  
  
> [!NOTE]
> Vlastní aktivity lze použít ve stejném projektu, ve kterém jsou definovány, pokud vlastní aktivita i aktivita, která ji používá, je kompilována (tj. načtena typem vytvořeným procesem sestavení), pokud Odkazovaná aktivita je načtena. dynamicky (například s použitím metodu ActivityXamlServices), pak by odkazované sestavení mělo být umístěno v jiném projektu, nebo je nutné ručně upravit XAML generovaný návrhářem, aby to bylo možné povolit.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Použití vlastní aktivity do projektu pracovního postupu  
  
1. Přidejte odkaz z projektu hostitele do projektu knihovny aktivit, který obsahuje vlastní aktivitu.  
  
2. Sestavte řešení.  
  
3. Chcete-li použít vlastní aktivitu v návrháři, najděte vlastní aktivitu v sadě nástrojů a přetáhněte aktivitu na plochu návrháře.  
  
4. Chcete-li použít vlastní aktivitu v kódu, přidejte příkaz using, který odkazuje na projekt vlastní aktivity a předejte novou instanci aktivity do <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
