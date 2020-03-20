---
title: <remove> – element pro <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154527"
---
# <a name="remove-element-for-configsections"></a>\<odebrat prvek \<> pro> konfiguračních oddílů

Odebere předdefinovaný oddíl nebo skupinu oddílů.

[**\<>konfigurace**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<odebrat>**

## <a name="syntax"></a>Syntaxe

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Atribut

|           | Popis |
| --------- | ----------- |
| **Jméno**  | Požadovaný atribut.<br><br>Určuje název oddílu nebo skupiny oddílů, které chcete odebrat. |

## <a name="parent-element"></a>Nadřazený prvek

|     | Popis |
| --- | ----------- |
| [** \<>konfigSections** Prvek](configsections-element-for-configuration.md) | Obsahuje konfigurační oddíl a deklarace oboru názvů. |

## <a name="child-elements"></a>Podřízené prvky

Žádný

## <a name="remarks"></a>Poznámky

Prvek ** \<odebrat>** můžete použít k odebrání oddílů a skupin oddílů z aplikace, které byly definovány na vyšší úrovni v hierarchii konfiguračních souborů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít prvek ** \<remove>** v konfiguračním souboru aplikace k odebrání oddílu dříve definovaného v konfiguračním souboru počítače.

Následující kód konfiguračního souboru stroje deklaruje ** \<ukázku oddíluOddíl>**:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

Následující kód konfiguračního souboru aplikace odebere ** \<ukázkový oddíl section>.** Po odebrání aplikace nemůže načíst nastavení v ** \<sampleSection>**.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Konfigurační soubor

Tento prvek lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače *(Machine.config*) a souborech *Web.config,* které nejsou na úrovni adresáře aplikace.

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru pro rozhraní .NET Framework](index.md)
