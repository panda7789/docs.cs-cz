---
title: Přidání odkazu na službu do řešení pracovního postupu
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 577026249e00b528cf5c6e7ccd9527e02cb22a28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597667"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a>Přidání odkazu na službu do řešení pracovního postupu

Přidání odkazu na službu v aplikaci pracovního postupu funguje trochu jinak než v běžné aplikaci WCF. Když vyberete možnost **Přidat**  >  **odkaz na službu** a zadáte adresu URL ke službě, stáhnou se metadata a vygenerují se vlastní aktivity, které vám umožní zavolat tuto službu WCF nebo službu pracovního postupu WCF. Po přidání odkazu na službu znovu sestavte řešení, aby byly vytvořeny generované aktivity. Budou se pak zobrazovat v sadě nástrojů návrháře pracovních postupů. To bude fungovat jenom v případě, že přidáváte odkaz na službu v rámci řešení pracovního postupu. Následující webové přetypování ukazuje, jak přidat odkaz na službu v jiných typech projektů: [volání služby WCF z pracovního postupu ve webovém projektu](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).

Pokud přidáte dva nebo více odkazů na služby, které obsahují stejný název operace, dojde k problému. Generované aktivity budou volat pouze první operaci služby. Pokud chcete tento problém obejít, přejmenujte operace služby tak, aby se lišily, nebo změňte název konfigurace koncového bodu v rámci každé generované aktivity.

## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](workflow-services.md)
- [Volání služby WCF z pracovního postupu ve webovém projektu](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
