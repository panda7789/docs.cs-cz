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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155424"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="b4b02-102">\<vymazat> \<prvek pro> konfiguračních oddílů</span><span class="sxs-lookup"><span data-stu-id="b4b02-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="b4b02-103">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="b4b02-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="b4b02-104">&nbsp; &nbsp; &nbsp; &nbsp; \*\* \<\*\* konfigurace &nbsp; &nbsp; [**>\<konfiguračnísekce>**](configsections-element-for-configuration.md) jasné>[\*\* \<\*\*](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4b02-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b4b02-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4b02-105">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="b4b02-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="b4b02-106">Attribute</span></span>

|           | <span data-ttu-id="b4b02-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b4b02-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b4b02-108">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="b4b02-108">**name**</span></span>  | <span data-ttu-id="b4b02-109">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b4b02-109">Required attribute.</span></span><br><br><span data-ttu-id="b4b02-110">Určuje název oddílu nebo skupiny oddílů, které chcete odebrat.</span><span class="sxs-lookup"><span data-stu-id="b4b02-110">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="b4b02-111">Nadřazený prvek</span><span class="sxs-lookup"><span data-stu-id="b4b02-111">Parent element</span></span>

|     | <span data-ttu-id="b4b02-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b4b02-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b4b02-113">\*\* \<>konfigSections\*\* Prvek</span><span class="sxs-lookup"><span data-stu-id="b4b02-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="b4b02-114">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b4b02-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b4b02-115">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b4b02-115">Child elements</span></span>

<span data-ttu-id="b4b02-116">Žádný</span><span class="sxs-lookup"><span data-stu-id="b4b02-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="b4b02-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4b02-117">Remarks</span></span>

<span data-ttu-id="b4b02-118">Prvek \*\* \<clear>\*\* odebere všechny oddíly a skupiny oddílů z aplikace, které byly definovány dříve v aktuálním konfiguračním souboru nebo na vyšší úrovni v hierarchii konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b4b02-118">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="b4b02-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4b02-119">Example</span></span>

<span data-ttu-id="b4b02-120">Tento příklad definuje konfigurační soubor počítače a konfigurační soubor aplikace a ukazuje, jak pomocí \*\* \<prvku clear>\*\* v konfiguračním souboru aplikace vymazat oddíly dříve definované v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="b4b02-120">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="b4b02-121">Následující kód konfiguračního souboru počítače deklaruje dvě části, \*\* \<sampleSection>\*\* a \*\* \<anotherSampleSection>\*\*, které jsou přečteny před konfiguračním souborem aplikace:</span><span class="sxs-lookup"><span data-stu-id="b4b02-121">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="b4b02-122">Následující kód konfiguračního souboru aplikace vymaže všechny dříve deklarované oddíly.</span><span class="sxs-lookup"><span data-stu-id="b4b02-122">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="b4b02-123">Aplikace nemůže použít ani načíst nastavení v některé z oddílů, které byly deklarovány v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="b4b02-123">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="b4b02-124">Však můžete použít nastavení z \*\* \<jinéhooddílu>\*\* protože přichází po \*\* \<prvek clear>.\*\*</span><span class="sxs-lookup"><span data-stu-id="b4b02-124">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="b4b02-125">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="b4b02-125">Configuration file</span></span>

<span data-ttu-id="b4b02-126">Tento prvek lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače *(Machine.config*) a souborech *Web.config,* které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4b02-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4b02-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4b02-127">See also</span></span>

- [<span data-ttu-id="b4b02-128">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4b02-128">Configuration file schema for the .NET Framework</span></span>](index.md)
