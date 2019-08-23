---
title: Schéma nastavení aplikace
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d02f9f952c0ca7651d27571111a2d29f3d1130fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921292"
---
# <a name="app-settings-schema"></a><span data-ttu-id="f4c48-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="f4c48-102">App Settings schema</span></span>

<span data-ttu-id="f4c48-103">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f4c48-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="f4c48-104">[ **\<> Konfigurace**](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f4c48-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="f4c48-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f4c48-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="f4c48-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add>** ](add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="f4c48-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="f4c48-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Vymazat >** ](clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="f4c48-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="f4c48-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<odebrat >** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="f4c48-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="f4c48-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4c48-109">Element</span></span> | <span data-ttu-id="f4c48-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f4c48-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="f4c48-111"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="f4c48-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="f4c48-112">**Obsahuje\<> Přidat**,  **\<vymazat >** a  **\<odebrat značky >** pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4c48-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f4c48-113">Má volitelný atribut **souboru** .</span><span class="sxs-lookup"><span data-stu-id="f4c48-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="f4c48-114"> **\<add>** </span><span class="sxs-lookup"><span data-stu-id="f4c48-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="f4c48-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="f4c48-115">Defines a setting.</span></span> <span data-ttu-id="f4c48-116">Podřízený objekt appSettings >.  **\<**</span><span class="sxs-lookup"><span data-stu-id="f4c48-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f4c48-117">Vyžaduje atributy **klíče** a **hodnoty** .</span><span class="sxs-lookup"><span data-stu-id="f4c48-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="f4c48-118"> **\<Vymazat >** </span><span class="sxs-lookup"><span data-stu-id="f4c48-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="f4c48-119">Vymaže všechna nastavení.</span><span class="sxs-lookup"><span data-stu-id="f4c48-119">Clears all settings.</span></span> <span data-ttu-id="f4c48-120">Podřízený objekt appSettings >.  **\<**</span><span class="sxs-lookup"><span data-stu-id="f4c48-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f4c48-121">Nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="f4c48-121">Has no attributes.</span></span> |
| [<span data-ttu-id="f4c48-122"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="f4c48-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="f4c48-123">Odebere nastavení.</span><span class="sxs-lookup"><span data-stu-id="f4c48-123">Removes a setting.</span></span> <span data-ttu-id="f4c48-124">Podřízený objekt appSettings >.  **\<**</span><span class="sxs-lookup"><span data-stu-id="f4c48-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f4c48-125">Vyžaduje atribut **Key** .</span><span class="sxs-lookup"><span data-stu-id="f4c48-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="f4c48-126">\<appSettings – element > element</span><span class="sxs-lookup"><span data-stu-id="f4c48-126">\<appSettings> element</span></span>

<span data-ttu-id="f4c48-127">Tento prvek obsahuje  **\<přidání >** ,  **\<vymazání >** a  **\<odebrání značek >** pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4c48-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f4c48-128">Definuje volitelný atribut pro **soubor**.</span><span class="sxs-lookup"><span data-stu-id="f4c48-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="f4c48-129">\<Přidat > element</span><span class="sxs-lookup"><span data-stu-id="f4c48-129">\<add> element</span></span>

<span data-ttu-id="f4c48-130">Přidá vlastní nastavení aplikace jako dvojici název-hodnota do kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4c48-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="f4c48-131">Definuje atributy pro **klíč** a **hodnotu**.</span><span class="sxs-lookup"><span data-stu-id="f4c48-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="f4c48-132">\<Vymazat > element</span><span class="sxs-lookup"><span data-stu-id="f4c48-132">\<clear> element</span></span>

<span data-ttu-id="f4c48-133">Odebere všechny odkazy na zděděná nastavení vlastní aplikace a povoluje pouze odkazy, které jsou přidány  **\<přidáním >** prvků po  **\<elementu Clear >** .</span><span class="sxs-lookup"><span data-stu-id="f4c48-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="f4c48-134">Nedefinuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="f4c48-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="f4c48-135">\<Odebrat element ></span><span class="sxs-lookup"><span data-stu-id="f4c48-135">\<remove> element</span></span>

<span data-ttu-id="f4c48-136">Odebere odkaz na zděděné nastavení vlastní aplikace z kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4c48-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="f4c48-137">Definuje atribut pro **klíč**.</span><span class="sxs-lookup"><span data-stu-id="f4c48-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="f4c48-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4c48-138">Example</span></span>

<span data-ttu-id="f4c48-139">Následující příklad ukazuje soubor nastavení externí aplikace (*Custom. config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="f4c48-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="f4c48-140">Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastavuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="f4c48-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f4c48-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4c48-141">See also</span></span>

- [<span data-ttu-id="f4c48-142">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="f4c48-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="f4c48-143">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="f4c48-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
