---
title: '&lt;konfigurace&gt; – element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5146ed8326b12e90d0fe6247b0c4aba3a69dd77
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485778"
---
# <a name="configuration-element"></a><span data-ttu-id="264ca-102">\<Konfigurace > – element</span><span class="sxs-lookup"><span data-stu-id="264ca-102">\<configuration> element</span></span>

<span data-ttu-id="264ca-103">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="264ca-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="264ca-104">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="264ca-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="264ca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="264ca-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="264ca-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="264ca-106">Attributes</span></span>

<span data-ttu-id="264ca-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="264ca-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="264ca-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="264ca-108">Parent element</span></span>

<span data-ttu-id="264ca-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="264ca-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="264ca-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="264ca-110">Child elements</span></span>

|     | <span data-ttu-id="264ca-111">Popis</span><span class="sxs-lookup"><span data-stu-id="264ca-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="264ca-112">**\<assemblybinding – >**</span><span class="sxs-lookup"><span data-stu-id="264ca-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="264ca-113">Určuje zásady vazeb sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="264ca-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="264ca-114">**\<Po spuštění >** schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="264ca-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="264ca-115">Všechny elementy ve schématu nastavení spuštění.</span><span class="sxs-lookup"><span data-stu-id="264ca-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="264ca-116">**\<modul runtime >** schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="264ca-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="264ca-117">Všechny prvky v schéma nastavení běhového prostředí.</span><span class="sxs-lookup"><span data-stu-id="264ca-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="264ca-118">**\<System.Runtime.Remoting >** schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="264ca-118">**\<system.runtime.remoting>** Settings Schema</span></span>](https://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="264ca-119">Všechny elementy ve schématu nastavení vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="264ca-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="264ca-120">**\<system.Net >** schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="264ca-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="264ca-121">Všechny elementy ve schématu nastavení sítě.</span><span class="sxs-lookup"><span data-stu-id="264ca-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="264ca-122">**\<cryptographySettings – >** schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="264ca-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="264ca-123">Všechny elementy ve schématu kryptografických nastavení.</span><span class="sxs-lookup"><span data-stu-id="264ca-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="264ca-124">**\<Konfigurace >** schéma oddílů</span><span class="sxs-lookup"><span data-stu-id="264ca-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="264ca-125">Všechny elementy ve schématu oddílu nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="264ca-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="264ca-126">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="264ca-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="264ca-127">Všechny elementy ve schématu nastavení trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="264ca-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="264ca-128">[Schéma konfigurace nastavení ASP.NET](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="264ca-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="264ca-129">Všechny elementy ve schématu konfigurace technologie ASP.NET, které zahrnuje prvky pro konfiguraci technologie ASP.NET webové stránky a aplikace.</span><span class="sxs-lookup"><span data-stu-id="264ca-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="264ca-130">Použít v *Web.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="264ca-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="264ca-131">**\<webové služby >** schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="264ca-131">**\<webServices>** Settings Schema</span></span>](https://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="264ca-132">Všechny elementy ve schématu nastavení webových služeb.</span><span class="sxs-lookup"><span data-stu-id="264ca-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="264ca-133">Schéma nastavení webu</span><span class="sxs-lookup"><span data-stu-id="264ca-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="264ca-134">Všechny elementy ve schématu nastavení webu, který obsahuje prvky pro konfiguraci spolupráce rozhraní ASP.NET s hostitelskou aplikací, například službou IIS.</span><span class="sxs-lookup"><span data-stu-id="264ca-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="264ca-135">Použít v *aspnet.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="264ca-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="264ca-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="264ca-136">Remarks</span></span>

<span data-ttu-id="264ca-137">Každý konfigurační soubor musí obsahovat přesně jeden  **\<konfigurace >** elementu.</span><span class="sxs-lookup"><span data-stu-id="264ca-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="264ca-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="264ca-138">See also</span></span>

[<span data-ttu-id="264ca-139">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="264ca-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
