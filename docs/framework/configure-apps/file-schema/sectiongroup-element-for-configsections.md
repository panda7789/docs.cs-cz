---
title: '&lt;sectionGroup&gt; element pro &lt;configSections&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 654a6e639a24120e1e0c993ebe36f14e75b46a12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="sectiongroup-element-for-configsections"></a>\<sectionGroup > elementu pro \<configSections >

Definuje obor názvů pro konfigurační oddíly.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**

## <a name="syntax"></a>Syntaxe

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **Jméno**  | Požadovaný atribut.<br><br>Určuje název oddílu skupiny, kterou definujete. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [**\<configSections >** – Element](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Obsahuje konfigurační oddíl a deklarace oboru názvů. |

## <a name="child-elements"></a>Podřízené prvky

|     | Popis |
| --- | ----------- |
| [**\<část >**](~/docs/framework/configure-apps/file-schema/section-element.md) | Obsahuje deklaraci konfigurační oddíl. |

## <a name="remarks"></a>Poznámky

Deklarování skupinu oddílů vytvoří značku kontejneru konfiguračních oddílů a zajišťuje, že neexistují žádné pojmenování je v konfliktu s konfiguračních oddílů, které jsou definované někdo jiný. Lze vnořit  **\<sectionGroup >** elementů v rámci navzájem.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat skupinu oddílů a deklarovat oddíly v rámci skupiny oddílů:

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
