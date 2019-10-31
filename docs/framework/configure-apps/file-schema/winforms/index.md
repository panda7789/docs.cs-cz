---
title: Konfigurační oddíl pro model Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4a54df0b6301f1aae14d5561c91c6792cb0a1620
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109816"
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
[Konfigurace \<](../configuration-element.md) | Kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a model Windows Forms aplikacemi |

## <a name="remarks"></a>Poznámky

Počínaje .NET Framework 4,7 `<System.Windows.Forms.ApplicationConfigurationSection>` prvek umožňuje nakonfigurovat model Windows Forms aplikace, aby využívaly funkce přidané v posledních verzích .NET Framework. 

Element `<System.Windows.Forms.ApplicationConfigurationSection>` může obsahovat jeden nebo více podřízených [`<add>`](windows-forms-add-configuration-element.md) prvků, z nichž každý definuje konkrétní nastavení konfigurace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../index.md)
- [Podpora vysokého rozlišení DPI v model Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md)
