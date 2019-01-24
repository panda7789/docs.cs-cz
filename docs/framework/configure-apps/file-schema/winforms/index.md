---
title: Konfigurační oddíl pro model Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
---
# <a name="windows-forms-configuration-section"></a>Konfigurační oddíl pro model Windows Forms
Povolit aplikaci Windows Forms k uložení nastavení konfigurace Windows Forms a načíst informace o nastavení vlastní aplikace, jako je podpora více monitorů, podpora vysoké rozlišení DPI a další předdefinované nastavení konfigurace.

Nastavení konfigurace aplikace Windows Forms jsou uloženy v souboru konfigurace aplikace `System.Windows.Forms.ApplicationConfigurationSection` elementu.

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
[\<configuration>](../configuration-element.md) | Kořenový element v každém konfiguračním souboru tak, že modul common language runtime a Windows Forms používané aplikace |

## <a name="remarks"></a>Poznámky

Od verze rozhraní .NET Framework 4.7, `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje konfigurace aplikací Windows Forms, abyste mohli využívat funkce přidané v posledních verzích rozhraní .NET Framework. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Element může obsahovat jednu nebo více podřízených [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) prvky, z nichž každý definuje konkrétní nastavení.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../index.md)
- [Podpora vysokého nastavení DPI ve Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
