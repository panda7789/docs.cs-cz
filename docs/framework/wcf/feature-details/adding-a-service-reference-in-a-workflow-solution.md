---
title: Přidání odkazu na službu do řešení pracovního postupu
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 7197ae991207efd60ea398794c7c23f427f6b0cc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964217"
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Přidání odkazu na službu do řešení pracovního postupu

Přidání odkazu na službu v aplikaci pracovního postupu funguje trochu jinak než v běžné aplikaci WCF. Když vyberete možnost **přidat > odkaz na službu** a zadáte adresu URL ke službě, stáhnou se metadata a generují se vlastní aktivity, které vám umožní zavolat službu WCF nebo službu pracovního postupu WCF, na kterou jste přidali odkaz. Po přidání odkazu na službu znovu sestavte řešení, aby byly vytvořeny generované aktivity. Budou se pak zobrazovat v sadě nástrojů návrháře pracovních postupů. Upozorňujeme však, že bude fungovat pouze v případě, že přidáváte odkaz na službu v rámci řešení pracovního postupu. Následující webové přetypování ukazuje, jak přidat odkaz na službu v jiných typech projektů: [volání služby WCF z pracovního postupu ve webovém projektu](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

Pokud přidáte dva nebo více odkazů na služby, které obsahují stejný název operace, dojde k problému. Generované aktivity budou volat pouze první operaci služby. Pokud chcete tento problém obejít, přejmenujte operace služby tak, aby se lišily, nebo změňte název konfigurace koncového bodu v rámci každé generované aktivity.

## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Volání služby WCF z pracovního postupu ve webovém projektu](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
