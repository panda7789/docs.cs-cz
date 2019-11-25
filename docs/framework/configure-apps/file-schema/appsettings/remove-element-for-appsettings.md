---
title: <remove> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0fcdb75aa733a9d7634ec1c3b31dcbbb87e090e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088722"
---
# <a name="remove-element-for-appsettings"></a>\<odebrat element > pro \<appSettings >

Odebere vlastní nastavení aplikace.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**

## <a name="syntax"></a>Syntaxe

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Atribut

|         | Popis |
| ------- | ----------- |
| **zkrat** | Požadovaný atribut.<br><br>Určuje název klíče, který se má odebrat. |

### <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odebrat vlastní nastavení konfigurace pro `ApplicationName`:

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](../index.md)
