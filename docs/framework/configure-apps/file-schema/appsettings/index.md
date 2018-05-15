---
title: Schéma nastavení aplikace
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 154f38880225fb420f9944f336ff885bd116e2c3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="app-settings-schema"></a><span data-ttu-id="40e4f-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="40e4f-102">App Settings schema</span></span>

<span data-ttu-id="40e4f-103">Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo všechny ostatní informace vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="40e4f-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="40e4f-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="40e4f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="40e4f-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="40e4f-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="40e4f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Přidat >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="40e4f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="40e4f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Clear >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="40e4f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="40e4f-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="40e4f-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="40e4f-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="40e4f-109">Element</span></span> | <span data-ttu-id="40e4f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="40e4f-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="40e4f-111">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="40e4f-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="40e4f-112">Obsahuje  **\<Přidat >**,  **\<clear >**, a  **\<odebrat >** značky pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="40e4f-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="40e4f-113">Má volitelný **souboru** atribut.</span><span class="sxs-lookup"><span data-stu-id="40e4f-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="40e4f-114">**\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="40e4f-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="40e4f-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="40e4f-115">Defines a setting.</span></span> <span data-ttu-id="40e4f-116">Podřízená položka  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="40e4f-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="40e4f-117">Vyžaduje **klíč** a **hodnotu** atributy.</span><span class="sxs-lookup"><span data-stu-id="40e4f-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="40e4f-118">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="40e4f-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="40e4f-119">Vymaže všechna nastavení.</span><span class="sxs-lookup"><span data-stu-id="40e4f-119">Clears all settings.</span></span> <span data-ttu-id="40e4f-120">Podřízená položka  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="40e4f-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="40e4f-121">Nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="40e4f-121">Has no attributes.</span></span> |
| [<span data-ttu-id="40e4f-122">**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="40e4f-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="40e4f-123">Odebere nastavení.</span><span class="sxs-lookup"><span data-stu-id="40e4f-123">Removes a setting.</span></span> <span data-ttu-id="40e4f-124">Podřízená položka  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="40e4f-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="40e4f-125">Vyžaduje **klíč** atribut.</span><span class="sxs-lookup"><span data-stu-id="40e4f-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="40e4f-126">\<appSettings > elementu</span><span class="sxs-lookup"><span data-stu-id="40e4f-126">\<appSettings> element</span></span>

<span data-ttu-id="40e4f-127">Tento prvek obsahuje  **\<Přidat >**,  **\<clear >**, a  **\<odebrat >** značky pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="40e4f-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="40e4f-128">Definuje volitelný atribut pro **soubor**.</span><span class="sxs-lookup"><span data-stu-id="40e4f-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="40e4f-129">\<Přidat > elementu</span><span class="sxs-lookup"><span data-stu-id="40e4f-129">\<add> element</span></span>

<span data-ttu-id="40e4f-130">Přidá vlastní nastavení aplikace jako dvojici název/hodnota do kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="40e4f-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="40e4f-131">Definuje atributy pro **klíč** a **hodnotu**.</span><span class="sxs-lookup"><span data-stu-id="40e4f-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="40e4f-132">\<Clear > elementu</span><span class="sxs-lookup"><span data-stu-id="40e4f-132">\<clear> element</span></span>

<span data-ttu-id="40e4f-133">Odebere všechny odkazy na zděděná vlastní nastavení aplikace a umožňuje pouze odkazy, které přidá  **\<Přidat >** následující prvky  **\<clear >** element.</span><span class="sxs-lookup"><span data-stu-id="40e4f-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="40e4f-134">Definuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="40e4f-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="40e4f-135">\<Odebrat > elementu</span><span class="sxs-lookup"><span data-stu-id="40e4f-135">\<remove> element</span></span>

<span data-ttu-id="40e4f-136">Odebere odkaz na zděděné vlastní nastavení aplikace z kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="40e4f-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="40e4f-137">Definuje atribut pro **klíč**.</span><span class="sxs-lookup"><span data-stu-id="40e4f-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="40e4f-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="40e4f-138">Example</span></span>

<span data-ttu-id="40e4f-139">Následující příklad ukazuje soubor s nastavením externí aplikaci (*custom.config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="40e4f-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="40e4f-140">Následující příklad ukazuje konfigurační soubor aplikace, která načítá nastavení v souboru externích nastavení a nastaví vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="40e4f-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="40e4f-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="40e4f-141">See also</span></span>

<span data-ttu-id="40e4f-142">[Přehled nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="40e4f-142">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="40e4f-143">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="40e4f-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
