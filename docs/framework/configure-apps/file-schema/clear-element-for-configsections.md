---
title: <clear> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c06fca8b83638fb47bedb21863cb9b200cd211f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927733"
---
# <a name="clear-element-for-configsections"></a>\<Clear – element > \<pro configSections >

Vymaže všechny dříve definované oddíly a skupiny oddílů.

[ **\<> Konfigurace**](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<Vymazat >**

## <a name="syntax"></a>Syntaxe

```xml
<clear/>
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **name**  | Požadovaný atribut.<br><br>Určuje název oddílu nebo skupiny oddílů, které se mají odebrat. |

## <a name="parent-element"></a>Nadřazený element

|     | Popis |
| --- | ----------- |
| [configSections – > element  **\<** ](configsections-element-for-configuration.md) | Obsahuje konfigurační oddíl a deklarace oboru názvů. |

## <a name="child-elements"></a>Podřízené prvky

Žádné

## <a name="remarks"></a>Poznámky

**\<Vymazat >** element odebere všechny oddíly a skupiny oddílů z vaší aplikace, které byly dříve definovány v aktuálním konfiguračním souboru nebo na vyšší úrovni v hierarchii konfigurační soubor.

## <a name="example"></a>Příklad

Tento příklad definuje konfigurační soubor počítače a konfigurační soubor aplikace a ukazuje, jak pomocí  **\<elementu Clear >** v konfiguračním souboru aplikace vymazat oddíly dříve definované v konfiguraci počítače. souborů.

Následující kód konfiguračního souboru počítače deklaruje dva oddíly,  **\<sampleSection >** a  **\<> anotherSampleSection**, které jsou čteny před konfiguračním souborem aplikace:

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

Následující kód konfiguračního souboru aplikace vymaže všechny dříve deklarované oddíly. Aplikace nemůže použít nebo načíst nastavení v některé z oddílů, které byly deklarovány v konfiguračním souboru počítače. Může však použít nastavení z  **\<anotherSection >**  **\<** , protože se nachází po elementu Clear >.

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

## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru pro .NET Framework](index.md)
