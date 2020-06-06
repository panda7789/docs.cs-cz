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
# <a name="section-element"></a><span data-ttu-id="66353-102">\<section> – element</span><span class="sxs-lookup"><span data-stu-id="66353-102">\<section> element</span></span>

<span data-ttu-id="66353-103">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="66353-103">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="66353-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66353-104">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="66353-105">Požadované atributy</span><span class="sxs-lookup"><span data-stu-id="66353-105">Required attributes</span></span>

|           | <span data-ttu-id="66353-106">Description</span><span class="sxs-lookup"><span data-stu-id="66353-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="66353-107">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="66353-107">**name**</span></span>  | <span data-ttu-id="66353-108">Určuje název konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="66353-108">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="66353-109">**textový**</span><span class="sxs-lookup"><span data-stu-id="66353-109">**type**</span></span>  | <span data-ttu-id="66353-110">Určuje název třídy obslužné rutiny konfiguračního oddílu, který čte oddíl z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="66353-110">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="66353-111">Hodnota typu obsahuje syntaxi "plně kvalifikované-oddíl-obslužné rutiny-název třídy", Simple-Assembly-Name ".</span><span class="sxs-lookup"><span data-stu-id="66353-111">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="66353-112">Jednoduchý název sestavení je kořenový název souboru bez přípony souboru *. dll* .</span><span class="sxs-lookup"><span data-stu-id="66353-112">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="66353-113">Volitelné atributy</span><span class="sxs-lookup"><span data-stu-id="66353-113">Optional attributes</span></span>

<span data-ttu-id="66353-114">Následující atributy platí pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="66353-114">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="66353-115">Konfigurační systém ignoruje tyto atributy pro jiné typy aplikací.</span><span class="sxs-lookup"><span data-stu-id="66353-115">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="66353-116">Description</span><span class="sxs-lookup"><span data-stu-id="66353-116">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="66353-117">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="66353-117">**allowDefinition**</span></span> | <span data-ttu-id="66353-118">Určuje, v jakém konfiguračním souboru se dá oddíl použít.</span><span class="sxs-lookup"><span data-stu-id="66353-118">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="66353-119">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="66353-119">Use one of the following values:</span></span><br><br><span data-ttu-id="66353-120">**Všude**</span><span class="sxs-lookup"><span data-stu-id="66353-120">**Everywhere**</span></span><br><span data-ttu-id="66353-121">Umožňuje použití oddílu v libovolném konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="66353-121">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="66353-122">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="66353-122">This is the default.</span></span><br><span data-ttu-id="66353-123">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="66353-123">**MachineOnly**</span></span><br><span data-ttu-id="66353-124">Umožňuje použít oddíl pouze v konfiguračním souboru počítače (*Machine. config*).</span><span class="sxs-lookup"><span data-stu-id="66353-124">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="66353-125">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="66353-125">**MachineToApplication**</span></span><br><span data-ttu-id="66353-126">Umožňuje použít oddíl v konfiguračním souboru počítače nebo v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="66353-126">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="66353-127">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="66353-127">**allowLocation**</span></span>   | <span data-ttu-id="66353-128">Určuje, zda lze oddíl použít v rámci **\<location>** elementu.</span><span class="sxs-lookup"><span data-stu-id="66353-128">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="66353-129">Použijte jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="66353-129">Use one of the following values:</span></span><br><br><span data-ttu-id="66353-130">**podmínka**</span><span class="sxs-lookup"><span data-stu-id="66353-130">**true**</span></span><br><span data-ttu-id="66353-131">Umožňuje použití oddílu v rámci **\<location>** elementu.</span><span class="sxs-lookup"><span data-stu-id="66353-131">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="66353-132">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="66353-132">This is the default.</span></span><br><span data-ttu-id="66353-133">**chybné**</span><span class="sxs-lookup"><span data-stu-id="66353-133">**false**</span></span><br><span data-ttu-id="66353-134">Nepovoluje použití oddílu v rámci **\<location>** elementu.</span><span class="sxs-lookup"><span data-stu-id="66353-134">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="66353-135">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="66353-135">Parent elements</span></span>

|     | <span data-ttu-id="66353-136">Description</span><span class="sxs-lookup"><span data-stu-id="66353-136">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="66353-137">**\<configSections>** Objekt</span><span class="sxs-lookup"><span data-stu-id="66353-137">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="66353-138">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="66353-138">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="66353-139">**\<sectionGroup>** Objekt</span><span class="sxs-lookup"><span data-stu-id="66353-139">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="66353-140">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="66353-140">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="66353-141">**\<section>** Prvek je podřízeným prvkem buď nebo, **\<configSections>** **\<sectionGroup>** ale ne obojího.</span><span class="sxs-lookup"><span data-stu-id="66353-141">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="66353-142">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="66353-142">Child elements</span></span>

<span data-ttu-id="66353-143">Žádné</span><span class="sxs-lookup"><span data-stu-id="66353-143">None</span></span>

## <a name="remarks"></a><span data-ttu-id="66353-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66353-144">Remarks</span></span>

<span data-ttu-id="66353-145">Deklarace konfiguračního oddílu v podstatě definuje nový prvek konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="66353-145">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="66353-146">Nový prvek obsahuje nastavení, která obslužná rutina konfiguračního oddílu (to znamená třída, která implementuje <xref:System.Configuration.IConfigurationSectionHandler> rozhraní) čte.</span><span class="sxs-lookup"><span data-stu-id="66353-146">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="66353-147">Atributy a podřízené prvky oddílu, který definujete, závisí na obslužné rutině oddílu, kterou použijete ke čtení nastavení.</span><span class="sxs-lookup"><span data-stu-id="66353-147">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="66353-148">Deklarace obslužné rutiny konfiguračního oddílu v souboru *Machine. config* umožňuje použít konfigurační oddíl v libovolném konfiguračním souboru aplikace v tomto počítači, pokud atribut **AllowDefinition** neurčuje jinak.</span><span class="sxs-lookup"><span data-stu-id="66353-148">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="66353-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="66353-149">Example</span></span>

<span data-ttu-id="66353-150">Následující příklad ukazuje, jak definovat konfigurační oddíl a definovat nastavení pro tuto část:</span><span class="sxs-lookup"><span data-stu-id="66353-150">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="66353-151">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="66353-151">Configuration file</span></span>

<span data-ttu-id="66353-152">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="66353-152">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="66353-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="66353-153">See also</span></span>

- [<span data-ttu-id="66353-154">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="66353-154">Configuration file schema for the .NET Framework</span></span>](index.md)
