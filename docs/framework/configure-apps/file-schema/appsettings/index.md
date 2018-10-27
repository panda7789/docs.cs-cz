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
ms.openlocfilehash: 9bf2568c8c18f8f6d18c445e802cc72df18fb8c4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191140"
---
# <a name="app-settings-schema"></a><span data-ttu-id="05f58-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="05f58-102">App Settings schema</span></span>

<span data-ttu-id="05f58-103">Obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="05f58-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="05f58-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="05f58-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="05f58-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="05f58-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="05f58-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Přidat >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="05f58-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="05f58-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Vymazat >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="05f58-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="05f58-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="05f58-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="05f58-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="05f58-109">Element</span></span> | <span data-ttu-id="05f58-110">Popis</span><span class="sxs-lookup"><span data-stu-id="05f58-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="05f58-111">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="05f58-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="05f58-112">Obsahuje  **\<Přidat >**,  **\<vymazat >**, a  **\<odebrat >** značek k nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="05f58-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="05f58-113">Má volitelnou **souboru** atribut.</span><span class="sxs-lookup"><span data-stu-id="05f58-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="05f58-114">**\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="05f58-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="05f58-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="05f58-115">Defines a setting.</span></span> <span data-ttu-id="05f58-116">Podřízený  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="05f58-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="05f58-117">Vyžaduje **klíč** a **hodnotu** atributy.</span><span class="sxs-lookup"><span data-stu-id="05f58-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="05f58-118">**\<Vymazat >**</span><span class="sxs-lookup"><span data-stu-id="05f58-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="05f58-119">Vymaže všechna nastavení.</span><span class="sxs-lookup"><span data-stu-id="05f58-119">Clears all settings.</span></span> <span data-ttu-id="05f58-120">Podřízený  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="05f58-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="05f58-121">nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="05f58-121">Has no attributes.</span></span> |
| [<span data-ttu-id="05f58-122">**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="05f58-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="05f58-123">Odebere nastavení.</span><span class="sxs-lookup"><span data-stu-id="05f58-123">Removes a setting.</span></span> <span data-ttu-id="05f58-124">Podřízený  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="05f58-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="05f58-125">Vyžaduje **klíč** atribut.</span><span class="sxs-lookup"><span data-stu-id="05f58-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="05f58-126">\<appSettings > – element</span><span class="sxs-lookup"><span data-stu-id="05f58-126">\<appSettings> element</span></span>

<span data-ttu-id="05f58-127">Tento prvek obsahuje  **\<Přidat >**,  **\<vymazat >**, a  **\<odebrat >** značek k nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="05f58-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="05f58-128">Definuje volitelný atribut pro **souboru**.</span><span class="sxs-lookup"><span data-stu-id="05f58-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="05f58-129">\<Přidat > – element</span><span class="sxs-lookup"><span data-stu-id="05f58-129">\<add> element</span></span>

<span data-ttu-id="05f58-130">Přidá vlastní nastavení aplikace jako dvojice název/hodnota do kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="05f58-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="05f58-131">Definuje atributy pro **klíč** a **hodnota**.</span><span class="sxs-lookup"><span data-stu-id="05f58-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="05f58-132">\<Vymazat > – element</span><span class="sxs-lookup"><span data-stu-id="05f58-132">\<clear> element</span></span>

<span data-ttu-id="05f58-133">Odebere všechny odkazy na zděděná nastavení vlastní aplikace a povoluje pouze odkazy, které jsou přidány pomocí  **\<Přidat >** prvky, které následují  **\<vymazat >** element.</span><span class="sxs-lookup"><span data-stu-id="05f58-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="05f58-134">Definuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="05f58-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="05f58-135">\<Odebrat > – element</span><span class="sxs-lookup"><span data-stu-id="05f58-135">\<remove> element</span></span>

<span data-ttu-id="05f58-136">Odebere odkaz na nastavení zděděné vlastní aplikace z aplikace nastavení kolekce.</span><span class="sxs-lookup"><span data-stu-id="05f58-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="05f58-137">Definuje atribut pro **klíč**.</span><span class="sxs-lookup"><span data-stu-id="05f58-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="05f58-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="05f58-138">Example</span></span>

<span data-ttu-id="05f58-139">Následující příklad ukazuje soubor nastavení externí aplikace (*custom.config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="05f58-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="05f58-140">Následující příklad ukazuje konfigurační soubor aplikace, která načítá nastavení v souboru externích nastavení a nastaví vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="05f58-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="05f58-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05f58-141">See also</span></span>

- [<span data-ttu-id="05f58-142">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="05f58-142">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)   
- [<span data-ttu-id="05f58-143">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="05f58-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
