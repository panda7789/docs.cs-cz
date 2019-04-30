---
title: Akce dokončení instance
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 646015fbcdb7c734ae8584c7ca3979d64b81339f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791115"
---
# <a name="instance-completion-action"></a>Akce dokončení instance
**Akce dokončení Instance** vlastnost Store Instance pracovního postupu SQL umožňuje určit, zda data a metadata instancí pracovních postupů je odstraněn z databáze stálost po dokončení instance. Povolené hodnoty pro tuto vlastnost **DeleteAll** a **DeleteNothing**. Následující seznam popisuje tyto možnosti:  
  
- **DeleteAll (výchozí).** Pokud je nastavena hodnota vlastnosti DeleteAll, data a metadata instancí pracovních postupů je odstranit z databáze stálost po dokončení instance.  
  
- **DeleteNothing.** Pokud je nastavena hodnota vlastnosti DeleteNothing, data a metadata instancí pracovních postupů, zůstane databáze trvalosti i po dokončení instance.  
  
    > [!CAUTION]
    >  Zachování informací o stavu instance instance po dokončení způsobí, že databáze stálost k rozvoji velikosti. Databázových operací, které provádí subsystému trvalost nárůstu velikosti databáze trvat déle, takže je třeba vymazat informace o stavu instance z databáze trvalosti pravidelně, aby se mají provést na úrovni služby, které splňují vaše požadavkům na výkon.
