---
title: element <clear> pro NameValueSectionHandler a DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fff5a5c2a523480f2eaebb127ec98ff6e9908acf
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088705"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<vymazat > elementu pro NameValueSectionHandler a DictionarySectionHandler

Vymaže všechna dříve definovaná nastavení v oddílu.

[ **\<configuration >** ](configuration-element.md) \
&nbsp;&nbsp;[ **\<sectiongroup >** ](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**

## <a name="syntax"></a>Syntaxe

```xml
<clear />
```

## <a name="attributes"></a>Atributy

Žádné

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ------------|
| [ **\<sectionGroup** Objekt](custom-element-2.md) | Definuje nastavení pro vlastní konfigurační oddíly, které používají třídy <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

Pomocí elementu **\<clear >** můžete odebrat všechna nastavení z aplikace, která byla definována na vyšší úrovni v hierarchii konfiguračního souboru.

## <a name="example"></a>Příklad

Tento příklad definuje konfigurační soubor počítače a konfigurační soubor aplikace a ukazuje, jak použít **\<clear >** elementu v konfiguračním souboru aplikace pro vymazání oddílů dříve definovaných v konfiguračním souboru počítače.

Následující kód konfiguračního souboru počítače deklaruje oddíl **\<mySection >** :

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

Následující kód konfiguračního souboru aplikace odebere všechna nastavení z **\<mySection >** . Aplikace nemůže načíst žádná nastavení, která byla deklarována v v části **\<mySection** konfiguračního souboru počítače.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
