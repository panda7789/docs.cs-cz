---
title: <remove>– element pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214758"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<remove>– element pro NameValueSectionHandler a DictionarySectionHandler

Odebere dříve definované nastavení.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntaxe

```xml
<add remove="key" />
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **zkrat**   | Požadovaný atribut.<br><br>Určuje název nastavení, které se má odebrat. |

## <a name="parent-element"></a>Nadřazený element

| Prvek | Description |
| ------- | ------------|
| [**\<sectionName>** Objekt](custom-element-2.md) | Definuje nastavení pro vlastní konfigurační oddíly, které používají <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> třídy a. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

Pomocí **\<remove>** elementu můžete odebrat nastavení z aplikace, které bylo definováno na vyšší úrovni v hierarchii konfiguračního souboru.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít **\<remove>** element v konfiguračním souboru aplikace k odebrání nastavení dříve definovaného v konfiguračním souboru počítače.

Následující kód konfiguračního souboru počítače deklaruje oddíl **\<mySection>** a přidá dvě nastavení `key1` a `key2` do něj:

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

Následující kód konfiguračního souboru aplikace odebere `key2` nastavení z **\<mySection>** :

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

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
