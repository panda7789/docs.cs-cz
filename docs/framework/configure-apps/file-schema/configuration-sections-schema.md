---
title: "Schéma konfigurace oddílů"
ms.date: 05/02/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c668cf3d2f2c0bcffda185cea01edfb9e55c6d6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="20673-102">Schéma konfigurace oddílů</span><span class="sxs-lookup"><span data-stu-id="20673-102">Configuration sections schema</span></span>

<span data-ttu-id="20673-103">Schéma konfigurace oddílů obsahuje prvky, které definují vlastní nastavení v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="20673-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="20673-104">Obecné informace o konfiguračních souborů a schémat, najdete v části [schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="20673-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="20673-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="20673-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="20673-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="20673-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="20673-107">[**\<Clear >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="20673-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="20673-108">[**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="20673-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="20673-109">[**\<část >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="20673-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="20673-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="20673-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="20673-111">Popis</span><span class="sxs-lookup"><span data-stu-id="20673-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="20673-112">**\<Clear >** pro  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="20673-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="20673-113">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="20673-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="20673-114">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="20673-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="20673-115">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="20673-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="20673-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="20673-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="20673-117">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="20673-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="20673-118">**\<Odebrat >** pro  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="20673-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="20673-119">Odstraní předdefinované části nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="20673-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="20673-120">**\<část >** pro  **\<configSections >** a  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="20673-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="20673-121">Obsahuje deklaraci konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="20673-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="20673-122">**\<sectionGroup >** pro  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="20673-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="20673-123">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="20673-123">Defines a namespace for configuration sections.</span></span> |
