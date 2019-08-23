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
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921248"
---
# <a name="configuration-element"></a><span data-ttu-id="373e8-102">\<element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="373e8-102">\<configuration> element</span></span>

<span data-ttu-id="373e8-103">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="373e8-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="373e8-104">**\<> Konfigurace**</span><span class="sxs-lookup"><span data-stu-id="373e8-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="373e8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="373e8-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="373e8-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="373e8-106">Attributes</span></span>

<span data-ttu-id="373e8-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="373e8-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="373e8-108">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="373e8-108">Parent element</span></span>

<span data-ttu-id="373e8-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="373e8-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="373e8-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="373e8-110">Child elements</span></span>

|     | <span data-ttu-id="373e8-111">Popis</span><span class="sxs-lookup"><span data-stu-id="373e8-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="373e8-112"> **\<assemblyBinding >** </span><span class="sxs-lookup"><span data-stu-id="373e8-112">**\<assemblyBinding>**</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="373e8-113">Určuje zásadu vazby sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="373e8-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="373e8-114">schéma nastavení **> po spuštění \<** </span><span class="sxs-lookup"><span data-stu-id="373e8-114">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="373e8-115">Všechny elementy ve schématu nastavení spouštění.</span><span class="sxs-lookup"><span data-stu-id="373e8-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="373e8-116">schéma nastavení **> modulu runtime \<** </span><span class="sxs-lookup"><span data-stu-id="373e8-116">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="373e8-117">Všechny elementy ve schématu nastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="373e8-117">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="373e8-118">[**System. Runtime. Vzdálená > Nastavení schématu \<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="373e8-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="373e8-119">Všechny elementy ve schématu nastavení vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="373e8-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="373e8-120">schéma nastavení **> systému .NET \<** </span><span class="sxs-lookup"><span data-stu-id="373e8-120">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="373e8-121">Všechny elementy ve schématu nastavení sítě.</span><span class="sxs-lookup"><span data-stu-id="373e8-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="373e8-122">schéma nastavení > cryptographySettings  **\<** </span><span class="sxs-lookup"><span data-stu-id="373e8-122">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="373e8-123">Všechny elementy ve schématu nastavení kryptografie.</span><span class="sxs-lookup"><span data-stu-id="373e8-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="373e8-124">schéma oddílů > Konfigurace  **\<** </span><span class="sxs-lookup"><span data-stu-id="373e8-124">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="373e8-125">Všechny elementy ve schématu nastavení konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="373e8-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="373e8-126">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="373e8-126">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="373e8-127">Všechny prvky ve schématu nastavení trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="373e8-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="373e8-128">[Schéma nastavení konfigurace ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="373e8-128">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="373e8-129">Všechny prvky ve schématu konfigurace ASP.NET, které zahrnuje prvky pro konfiguraci webů a aplikací ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="373e8-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="373e8-130">Používá se v souborech *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="373e8-130">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="373e8-131">[schéma nastavení > služeb pro WebServices  **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="373e8-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="373e8-132">Všechny prvky ve schématu nastavení webových služeb.</span><span class="sxs-lookup"><span data-stu-id="373e8-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="373e8-133">Schéma nastavení webu</span><span class="sxs-lookup"><span data-stu-id="373e8-133">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="373e8-134">Všechny prvky ve schématu nastavení webu, které obsahují prvky pro konfiguraci způsobu, jakým ASP.NET pracuje s hostitelskou aplikací, jako je služba IIS.</span><span class="sxs-lookup"><span data-stu-id="373e8-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="373e8-135">Používá se v souborech *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="373e8-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="373e8-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="373e8-136">Remarks</span></span>

<span data-ttu-id="373e8-137">Každý konfigurační soubor musí obsahovat právě jeden  **\<element konfigurace >** .</span><span class="sxs-lookup"><span data-stu-id="373e8-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="373e8-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="373e8-138">See also</span></span>

- [<span data-ttu-id="373e8-139">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="373e8-139">Configuration file schema for the .NET Framework</span></span>](index.md)
