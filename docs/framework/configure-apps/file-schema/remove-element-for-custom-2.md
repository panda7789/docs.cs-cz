---
title: element <remove> pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6cdd5833e14da1ab5185e56dce1190adfee4a2bf
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089029"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<odebrat > element pro NameValueSectionHandler a DictionarySectionHandler

Odebere dříve definované nastavení.

[ **\<configuration >** ](configuration-element.md) \
&nbsp;&nbsp;[ **\<sectiongroup >** ](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**

## <a name="syntax"></a>Syntaxe

```xml
<add remove="key" />
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **zkrat**   | Požadovaný atribut.<br><br>Určuje název nastavení, které se má odebrat. |

## <a name="parent-element"></a>Nadřazený element

| Prvek | Popis |
| ------- | ------------|
| [ **\<sectionGroup** Objekt](custom-element-2.md) | Definuje nastavení pro vlastní konfigurační oddíly, které používají třídy <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

Pomocí elementu **\<remove >** můžete odebrat nastavení z aplikace, které bylo definováno na vyšší úrovni v hierarchii konfiguračního souboru.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít **\<odebrat >** elementu v konfiguračním souboru aplikace k odebrání nastavení dříve definovaného v konfiguračním souboru počítače.

Následující kód konfiguračního souboru počítače deklaruje oddíl **\<mySection >** a přidává do něj dvě nastavení, `key1` a `key2`:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Následující kód konfiguračního souboru aplikace odebere `key2` nastavení z **\<mySection >** :

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
