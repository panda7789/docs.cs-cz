---
title: '&lt;část&gt; – element'
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
ms.openlocfilehash: 17b44ca93efc26f4732f5fe2926f894257d8f984
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746433"
---
# <a name="section-element"></a>\<část > elementu

Obsahuje deklaraci konfigurační oddíl.

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<část >**

[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<část >**

## <a name="syntax"></a>Syntaxe

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Povinné atributy

|           | Popis |
| --------- | ----------- |
| **Jméno**  | Určuje název konfiguračního oddílu. |
| **Typ**  | Určuje název třídy obslužné rutiny konfigurace oddílu, který čte části z konfiguračního souboru. Hodnota typu má syntaxi "fully-qualified-section-handler-class-name, název sestavení jednoduchý". Název jednoduché sestavení je název souboru kořenové bez *.dll* příponu souboru. |

## <a name="optional-attributes"></a>Volitelných atributů

Následující atributy se dají použít jenom pro aplikace ASP.NET. Konfigurační systém ignoruje tyto atributy pro jiné typy aplikací.

|                     | Popis |
| ------------------- | ----------- |
| **allowDefinition** | Určuje, který soubor konfigurace mohou být používány v části. Použijte jednu z následujících hodnot:<br><br>**Everywhere**<br>Umožňuje oddílu, který má být používány všechny konfigurační soubor. Toto nastavení je výchozí.<br>**MachineOnly**<br>Umožňuje oddílu, který má být použita pouze v konfiguračním souboru počítače (*Machine.config*).<br>**MachineToApplication**<br>Umožňuje oddílu, který má být použit v konfiguračním souboru počítače nebo v konfiguračním souboru aplikace. |
| **allowLocation**   | Určuje, jestli je možné použít v části v rámci  **\<umístění >** element. Použijte jednu z následujících hodnot:<br><br>**true**<br>Umožňuje oddílu, který má být použit  **\<umístění >** element. Toto nastavení je výchozí.<br>**false**<br>Neumožňuje oddílu, který má být použit  **\<umístění >** element. |

## <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [**\<configSections >** – Element](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Obsahuje konfigurační oddíl a deklarace oboru názvů. |
| [**\<sectionGroup >** – Element](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Definuje obor názvů pro konfigurační oddíly. |

> [!NOTE]
> A  **\<části >** prvek je podřízený prvek buď  **\<configSections >** nebo  **\<sectionGroup >** ale ne obě.

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

V podstatě deklarace konfigurační oddíl definuje nového elementu konfiguračního souboru. Nový element obsahuje nastavení, konfiguraci části obslužné rutiny (tedy třídu, která implementuje <xref:System.Configuration.IConfigurationSectionHandler> rozhraní) čte. Atributy a podřízených elementů části, které definujete závisí na části obslužná rutina, kterou můžete použít ke čtení nastavení.

Deklarování obslužnou rutinu konfiguračního oddílu v *Machine.config* souboru umožňuje používat konfigurační oddíl v konfiguračním souboru všechny aplikace na tomto počítači, pokud **allowDefinition**atribut neurčí jinak.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat oddíl konfigurace a nastavení pro daný oddíl:

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

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.

## <a name="see-also"></a>Viz také

[Schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
