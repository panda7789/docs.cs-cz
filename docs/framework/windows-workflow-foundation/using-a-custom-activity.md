---
title: Použití vlastní aktivity
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 47ddd42168445aa23eaaded6fd19ffe4698e4117
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669573"
---
# <a name="using-a-custom-activity"></a>Použití vlastní aktivity
Aktivity, které jsou odvozeny z <xref:System.Activities.Activity> nebo jejích podtříd složený do větší pracovních postupů, nebo přímo v kódu. Toto téma popisuje použití vlastních aktivit v vytvořených v kódu nebo v Návrháři pracovních postupů.  
  
> [!NOTE]
>  Můžete použít vlastní aktivity ve stejném projektu, ve kterém jsou definovány, tak dlouho, dokud vlastní aktivity a aktivity, která ji používá jsou zkompilovány (například načíst konkretizujete typem generovaných proces sestavení) Pokud je načtena odkazující aktivita dynamicky (např. při použití služba ActivityXAMLServices), pak odkazované sestavení umístit do jiného projektu nebo generovaný návrhářem XAML je třeba ručně upravit a povolit.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Použití vlastní aktivity do projektu pracovního postupu  
  
1. Přidáte odkaz na projekt knihovny aktivit obsahující vlastní aktivitu z projektu hostitel.  
  
2. Sestavte řešení.  
  
3. Chcete-li použít vlastní aktivity v návrháři, vyhledejte vlastní aktivity v sadě nástrojů a přetažením aktivity na plochu návrháře.  
  
4. Použití vlastní aktivity v kódu, přidejte příkaz Using, který odkazuje na projekt vlastní aktivity a předat novou instanci třídy aktivity na <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
