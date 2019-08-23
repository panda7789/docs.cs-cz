---
title: Konfigurační oddíl pro model Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e76e11ef8bb39d72cb16655c948354bc326e75bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913086"
---
# <a name="windows-forms-configuration-section"></a>Konfigurační oddíl pro model Windows Forms
Nastavení konfigurace model Windows Forms umožňuje aplikaci model Windows Forms ukládat a načítat informace o přizpůsobených nastaveních aplikace, jako je podpora více monitorů, podpora vysokého rozlišení DPI a další předdefinovaná nastavení konfigurace.

Model Windows Forms nastavení konfigurace aplikace jsou uložena v `System.Windows.Forms.ApplicationConfigurationSection` elementu konfiguračního souboru aplikace.

## <a name="syntax"></a>Syntaxe

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

Žádné

### <a name="child-elements"></a>Podřízené prvky

Prvek  |Popis |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | Přidá klíč nastavení konfigurace se zadanou hodnotou. |

### <a name="parent-elements"></a>Nadřazené prvky

Prvek  |Popis |
---------|---------|
[\<> Konfigurace](../configuration-element.md) | Kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a model Windows Forms aplikacemi |

## <a name="remarks"></a>Poznámky

Počínaje .NET Framework 4,7 `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje nakonfigurovat model Windows Forms aplikace, aby využívaly výhody funkcí přidaných v posledních verzích .NET Framework. 

Element může obsahovat jeden nebo více podřízených [`<add>`](windows-forms-add-configuration-element.md) elementů, z nichž každý definuje konkrétní nastavení konfigurace. `<System.Windows.Forms.ApplicationConfigurationSection>`

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../index.md)
- [Podpora vysokého rozlišení DPI v model Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md)
