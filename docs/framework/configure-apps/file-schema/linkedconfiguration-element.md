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
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921016"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration – element >

Určuje konfigurační soubor, který se má zahrnout.

[ **\<> Konfigurace**](configuration-element.md)   
&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**

## <a name="syntax"></a>Syntaxe

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **href**  | Požadovaný atribut.<br><br>Adresa URL konfiguračního souboru, který se má zahrnout. Jediným formátem, který je podporován pro atribut `file://`href, je. Podporují se místní soubory a soubory UNC. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [assemblyBinding – element >  **\<** ](assemblybinding-element-for-configuration.md) | Určuje zásadu vazby sestavení na úrovni konfigurace. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

**\<Linkedconfiguration – >** element zjednodušuje údržbu pro sestavení komponent. Pokud jeden nebo více aplikací používat sestavení, která obsahuje konfigurační soubor umístěný v dobře známého umístění, můžete použít konfigurační soubory aplikace, které používají sestavení **\<linkedconfiguration – >** Element zahrnout konfigurační soubor sestavení, nikoli přímo včetně informací o konfiguraci. V případě, že je použito sestavení komponenty, aktualizace společného konfiguračního souboru poskytne aktualizované informace o konfiguraci pro všechny aplikace, které používají sestavení.

> [!NOTE]
> **\<Linkedconfiguration – >** element není podporován pro aplikace s Windows manifesty vedle sebe.

Použití propojených konfiguračních souborů závisí na následujících pravidlech:

- Nastavení v zahrnutých konfiguračních souborech ovlivní pouze zásady vazby zavaděče a používají se pouze zavaděč. Zahrnuté konfigurační soubory mohou mít nastavení jiné než zásady vazeb, ale tato nastavení nemají žádný vliv.

- Jediným formátem, který je `href` podporován pro `file://`atribut, je. Podporují se místní soubory a soubory UNC.

- Počet propojených konfigurací na konfigurační soubor není nijak omezený.

- Všechny propojené konfigurační soubory jsou sloučeny, aby tvořily jeden soubor podobný chování `#include` direktivy v C/.C++

- **\<Linkedconfiguration – >** element je povolen pouze v konfiguračních souborech aplikace, je ignorován v *Machine.config*.

- Byly zjištěny a ukončeny cyklické odkazy. To znamená, že pokud  **\<linkedConfiguration >** prvky řady konfiguračních souborů tvoří smyčku, je tato smyčka zjištěna a zastavena.

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

- [assemblyBinding – element >  **\<** ](assemblybinding-element-for-configuration.md)
- [Schéma konfiguračního souboru pro .NET Framework](index.md)
