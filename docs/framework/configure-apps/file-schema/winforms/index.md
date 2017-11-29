---
title: "Windows Forms konfigurační oddíl"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b83f00f82de727812c5737915a6dc35ec98e4734
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="windows-forms-configuration-section"></a>Windows Forms konfigurační oddíl
Windows Forms – nastavení konfigurace povolit aplikaci Windows Forms k ukládání a načíst informace o nastavení vlastní aplikace, jako je například více monitorů, vysoké DPI podpory a další předdefinovaná nastavení konfigurace.

Nastavení konfigurace aplikace Windows Forms jsou uložené v souboru konfigurace aplikace `System.Windows.Forms.ApplicationConfigurationSection` elementu.

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
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | Přidá klíč nastavení konfigurace se zadanou hodnotou |

### <a name="parent-elements"></a>Nadřazené prvky

Prvek  |Popis |
---------|---------|
[\<Konfigurace >](../configuration-element.md) | Kořenový element v každém konfiguračním souboru používá modul common language runtime a systém Windows Forms aplikace |

## <a name="remarks"></a>Poznámky

Od verze 4.7 rozhraní .NET Framework, `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje nakonfigurovat aplikace Windows Forms chcete využít výhod funkce přidané v posledních verzích rozhraní .NET Framework. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Element může obsahovat jeden nebo více podřízených [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) prvky, z nichž každý definuje konkrétní konfigurační nastavení.

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru](../index.md)   
[Podpora vysoké DPI ve Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
