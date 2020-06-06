---
title: <linkedConfiguration> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: 14ee2275ecf690ab16ffaabd71fbbe7e1a4897bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087963"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration> – element

Určuje konfigurační soubor, který se má zahrnout.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a>Syntaxe

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **odkaz**  | Požadovaný atribut.<br><br>Adresa URL konfiguračního souboru, který se má zahrnout. Jediným formátem, který je podporován pro atribut **href** , je `file://` . Podporují se místní soubory a soubory UNC. |

## <a name="parent-element"></a>Nadřazený element

|     | Description |
| --- | ----------- |
| [**\<assemblyBinding>** Objekt](assemblybinding-element-for-configuration.md) | Určuje zásadu vazby sestavení na úrovni konfigurace. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

**\<linkedConfiguration>** Element zjednodušuje údržbu pro sestavení komponent. Pokud jedna nebo více aplikací používá sestavení, které má konfigurační soubor umístěný v dobře známém umístění, mohou konfigurační soubory aplikací, které používají sestavení, použít **\<linkedConfiguration>** element k zahrnutí konfiguračního souboru sestavení místo toho, aby byly přímo informace o konfiguraci. V případě, že je použito sestavení komponenty, aktualizace společného konfiguračního souboru poskytne aktualizované informace o konfiguraci pro všechny aplikace, které používají sestavení.

> [!NOTE]
> **\<linkedConfiguration>** Element není podporován pro aplikace s manifesty vedle sebe v systému Windows.

Použití propojených konfiguračních souborů závisí na následujících pravidlech:

- Nastavení v zahrnutých konfiguračních souborech ovlivní pouze zásady vazby zavaděče a používají se pouze zavaděč. Zahrnuté konfigurační soubory mohou mít nastavení jiné než zásady vazeb, ale tato nastavení nemají žádný vliv.

- Jediným formátem, který je podporován pro `href` atribut, je `file://` . Podporují se místní soubory a soubory UNC.

- Počet propojených konfigurací na konfigurační soubor není nijak omezený.

- Všechny propojené konfigurační soubory jsou sloučeny, aby tvořily jeden soubor podobný chování `#include` direktivy v C/C++.

- **\<linkedConfiguration>** Element je povolen pouze v konfiguračních souborech aplikace; ignoruje se v souboru *Machine. config*.

- Byly zjištěny a ukončeny cyklické odkazy. To znamená, že pokud **\<linkedConfiguration>** prvky řady konfiguračních souborů tvoří smyčku, je tato smyčka zjištěna a zastavena.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zahrnout konfigurační soubor z místního pevného disku:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Viz také

- [**\<assemblyBinding>** Objekt](assemblybinding-element-for-configuration.md)
- [Schéma konfiguračního souboru pro .NET Framework](index.md)
