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
ms.openlocfilehash: 62913face910ae9500aa5e6f2f443db67ffd4240
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301282"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="25c3a-102">\<Odebrat > – element pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="25c3a-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="25c3a-103">Odebere vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="25c3a-103">Removes custom application settings.</span></span>

<span data-ttu-id="25c3a-104">[ **\<Konfigurace >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="25c3a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="25c3a-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="25c3a-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="25c3a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="25c3a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="25c3a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25c3a-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="25c3a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="25c3a-108">Attribute</span></span>

|         | <span data-ttu-id="25c3a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="25c3a-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="25c3a-110">**key**</span><span class="sxs-lookup"><span data-stu-id="25c3a-110">**key**</span></span> | <span data-ttu-id="25c3a-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="25c3a-111">Required attribute.</span></span><br><br><span data-ttu-id="25c3a-112">Určuje název klíč k odebrání.</span><span class="sxs-lookup"><span data-stu-id="25c3a-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="25c3a-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="25c3a-113">Parent element</span></span>

|     | <span data-ttu-id="25c3a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="25c3a-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="25c3a-115"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="25c3a-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="25c3a-116">Obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="25c3a-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="25c3a-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="25c3a-117">Child elements</span></span>

<span data-ttu-id="25c3a-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="25c3a-118">None</span></span>

## <a name="example"></a><span data-ttu-id="25c3a-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="25c3a-119">Example</span></span>

<span data-ttu-id="25c3a-120">Následující příklad ukazuje, jak odebrat vlastní nastavení pro `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="25c3a-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="25c3a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25c3a-121">See also</span></span>

- [<span data-ttu-id="25c3a-122">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="25c3a-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
