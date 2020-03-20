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
# <a name="section-element"></a><span data-ttu-id="989b0-102">\<prvek> oddílu</span><span class="sxs-lookup"><span data-stu-id="989b0-102">\<section> element</span></span>

<span data-ttu-id="989b0-103">Obsahuje deklaraci oddílu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="989b0-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="989b0-104">[**\<>konfigurace**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="989b0-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="989b0-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="989b0-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="989b0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>oddílu**</span><span class="sxs-lookup"><span data-stu-id="989b0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="989b0-107">[**\<>konfigurace**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="989b0-107">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="989b0-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="989b0-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="989b0-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<oddílSkupina>**](sectiongroup-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="989b0-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>\
<span data-ttu-id="989b0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>oddílu**</span><span class="sxs-lookup"><span data-stu-id="989b0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="989b0-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="989b0-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="989b0-112">Povinné atributy</span><span class="sxs-lookup"><span data-stu-id="989b0-112">Required attributes</span></span>

|           | <span data-ttu-id="989b0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="989b0-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="989b0-114">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="989b0-114">**name**</span></span>  | <span data-ttu-id="989b0-115">Určuje název konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="989b0-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="989b0-116">**Typ**</span><span class="sxs-lookup"><span data-stu-id="989b0-116">**type**</span></span>  | <span data-ttu-id="989b0-117">Určuje název třídy obslužné rutiny konfiguračního oddílu, která čte oddíl z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="989b0-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="989b0-118">Hodnota typu má syntaxi "plně kvalifikovaný-sekce-handler-class-name, simple-assembly-name".</span><span class="sxs-lookup"><span data-stu-id="989b0-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="989b0-119">Jednoduchý název sestavení je kořenový název souboru bez přípony *souboru DLL.*</span><span class="sxs-lookup"><span data-stu-id="989b0-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="989b0-120">Volitelné atributy</span><span class="sxs-lookup"><span data-stu-id="989b0-120">Optional attributes</span></span>

<span data-ttu-id="989b0-121">Následující atributy platí pouze pro ASP.NET aplikace.</span><span class="sxs-lookup"><span data-stu-id="989b0-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="989b0-122">Konfigurační systém ignoruje tyto atributy pro jiné typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="989b0-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="989b0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="989b0-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="989b0-124">**Allowdefinition**</span><span class="sxs-lookup"><span data-stu-id="989b0-124">**allowDefinition**</span></span> | <span data-ttu-id="989b0-125">Určuje, ve kterém konfiguračním souboru lze oddíl použít.</span><span class="sxs-lookup"><span data-stu-id="989b0-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="989b0-126">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="989b0-126">Use one of the following values:</span></span><br><br><span data-ttu-id="989b0-127">**Všude**</span><span class="sxs-lookup"><span data-stu-id="989b0-127">**Everywhere**</span></span><br><span data-ttu-id="989b0-128">Umožňuje použití oddílu v libovolném konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="989b0-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="989b0-129">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="989b0-129">This is the default.</span></span><br><span data-ttu-id="989b0-130">**Pouze stroj**</span><span class="sxs-lookup"><span data-stu-id="989b0-130">**MachineOnly**</span></span><br><span data-ttu-id="989b0-131">Umožňuje použití oddílu pouze v konfiguračním souboru počítače *(Machine.config).*</span><span class="sxs-lookup"><span data-stu-id="989b0-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="989b0-132">**Machinetoapplication**</span><span class="sxs-lookup"><span data-stu-id="989b0-132">**MachineToApplication**</span></span><br><span data-ttu-id="989b0-133">Umožňuje použití oddílu v konfiguračním souboru počítače nebo v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="989b0-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="989b0-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="989b0-134">**allowLocation**</span></span>   | <span data-ttu-id="989b0-135">Určuje, zda lze oddíl použít v rámci \*\* \<>\*\* prvku umístění.</span><span class="sxs-lookup"><span data-stu-id="989b0-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="989b0-136">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="989b0-136">Use one of the following values:</span></span><br><br><span data-ttu-id="989b0-137">**true**</span><span class="sxs-lookup"><span data-stu-id="989b0-137">**true**</span></span><br><span data-ttu-id="989b0-138">Umožňuje oddíl, který má být použit v rámci \*\* \<umístění>\*\* prvku.</span><span class="sxs-lookup"><span data-stu-id="989b0-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="989b0-139">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="989b0-139">This is the default.</span></span><br><span data-ttu-id="989b0-140">**false (nepravda)**</span><span class="sxs-lookup"><span data-stu-id="989b0-140">**false**</span></span><br><span data-ttu-id="989b0-141">Neumožňuje oddíl, který má být použit v rámci \*\* \<umístění>\*\* prvek.</span><span class="sxs-lookup"><span data-stu-id="989b0-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="989b0-142">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="989b0-142">Parent elements</span></span>

|     | <span data-ttu-id="989b0-143">Popis</span><span class="sxs-lookup"><span data-stu-id="989b0-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="989b0-144">\*\* \<>konfigSections\*\* Prvek</span><span class="sxs-lookup"><span data-stu-id="989b0-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="989b0-145">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="989b0-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="989b0-146">\*\* \<sectionSkupina>\*\* Prvek</span><span class="sxs-lookup"><span data-stu-id="989b0-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="989b0-147">Definuje obor názvů pro oddíly konfigurace.</span><span class="sxs-lookup"><span data-stu-id="989b0-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="989b0-148">\*\* \<Oddíl>\*\* element je podřízený prvek \*\* \<buď configSections>\*\* nebo \*\* \<sectionGroup>,\*\* ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="989b0-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="989b0-149">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="989b0-149">Child elements</span></span>

<span data-ttu-id="989b0-150">Žádný</span><span class="sxs-lookup"><span data-stu-id="989b0-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="989b0-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="989b0-151">Remarks</span></span>

<span data-ttu-id="989b0-152">Deklarování konfiguračního oddílu v podstatě definuje nový prvek pro konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="989b0-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="989b0-153">Nový prvek obsahuje nastavení, které čtení obslužné rutiny oddílu konfigurace (to znamená, že třída, která implementuje <xref:System.Configuration.IConfigurationSectionHandler> rozhraní).</span><span class="sxs-lookup"><span data-stu-id="989b0-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="989b0-154">Atributy a podřízené prvky oddílu, který definujete, závisí na obslužné rutině oddílu, kterou používáte ke čtení nastavení.</span><span class="sxs-lookup"><span data-stu-id="989b0-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="989b0-155">Deklarování obslužné rutiny oddílu konfigurace v souboru *Machine.config* umožňuje použít oddíl konfigurace v libovolném konfiguračním souboru aplikace v tomto počítači, pokud atribut **allowDefinition** neurčuje jinak.</span><span class="sxs-lookup"><span data-stu-id="989b0-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="989b0-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="989b0-156">Example</span></span>

<span data-ttu-id="989b0-157">Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tento oddíl:</span><span class="sxs-lookup"><span data-stu-id="989b0-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="989b0-158">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="989b0-158">Configuration file</span></span>

<span data-ttu-id="989b0-159">Tento prvek lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače *(Machine.config*) a souborech *Web.config,* které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="989b0-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="989b0-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="989b0-160">See also</span></span>

- [<span data-ttu-id="989b0-161">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="989b0-161">Configuration file schema for the .NET Framework</span></span>](index.md)
