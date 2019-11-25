---
title: <clear> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d321f3169344e9aa40d65b1722a533549de5315a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088740"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="aeeb8-102">\<Clear > elementu pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="aeeb8-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="aeeb8-103">Vymaže vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="aeeb8-103">Clears custom application settings.</span></span>

<span data-ttu-id="aeeb8-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aeeb8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aeeb8-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="aeeb8-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="aeeb8-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="aeeb8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="aeeb8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aeeb8-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="aeeb8-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="aeeb8-108">Attributes</span></span>

<span data-ttu-id="aeeb8-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="aeeb8-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="aeeb8-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="aeeb8-110">Parent element</span></span>

|     | <span data-ttu-id="aeeb8-111">Popis</span><span class="sxs-lookup"><span data-stu-id="aeeb8-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="aeeb8-112"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="aeeb8-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="aeeb8-113">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="aeeb8-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="aeeb8-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="aeeb8-114">Child elements</span></span>

<span data-ttu-id="aeeb8-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="aeeb8-115">None</span></span>

## <a name="example"></a><span data-ttu-id="aeeb8-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="aeeb8-116">Example</span></span>

<span data-ttu-id="aeeb8-117">Následující příklad ukazuje, jak vymazat vlastní nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="aeeb8-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="aeeb8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aeeb8-118">See also</span></span>

- [<span data-ttu-id="aeeb8-119">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aeeb8-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
