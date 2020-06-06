---
title: <clear> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 266d32ccb8b322f0472e0f552f9c0fc877c9a78e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214817"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="97657-102">\<clear> – element pro \<appSettings></span><span class="sxs-lookup"><span data-stu-id="97657-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="97657-103">Vymaže vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="97657-103">Clears custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="97657-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97657-104">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="97657-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="97657-105">Attributes</span></span>

<span data-ttu-id="97657-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="97657-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="97657-107">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="97657-107">Parent element</span></span>

|     | <span data-ttu-id="97657-108">Description</span><span class="sxs-lookup"><span data-stu-id="97657-108">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="97657-109">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="97657-109">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="97657-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="97657-110">Child elements</span></span>

<span data-ttu-id="97657-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="97657-111">None</span></span>

## <a name="example"></a><span data-ttu-id="97657-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="97657-112">Example</span></span>

<span data-ttu-id="97657-113">Následující příklad ukazuje, jak vymazat vlastní nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="97657-113">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="97657-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="97657-114">See also</span></span>

- [<span data-ttu-id="97657-115">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="97657-115">Configuration file schema for the .NET Framework</span></span>](../index.md)
