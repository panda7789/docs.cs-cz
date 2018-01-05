---
title: '&lt;Odebrat&gt; element pro &lt;appSettings&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e803561ef20bb17ed7c637eb487027466b65077
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="df2fe-102">\<Odebrat > elementu pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="df2fe-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="df2fe-103">Odebere vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="df2fe-103">Removes custom application settings.</span></span>

<span data-ttu-id="df2fe-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="df2fe-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="df2fe-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="df2fe-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="df2fe-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="df2fe-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="df2fe-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df2fe-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="df2fe-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="df2fe-108">Attribute</span></span>

|         | <span data-ttu-id="df2fe-109">Popis</span><span class="sxs-lookup"><span data-stu-id="df2fe-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="df2fe-110">**klíč**</span><span class="sxs-lookup"><span data-stu-id="df2fe-110">**key**</span></span> | <span data-ttu-id="df2fe-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="df2fe-111">Required attribute.</span></span><br><br><span data-ttu-id="df2fe-112">Určuje název klíč k odebrání.</span><span class="sxs-lookup"><span data-stu-id="df2fe-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="df2fe-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="df2fe-113">Parent element</span></span>

|     | <span data-ttu-id="df2fe-114">Popis</span><span class="sxs-lookup"><span data-stu-id="df2fe-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="df2fe-115">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="df2fe-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="df2fe-116">Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo všechny ostatní informace vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="df2fe-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="df2fe-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="df2fe-117">Child elements</span></span>

<span data-ttu-id="df2fe-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="df2fe-118">None</span></span>

## <a name="example"></a><span data-ttu-id="df2fe-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="df2fe-119">Example</span></span>

<span data-ttu-id="df2fe-120">Následující příklad ukazuje, jak odebrat vlastní nastavení pro `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="df2fe-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="df2fe-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="df2fe-121">See also</span></span>

[<span data-ttu-id="df2fe-122">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="df2fe-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
