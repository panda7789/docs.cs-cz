---
title: Konfigurační oddíl pro model Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151829"
---
# <a name="windows-forms-configuration-section"></a>Konfigurační oddíl pro model Windows Forms
Nastavení konfigurace model Windows Forms umožňuje aplikaci model Windows Forms ukládat a načítat informace o přizpůsobených nastaveních aplikace, jako je podpora více monitorů, podpora vysokého rozlišení DPI a další předdefinovaná nastavení konfigurace.

Model Windows Forms nastavení konfigurace aplikace jsou uložena v elementu konfiguračního souboru aplikace `System.Windows.Forms.ApplicationConfigurationSection` .

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

Prvek  |Description |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | Přidá klíč nastavení konfigurace se zadanou hodnotou. |

### <a name="parent-elements"></a>Nadřazené prvky

Prvek  |Description |
---------|---------|
[\<configuration>](../configuration-element.md) | Kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a model Windows Forms aplikacemi |

## <a name="remarks"></a>Poznámky

Počínaje .NET Framework 4,7 `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje nakonfigurovat model Windows Forms aplikace, aby využívaly výhody funkcí přidaných v posledních verzích .NET Framework.

`<System.Windows.Forms.ApplicationConfigurationSection>`Element může obsahovat jeden nebo více podřízených [`<add>`](windows-forms-add-configuration-element.md) elementů, z nichž každý definuje konkrétní nastavení konfigurace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru](../index.md)
- [Podpora vysokého rozlišení DPI v model Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md)
