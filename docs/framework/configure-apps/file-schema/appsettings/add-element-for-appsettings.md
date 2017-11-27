---
title: "&lt;Přidat&gt; element pro &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b00af6f7d735d5db8fd746205ba225253cad133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="3f776-102">\<Přidat > elementu pro \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="3f776-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="3f776-103">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="3f776-103">Adds a custom application setting.</span></span>

<span data-ttu-id="3f776-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3f776-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="3f776-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3f776-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="3f776-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="3f776-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3f776-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f776-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="3f776-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="3f776-108">Attributes</span></span>

|           | <span data-ttu-id="3f776-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3f776-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="3f776-110">**klíč**</span><span class="sxs-lookup"><span data-stu-id="3f776-110">**key**</span></span>   | <span data-ttu-id="3f776-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3f776-111">Required attribute.</span></span><br><br><span data-ttu-id="3f776-112">Určuje název klíč k přidání.</span><span class="sxs-lookup"><span data-stu-id="3f776-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="3f776-113">**Hodnota**</span><span class="sxs-lookup"><span data-stu-id="3f776-113">**value**</span></span> | <span data-ttu-id="3f776-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3f776-114">Required attribute.</span></span><br><br><span data-ttu-id="3f776-115">Určuje hodnotu klíč k přidání.</span><span class="sxs-lookup"><span data-stu-id="3f776-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="3f776-116">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="3f776-116">Parent element</span></span>

|     | <span data-ttu-id="3f776-117">Popis</span><span class="sxs-lookup"><span data-stu-id="3f776-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3f776-118">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="3f776-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="3f776-119">Obsahuje nastavení vlastní aplikace, například cesty k souborům, adresy URL XML webových služeb nebo všechny ostatní informace vlastní konfigurace pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3f776-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3f776-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="3f776-120">Child elements</span></span>

<span data-ttu-id="3f776-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="3f776-121">None</span></span>

## <a name="example"></a><span data-ttu-id="3f776-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f776-122">Example</span></span>

<span data-ttu-id="3f776-123">Následující příklad ukazuje, jak přidat vlastní konfigurace nastavení pro název aplikace:</span><span class="sxs-lookup"><span data-stu-id="3f776-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="3f776-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f776-124">See also</span></span>

[<span data-ttu-id="3f776-125">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3f776-125">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
