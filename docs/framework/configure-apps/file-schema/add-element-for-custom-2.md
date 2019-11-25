---
title: element <add> pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac07fc9ba6f030209a5e0d0160689fab95bc1b4a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088767"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<přidat > element pro NameValueSectionHandler a DictionarySectionHandler

Přidá vlastní nastavení aplikace. Každý **\<přidat značku >** obsahuje dvojici klíč/hodnota.

[ **\<configuration >** ](configuration-element.md) \
&nbsp;&nbsp;[ **\<sectiongroup >** ](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<přidat >**

## <a name="syntax"></a>Syntaxe

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Atributy

| Atribut | Popis |
| --------- | ----------- |
| **zkrat**   | Požadovaný atribut.<br><br>Určuje název nastavení. |
| **value** | Požadovaný atribut.<br><br>Určuje hodnotu nastavení. |

## <a name="parent-element"></a>Nadřazený element

| Prvek | Popis |
| ------- | ------------|
| [ **\<sectionGroup** Objekt](custom-element-2.md) | Definuje nastavení pro vlastní konfigurační oddíly, které používají třídy <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat vlastní konfigurační oddíl a použít **\<přidat >** elementu pro vložení nastavení do oddílu:

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
