---
title: <clear> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d4d96143dbd1db440de2247a7dc2f0c66f20403
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301302"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="71824-102">\<Vymazat > – element pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="71824-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="71824-103">Vymaže nastavení vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="71824-103">Clears custom application settings.</span></span>

<span data-ttu-id="71824-104">[ **\<Konfigurace >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="71824-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="71824-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="71824-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="71824-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Vymazat >**</span><span class="sxs-lookup"><span data-stu-id="71824-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="71824-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71824-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="71824-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="71824-108">Attributes</span></span>

<span data-ttu-id="71824-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="71824-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="71824-110">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="71824-110">Parent element</span></span>

|     | <span data-ttu-id="71824-111">Popis</span><span class="sxs-lookup"><span data-stu-id="71824-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="71824-112"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="71824-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="71824-113">Obsahuje vlastní nastavení aplikace, jako je například cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací konfigurace vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="71824-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="71824-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="71824-114">Child elements</span></span>

<span data-ttu-id="71824-115">Žádný</span><span class="sxs-lookup"><span data-stu-id="71824-115">None</span></span>

## <a name="example"></a><span data-ttu-id="71824-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="71824-116">Example</span></span>

<span data-ttu-id="71824-117">Následující příklad ukazuje, jak vymazat nastavení vlastní konfigurace:</span><span class="sxs-lookup"><span data-stu-id="71824-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="71824-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71824-118">See also</span></span>

- [<span data-ttu-id="71824-119">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="71824-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
