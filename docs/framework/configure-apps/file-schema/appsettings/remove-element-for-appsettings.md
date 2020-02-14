---
title: <remove> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215474"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="bd795-102">\<odebrat element > pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="bd795-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="bd795-103">Odebere vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd795-103">Removes custom application settings.</span></span>

<span data-ttu-id="bd795-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd795-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd795-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="bd795-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="bd795-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="bd795-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bd795-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd795-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="bd795-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="bd795-108">Attribute</span></span>

|         | <span data-ttu-id="bd795-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bd795-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="bd795-110">**key**</span><span class="sxs-lookup"><span data-stu-id="bd795-110">**key**</span></span> | <span data-ttu-id="bd795-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bd795-111">Required attribute.</span></span><br><br><span data-ttu-id="bd795-112">Určuje název klíče, který se má odebrat.</span><span class="sxs-lookup"><span data-stu-id="bd795-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="bd795-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="bd795-113">Parent element</span></span>

|     | <span data-ttu-id="bd795-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bd795-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bd795-115"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="bd795-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="bd795-116">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd795-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="bd795-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="bd795-117">Child elements</span></span>

<span data-ttu-id="bd795-118">Žádná</span><span class="sxs-lookup"><span data-stu-id="bd795-118">None</span></span>

## <a name="example"></a><span data-ttu-id="bd795-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd795-119">Example</span></span>

<span data-ttu-id="bd795-120">Následující příklad ukazuje, jak odebrat vlastní nastavení konfigurace pro `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="bd795-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="bd795-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd795-121">See also</span></span>

- [<span data-ttu-id="bd795-122">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bd795-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
