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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215474"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="65d6a-102">\<remove> – element pro \<appSettings></span><span class="sxs-lookup"><span data-stu-id="65d6a-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="65d6a-103">Odebere vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="65d6a-103">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="65d6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65d6a-104">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="65d6a-105">Atribut</span><span class="sxs-lookup"><span data-stu-id="65d6a-105">Attribute</span></span>

|         | <span data-ttu-id="65d6a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="65d6a-106">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="65d6a-107">**zkrat**</span><span class="sxs-lookup"><span data-stu-id="65d6a-107">**key**</span></span> | <span data-ttu-id="65d6a-108">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="65d6a-108">Required attribute.</span></span><br><br><span data-ttu-id="65d6a-109">Určuje název klíče, který se má odebrat.</span><span class="sxs-lookup"><span data-stu-id="65d6a-109">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="65d6a-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="65d6a-110">Parent element</span></span>

|     | <span data-ttu-id="65d6a-111">Description</span><span class="sxs-lookup"><span data-stu-id="65d6a-111">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="65d6a-112">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="65d6a-112">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="65d6a-113">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="65d6a-113">Child elements</span></span>

<span data-ttu-id="65d6a-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="65d6a-114">None</span></span>

## <a name="example"></a><span data-ttu-id="65d6a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="65d6a-115">Example</span></span>

<span data-ttu-id="65d6a-116">Následující příklad ukazuje, jak odebrat vlastní nastavení konfigurace pro `ApplicationName` :</span><span class="sxs-lookup"><span data-stu-id="65d6a-116">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="65d6a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="65d6a-117">See also</span></span>

- [<span data-ttu-id="65d6a-118">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="65d6a-118">Configuration file schema for the .NET Framework</span></span>](../index.md)
