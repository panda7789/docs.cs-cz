---
title: '&lt;Odebrat&gt; – element pro &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: e9b79a8319b320289f43adac5a82ef22fa5e32b0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199692"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="ec934-102">\<Odebrat > – element pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="ec934-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="ec934-103">Odebere vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec934-103">Removes custom application settings.</span></span>

<span data-ttu-id="ec934-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ec934-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="ec934-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="ec934-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="ec934-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="ec934-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ec934-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec934-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="ec934-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ec934-108">Attribute</span></span>

|         | <span data-ttu-id="ec934-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ec934-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="ec934-110">**Klíč**</span><span class="sxs-lookup"><span data-stu-id="ec934-110">**key**</span></span> | <span data-ttu-id="ec934-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ec934-111">Required attribute.</span></span><br><br><span data-ttu-id="ec934-112">Určuje název klíč k odebrání.</span><span class="sxs-lookup"><span data-stu-id="ec934-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="ec934-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="ec934-113">Parent element</span></span>

|     | <span data-ttu-id="ec934-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ec934-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ec934-115">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="ec934-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="ec934-116">Obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec934-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ec934-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ec934-117">Child elements</span></span>

<span data-ttu-id="ec934-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec934-118">None</span></span>

## <a name="example"></a><span data-ttu-id="ec934-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec934-119">Example</span></span>

<span data-ttu-id="ec934-120">Následující příklad ukazuje, jak odebrat vlastní nastavení pro `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="ec934-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="ec934-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec934-121">See also</span></span>

- [<span data-ttu-id="ec934-122">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ec934-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
