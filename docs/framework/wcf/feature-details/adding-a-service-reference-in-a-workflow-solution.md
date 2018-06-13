---
title: Přidání odkazu na službu do řešení pracovního postupu
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 01bf4b0040d545ce42a9a7c803767aa4925de75e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488322"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Přidání odkazu na službu do řešení pracovního postupu
Přidání odkazu na službu do pracovního postupu aplikace funguje trochu jinak, než regulární aplikace WCF. Když vyberete Přidat odkaz na službu a zadejte adresu URL služby stáhne metadata a jsou generovány vlastních aktivit, které vám umožní volání služby WCF nebo pracovního postupu služby WCF přidat odkaz na. Po přidání odkazu na službu, znovu sestavte řešení, tak generovaného aktivity jsou vytvořeny. Se potom zobrazí v panelu nástrojů Návrháře pracovního postupu. Všimněte si však, že bude fungovat pouze pokud přidáváte odkazu na službu v rámci řešení pracovního postupu. Následující webové přetypování ukazuje, jak přidat odkaz na službu v jiné typy projektů: [volání z pracovního postupu v projektu webové služby WCF](http://go.microsoft.com/fwlink/?LinkId=207725).  
  
 Přidání dvou nebo více odkazů na služby pro služby, které obsahují stejný název operace způsobí, že problém. Vygenerovaný aktivity bude volat pouze první operaci služby. Chcete-li vyřešit tento problém přejmenování operací služby tak, aby se liší nebo změňte název konfigurace koncového bodu uvnitř generovaného aktivity.  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Postupy: Vytvoření služby pracovních postupů, která volá jinou službu pracovních postupů](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [Volání z pracovního postupu v projektu webové služby WCF](http://go.microsoft.com/fwlink/?LinkId=207725)
