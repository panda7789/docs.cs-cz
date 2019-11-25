---
title: Schéma nastavení aplikace
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 609ddba9cd4d58f9c388cf669039ee128e87efd0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088084"
---
# <a name="app-settings-schema"></a><span data-ttu-id="63ccc-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="63ccc-102">App Settings schema</span></span>

<span data-ttu-id="63ccc-103">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63ccc-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="63ccc-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="63ccc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="63ccc-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="63ccc-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="63ccc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<přidat >** ](add-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="63ccc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)</span></span>\
<span data-ttu-id="63ccc-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear >** ](clear-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="63ccc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)</span></span>\
<span data-ttu-id="63ccc-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<odebrat >** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="63ccc-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="63ccc-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="63ccc-109">Element</span></span> | <span data-ttu-id="63ccc-110">Popis</span><span class="sxs-lookup"><span data-stu-id="63ccc-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="63ccc-111"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="63ccc-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="63ccc-112">Obsahuje **\<přidat >** , **\<vymazat >** a **\<odebrat značky >** pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="63ccc-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="63ccc-113">Má volitelný atribut **souboru** .</span><span class="sxs-lookup"><span data-stu-id="63ccc-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="63ccc-114"> **\<přidat >** </span><span class="sxs-lookup"><span data-stu-id="63ccc-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="63ccc-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="63ccc-115">Defines a setting.</span></span> <span data-ttu-id="63ccc-116">Podřízená položka **\<appSettings**</span><span class="sxs-lookup"><span data-stu-id="63ccc-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="63ccc-117">Vyžaduje atributy **klíče** a **hodnoty** .</span><span class="sxs-lookup"><span data-stu-id="63ccc-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="63ccc-118"> **\<vymazat >** </span><span class="sxs-lookup"><span data-stu-id="63ccc-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="63ccc-119">Vymaže všechna nastavení.</span><span class="sxs-lookup"><span data-stu-id="63ccc-119">Clears all settings.</span></span> <span data-ttu-id="63ccc-120">Podřízená položka **\<appSettings**</span><span class="sxs-lookup"><span data-stu-id="63ccc-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="63ccc-121">Nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="63ccc-121">Has no attributes.</span></span> |
| [<span data-ttu-id="63ccc-122"> **\<odebrat >** </span><span class="sxs-lookup"><span data-stu-id="63ccc-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="63ccc-123">Odebere nastavení.</span><span class="sxs-lookup"><span data-stu-id="63ccc-123">Removes a setting.</span></span> <span data-ttu-id="63ccc-124">Podřízená položka **\<appSettings**</span><span class="sxs-lookup"><span data-stu-id="63ccc-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="63ccc-125">Vyžaduje atribut **Key** .</span><span class="sxs-lookup"><span data-stu-id="63ccc-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="63ccc-126">element \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="63ccc-126">\<appSettings> element</span></span>

<span data-ttu-id="63ccc-127">Tento prvek obsahuje **\<přidat >** , **\<vymazat >** a **\<odebrat značky >** pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="63ccc-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="63ccc-128">Definuje volitelný atribut pro **soubor**.</span><span class="sxs-lookup"><span data-stu-id="63ccc-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="63ccc-129">\<přidat > element</span><span class="sxs-lookup"><span data-stu-id="63ccc-129">\<add> element</span></span>

<span data-ttu-id="63ccc-130">Přidá vlastní nastavení aplikace jako dvojici název-hodnota do kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="63ccc-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="63ccc-131">Definuje atributy pro **klíč** a **hodnotu**.</span><span class="sxs-lookup"><span data-stu-id="63ccc-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="63ccc-132">\<vymazat > element</span><span class="sxs-lookup"><span data-stu-id="63ccc-132">\<clear> element</span></span>

<span data-ttu-id="63ccc-133">Odebere všechny odkazy na zděděná vlastní nastavení aplikace a povoluje pouze odkazy, které jsou přidány pomocí **\<přidat >** prvky za **\<jasný >** element.</span><span class="sxs-lookup"><span data-stu-id="63ccc-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="63ccc-134">Nedefinuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="63ccc-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="63ccc-135">\<odebrat element ></span><span class="sxs-lookup"><span data-stu-id="63ccc-135">\<remove> element</span></span>

<span data-ttu-id="63ccc-136">Odebere odkaz na zděděné nastavení vlastní aplikace z kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="63ccc-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="63ccc-137">Definuje atribut pro **klíč**.</span><span class="sxs-lookup"><span data-stu-id="63ccc-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="63ccc-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="63ccc-138">Example</span></span>

<span data-ttu-id="63ccc-139">Následující příklad ukazuje soubor nastavení externí aplikace (*Custom. config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="63ccc-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="63ccc-140">Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastavuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="63ccc-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="63ccc-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63ccc-141">See also</span></span>

- [<span data-ttu-id="63ccc-142">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="63ccc-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="63ccc-143">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="63ccc-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
