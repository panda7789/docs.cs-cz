---
title: '&lt;Vymazat&gt; element pro &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 525818309ddc142fdb3ad65ce841ea58c1d635a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350663"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="64ccf-102">\<Clear > elementu pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="64ccf-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="64ccf-103">Vymaže vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="64ccf-103">Clears custom application settings.</span></span>

<span data-ttu-id="64ccf-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="64ccf-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="64ccf-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="64ccf-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="64ccf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="64ccf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="64ccf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64ccf-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="64ccf-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="64ccf-108">Attributes</span></span>

<span data-ttu-id="64ccf-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="64ccf-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="64ccf-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="64ccf-110">Parent element</span></span>

|     | <span data-ttu-id="64ccf-111">Popis</span><span class="sxs-lookup"><span data-stu-id="64ccf-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="64ccf-112">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="64ccf-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="64ccf-113">Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo jakékoli jiné informace o konfiguraci vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="64ccf-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="64ccf-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="64ccf-114">Child elements</span></span>

<span data-ttu-id="64ccf-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="64ccf-115">None</span></span>

## <a name="example"></a><span data-ttu-id="64ccf-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="64ccf-116">Example</span></span>

<span data-ttu-id="64ccf-117">Následující příklad ukazuje, jak vymazat nastavení vlastní konfigurace:</span><span class="sxs-lookup"><span data-stu-id="64ccf-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="64ccf-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="64ccf-118">See also</span></span>

[<span data-ttu-id="64ccf-119">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="64ccf-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
