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
ms.openlocfilehash: 8785523d664294e3ca3792fb0f84d739d1f1a376
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215719"
---
# <a name="section-element"></a><span data-ttu-id="6290b-102">oddíl > elementu \<</span><span class="sxs-lookup"><span data-stu-id="6290b-102">\<section> element</span></span>

<span data-ttu-id="6290b-103">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="6290b-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="6290b-104">[**konfigurační >\<** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6290b-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="6290b-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="6290b-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="6290b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<části >**</span><span class="sxs-lookup"><span data-stu-id="6290b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="6290b-107">[**konfigurační >\<** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6290b-107">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="6290b-108">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="6290b-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="6290b-109">&nbsp;&nbsp;&nbsp;&nbsp;\<[**oddíly**](sectiongroup-element-for-configsections.md) ></span><span class="sxs-lookup"><span data-stu-id="6290b-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>\
<span data-ttu-id="6290b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<části** ></span><span class="sxs-lookup"><span data-stu-id="6290b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6290b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6290b-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="6290b-112">Požadované atributy</span><span class="sxs-lookup"><span data-stu-id="6290b-112">Required attributes</span></span>

|           | <span data-ttu-id="6290b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6290b-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="6290b-114">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="6290b-114">**name**</span></span>  | <span data-ttu-id="6290b-115">Určuje název konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="6290b-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="6290b-116">**type**</span><span class="sxs-lookup"><span data-stu-id="6290b-116">**type**</span></span>  | <span data-ttu-id="6290b-117">Určuje název třídy obslužné rutiny konfiguračního oddílu, který čte oddíl z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="6290b-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="6290b-118">Hodnota typu obsahuje syntaxi "plně kvalifikované-oddíl-obslužné rutiny-název třídy", Simple-Assembly-Name ".</span><span class="sxs-lookup"><span data-stu-id="6290b-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="6290b-119">Jednoduchý název sestavení je kořenový název souboru bez přípony souboru *. dll* .</span><span class="sxs-lookup"><span data-stu-id="6290b-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="6290b-120">Volitelné atributy</span><span class="sxs-lookup"><span data-stu-id="6290b-120">Optional attributes</span></span>

<span data-ttu-id="6290b-121">Následující atributy platí pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6290b-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="6290b-122">Konfigurační systém ignoruje tyto atributy pro jiné typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="6290b-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="6290b-123">Popis</span><span class="sxs-lookup"><span data-stu-id="6290b-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="6290b-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="6290b-124">**allowDefinition**</span></span> | <span data-ttu-id="6290b-125">Určuje, v jakém konfiguračním souboru se dá oddíl použít.</span><span class="sxs-lookup"><span data-stu-id="6290b-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="6290b-126">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="6290b-126">Use one of the following values:</span></span><br><br><span data-ttu-id="6290b-127">**Všude**</span><span class="sxs-lookup"><span data-stu-id="6290b-127">**Everywhere**</span></span><br><span data-ttu-id="6290b-128">Umožňuje použití oddílu v libovolném konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="6290b-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="6290b-129">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="6290b-129">This is the default.</span></span><br><span data-ttu-id="6290b-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="6290b-130">**MachineOnly**</span></span><br><span data-ttu-id="6290b-131">Umožňuje použít oddíl pouze v konfiguračním souboru počítače (*Machine. config*).</span><span class="sxs-lookup"><span data-stu-id="6290b-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="6290b-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="6290b-132">**MachineToApplication**</span></span><br><span data-ttu-id="6290b-133">Umožňuje použít oddíl v konfiguračním souboru počítače nebo v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6290b-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="6290b-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="6290b-134">**allowLocation**</span></span>   | <span data-ttu-id="6290b-135">Určuje, zda lze oddíl použít v rámci **\<umístění >** elementu.</span><span class="sxs-lookup"><span data-stu-id="6290b-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="6290b-136">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="6290b-136">Use one of the following values:</span></span><br><br><span data-ttu-id="6290b-137">**true**</span><span class="sxs-lookup"><span data-stu-id="6290b-137">**true**</span></span><br><span data-ttu-id="6290b-138">Umožňuje použití oddílu v rámci **\<umístění >** elementu.</span><span class="sxs-lookup"><span data-stu-id="6290b-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="6290b-139">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="6290b-139">This is the default.</span></span><br><span data-ttu-id="6290b-140">**false**</span><span class="sxs-lookup"><span data-stu-id="6290b-140">**false**</span></span><br><span data-ttu-id="6290b-141">Nepovoluje použití oddílu v **\<umístění >** elementu.</span><span class="sxs-lookup"><span data-stu-id="6290b-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="6290b-142">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6290b-142">Parent elements</span></span>

|     | <span data-ttu-id="6290b-143">Popis</span><span class="sxs-lookup"><span data-stu-id="6290b-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6290b-144"> **\<configSections >** Objekt</span><span class="sxs-lookup"><span data-stu-id="6290b-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="6290b-145">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6290b-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="6290b-146"> **>\<sectionGroup** Objekt</span><span class="sxs-lookup"><span data-stu-id="6290b-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="6290b-147">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="6290b-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="6290b-148">**Oddíl\<>** prvek je podřízeným prvkem buď **\<configSections >** nebo **\<sectionGroup** , ale ne obojího.</span><span class="sxs-lookup"><span data-stu-id="6290b-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="6290b-149">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6290b-149">Child elements</span></span>

<span data-ttu-id="6290b-150">Žádná</span><span class="sxs-lookup"><span data-stu-id="6290b-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="6290b-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6290b-151">Remarks</span></span>

<span data-ttu-id="6290b-152">Deklarace konfiguračního oddílu v podstatě definuje nový prvek konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="6290b-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="6290b-153">Nový prvek obsahuje nastavení, která obslužná rutina konfiguračního oddílu (to znamená třída, která implementuje rozhraní <xref:System.Configuration.IConfigurationSectionHandler>) čte.</span><span class="sxs-lookup"><span data-stu-id="6290b-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="6290b-154">Atributy a podřízené prvky oddílu, který definujete, závisí na obslužné rutině oddílu, kterou použijete ke čtení nastavení.</span><span class="sxs-lookup"><span data-stu-id="6290b-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="6290b-155">Deklarace obslužné rutiny konfiguračního oddílu v souboru *Machine. config* umožňuje použít konfigurační oddíl v libovolném konfiguračním souboru aplikace v tomto počítači, pokud atribut **AllowDefinition** neurčuje jinak.</span><span class="sxs-lookup"><span data-stu-id="6290b-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="6290b-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="6290b-156">Example</span></span>

<span data-ttu-id="6290b-157">Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tuto část:</span><span class="sxs-lookup"><span data-stu-id="6290b-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="6290b-158">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="6290b-158">Configuration file</span></span>

<span data-ttu-id="6290b-159">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="6290b-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6290b-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="6290b-160">See also</span></span>

- [<span data-ttu-id="6290b-161">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6290b-161">Configuration file schema for the .NET Framework</span></span>](index.md)
