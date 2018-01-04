---
title: "Schéma nastavení aplikace"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 028fdbeb90a1499459803f24f3aa62923452edba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="app-settings-schema"></a><span data-ttu-id="299a3-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="299a3-102">App Settings schema</span></span>

<span data-ttu-id="299a3-103">Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo všechny ostatní informace vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="299a3-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="299a3-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="299a3-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="299a3-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="299a3-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="299a3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Přidat >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="299a3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="299a3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Clear >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="299a3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="299a3-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="299a3-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="299a3-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="299a3-109">Element</span></span> | <span data-ttu-id="299a3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="299a3-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="299a3-111">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="299a3-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="299a3-112">Obsahuje  **\<Přidat >**,  **\<clear >**, a  **\<odebrat >** značky pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="299a3-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="299a3-113">Má volitelný **souboru** atribut.</span><span class="sxs-lookup"><span data-stu-id="299a3-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="299a3-114">**\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="299a3-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="299a3-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="299a3-115">Defines a setting.</span></span> <span data-ttu-id="299a3-116">Podřízená položka  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="299a3-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="299a3-117">Vyžaduje **klíč** a **hodnotu** atributy.</span><span class="sxs-lookup"><span data-stu-id="299a3-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="299a3-118">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="299a3-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="299a3-119">Vymaže všechna nastavení.</span><span class="sxs-lookup"><span data-stu-id="299a3-119">Clears all settings.</span></span> <span data-ttu-id="299a3-120">Podřízená položka  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="299a3-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="299a3-121">Nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="299a3-121">Has no attributes.</span></span> |
| [<span data-ttu-id="299a3-122">**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="299a3-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="299a3-123">Odebere nastavení.</span><span class="sxs-lookup"><span data-stu-id="299a3-123">Removes a setting.</span></span> <span data-ttu-id="299a3-124">Podřízená položka  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="299a3-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="299a3-125">Vyžaduje **klíč** atribut.</span><span class="sxs-lookup"><span data-stu-id="299a3-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="299a3-126">\<appSettings > elementu</span><span class="sxs-lookup"><span data-stu-id="299a3-126">\<appSettings> element</span></span>

<span data-ttu-id="299a3-127">Tento prvek obsahuje  **\<Přidat >**,  **\<clear >**, a  **\<odebrat >** značky pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="299a3-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="299a3-128">Definuje volitelný atribut pro **soubor**.</span><span class="sxs-lookup"><span data-stu-id="299a3-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="299a3-129">\<Přidat > elementu</span><span class="sxs-lookup"><span data-stu-id="299a3-129">\<add> element</span></span>

<span data-ttu-id="299a3-130">Přidá vlastní nastavení aplikace jako dvojici název/hodnota do kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="299a3-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="299a3-131">Definuje atributy pro **klíč** a **hodnotu**.</span><span class="sxs-lookup"><span data-stu-id="299a3-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="299a3-132">\<Clear > elementu</span><span class="sxs-lookup"><span data-stu-id="299a3-132">\<clear> element</span></span>

<span data-ttu-id="299a3-133">Odebere všechny odkazy na zděděná vlastní nastavení aplikace a umožňuje pouze odkazy, které přidá  **\<Přidat >** následující prvky  **\<clear >** element.</span><span class="sxs-lookup"><span data-stu-id="299a3-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="299a3-134">Definuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="299a3-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="299a3-135">\<Odebrat > elementu</span><span class="sxs-lookup"><span data-stu-id="299a3-135">\<remove> element</span></span>

<span data-ttu-id="299a3-136">Odebere odkaz na zděděné vlastní nastavení aplikace z kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="299a3-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="299a3-137">Definuje atribut pro **klíč**.</span><span class="sxs-lookup"><span data-stu-id="299a3-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="299a3-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="299a3-138">Example</span></span>

<span data-ttu-id="299a3-139">Následující příklad ukazuje soubor s nastavením externí aplikaci (*custom.config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="299a3-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="299a3-140">Následující příklad ukazuje konfigurační soubor aplikace, která načítá nastavení v souboru externích nastavení a nastaví vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="299a3-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="299a3-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="299a3-141">See also</span></span>

<span data-ttu-id="299a3-142">[Přehled nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="299a3-142">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="299a3-143">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="299a3-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
