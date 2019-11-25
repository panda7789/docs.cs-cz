---
title: <remove> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0fcdb75aa733a9d7634ec1c3b31dcbbb87e090e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088722"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="eeba4-102">\<odebrat element > pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="eeba4-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="eeba4-103">Odebere vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="eeba4-103">Removes custom application settings.</span></span>

<span data-ttu-id="eeba4-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="eeba4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eeba4-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="eeba4-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="eeba4-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="eeba4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="eeba4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eeba4-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="eeba4-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="eeba4-108">Attribute</span></span>

|         | <span data-ttu-id="eeba4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="eeba4-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="eeba4-110">**zkrat**</span><span class="sxs-lookup"><span data-stu-id="eeba4-110">**key**</span></span> | <span data-ttu-id="eeba4-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="eeba4-111">Required attribute.</span></span><br><br><span data-ttu-id="eeba4-112">Určuje název klíče, který se má odebrat.</span><span class="sxs-lookup"><span data-stu-id="eeba4-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="eeba4-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="eeba4-113">Parent element</span></span>

|     | <span data-ttu-id="eeba4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="eeba4-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="eeba4-115"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="eeba4-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="eeba4-116">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eeba4-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="eeba4-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="eeba4-117">Child elements</span></span>

<span data-ttu-id="eeba4-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="eeba4-118">None</span></span>

## <a name="example"></a><span data-ttu-id="eeba4-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="eeba4-119">Example</span></span>

<span data-ttu-id="eeba4-120">Následující příklad ukazuje, jak odebrat vlastní nastavení konfigurace pro `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="eeba4-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="eeba4-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eeba4-121">See also</span></span>

- [<span data-ttu-id="eeba4-122">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="eeba4-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
