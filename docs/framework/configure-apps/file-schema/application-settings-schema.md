---
title: Schéma nastavení aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 89a08434332b0242fe57e9dcaa3b3ebcc5692d06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927753"
---
# <a name="application-settings-schema"></a>Schéma nastavení aplikace

Nastavení aplikace umožňuje aplikaci model Windows Forms nebo ASP.NET ukládat a načítat nastavení s rozsahem aplikace a uživatelem. V tomto kontextu je *nastavením* jakékoli informace, které mohou být specifické pro aplikaci nebo specifické pro aktuálního uživatele – cokoli z databázového připojovacího řetězce až po upřednostňovanou výchozí velikost okna uživatele.

Ve výchozím nastavení používá <xref:System.Configuration.LocalFileSettingsProvider> nastavení aplikace v model Windows Forms aplikace třídu, která používá konfigurační systém .NET k ukládání nastavení v konfiguračním souboru XML. Další informace o souborech používaných nastavením aplikace najdete v tématu [Architektura nastavení aplikace](../../winforms/advanced/application-settings-architecture.md).

Nastavení aplikace definuje následující prvky jako součást konfiguračních souborů, které používá.

| Prvek                    | Popis                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | Obsahuje všechna  **\<nastavení >** značek specifických pro aplikaci.                         |
| **\<userSettings>**        | Obsahuje všechna  **\<nastavení >** značek specifických pro aktuálního uživatele.                        |
| **\<Nastavení >**             | Definuje nastavení. Podřízená položka buď  **\<ApplicationSettings >** nebo  **\<UserSettings >** . |
| **\<value>**               | Definuje hodnotu nastavení. Podřízená položka  **Nastavení>.\<**                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings – element >

Tento prvek obsahuje všechna  **\<nastavení >** značek, které jsou specifické pro instanci aplikace v klientském počítači. Nedefinuje žádné atributy.

## <a name="usersettings-element"></a>\<userSettings – element >

Tento prvek obsahuje všechna  **\<nastavení >** značek, které jsou specifické pro uživatele, který aktuálně používá aplikaci. Nedefinuje žádné atributy.

## <a name="setting-element"></a>\<nastavení elementu >

Tento prvek definuje nastavení. Má následující atributy.

| Atribut        | Popis |
| ---------------- | ----------- |
| **name**         | Povinný parametr. Jedinečné ID nastavení Nastavení vytvořená pomocí sady Visual Studio se ukládají s `ProjectName.Properties.Settings`názvem. |
| **serializedAs** | Povinný parametr. Formát, který má být použit pro serializaci hodnoty na text. Platné hodnoty jsou:<br><br>- `string`. Hodnota je serializována jako řetězec pomocí <xref:System.ComponentModel.TypeConverter>.<br>- `xml`. Hodnota je serializovaná pomocí serializace XML.<br>- `binary`. Hodnota je serializována jako textový soubor s kódováním pomocí binární serializace.<br />- `custom`. Poskytovatel nastavení má znalosti tohoto nastavení a serializace a deserializace. |

## <a name="value-element"></a>\<Value – element >

Tento prvek obsahuje hodnotu nastavení.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor nastavení aplikace, který definuje dvě nastavení rozsahu aplikace a dvě nastavení v uživatelském rozsahu:

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

## <a name="see-also"></a>Viz také:

- [Přehled nastavení aplikace](../../winforms/advanced/application-settings-overview.md)
- [Architektura nastavení aplikace](../../winforms/advanced/application-settings-architecture.md)
