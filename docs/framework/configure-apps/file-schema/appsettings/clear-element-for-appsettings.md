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
ms.openlocfilehash: c3e1c3a3cfd61a9fa8e7abdae9a25ec1bc674492
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119232"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="c0942-102">\<Clear > elementu pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="c0942-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="c0942-103">Vymaže vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0942-103">Clears custom application settings.</span></span>

<span data-ttu-id="c0942-104">[**konfigurační >\<** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c0942-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="c0942-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="c0942-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="c0942-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="c0942-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c0942-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0942-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="c0942-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0942-108">Attributes</span></span>

<span data-ttu-id="c0942-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="c0942-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="c0942-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="c0942-110">Parent element</span></span>

|     | <span data-ttu-id="c0942-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c0942-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c0942-112"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="c0942-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="c0942-113">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0942-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c0942-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c0942-114">Child elements</span></span>

<span data-ttu-id="c0942-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="c0942-115">None</span></span>

## <a name="example"></a><span data-ttu-id="c0942-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0942-116">Example</span></span>

<span data-ttu-id="c0942-117">Následující příklad ukazuje, jak vymazat vlastní nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="c0942-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="c0942-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0942-118">See also</span></span>

- [<span data-ttu-id="c0942-119">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c0942-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
