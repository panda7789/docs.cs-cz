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
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153724"
---
# <a name="section-element"></a>\<section> – element

Obsahuje deklaraci konfiguračního oddílu.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a>Syntaxe

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Požadované atributy

|           | Description |
| --------- | ----------- |
| **Jméno**  | Určuje název konfiguračního oddílu. |
| **textový**  | Určuje název třídy obslužné rutiny konfiguračního oddílu, který čte oddíl z konfiguračního souboru. Hodnota typu obsahuje syntaxi "plně kvalifikované-oddíl-obslužné rutiny-název třídy", Simple-Assembly-Name ". Jednoduchý název sestavení je kořenový název souboru bez přípony souboru *. dll* . |

## <a name="optional-attributes"></a>Volitelné atributy

Následující atributy platí pouze pro aplikace ASP.NET. Konfigurační systém ignoruje tyto atributy pro jiné typy aplikací.

|                     | Description |
| ------------------- | ----------- |
| **allowDefinition** | Určuje, v jakém konfiguračním souboru se dá oddíl použít. Použijte jednu z následujících hodnot:<br><br>**Všude**<br>Umožňuje použití oddílu v libovolném konfiguračním souboru. Toto nastavení je výchozí.<br>**MachineOnly**<br>Umožňuje použít oddíl pouze v konfiguračním souboru počítače (*Machine. config*).<br>**MachineToApplication**<br>Umožňuje použít oddíl v konfiguračním souboru počítače nebo v konfiguračním souboru aplikace. |
| **allowLocation**   | Určuje, zda lze oddíl použít v rámci **\<location>** elementu. Použijte jednu z následujících hodnot:<br><br>**podmínka**<br>Umožňuje použití oddílu v rámci **\<location>** elementu. Toto nastavení je výchozí.<br>**chybné**<br>Nepovoluje použití oddílu v rámci **\<location>** elementu. |

## <a name="parent-elements"></a>Nadřazené prvky

|     | Description |
| --- | ----------- |
| [**\<configSections>** Objekt](configsections-element-for-configuration.md) | Obsahuje konfigurační oddíl a deklarace oboru názvů. |
| [**\<sectionGroup>** Objekt](sectiongroup-element-for-configsections.md) | Definuje obor názvů pro konfigurační oddíly. |

> [!NOTE]
> **\<section>** Prvek je podřízeným prvkem buď nebo, **\<configSections>** **\<sectionGroup>** ale ne obojího.

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

Deklarace konfiguračního oddílu v podstatě definuje nový prvek konfiguračního souboru. Nový prvek obsahuje nastavení, která obslužná rutina konfiguračního oddílu (to znamená třída, která implementuje <xref:System.Configuration.IConfigurationSectionHandler> rozhraní) čte. Atributy a podřízené prvky oddílu, který definujete, závisí na obslužné rutině oddílu, kterou použijete ke čtení nastavení.

Deklarace obslužné rutiny konfiguračního oddílu v souboru *Machine. config* umožňuje použít konfigurační oddíl v libovolném konfiguračním souboru aplikace v tomto počítači, pokud atribut **AllowDefinition** neurčuje jinak.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tuto část:

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

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
