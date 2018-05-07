---
title: '&lt;Přidat&gt; element NameValueSectionHandler a DictionarySectionHandler'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
ms.openlocfilehash: aeb3e3a4be201369ca2df8d231498dd2400d3c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Přidat > element NameValueSectionHandler a DictionarySectionHandler

Přidá nastavení vlastní aplikace. Každý  **\<Přidat >** značka obsahuje dvojice klíč/hodnota.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Přidat >**

## <a name="syntax"></a>Syntaxe

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Atributy

| Atribut | Popis |
| --------- | ----------- |
| **Klíč**   | Požadovaný atribut.<br><br>Určuje název nastavení. |
| **value** | Požadovaný atribut.<br><br>Určuje hodnotu nastavení. |

## <a name="parent-element"></a>Nadřazený element

| Prvek | Popis |
| ------- | ------------|
| [**\<sectionName >** – Element](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Definuje nastavení pro vlastní konfiguračních oddílů, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat vlastní oddíl konfigurace a použít  **\<Přidat >** element převést nastavení do části:

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

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
