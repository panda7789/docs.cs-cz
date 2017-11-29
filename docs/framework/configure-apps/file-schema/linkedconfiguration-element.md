---
title: "&lt;linkedconfiguration –&gt; – element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bfea438ec19303c35ad9d7a2816cb7b9473a00c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linkedconfiguration-element"></a>\<linkedconfiguration – > elementu

Určuje konfigurační soubor pro zahrnout.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<assemblybinding – >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedconfiguration – >**

## <a name="syntax"></a>Syntaxe

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **href**  | Požadovaný atribut.<br><br>Adresa URL konfiguračního souboru, který chcete zahrnout. Pouze formát pro podporována **href** atribut je `file://`. Jsou podporovány místní soubory a soubory ve formátu UNC. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<assemblybinding – >** – Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Určuje sestavení vazby zásady na úrovni konfigurace. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

**\<Linkedconfiguration – >** element zjednodušuje údržbu sestavení součástí. Pokud jeden nebo více aplikací používat sestavení, který má konfigurační soubor umístěný v dobře známé umístění, můžete použít konfigurační soubory aplikace, které používají sestavení  **\<linkedconfiguration – >** Element zahrnout konfiguračního souboru sestavení, nikoli přímo včetně informace o konfiguraci. Při sestavení součástí je údržba, aktualizace konfiguračního souboru běžné poskytuje aktualizovaný konfigurační informace pro všechny aplikace, které používají sestavení.

> [!NOTE]
> **\<Linkedconfiguration – >** element není podporován pro aplikace s manifesty Windows vedle sebe.

Následující pravidla budou řídit použití propojené konfigurační soubory:

- Nastavení v zahrnuté konfigurační soubory pouze ovlivnit zavaděč vazby zásad a jsou používány pouze zavaděč. Zahrnuté konfigurační soubory, které může mít pouze vazby zásady nastavení, ale tato nastavení nemají žádný vliv.

- Pouze formát pro podporována `href` atribut je `file://`. Jsou podporovány místní soubory a soubory ve formátu UNC.

- Neexistuje žádné omezení počtu propojené konfigurace na konfigurační soubor.

- Všechny propojené konfigurační soubory jsou sloučeny do jednoho souboru, podobně jako u chování `#include` direktivy v jazyce C/C++.

- **\<Linkedconfiguration – >** element je povolena pouze v konfigurační soubory aplikace; je ignorován v *Machine.config*.

- Cyklické odkazy jsou zjištěna a byla ukončena. To znamená pokud  **\<linkedconfiguration – >** elementy řady konfigurační soubory tvoří cyklus, smyčky je zjištěna a zastavena.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zahrnout soubor konfigurace z místního pevného disku:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Viz také

[**\<assemblybinding – >** – Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
