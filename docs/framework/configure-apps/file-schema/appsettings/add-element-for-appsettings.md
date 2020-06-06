---
title: <add> – element pro <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: 5c7de79ec626966e71d461dd3865b294a8979db2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214815"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="f277a-102">\<add> – element pro \<appSettings></span><span class="sxs-lookup"><span data-stu-id="f277a-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="f277a-103">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f277a-103">Adds a custom application setting.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="f277a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f277a-104">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="f277a-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="f277a-105">Attributes</span></span>

|           | <span data-ttu-id="f277a-106">Description</span><span class="sxs-lookup"><span data-stu-id="f277a-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f277a-107">**zkrat**</span><span class="sxs-lookup"><span data-stu-id="f277a-107">**key**</span></span>   | <span data-ttu-id="f277a-108">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f277a-108">Required attribute.</span></span><br><br><span data-ttu-id="f277a-109">Určuje název klíče, který chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="f277a-109">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="f277a-110">**osa**</span><span class="sxs-lookup"><span data-stu-id="f277a-110">**value**</span></span> | <span data-ttu-id="f277a-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f277a-111">Required attribute.</span></span><br><br><span data-ttu-id="f277a-112">Určuje hodnotu klíče, který se má přidat.</span><span class="sxs-lookup"><span data-stu-id="f277a-112">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f277a-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="f277a-113">Parent element</span></span>

|     | <span data-ttu-id="f277a-114">Description</span><span class="sxs-lookup"><span data-stu-id="f277a-114">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="f277a-115">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f277a-115">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f277a-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="f277a-116">Child elements</span></span>

<span data-ttu-id="f277a-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="f277a-117">None</span></span>

## <a name="example"></a><span data-ttu-id="f277a-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="f277a-118">Example</span></span>

<span data-ttu-id="f277a-119">Následující příklad ukazuje, jak přidat vlastní nastavení konfigurace pro název aplikace:</span><span class="sxs-lookup"><span data-stu-id="f277a-119">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="f277a-120">Následující příklad používá `<add>` element k definování dvou nastavení kompatibility v aplikaci ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="f277a-120">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="f277a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f277a-121">See also</span></span>

- [<span data-ttu-id="f277a-122">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f277a-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
