---
title: <section> – element
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
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259212"
---
# <a name="section-element"></a><span data-ttu-id="5ebed-102">\<část > – element</span><span class="sxs-lookup"><span data-stu-id="5ebed-102">\<section> element</span></span>

<span data-ttu-id="5ebed-103">Obsahuje deklarace oddíl konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5ebed-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="5ebed-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5ebed-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="5ebed-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5ebed-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="5ebed-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<část >**</span><span class="sxs-lookup"><span data-stu-id="5ebed-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="5ebed-107">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5ebed-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="5ebed-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5ebed-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="5ebed-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="5ebed-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="5ebed-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<část >**</span><span class="sxs-lookup"><span data-stu-id="5ebed-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5ebed-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ebed-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="5ebed-112">Vyžadované atributy</span><span class="sxs-lookup"><span data-stu-id="5ebed-112">Required attributes</span></span>

|           | <span data-ttu-id="5ebed-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5ebed-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="5ebed-114">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="5ebed-114">**name**</span></span>  | <span data-ttu-id="5ebed-115">Určuje název konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="5ebed-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="5ebed-116">**type**</span><span class="sxs-lookup"><span data-stu-id="5ebed-116">**type**</span></span>  | <span data-ttu-id="5ebed-117">Určuje název třídy konfigurace části obslužná rutina, která čte části z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5ebed-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="5ebed-118">Hodnota typu má syntaxi "fully-qualified-section-handler-class-name jednoduchý název sestavení".</span><span class="sxs-lookup"><span data-stu-id="5ebed-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="5ebed-119">Název sestavení jednoduché je kořenový název souboru bez *.dll* příponu souboru.</span><span class="sxs-lookup"><span data-stu-id="5ebed-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="5ebed-120">Volitelné atributy</span><span class="sxs-lookup"><span data-stu-id="5ebed-120">Optional attributes</span></span>

<span data-ttu-id="5ebed-121">Následující atributy platí pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5ebed-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="5ebed-122">Konfigurační systém ignoruje tyto atributy pro ostatní typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="5ebed-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="5ebed-123">Popis</span><span class="sxs-lookup"><span data-stu-id="5ebed-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="5ebed-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="5ebed-124">**allowDefinition**</span></span> | <span data-ttu-id="5ebed-125">Určuje, které konfigurační soubor může být používáno v části.</span><span class="sxs-lookup"><span data-stu-id="5ebed-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="5ebed-126">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="5ebed-126">Use one of the following values:</span></span><br><br><span data-ttu-id="5ebed-127">**Všude**</span><span class="sxs-lookup"><span data-stu-id="5ebed-127">**Everywhere**</span></span><br><span data-ttu-id="5ebed-128">Umožňuje oddílu, který má použít v jakékoli konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="5ebed-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="5ebed-129">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="5ebed-129">This is the default.</span></span><br><span data-ttu-id="5ebed-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="5ebed-130">**MachineOnly**</span></span><br><span data-ttu-id="5ebed-131">Umožňuje oddílu, který má použít pouze v konfiguračním souboru počítače (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="5ebed-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="5ebed-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="5ebed-132">**MachineToApplication**</span></span><br><span data-ttu-id="5ebed-133">Umožňuje oddílu, který má být použit v konfiguračním souboru počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ebed-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="5ebed-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="5ebed-134">**allowLocation**</span></span>   | <span data-ttu-id="5ebed-135">Určuje, jestli v části lze použít v rámci  **\<umístění >** elementu.</span><span class="sxs-lookup"><span data-stu-id="5ebed-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="5ebed-136">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="5ebed-136">Use one of the following values:</span></span><br><br><span data-ttu-id="5ebed-137">**true**</span><span class="sxs-lookup"><span data-stu-id="5ebed-137">**true**</span></span><br><span data-ttu-id="5ebed-138">Umožňuje použít v rámci sekce  **\<umístění >** elementu.</span><span class="sxs-lookup"><span data-stu-id="5ebed-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="5ebed-139">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="5ebed-139">This is the default.</span></span><br><span data-ttu-id="5ebed-140">**false**</span><span class="sxs-lookup"><span data-stu-id="5ebed-140">**false**</span></span><br><span data-ttu-id="5ebed-141">Neumožňuje oddílu, který má použít v rámci  **\<umístění >** elementu.</span><span class="sxs-lookup"><span data-stu-id="5ebed-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="5ebed-142">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="5ebed-142">Parent elements</span></span>

|     | <span data-ttu-id="5ebed-143">Popis</span><span class="sxs-lookup"><span data-stu-id="5ebed-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5ebed-144">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="5ebed-144">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="5ebed-145">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5ebed-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="5ebed-146">**\<sectionGroup>** Element</span><span class="sxs-lookup"><span data-stu-id="5ebed-146">**\<sectionGroup>** Element</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="5ebed-147">Definuje obor názvů pro oddíly konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5ebed-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="5ebed-148">A  **\<části >** element je podřízeným prvkem buď  **\<configSections >** nebo  **\<sectionGroup >** , ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="5ebed-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="5ebed-149">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="5ebed-149">Child elements</span></span>

<span data-ttu-id="5ebed-150">Žádná</span><span class="sxs-lookup"><span data-stu-id="5ebed-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5ebed-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ebed-151">Remarks</span></span>

<span data-ttu-id="5ebed-152">Deklarování konfiguračního oddílu v podstatě definuje nový prvek pro konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="5ebed-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="5ebed-153">Nový element obsahuje nastavení, konfigurace části obslužné rutiny (tedy třídy, která implementuje <xref:System.Configuration.IConfigurationSectionHandler> rozhraní) čte.</span><span class="sxs-lookup"><span data-stu-id="5ebed-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="5ebed-154">Atributy a podřízené prvky, které definujete oddílu závisí na obslužné rutiny oddílu, který použijete ke čtení nastavení.</span><span class="sxs-lookup"><span data-stu-id="5ebed-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="5ebed-155">Deklarace obslužné rutiny konfiguračního oddílu v *Machine.config* soubor umožňuje používat konfiguračního oddílu v konfiguračním souboru libovolné aplikace na tomto počítači, není-li **allowDefinition**atribut neurčí jinak.</span><span class="sxs-lookup"><span data-stu-id="5ebed-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="5ebed-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ebed-156">Example</span></span>

<span data-ttu-id="5ebed-157">Následující příklad ukazuje, jak definovat konfiguračního oddílu a určit nastavení pro daný oddíl:</span><span class="sxs-lookup"><span data-stu-id="5ebed-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="5ebed-158">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="5ebed-158">Configuration file</span></span>

<span data-ttu-id="5ebed-159">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ebed-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ebed-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ebed-160">See also</span></span>

- [<span data-ttu-id="5ebed-161">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5ebed-161">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
