---
title: Schéma nastavení aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f11be59941759687806591feb1edcce28b2119e6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203144"
---
# <a name="application-settings-schema"></a>Schéma nastavení aplikace

Nastavení aplikace umožňují aplikace Windows Forms nebo technologii ASP.NET ukládat a načítat nastavení s rozsahem aplikace a nastavení uživatele. V tomto kontextu *nastavení* libovolné informace, které může být specifické pro aplikaci nebo specifické pro aktuálního uživatele je – vše od připojovací řetězec databáze pro uživatele upřednostňovaného výchozí velikost okna.

Ve výchozím nastavení aplikace v aplikaci Windows Forms používá <xref:System.Configuration.LocalFileSettingsProvider> třídu, která využívá konfigurační systém .NET k ukládání nastavení do konfiguračního souboru XML. Další informace o souborech, které používají nastavení aplikace najdete v tématu [architektura nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-architecture.md).

Nastavení aplikace definuje následující prvky jako součást konfigurační soubory, které používá.

| Prvek                    | Popis                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | Obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro aplikaci.                         |
| **\<userSettings >**        | Obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro aktuálního uživatele.                        |
| **\<Nastavení >**             | Definuje nastavení. Podřízené buď  **\<applicationSettings >** nebo  **\<userSettings >**. |
| **\<Hodnota >**               | Definuje hodnoty nastavení. Podřízený  **\<Nastavení >**.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > – element

Tento prvek obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro instanci aplikace na klientském počítači. Definuje žádné atributy.

## <a name="usersettings-element"></a>\<userSettings > – element

Tento prvek obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro uživatele, který právě používá aplikace. Definuje žádné atributy.

## <a name="setting-element"></a>\<Nastavení > – element

Tento prvek definuje nastavení. Má následující atributy.

| Atribut        | Popis |
| ---------------- | ----------- |
| **Jméno**         | Požadováno. Jedinečné ID nastavení. Nastavení vytvořená pomocí sady Visual Studio se uloží s názvem `ProjectName.Properties.Settings`. |
| **serializedAs** | Požadováno. Formát, který se má použít pro serializaci hodnotu na text. Platné hodnoty jsou:<br><br>- `string`. Hodnota je serializován jako řetězec pomocí <xref:System.ComponentModel.TypeConverter>.<br>- `xml`. Hodnota je serializována použití serializace XML.<br>- `binary`. Hodnota je serializována jako binární kódování textu pomocí binární serializace.<br />- `custom`. Poskytovatel nastavení má vlastní znalostní báze tohoto nastavení a serializuje a deserializuje. |

## <a name="value-element"></a>\<Hodnota > – element

Tento prvek obsahuje hodnoty nastavení.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor nastavení aplikace, která definuje dvě nastavení s rozsahem aplikace a dvě nastavení rozsahu uživatele:

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

[Přehled nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[Architektura nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-architecture.md)
