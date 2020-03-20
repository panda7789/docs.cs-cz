---
title: Konfigurační oddíl pro model Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151829"
---
# <a name="windows-forms-configuration-section"></a>Konfigurační oddíl pro model Windows Forms
Nastavení konfigurace windows forms umožňují aplikaci Windows Forms ukládat a načítat informace o přizpůsobených nastaveních aplikací, jako je podpora více monitorů, vysoká podpora DPI a další předdefinovaná nastavení konfigurace.

Nastavení konfigurace aplikace windows forms jsou uložena `System.Windows.Forms.ApplicationConfigurationSection` v prvku konfiguračního souboru aplikace.

## <a name="syntax"></a>Syntaxe

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

Žádné.

### <a name="child-elements"></a>Podřízené prvky

Element  |Popis |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | Přidá klíč nastavení konfigurace se zadanou hodnotou. |

### <a name="parent-elements"></a>Nadřazené prvky

Element  |Popis |
---------|---------|
[\<>konfigurace](../configuration-element.md) | Kořenový prvek v každém konfiguračním souboru používaném běžným jazykem runtime a aplikacemi Windows Forms |

## <a name="remarks"></a>Poznámky

Počínaje rozhraním .NET Framework 4.7 umožňuje `<System.Windows.Forms.ApplicationConfigurationSection>` tento prvek konfigurovat aplikace windows forms tak, aby využívaly funkce přidané v posledních verzích rozhraní .NET Framework.

Prvek `<System.Windows.Forms.ApplicationConfigurationSection>` může obsahovat jeden [`<add>`](windows-forms-add-configuration-element.md) nebo více podřízených prvků, z nichž každý definuje konkrétní nastavení konfigurace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru](../index.md)
- [Vysoká podpora DPI ve formulářích systému Windows](../../../winforms/high-dpi-support-in-windows-forms.md)
