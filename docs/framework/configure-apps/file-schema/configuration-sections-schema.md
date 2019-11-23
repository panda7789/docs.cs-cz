---
title: Schéma konfiguračních oddílů
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a17d30af9d7abc3eea6b87d5e8768ac49a7c05ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118933"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="46c8b-102">Schéma konfiguračních oddílů</span><span class="sxs-lookup"><span data-stu-id="46c8b-102">Configuration sections schema</span></span>

<span data-ttu-id="46c8b-103">Schéma konfiguračních oddílů obsahuje prvky, které definují vlastní nastavení v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="46c8b-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="46c8b-104">Obecné informace o konfiguračních souborech a schématech najdete v tématu [Schéma konfiguračního souboru pro .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="46c8b-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="46c8b-105">[**konfigurační >\<** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="46c8b-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="46c8b-106">[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="46c8b-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="46c8b-107">[ **\<vymazat >** ](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="46c8b-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="46c8b-108">[ **\<remove>** ](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="46c8b-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="46c8b-109">[**oddíl\<>** ](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="46c8b-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="46c8b-110"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="46c8b-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="46c8b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="46c8b-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="46c8b-112"> **\<vymazat >** pro **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="46c8b-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="46c8b-113">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="46c8b-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="46c8b-114"> **\<vymazat >** </span><span class="sxs-lookup"><span data-stu-id="46c8b-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="46c8b-115">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="46c8b-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="46c8b-116"> **\<configSections>** </span><span class="sxs-lookup"><span data-stu-id="46c8b-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="46c8b-117">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46c8b-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="46c8b-118"> **\<odebrat >** pro **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="46c8b-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="46c8b-119">Odebere předdefinovanou sekci nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="46c8b-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="46c8b-120"> **\<oddíl >** pro **\<configSections >** a **\<oddílů** ></span><span class="sxs-lookup"><span data-stu-id="46c8b-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="46c8b-121">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="46c8b-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="46c8b-122"> **> oddílu\<** pro **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="46c8b-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="46c8b-123">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="46c8b-123">Defines a namespace for configuration sections.</span></span> |
