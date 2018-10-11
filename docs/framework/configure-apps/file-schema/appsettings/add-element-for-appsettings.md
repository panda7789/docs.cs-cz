---
title: '&lt;Přidat&gt; – element pro &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bcdac76528e7a8b07b56b6fd1d827c3c8072c371
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086315"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="bdd37-102">\<Přidat > – element pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="bdd37-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="bdd37-103">Přidá nastavení vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdd37-103">Adds a custom application setting.</span></span>

<span data-ttu-id="bdd37-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bdd37-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="bdd37-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="bdd37-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="bdd37-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="bdd37-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bdd37-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdd37-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="bdd37-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="bdd37-108">Attributes</span></span>

|           | <span data-ttu-id="bdd37-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bdd37-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="bdd37-110">**Klíč**</span><span class="sxs-lookup"><span data-stu-id="bdd37-110">**key**</span></span>   | <span data-ttu-id="bdd37-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bdd37-111">Required attribute.</span></span><br><br><span data-ttu-id="bdd37-112">Určuje název klíče pro přidání.</span><span class="sxs-lookup"><span data-stu-id="bdd37-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="bdd37-113">**value**</span><span class="sxs-lookup"><span data-stu-id="bdd37-113">**value**</span></span> | <span data-ttu-id="bdd37-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bdd37-114">Required attribute.</span></span><br><br><span data-ttu-id="bdd37-115">Určuje hodnotu klíče pro přidání.</span><span class="sxs-lookup"><span data-stu-id="bdd37-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="bdd37-116">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="bdd37-116">Parent element</span></span>

|     | <span data-ttu-id="bdd37-117">Popis</span><span class="sxs-lookup"><span data-stu-id="bdd37-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bdd37-118">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="bdd37-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="bdd37-119">Obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bdd37-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="bdd37-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="bdd37-120">Child elements</span></span>

<span data-ttu-id="bdd37-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="bdd37-121">None</span></span>

## <a name="example"></a><span data-ttu-id="bdd37-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdd37-122">Example</span></span>

<span data-ttu-id="bdd37-123">Následující příklad ukazuje, jak přidat vlastní nastavení pro název aplikace:</span><span class="sxs-lookup"><span data-stu-id="bdd37-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="bdd37-124">V následujícím příkladu `<add>` element definovat dvě nastavení kompatibility v aplikaci technologie ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="bdd37-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="bdd37-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdd37-125">See also</span></span>

[<span data-ttu-id="bdd37-126">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bdd37-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
