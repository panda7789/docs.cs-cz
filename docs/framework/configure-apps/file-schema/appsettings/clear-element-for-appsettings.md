---
title: '&lt;Vymazat&gt; element pro &lt;appSettings&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ac1e9a86d0c3e1bb1f23b753fd9867effef03ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="15c02-102">\<Clear > elementu pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="15c02-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="15c02-103">Vymaže vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="15c02-103">Clears custom application settings.</span></span>

<span data-ttu-id="15c02-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="15c02-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="15c02-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="15c02-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="15c02-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="15c02-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="15c02-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15c02-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="15c02-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="15c02-108">Attributes</span></span>

<span data-ttu-id="15c02-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="15c02-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="15c02-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="15c02-110">Parent element</span></span>

|     | <span data-ttu-id="15c02-111">Popis</span><span class="sxs-lookup"><span data-stu-id="15c02-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="15c02-112">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="15c02-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="15c02-113">Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo jakékoli jiné informace o konfiguraci vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="15c02-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="15c02-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="15c02-114">Child elements</span></span>

<span data-ttu-id="15c02-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="15c02-115">None</span></span>

## <a name="example"></a><span data-ttu-id="15c02-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="15c02-116">Example</span></span>

<span data-ttu-id="15c02-117">Následující příklad ukazuje, jak vymazat nastavení vlastní konfigurace:</span><span class="sxs-lookup"><span data-stu-id="15c02-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="15c02-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="15c02-118">See also</span></span>

[<span data-ttu-id="15c02-119">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15c02-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
