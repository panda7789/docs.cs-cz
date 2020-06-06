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
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921248"
---
# <a name="configuration-element"></a><span data-ttu-id="ce4bc-102">\<configuration> – element</span><span class="sxs-lookup"><span data-stu-id="ce4bc-102">\<configuration> element</span></span>

<span data-ttu-id="ce4bc-103">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="ce4bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce4bc-104">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="ce4bc-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="ce4bc-105">Attributes</span></span>

<span data-ttu-id="ce4bc-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="ce4bc-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="ce4bc-107">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="ce4bc-107">Parent element</span></span>

<span data-ttu-id="ce4bc-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="ce4bc-108">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="ce4bc-109">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ce4bc-109">Child elements</span></span>

|     | <span data-ttu-id="ce4bc-110">Description</span><span class="sxs-lookup"><span data-stu-id="ce4bc-110">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="ce4bc-111">Určuje zásadu vazby sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-111">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="ce4bc-112">**\<startup>** Schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="ce4bc-112">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="ce4bc-113">Všechny elementy ve schématu nastavení spouštění.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-113">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="ce4bc-114">**\<runtime>** Schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="ce4bc-114">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="ce4bc-115">Všechny elementy ve schématu nastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-115">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="ce4bc-116">[**\<system.runtime.remoting>** Schéma nastavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce4bc-116">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="ce4bc-117">Všechny elementy ve schématu nastavení vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-117">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="ce4bc-118">**\<system.Net>** Schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="ce4bc-118">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="ce4bc-119">Všechny elementy ve schématu nastavení sítě.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-119">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="ce4bc-120">**\<cryptographySettings>** Schéma nastavení</span><span class="sxs-lookup"><span data-stu-id="ce4bc-120">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="ce4bc-121">Všechny elementy ve schématu nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-121">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="ce4bc-122">**\<configuration>** Schéma oddílů</span><span class="sxs-lookup"><span data-stu-id="ce4bc-122">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="ce4bc-123">Všechny elementy ve schématu nastavení konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-123">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="ce4bc-124">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="ce4bc-124">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="ce4bc-125">Všechny prvky ve schématu nastavení trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-125">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="ce4bc-126">[Schéma nastavení konfigurace ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce4bc-126">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="ce4bc-127">Všechny prvky ve schématu konfigurace ASP.NET, které zahrnuje prvky pro konfiguraci webů a aplikací ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-127">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="ce4bc-128">Používá se v souborech *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="ce4bc-128">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="ce4bc-129">[**\<webServices>** Schéma nastavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce4bc-129">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="ce4bc-130">Všechny prvky ve schématu nastavení webových služeb.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-130">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="ce4bc-131">Schéma nastavení webu</span><span class="sxs-lookup"><span data-stu-id="ce4bc-131">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="ce4bc-132">Všechny prvky ve schématu nastavení webu, které obsahují prvky pro konfiguraci způsobu, jakým ASP.NET pracuje s hostitelskou aplikací, jako je služba IIS.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-132">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="ce4bc-133">Používá se v souborech *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="ce4bc-133">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ce4bc-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce4bc-134">Remarks</span></span>

<span data-ttu-id="ce4bc-135">Každý konfigurační soubor musí obsahovat přesně jeden **\<configuration>** element.</span><span class="sxs-lookup"><span data-stu-id="ce4bc-135">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce4bc-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce4bc-136">See also</span></span>

- [<span data-ttu-id="ce4bc-137">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce4bc-137">Configuration file schema for the .NET Framework</span></span>](index.md)
