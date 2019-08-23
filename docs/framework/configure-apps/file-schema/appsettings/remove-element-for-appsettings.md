---
title: <remove> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 121b1c4b124ba07ff3bd312fd3832d3da592f486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921285"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="4eec0-102">\<Odebrat element > pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="4eec0-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="4eec0-103">Odebere vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="4eec0-103">Removes custom application settings.</span></span>

<span data-ttu-id="4eec0-104">[ **\<> Konfigurace**](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4eec0-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="4eec0-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4eec0-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="4eec0-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="4eec0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4eec0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4eec0-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="4eec0-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="4eec0-108">Attribute</span></span>

|         | <span data-ttu-id="4eec0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4eec0-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="4eec0-110">**key**</span><span class="sxs-lookup"><span data-stu-id="4eec0-110">**key**</span></span> | <span data-ttu-id="4eec0-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="4eec0-111">Required attribute.</span></span><br><br><span data-ttu-id="4eec0-112">Určuje název klíče, který se má odebrat.</span><span class="sxs-lookup"><span data-stu-id="4eec0-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="4eec0-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="4eec0-113">Parent element</span></span>

|     | <span data-ttu-id="4eec0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4eec0-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4eec0-115"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="4eec0-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="4eec0-116">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4eec0-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4eec0-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="4eec0-117">Child elements</span></span>

<span data-ttu-id="4eec0-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="4eec0-118">None</span></span>

## <a name="example"></a><span data-ttu-id="4eec0-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="4eec0-119">Example</span></span>

<span data-ttu-id="4eec0-120">Následující příklad ukazuje, jak odebrat vlastní nastavení konfigurace pro `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="4eec0-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="4eec0-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4eec0-121">See also</span></span>

- [<span data-ttu-id="4eec0-122">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4eec0-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
