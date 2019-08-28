---
title: Akce dokončení instance
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 698ac0ed5a7cbd4f6a5623cf8d9b6fbea1128d0a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044333"
---
# <a name="instance-completion-action"></a>Akce dokončení instance

Vlastnost **Akce dokončení instance** úložiště instance pracovního postupu SQL umožňuje určit, zda jsou data a metadata instancí pracovních postupů po dokončení instancí odstraněny z databáze trvalosti. Povolené hodnoty pro tuto vlastnost jsou **DeleteAll** a **DeleteNothing**. Následující seznam popisuje tyto možnosti:

- **DeleteAll (výchozí).** Pokud je hodnota vlastnosti nastavena na DeleteAll, data a metadata instancí pracovního postupu jsou po dokončení instancí odstraněny z databáze trvalosti.

- **DeleteNothing.** Pokud je hodnota vlastnosti nastavena na DeleteNothing, data a metadata instancí pracovního postupu jsou uchovávány v databázi trvalosti i po dokončení instancí.

  > [!CAUTION]
  > Uchovávání informací o stavu instance po dokončení instancí způsobí, že databáze trvala velikost. Vzhledem k tomu, že velikost databáze rozroste databázové operace, které podsystém trvalosti trvá, je třeba pravidelně vyprázdnit informace o stavu instance z databáze trvalosti, aby služby prováděly na úrovni, která vyhovuje vašim požadavky na výkon.
