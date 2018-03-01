---
title: '&lt;Vymazat&gt; element pro &lt;appSettings&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54479cab9abc2c1a107cd055341404c0fe1308fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="d9d5e-102">\<Clear > elementu pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="d9d5e-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="d9d5e-103">Vymaže vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9d5e-103">Clears custom application settings.</span></span>

<span data-ttu-id="d9d5e-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d9d5e-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d9d5e-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d9d5e-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="d9d5e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="d9d5e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d9d5e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9d5e-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="d9d5e-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="d9d5e-108">Attributes</span></span>

<span data-ttu-id="d9d5e-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="d9d5e-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="d9d5e-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="d9d5e-110">Parent element</span></span>

|     | <span data-ttu-id="d9d5e-111">Popis</span><span class="sxs-lookup"><span data-stu-id="d9d5e-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d9d5e-112">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="d9d5e-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="d9d5e-113">Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo jakékoli jiné informace o konfiguraci vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="d9d5e-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d9d5e-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="d9d5e-114">Child elements</span></span>

<span data-ttu-id="d9d5e-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="d9d5e-115">None</span></span>

## <a name="example"></a><span data-ttu-id="d9d5e-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9d5e-116">Example</span></span>

<span data-ttu-id="d9d5e-117">Následující příklad ukazuje, jak vymazat nastavení vlastní konfigurace:</span><span class="sxs-lookup"><span data-stu-id="d9d5e-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="d9d5e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9d5e-118">See also</span></span>

[<span data-ttu-id="d9d5e-119">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d9d5e-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
