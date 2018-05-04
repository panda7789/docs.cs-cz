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
manager: markl
ms.openlocfilehash: 7af6342e9c05fc4e6c1bf4daac59db14ccdf22c7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="application-settings-schema"></a>Schéma nastavení aplikace

Nastavení aplikace umožňují k aplikaci Windows Forms nebo v technologii ASP.NET pro ukládání a načítání nastavení obor aplikace a nastavení uživatele. V tomto kontextu *nastavení* je jakékoliv informace, které může být specifické pro aplikace nebo specifické pro aktuálního uživatele – vše od připojovací řetězec databáze pro uživatele preferovaný výchozí velikost okna.

Ve výchozím nastavení aplikace v aplikaci Windows Forms používá <xref:System.Configuration.LocalFileSettingsProvider> třídy, která používá konfigurační systém .NET k ukládání nastavení v konfiguračním souboru XML. Další informace o souborech používá nastavení aplikace najdete v tématu [architektura nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-architecture.md).

Nastavení aplikace definuje následující prvky jako součást konfiguračních souborů, které používá.

| Prvek                    | Popis                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | Obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro aplikaci.                         |
| **\<userSettings >**        | Obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro aktuálního uživatele.                        |
| **\<Nastavení >**             | Definuje nastavení. Podřízená položka buď  **\<applicationSettings >** nebo  **\<userSettings >**. |
| **\<Hodnota >**               | Definuje hodnoty nastavení. Podřízená položka  **\<Nastavení >**.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > elementu

Tento prvek obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro instance aplikace na klientském počítači. Definuje žádné atributy.

## <a name="usersettings-element"></a>\<userSettings > elementu

Tento prvek obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro uživatele, který je aktuálně používá aplikace. Definuje žádné atributy.

## <a name="setting-element"></a>\<Nastavení > elementu

Tento element definuje nastavení. Má následující atributy.

| Atribut        | Popis |
| ---------------- | ----------- |
| **Jméno**         | Požadováno. Jedinečné ID nastavení. Nastavení vytvořená pomocí sady Visual Studio se uloží s názvem `ProjectName.Properties.Settings`. |
| **serializedAs** | Požadováno. Formát, který se má použít pro serializaci hodnotu na text. Platné hodnoty jsou:<br><br>- `string`. Hodnota je serializován jako řetězec pomocí <xref:System.ComponentModel.TypeConverter>.<br>- `xml`. Hodnota serializován pomocí serializace XML.<br>- `binary`. Hodnota je serializováno jako binární kódování textu pomocí binární serializace.<br />- `custom`. Poskytovatel nastavení má informace o toto nastavení serializuje a poté serializuje ho. |

## <a name="value-element"></a>\<Hodnota > elementu

Tento prvek obsahuje hodnotu nastavení.

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor nastavení aplikace, který definuje dvě nastavení obor aplikace a dvě uživatelských nastavení:

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

[Přehled nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[Architektura nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-architecture.md)
