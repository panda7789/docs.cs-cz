---
title: '&lt;Vymazat&gt; element NameValueSectionHandler a DictionarySectionHandler'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: a1cbd682faa4c60e50bc3b73b58ef226dd599da2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Clear > elementu NameValueSectionHandler a DictionarySectionHandler

Vymaže všechny dříve definované nastavení v oddílu.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**

## <a name="syntax"></a>Syntaxe

```xml
<clear />
```

## <a name="attributes"></a>Atributy

Žádné

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ------------|
| [**\<sectionName >** – Element](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Definuje nastavení pro vlastní konfiguračních oddílů, které používají <xref:System.Configuration.NameValueSectionHandler> a <xref:System.Configuration.DictionarySectionHandler> třídy. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

Můžete použít  **\<clear >** elementu, který chcete odebrat všechna nastavení z vaší aplikace, které byly definované na vyšší úrovni v hierarchii souboru konfigurace.

## <a name="example"></a>Příklad

Tento příklad definuje konfigurační soubor a konfiguračním souboru aplikace a ukazuje, jak používat  **\<vymazat >** element v konfiguračním souboru aplikace, vymazat dříve definované v části konfigurační soubor počítače.

Následující počítače konfigurační soubor kód deklaruje části  **\<mySection >**:

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

Následující kód soubor konfigurace aplikace odebere všechna nastavení z  **\<mySection >**. Aplikaci nelze načíst nastavení, které byly deklarované v v  **\<mySection >** části konfiguračním souboru počítače.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
