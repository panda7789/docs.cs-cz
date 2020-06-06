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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215432"
---
# <a name="app-settings-schema"></a><span data-ttu-id="31170-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="31170-102">App Settings schema</span></span>

<span data-ttu-id="31170-103">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="31170-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="31170-104">Prvek</span><span class="sxs-lookup"><span data-stu-id="31170-104">Element</span></span> | <span data-ttu-id="31170-105">Description</span><span class="sxs-lookup"><span data-stu-id="31170-105">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="31170-106">Obsahuje **\<add>** **\<clear>** značky, a **\<remove>** pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="31170-106">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="31170-107">Má volitelný atribut **souboru** .</span><span class="sxs-lookup"><span data-stu-id="31170-107">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="31170-108">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="31170-108">Defines a setting.</span></span> <span data-ttu-id="31170-109">Podřízená položka **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="31170-109">Child of **\<appSettings>**.</span></span> <span data-ttu-id="31170-110">Vyžaduje atributy **klíče** a **hodnoty** .</span><span class="sxs-lookup"><span data-stu-id="31170-110">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="31170-111">Vymaže všechna nastavení.</span><span class="sxs-lookup"><span data-stu-id="31170-111">Clears all settings.</span></span> <span data-ttu-id="31170-112">Podřízená položka **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="31170-112">Child of **\<appSettings>**.</span></span> <span data-ttu-id="31170-113">Nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="31170-113">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="31170-114">Odebere nastavení.</span><span class="sxs-lookup"><span data-stu-id="31170-114">Removes a setting.</span></span> <span data-ttu-id="31170-115">Podřízená položka **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="31170-115">Child of **\<appSettings>**.</span></span> <span data-ttu-id="31170-116">Vyžaduje atribut **Key** .</span><span class="sxs-lookup"><span data-stu-id="31170-116">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="31170-117">\<appSettings> – element</span><span class="sxs-lookup"><span data-stu-id="31170-117">\<appSettings> element</span></span>

<span data-ttu-id="31170-118">Tento element obsahuje **\<add>** **\<clear>** značky, a **\<remove>** pro řízení nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="31170-118">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="31170-119">Definuje volitelný atribut pro **soubor**.</span><span class="sxs-lookup"><span data-stu-id="31170-119">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="31170-120">\<add> – element</span><span class="sxs-lookup"><span data-stu-id="31170-120">\<add> element</span></span>

<span data-ttu-id="31170-121">Přidá vlastní nastavení aplikace jako dvojici název-hodnota do kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="31170-121">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="31170-122">Definuje atributy pro **klíč** a **hodnotu**.</span><span class="sxs-lookup"><span data-stu-id="31170-122">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="31170-123">\<clear> – element</span><span class="sxs-lookup"><span data-stu-id="31170-123">\<clear> element</span></span>

<span data-ttu-id="31170-124">Odebere všechny odkazy na zděděná nastavení vlastní aplikace a povoluje pouze odkazy, které jsou přidány **\<add>** prvky, které následují za **\<clear>** elementem.</span><span class="sxs-lookup"><span data-stu-id="31170-124">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="31170-125">Nedefinuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="31170-125">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="31170-126">\<remove> – element</span><span class="sxs-lookup"><span data-stu-id="31170-126">\<remove> element</span></span>

<span data-ttu-id="31170-127">Odebere odkaz na zděděné nastavení vlastní aplikace z kolekce nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="31170-127">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="31170-128">Definuje atribut pro **klíč**.</span><span class="sxs-lookup"><span data-stu-id="31170-128">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="31170-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="31170-129">Example</span></span>

<span data-ttu-id="31170-130">Následující příklad ukazuje soubor nastavení externí aplikace (*Custom. config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="31170-130">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="31170-131">Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastavuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="31170-131">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="31170-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="31170-132">See also</span></span>

- [<span data-ttu-id="31170-133">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="31170-133">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="31170-134">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="31170-134">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
