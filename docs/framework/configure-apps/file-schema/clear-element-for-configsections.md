---
title: <clear> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155424"
---
# <a name="clear-element-for-configsections"></a>\<clear> – element pro \<configSections>

Vymaže všechny dříve definované oddíly a skupiny oddílů.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>Syntaxe

```xml
<clear/>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **Jméno**  | Požadovaný atribut.<br><br>Určuje název oddílu nebo skupiny oddílů, které se mají odebrat. |

## <a name="parent-element"></a>Nadřazený element

|     | Description |
| --- | ----------- |
| [**\<configSections>** Objekt](configsections-element-for-configuration.md) | Obsahuje konfigurační oddíl a deklarace oboru názvů. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

**\<clear>** Element odebere všechny oddíly a skupiny oddílů z vaší aplikace, které byly definovány dříve v aktuálním konfiguračním souboru nebo na vyšší úrovni v hierarchii konfiguračního souboru.

## <a name="example"></a>Příklad

Tento příklad definuje konfigurační soubor počítače a konfigurační soubor aplikace a ukazuje, jak použít **\<clear>** element v konfiguračním souboru aplikace pro vymazání oddílů dříve definovaných v konfiguračním souboru počítače.

Následující kód konfiguračního souboru počítače deklaruje dva oddíly **\<sampleSection>** a **\<anotherSampleSection>** , které jsou čteny před konfiguračním souborem aplikace:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

Následující kód konfiguračního souboru aplikace vymaže všechny dříve deklarované oddíly. Aplikace nemůže použít nebo načíst nastavení v některé z oddílů, které byly deklarovány v konfiguračním souboru počítače. Může však použít nastavení z, **\<anotherSection>** protože se nachází po **\<clear>** elementu.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
