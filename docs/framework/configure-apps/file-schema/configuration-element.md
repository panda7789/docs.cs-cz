---
title: <configuration> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 9a7b25c74763c020c0e19c3f6099db9001acf773
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705412"
---
# <a name="configuration-element"></a><span data-ttu-id="054c8-102">\<Konfigurace > – element</span><span class="sxs-lookup"><span data-stu-id="054c8-102">\<configuration> element</span></span>

<span data-ttu-id="054c8-103">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="054c8-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="054c8-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="054c8-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="054c8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="054c8-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="054c8-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="054c8-106">Attributes</span></span>

<span data-ttu-id="054c8-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="054c8-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="054c8-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="054c8-108">Parent element</span></span>

<span data-ttu-id="054c8-109">Žádný</span><span class="sxs-lookup"><span data-stu-id="054c8-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="054c8-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="054c8-110">Child elements</span></span>

|     | <span data-ttu-id="054c8-111">Popis</span><span class="sxs-lookup"><span data-stu-id="054c8-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="054c8-112">**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="054c8-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="054c8-113">Určuje zásady vazeb sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="054c8-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="054c8-114">**\<Po spuštění >** schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="054c8-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="054c8-115">Všechny elementy ve schématu nastavení spuštění.</span><span class="sxs-lookup"><span data-stu-id="054c8-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="054c8-116">**\<modul runtime >** schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="054c8-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="054c8-117">Všechny prvky v schéma nastavení běhového prostředí.</span><span class="sxs-lookup"><span data-stu-id="054c8-117">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="054c8-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="054c8-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="054c8-119">Všechny elementy ve schématu nastavení vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="054c8-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="054c8-120">**\<system.Net>** Settings Schema</span><span class="sxs-lookup"><span data-stu-id="054c8-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="054c8-121">Všechny elementy ve schématu nastavení sítě.</span><span class="sxs-lookup"><span data-stu-id="054c8-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="054c8-122">**\<cryptographySettings – >** schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="054c8-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="054c8-123">Všechny elementy ve schématu kryptografických nastavení.</span><span class="sxs-lookup"><span data-stu-id="054c8-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="054c8-124">**\<Konfigurace >** schéma oddílů</span><span class="sxs-lookup"><span data-stu-id="054c8-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="054c8-125">Všechny elementy ve schématu oddílu nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="054c8-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="054c8-126">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="054c8-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="054c8-127">Všechny elementy ve schématu nastavení trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="054c8-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="054c8-128">[Schéma konfigurace nastavení ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="054c8-128">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="054c8-129">Všechny elementy ve schématu konfigurace technologie ASP.NET, které zahrnuje prvky pro konfiguraci technologie ASP.NET webové stránky a aplikace.</span><span class="sxs-lookup"><span data-stu-id="054c8-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="054c8-130">Použít v *Web.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="054c8-130">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="054c8-131">[**\<webové služby >** schéma nastavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="054c8-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="054c8-132">Všechny elementy ve schématu nastavení webových služeb.</span><span class="sxs-lookup"><span data-stu-id="054c8-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="054c8-133">Schéma nastavení webu</span><span class="sxs-lookup"><span data-stu-id="054c8-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="054c8-134">Všechny elementy ve schématu nastavení webu, který obsahuje prvky pro konfiguraci spolupráce rozhraní ASP.NET s hostitelskou aplikací, například službou IIS.</span><span class="sxs-lookup"><span data-stu-id="054c8-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="054c8-135">Použít v *aspnet.config* soubory.</span><span class="sxs-lookup"><span data-stu-id="054c8-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="054c8-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="054c8-136">Remarks</span></span>

<span data-ttu-id="054c8-137">Každý konfigurační soubor musí obsahovat přesně jeden  **\<konfigurace >** elementu.</span><span class="sxs-lookup"><span data-stu-id="054c8-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="054c8-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="054c8-138">See also</span></span>

- [<span data-ttu-id="054c8-139">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="054c8-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
