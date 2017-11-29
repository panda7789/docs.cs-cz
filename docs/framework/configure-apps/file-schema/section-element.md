---
title: "&lt;část&gt; – element"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8ed8b0211c8366d799fe158d91dcb42f92ad0cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="section-element"></a><span data-ttu-id="36527-102">\<část > elementu</span><span class="sxs-lookup"><span data-stu-id="36527-102">\<section> element</span></span>

<span data-ttu-id="36527-103">Obsahuje deklaraci konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="36527-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="36527-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="36527-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="36527-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="36527-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="36527-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<část >**</span><span class="sxs-lookup"><span data-stu-id="36527-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="36527-107">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="36527-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="36527-108">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="36527-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="36527-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="36527-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="36527-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<část >**</span><span class="sxs-lookup"><span data-stu-id="36527-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="36527-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36527-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="36527-112">Povinné atributy</span><span class="sxs-lookup"><span data-stu-id="36527-112">Required attributes</span></span>

|           | <span data-ttu-id="36527-113">Popis</span><span class="sxs-lookup"><span data-stu-id="36527-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="36527-114">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="36527-114">**name**</span></span>  | <span data-ttu-id="36527-115">Určuje název konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="36527-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="36527-116">**Typ**</span><span class="sxs-lookup"><span data-stu-id="36527-116">**type**</span></span>  | <span data-ttu-id="36527-117">Určuje název třídy obslužné rutiny konfigurace oddílu, který čte části z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="36527-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="36527-118">Hodnota typu má syntaxi "fully-qualified-section-handler-class-name, název sestavení jednoduchý".</span><span class="sxs-lookup"><span data-stu-id="36527-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="36527-119">Název jednoduché sestavení je název souboru kořenové bez *.dll* příponu souboru.</span><span class="sxs-lookup"><span data-stu-id="36527-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="36527-120">Volitelných atributů</span><span class="sxs-lookup"><span data-stu-id="36527-120">Optional attributes</span></span>

<span data-ttu-id="36527-121">Následující atributy se dají použít jenom pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="36527-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="36527-122">Konfigurační systém ignoruje tyto atributy pro jiné typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="36527-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="36527-123">Popis</span><span class="sxs-lookup"><span data-stu-id="36527-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="36527-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="36527-124">**allowDefinition**</span></span> | <span data-ttu-id="36527-125">Určuje, který soubor konfigurace mohou být používány v části.</span><span class="sxs-lookup"><span data-stu-id="36527-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="36527-126">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="36527-126">Use one of the following values:</span></span><br><br><span data-ttu-id="36527-127">**Everywhere**</span><span class="sxs-lookup"><span data-stu-id="36527-127">**Everywhere**</span></span><br><span data-ttu-id="36527-128">Umožňuje oddílu, který má být používány všechny konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="36527-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="36527-129">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="36527-129">This is the default.</span></span><br><span data-ttu-id="36527-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="36527-130">**MachineOnly**</span></span><br><span data-ttu-id="36527-131">Umožňuje oddílu, který má být použita pouze v konfiguračním souboru počítače (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="36527-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="36527-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="36527-132">**MachineToApplication**</span></span><br><span data-ttu-id="36527-133">Umožňuje oddílu, který má být použit v konfiguračním souboru počítače nebo v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="36527-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="36527-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="36527-134">**allowLocation**</span></span>   | <span data-ttu-id="36527-135">Určuje, jestli je možné použít v části v rámci  **\<umístění >** element.</span><span class="sxs-lookup"><span data-stu-id="36527-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="36527-136">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="36527-136">Use one of the following values:</span></span><br><br><span data-ttu-id="36527-137">**Hodnota TRUE**</span><span class="sxs-lookup"><span data-stu-id="36527-137">**true**</span></span><br><span data-ttu-id="36527-138">Umožňuje oddílu, který má být použit  **\<umístění >** element.</span><span class="sxs-lookup"><span data-stu-id="36527-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="36527-139">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="36527-139">This is the default.</span></span><br><span data-ttu-id="36527-140">**false**</span><span class="sxs-lookup"><span data-stu-id="36527-140">**false**</span></span><br><span data-ttu-id="36527-141">Neumožňuje oddílu, který má být použit  **\<umístění >** element.</span><span class="sxs-lookup"><span data-stu-id="36527-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="36527-142">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="36527-142">Parent elements</span></span>

|     | <span data-ttu-id="36527-143">Popis</span><span class="sxs-lookup"><span data-stu-id="36527-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="36527-144">**\<configSections >** – Element</span><span class="sxs-lookup"><span data-stu-id="36527-144">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="36527-145">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="36527-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="36527-146">**\<sectionGroup >** – Element</span><span class="sxs-lookup"><span data-stu-id="36527-146">**\<sectionGroup>** Element</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="36527-147">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="36527-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="36527-148">A  **\<části >** prvek je podřízený prvek buď  **\<configSections >** nebo  **\<sectionGroup >** ale ne obě.</span><span class="sxs-lookup"><span data-stu-id="36527-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="36527-149">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="36527-149">Child elements</span></span>

<span data-ttu-id="36527-150">Žádné</span><span class="sxs-lookup"><span data-stu-id="36527-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="36527-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36527-151">Remarks</span></span>

<span data-ttu-id="36527-152">V podstatě deklarace konfigurační oddíl definuje nového elementu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="36527-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="36527-153">Nový element obsahuje nastavení, konfiguraci části obslužné rutiny (tedy třídu, která implementuje <xref:System.Configuration.IConfigurationSectionHandler> rozhraní) čte.</span><span class="sxs-lookup"><span data-stu-id="36527-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="36527-154">Atributy a podřízených elementů části, které definujete závisí na části obslužná rutina, kterou můžete použít ke čtení nastavení.</span><span class="sxs-lookup"><span data-stu-id="36527-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="36527-155">Deklarování obslužnou rutinu konfiguračního oddílu v *Machine.config* souboru umožňuje používat konfigurační oddíl v konfiguračním souboru všechny aplikace na tomto počítači, pokud **allowDefinition**atribut neurčí jinak.</span><span class="sxs-lookup"><span data-stu-id="36527-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="36527-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="36527-156">Example</span></span>

<span data-ttu-id="36527-157">Následující příklad ukazuje, jak definovat oddíl konfigurace a nastavení pro daný oddíl:</span><span class="sxs-lookup"><span data-stu-id="36527-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="36527-158">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="36527-158">Configuration file</span></span>

<span data-ttu-id="36527-159">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="36527-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="36527-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="36527-160">See also</span></span>

[<span data-ttu-id="36527-161">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="36527-161">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
