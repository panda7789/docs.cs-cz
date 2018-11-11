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
ms.sourcegitcommit: 0fbd677fcdc5bf46c4d827f492eaaa970edc07b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2018
ms.locfileid: "50235775"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="23e4f-102">\<Odebrat > – element pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="23e4f-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="23e4f-103">Odebere vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="23e4f-103">Removes custom application settings.</span></span>

<span data-ttu-id="23e4f-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="23e4f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="23e4f-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="23e4f-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="23e4f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Odebrat >**</span><span class="sxs-lookup"><span data-stu-id="23e4f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="23e4f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23e4f-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="23e4f-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="23e4f-108">Attribute</span></span>

|         | <span data-ttu-id="23e4f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="23e4f-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="23e4f-110">**Klíč**</span><span class="sxs-lookup"><span data-stu-id="23e4f-110">**key**</span></span> | <span data-ttu-id="23e4f-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="23e4f-111">Required attribute.</span></span><br><br><span data-ttu-id="23e4f-112">Určuje název klíč k odebrání.</span><span class="sxs-lookup"><span data-stu-id="23e4f-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="23e4f-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="23e4f-113">Parent element</span></span>

|     | <span data-ttu-id="23e4f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="23e4f-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="23e4f-115">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="23e4f-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="23e4f-116">Obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="23e4f-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="23e4f-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="23e4f-117">Child elements</span></span>

<span data-ttu-id="23e4f-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="23e4f-118">None</span></span>

## <a name="example"></a><span data-ttu-id="23e4f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="23e4f-119">Example</span></span>

<span data-ttu-id="23e4f-120">Následující příklad ukazuje, jak odebrat vlastní nastavení pro `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="23e4f-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="23e4f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23e4f-121">See also</span></span>

- [<span data-ttu-id="23e4f-122">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="23e4f-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
