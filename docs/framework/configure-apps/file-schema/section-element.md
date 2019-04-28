---
title: <section>  – element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 58f823ce0c128f30e361b4a631d41286533b5f0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701499"
---
# <a name="section-element"></a>\<část > – element

Obsahuje deklarace oddíl konfigurace.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<část >**

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<část >**

## <a name="syntax"></a>Syntaxe

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Vyžadované atributy

|           | Popis |
| --------- | ----------- |
| **Jméno**  | Určuje název konfiguračního oddílu. |
| **type**  | Určuje název třídy konfigurace části obslužná rutina, která čte části z konfiguračního souboru. Hodnota typu má syntaxi "fully-qualified-section-handler-class-name jednoduchý název sestavení". Název sestavení jednoduché je kořenový název souboru bez *.dll* příponu souboru. |

## <a name="optional-attributes"></a>Volitelné atributy

Následující atributy platí pouze pro aplikace ASP.NET. Konfigurační systém ignoruje tyto atributy pro ostatní typy aplikací.

|                     | Popis |
| ------------------- | ----------- |
| **allowDefinition** | Určuje, které konfigurační soubor může být používáno v části. Použijte jednu z následujících hodnot:<br><br>**Všude**<br>Umožňuje oddílu, který má použít v jakékoli konfigurační soubor. Toto nastavení je výchozí.<br>**MachineOnly**<br>Umožňuje oddílu, který má použít pouze v konfiguračním souboru počítače (*Machine.config*).<br>**MachineToApplication**<br>Umožňuje oddílu, který má být použit v konfiguračním souboru počítače nebo konfiguračního souboru aplikace. |
| **allowLocation**   | Určuje, jestli v části lze použít v rámci  **\<umístění >** elementu. Použijte jednu z následujících hodnot:<br><br>**true**<br>Umožňuje použít v rámci sekce  **\<umístění >** elementu. Toto nastavení je výchozí.<br>**false**<br>Neumožňuje oddílu, který má použít v rámci  **\<umístění >** elementu. |

## <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [**\<configSections>** Element](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Obsahuje konfigurační oddíl a deklarace oboru názvů. |
| [**\<sectionGroup>** Element](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Definuje obor názvů pro oddíly konfigurace. |

> [!NOTE]
> A  **\<části >** element je podřízeným prvkem buď  **\<configSections >** nebo  **\<sectionGroup >** , ale ne obojí.

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

Deklarování konfiguračního oddílu v podstatě definuje nový prvek pro konfigurační soubor. Nový element obsahuje nastavení, konfigurace části obslužné rutiny (tedy třídy, která implementuje <xref:System.Configuration.IConfigurationSectionHandler> rozhraní) čte. Atributy a podřízené prvky, které definujete oddílu závisí na obslužné rutiny oddílu, který použijete ke čtení nastavení.

Deklarace obslužné rutiny konfiguračního oddílu v *Machine.config* soubor umožňuje používat konfiguračního oddílu v konfiguračním souboru libovolné aplikace na tomto počítači, není-li **allowDefinition**atribut neurčí jinak.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat konfiguračního oddílu a určit nastavení pro daný oddíl:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
