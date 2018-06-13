---
title: Schéma konfigurace oddílů
ms.date: 05/02/2017
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
ms.openlocfilehash: edd2b2e11b02d69b7bba7c3cc7d8a9a0814e0c51
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743508"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="97043-102">Schéma konfigurace oddílů</span><span class="sxs-lookup"><span data-stu-id="97043-102">Configuration sections schema</span></span>

<span data-ttu-id="97043-103">Schéma konfigurace oddílů obsahuje prvky, které definují vlastní nastavení v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="97043-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="97043-104">Obecné informace o konfiguračních souborů a schémat, najdete v části [schéma konfiguračního souboru pro rozhraní .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="97043-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="97043-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="97043-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="97043-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="97043-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="97043-107">[**\<Clear >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="97043-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="97043-108">[**\<Odebrat >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="97043-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="97043-109">[**\<část >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="97043-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="97043-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="97043-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="97043-111">Popis</span><span class="sxs-lookup"><span data-stu-id="97043-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="97043-112">**\<Clear >** pro  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="97043-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="97043-113">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="97043-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="97043-114">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="97043-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="97043-115">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="97043-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="97043-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="97043-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="97043-117">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="97043-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="97043-118">**\<Odebrat >** pro  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="97043-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="97043-119">Odstraní předdefinované části nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="97043-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="97043-120">**\<část >** pro  **\<configSections >** a  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="97043-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="97043-121">Obsahuje deklaraci konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="97043-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="97043-122">**\<sectionGroup >** pro  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="97043-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="97043-123">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="97043-123">Defines a namespace for configuration sections.</span></span> |
