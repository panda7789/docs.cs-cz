---
title: Schéma nastavení aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242826"
---
# <a name="application-settings-schema"></a>Schéma nastavení aplikace

Nastavení aplikace umožňují formulářům systému Windows nebo ASP.NET aplikaci ukládat a načítat nastavení s rozsahem aplikace a s rozsahem uživatele. V tomto kontextu *nastavení* je libovolná část informace, která může být specifická pro aplikaci nebo specifické pro aktuálního uživatele – cokoli od připojovacího řetězce databáze až po upřednostňovanou výchozí velikost okna uživatele.

Ve výchozím nastavení používá nastavení aplikace <xref:System.Configuration.LocalFileSettingsProvider> v aplikaci Windows Forms třídu, která používá konfigurační systém .NET k ukládání nastavení do konfiguračního souboru XML. Další informace o souborech používaných v nastavení aplikace naleznete v [tématu Architektura nastavení aplikace](../../winforms/advanced/application-settings-architecture.md).

Nastavení aplikace definuje následující prvky jako součást konfiguračních souborů, které používá.

| Prvek                    | Popis                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<aplikaceNastavení>** | Obsahuje ** \<** všechna nastavení>značky specifické pro aplikaci.                         |
| **\<uživatelNastavení>**        | Obsahuje ** \<** všechna nastavení>značky specifické pro aktuálního uživatele.                        |
| **\<nastavení>**             | Definuje nastavení. Podřízená ** \<aplikaceNastavení>** nebo ** \<userSettings>**. |
| **\<hodnota>**               | Definuje hodnotu nastavení. Dítě ** \<nastavení>**.                                   |

## <a name="applicationsettings-element"></a>\<applicationNastavení> elementu

Tento prvek ** \<** obsahuje všechna nastavení>značky, které jsou specifické pro instanci aplikace v klientském počítači. Definuje žádné atributy.

## <a name="usersettings-element"></a>\<userSettings> element

Tento prvek ** \<** obsahuje všechna nastavení>značky, které jsou specifické pro uživatele, který aktuálně používá aplikaci. Definuje žádné atributy.

## <a name="setting-element"></a>\<nastavení> prvku

Tento prvek definuje nastavení. Má následující atributy.

| Atribut        | Popis |
| ---------------- | ----------- |
| **Jméno**         | Povinná hodnota. Jedinečné ID nastavení. Nastavení vytvořená prostřednictvím sady `ProjectName.Properties.Settings`Visual Studio jsou uložena s názvem . |
| **serializeAs** | Povinná hodnota. Formát, který se má použít pro serializaci hodnoty na text. Platné hodnoty jsou:<br><br>- `string`. Hodnota je serializována jako <xref:System.ComponentModel.TypeConverter>řetězec pomocí .<br>- `xml`. Hodnota je serializována pomocí serializace XML.<br>- `binary`. Hodnota je serializována jako binární kódovaný text pomocí binární serializace.<br />- `custom`. Poskytovatel nastavení má vlastní znalosti o tomto nastavení a serializuje a deserializuje jej. |

## <a name="value-element"></a>\<prvek> hodnoty

Tento prvek obsahuje hodnotu nastavení.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor nastavení aplikace, který definuje dvě nastavení s rozsahem aplikace a dvě nastavení s rozsahem uživatele:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Přehled nastavení aplikace](../../winforms/advanced/application-settings-overview.md)
- [Architektura nastavení aplikace](../../winforms/advanced/application-settings-architecture.md)
