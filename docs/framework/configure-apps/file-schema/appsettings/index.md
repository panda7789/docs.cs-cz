---
title: Schéma nastavení aplikace
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215432"
---
# <a name="app-settings-schema"></a><span data-ttu-id="85b9c-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="85b9c-102">App Settings schema</span></span>

<span data-ttu-id="85b9c-103">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="85b9c-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="85b9c-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="85b9c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="85b9c-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="85b9c-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="85b9c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<přidat >** ](add-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="85b9c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)</span></span>\
<span data-ttu-id="85b9c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear >** ](clear-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="85b9c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)</span></span>\
<span data-ttu-id="85b9c-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<odebrat >** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="85b9c-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="85b9c-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="85b9c-109">Element</span></span> | <span data-ttu-id="85b9c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="85b9c-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="85b9c-111"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="85b9c-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="85b9c-112">Obsahuje **\<přidat >** , **\<vymazat >** a **\<odebrat značky >** pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="85b9c-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="85b9c-113">Má volitelný atribut **souboru** .</span><span class="sxs-lookup"><span data-stu-id="85b9c-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="85b9c-114"> **\<přidat >** </span><span class="sxs-lookup"><span data-stu-id="85b9c-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="85b9c-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="85b9c-115">Defines a setting.</span></span> <span data-ttu-id="85b9c-116">Podřízená položka **>\<appSettings**</span><span class="sxs-lookup"><span data-stu-id="85b9c-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="85b9c-117">Vyžaduje atributy **klíče** a **hodnoty** .</span><span class="sxs-lookup"><span data-stu-id="85b9c-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="85b9c-118"> **\<vymazat >** </span><span class="sxs-lookup"><span data-stu-id="85b9c-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="85b9c-119">Vymaže všechna nastavení.</span><span class="sxs-lookup"><span data-stu-id="85b9c-119">Clears all settings.</span></span> <span data-ttu-id="85b9c-120">Podřízená položka **>\<appSettings**</span><span class="sxs-lookup"><span data-stu-id="85b9c-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="85b9c-121">Nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="85b9c-121">Has no attributes.</span></span> |
| [<span data-ttu-id="85b9c-122"> **\<odebrat >** </span><span class="sxs-lookup"><span data-stu-id="85b9c-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="85b9c-123">Odebere nastavení.</span><span class="sxs-lookup"><span data-stu-id="85b9c-123">Removes a setting.</span></span> <span data-ttu-id="85b9c-124">Podřízená položka **>\<appSettings**</span><span class="sxs-lookup"><span data-stu-id="85b9c-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="85b9c-125">Vyžaduje atribut **Key** .</span><span class="sxs-lookup"><span data-stu-id="85b9c-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="85b9c-126">element \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="85b9c-126">\<appSettings> element</span></span>

<span data-ttu-id="85b9c-127">Tento prvek obsahuje **\<přidat >** , **\<vymazat >** a **\<odebrat značky >** pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="85b9c-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="85b9c-128">Definuje volitelný atribut pro **soubor**.</span><span class="sxs-lookup"><span data-stu-id="85b9c-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="85b9c-129">\<přidat > element</span><span class="sxs-lookup"><span data-stu-id="85b9c-129">\<add> element</span></span>

<span data-ttu-id="85b9c-130">Přidá vlastní nastavení aplikace jako dvojici název-hodnota do kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="85b9c-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="85b9c-131">Definuje atributy pro **klíč** a **hodnotu**.</span><span class="sxs-lookup"><span data-stu-id="85b9c-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="85b9c-132">\<vymazat > element</span><span class="sxs-lookup"><span data-stu-id="85b9c-132">\<clear> element</span></span>

<span data-ttu-id="85b9c-133">Odebere všechny odkazy na zděděná vlastní nastavení aplikace a povoluje pouze odkazy, které jsou přidány pomocí **\<přidat >** prvky za **\<jasný >** element.</span><span class="sxs-lookup"><span data-stu-id="85b9c-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="85b9c-134">Nedefinuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="85b9c-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="85b9c-135">\<odebrat element ></span><span class="sxs-lookup"><span data-stu-id="85b9c-135">\<remove> element</span></span>

<span data-ttu-id="85b9c-136">Odebere odkaz na zděděné nastavení vlastní aplikace z kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="85b9c-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="85b9c-137">Definuje atribut pro **klíč**.</span><span class="sxs-lookup"><span data-stu-id="85b9c-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="85b9c-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="85b9c-138">Example</span></span>

<span data-ttu-id="85b9c-139">Následující příklad ukazuje soubor nastavení externí aplikace (*Custom. config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="85b9c-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="85b9c-140">Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastavuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="85b9c-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="85b9c-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="85b9c-141">See also</span></span>

- [<span data-ttu-id="85b9c-142">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="85b9c-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="85b9c-143">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="85b9c-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
