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
ms.openlocfilehash: 909ee7cbb7cd31cf213f305b23237cb69e295882
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674646"
---
# <a name="linkedconfiguration-element"></a>\<linkedconfiguration – > – element

Určuje konfigurační soubor, který chcete zahrnout.

[ **\<Konfigurace >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<assemblybinding – >** ](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**

## <a name="syntax"></a>Syntaxe

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **href**  | Požadovaný atribut.<br><br>Adresa URL konfiguračního souboru chcete zahrnout. Jediným formátem podporovaným **href** atribut je `file://`. Jsou podporovány místní soubory a soubory ve formátu UNC. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [ **\<assemblybinding – >** – Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Určuje zásady vazeb sestavení na úrovni konfigurace. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

**\<Linkedconfiguration – >** element zjednodušuje údržbu pro sestavení komponent. Pokud jeden nebo více aplikací používat sestavení, která obsahuje konfigurační soubor umístěný v dobře známého umístění, můžete použít konfigurační soubory aplikace, které používají sestavení **\<linkedconfiguration – >** Element zahrnout konfigurační soubor sestavení, nikoli přímo včetně informací o konfiguraci. Při sestavení součástí je údržba, aktualizace společné konfigurační soubor obsahuje informace aktualizovanou konfiguraci pro všechny aplikace, které používají sestavení.

> [!NOTE]
> **\<Linkedconfiguration – >** element není podporován pro aplikace s Windows manifesty vedle sebe.

Následující pravidla určují, použití propojené konfigurační soubory:

- Nastavení v souborech konfigurace na zahrnuté pouze ovlivnit zavaděč zásady vazeb a jsou používány pouze zavaděč. Konfigurace zahrnuté soubory mohou mít nastavení vazby zásady, ale tato nastavení nemají žádný vliv.

- Jediným formátem podporovaným `href` atribut je `file://`. Jsou podporovány místní soubory a soubory ve formátu UNC.

- Neexistuje žádné omezení počtu propojené konfigurace na konfigurační soubor.

- Všechny propojené konfigurační soubory jsou sloučeny do jednoho souboru, podobně jako chování `#include` direktiva v jazyce C/C++.

- **\<Linkedconfiguration – >** element je povolen pouze v konfiguračních souborech aplikace, je ignorován v *Machine.config*.

- Cyklické odkazy jsou zjištěny a byla ukončena. To znamená pokud  **\<linkedconfiguration – >** prvky z řady konfigurační soubory tvoří cyklus, smyčky je zjištěna a zastavena.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zahrnout konfigurační soubor z místního pevného disku:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [ **\<assemblybinding – >** – Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)
- [Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
