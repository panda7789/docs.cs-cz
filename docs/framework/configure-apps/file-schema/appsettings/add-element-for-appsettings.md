---
title: <add> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09864ea8f174d0c23f26db49f8cc0d43608522a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119342"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="8114b-102">\<přidat > element pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="8114b-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="8114b-103">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="8114b-103">Adds a custom application setting.</span></span>

<span data-ttu-id="8114b-104">[**konfigurační >\<** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8114b-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="8114b-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="8114b-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="8114b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<přidat >**</span><span class="sxs-lookup"><span data-stu-id="8114b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8114b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8114b-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="8114b-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="8114b-108">Attributes</span></span>

|           | <span data-ttu-id="8114b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8114b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="8114b-110">**zkrat**</span><span class="sxs-lookup"><span data-stu-id="8114b-110">**key**</span></span>   | <span data-ttu-id="8114b-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8114b-111">Required attribute.</span></span><br><br><span data-ttu-id="8114b-112">Určuje název klíče, který chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="8114b-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="8114b-113">**value**</span><span class="sxs-lookup"><span data-stu-id="8114b-113">**value**</span></span> | <span data-ttu-id="8114b-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8114b-114">Required attribute.</span></span><br><br><span data-ttu-id="8114b-115">Určuje hodnotu klíče, který se má přidat.</span><span class="sxs-lookup"><span data-stu-id="8114b-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="8114b-116">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="8114b-116">Parent element</span></span>

|     | <span data-ttu-id="8114b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="8114b-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8114b-118"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="8114b-118">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="8114b-119">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8114b-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8114b-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="8114b-120">Child elements</span></span>

<span data-ttu-id="8114b-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="8114b-121">None</span></span>

## <a name="example"></a><span data-ttu-id="8114b-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="8114b-122">Example</span></span>

<span data-ttu-id="8114b-123">Následující příklad ukazuje, jak přidat vlastní nastavení konfigurace pro název aplikace:</span><span class="sxs-lookup"><span data-stu-id="8114b-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="8114b-124">Následující příklad používá element `<add>` k definování dvou nastavení kompatibility v aplikaci ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="8114b-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="8114b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8114b-125">See also</span></span>

- [<span data-ttu-id="8114b-126">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8114b-126">Configuration file schema for the .NET Framework</span></span>](../index.md)
