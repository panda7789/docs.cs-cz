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
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214817"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="384a1-102">\<Clear > elementu pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="384a1-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="384a1-103">Vymaže vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="384a1-103">Clears custom application settings.</span></span>

<span data-ttu-id="384a1-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="384a1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="384a1-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="384a1-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="384a1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="384a1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="384a1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="384a1-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="384a1-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="384a1-108">Attributes</span></span>

<span data-ttu-id="384a1-109">Žádná</span><span class="sxs-lookup"><span data-stu-id="384a1-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="384a1-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="384a1-110">Parent element</span></span>

|     | <span data-ttu-id="384a1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="384a1-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="384a1-112"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="384a1-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="384a1-113">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="384a1-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="384a1-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="384a1-114">Child elements</span></span>

<span data-ttu-id="384a1-115">Žádná</span><span class="sxs-lookup"><span data-stu-id="384a1-115">None</span></span>

## <a name="example"></a><span data-ttu-id="384a1-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="384a1-116">Example</span></span>

<span data-ttu-id="384a1-117">Následující příklad ukazuje, jak vymazat vlastní nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="384a1-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="384a1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="384a1-118">See also</span></span>

- [<span data-ttu-id="384a1-119">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="384a1-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
