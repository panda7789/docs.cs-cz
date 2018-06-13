---
title: '&lt;assemblybinding –&gt; element pro &lt;konfigurace&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6a3358b2d64ade65e641caa203e2e760dcc4be2c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743118"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="61d95-102">\<assemblybinding – > elementu pro \<konfigurace ></span><span class="sxs-lookup"><span data-stu-id="61d95-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="61d95-103">Určuje sestavení vazby zásady na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="61d95-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="61d95-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="61d95-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="61d95-105">&nbsp;&nbsp;**\<assemblybinding – >**</span><span class="sxs-lookup"><span data-stu-id="61d95-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="61d95-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61d95-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="61d95-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="61d95-107">Attribute</span></span>

|           | <span data-ttu-id="61d95-108">Popis</span><span class="sxs-lookup"><span data-stu-id="61d95-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="61d95-109">**atribut xmlns**</span><span class="sxs-lookup"><span data-stu-id="61d95-109">**xmlns**</span></span> | <span data-ttu-id="61d95-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="61d95-110">Required attribute.</span></span><br><br><span data-ttu-id="61d95-111">Určuje obor názvů XML, které jsou potřebné pro sestavení – vazby.</span><span class="sxs-lookup"><span data-stu-id="61d95-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="61d95-112">Použít řetězec "urn: schémata-microsoft-com:asm.v1" jako hodnotu.</span><span class="sxs-lookup"><span data-stu-id="61d95-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="61d95-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="61d95-113">Parent element</span></span>

|     | <span data-ttu-id="61d95-114">Popis</span><span class="sxs-lookup"><span data-stu-id="61d95-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="61d95-115">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="61d95-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="61d95-116">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61d95-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="61d95-117">Podřízený element</span><span class="sxs-lookup"><span data-stu-id="61d95-117">Child element</span></span>

|     | <span data-ttu-id="61d95-118">Popis</span><span class="sxs-lookup"><span data-stu-id="61d95-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="61d95-119">**\<linkedconfiguration – >**</span><span class="sxs-lookup"><span data-stu-id="61d95-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="61d95-120">Určuje konfigurační soubor pro zahrnout.</span><span class="sxs-lookup"><span data-stu-id="61d95-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="61d95-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61d95-121">Remarks</span></span>

<span data-ttu-id="61d95-122">[  **\<Linkedconfiguration – >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element zjednodušuje správu sestavení součástí tím, že konfigurační soubory v konfigurační soubory aplikace zahrnete sestavení dobře známé umístění, a nikoli duplicitní nastavení konfigurace sestavení.</span><span class="sxs-lookup"><span data-stu-id="61d95-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="61d95-123">**\<Linkedconfiguration – >** element není podporován pro aplikace s manifesty Windows vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="61d95-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="61d95-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="61d95-124">Example</span></span>

<span data-ttu-id="61d95-125">Následující příklad ukazuje, jak chcete zahrnout konfigurační soubor na místní pevný disk:</span><span class="sxs-lookup"><span data-stu-id="61d95-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="61d95-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="61d95-126">See also</span></span>

[<span data-ttu-id="61d95-127">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="61d95-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
