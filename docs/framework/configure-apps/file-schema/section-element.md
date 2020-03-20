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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153724"
---
# <a name="section-element"></a>\<prvek> oddílu

Obsahuje deklaraci oddílu konfigurace.

[**\<>konfigurace**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>oddílu**

[**\<>konfigurace**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<oddílSkupina>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>oddílu**

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
| **Typ**  | Určuje název třídy obslužné rutiny konfiguračního oddílu, která čte oddíl z konfiguračního souboru. Hodnota typu má syntaxi "plně kvalifikovaný-sekce-handler-class-name, simple-assembly-name". Jednoduchý název sestavení je kořenový název souboru bez přípony *souboru DLL.* |

## <a name="optional-attributes"></a>Volitelné atributy

Následující atributy platí pouze pro ASP.NET aplikace. Konfigurační systém ignoruje tyto atributy pro jiné typy aplikací.

|                     | Popis |
| ------------------- | ----------- |
| **Allowdefinition** | Určuje, ve kterém konfiguračním souboru lze oddíl použít. Použijte jednu z následujících hodnot:<br><br>**Všude**<br>Umožňuje použití oddílu v libovolném konfiguračním souboru. Toto nastavení je výchozí.<br>**Pouze stroj**<br>Umožňuje použití oddílu pouze v konfiguračním souboru počítače *(Machine.config).*<br>**Machinetoapplication**<br>Umožňuje použití oddílu v konfiguračním souboru počítače nebo v konfiguračním souboru aplikace. |
| **allowLocation**   | Určuje, zda lze oddíl použít v rámci ** \<>** prvku umístění. Použijte jednu z následujících hodnot:<br><br>**true**<br>Umožňuje oddíl, který má být použit v rámci ** \<umístění>** prvku. Toto nastavení je výchozí.<br>**false (nepravda)**<br>Neumožňuje oddíl, který má být použit v rámci ** \<umístění>** prvek. |

## <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [** \<>konfigSections** Prvek](configsections-element-for-configuration.md) | Obsahuje konfigurační oddíl a deklarace oboru názvů. |
| [** \<sectionSkupina>** Prvek](sectiongroup-element-for-configsections.md) | Definuje obor názvů pro oddíly konfigurace. |

> [!NOTE]
> ** \<Oddíl>** element je podřízený prvek ** \<buď configSections>** nebo ** \<sectionGroup>,** ale ne obojí.

## <a name="child-elements"></a>Podřízené prvky

Žádný

## <a name="remarks"></a>Poznámky

Deklarování konfiguračního oddílu v podstatě definuje nový prvek pro konfigurační soubor. Nový prvek obsahuje nastavení, které čtení obslužné rutiny oddílu konfigurace (to znamená, že třída, která implementuje <xref:System.Configuration.IConfigurationSectionHandler> rozhraní). Atributy a podřízené prvky oddílu, který definujete, závisí na obslužné rutině oddílu, kterou používáte ke čtení nastavení.

Deklarování obslužné rutiny oddílu konfigurace v souboru *Machine.config* umožňuje použít oddíl konfigurace v libovolném konfiguračním souboru aplikace v tomto počítači, pokud atribut **allowDefinition** neurčuje jinak.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tento oddíl:

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

Tento prvek lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače *(Machine.config*) a souborech *Web.config,* které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](index.md)
