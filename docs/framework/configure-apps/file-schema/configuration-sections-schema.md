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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 120733873a7ea29303fe7f82c4c324d411532897
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921211"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="b35b6-102">Schéma konfiguračních oddílů</span><span class="sxs-lookup"><span data-stu-id="b35b6-102">Configuration sections schema</span></span>

<span data-ttu-id="b35b6-103">Schéma konfiguračních oddílů obsahuje prvky, které definují vlastní nastavení v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="b35b6-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="b35b6-104">Obecné informace o konfiguračních souborech a schématech najdete v tématu [Schéma konfiguračního souboru pro .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="b35b6-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="b35b6-105">[ **\<> Konfigurace**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b35b6-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="b35b6-106">[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="b35b6-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="b35b6-107">[ **\<Vymazat >** ](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="b35b6-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="b35b6-108">[ **\<remove>** ](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="b35b6-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="b35b6-109">[ **\<> oddílu**](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="b35b6-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="b35b6-110"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="b35b6-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="b35b6-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b35b6-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b35b6-112">Vymazat > pro  **\<**  **configSections>\<** </span><span class="sxs-lookup"><span data-stu-id="b35b6-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="b35b6-113">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="b35b6-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="b35b6-114"> **\<Vymazat >** </span><span class="sxs-lookup"><span data-stu-id="b35b6-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="b35b6-115">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="b35b6-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="b35b6-116"> **\<configSections>** </span><span class="sxs-lookup"><span data-stu-id="b35b6-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="b35b6-117">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b35b6-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="b35b6-118">odebrání > pro  **\<**  **configSections>\<** </span><span class="sxs-lookup"><span data-stu-id="b35b6-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="b35b6-119">Odebere předdefinovanou sekci nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="b35b6-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="b35b6-120">oddíl > **pro >configSections\<** a  **sectionGroup\<>**  **\<** </span><span class="sxs-lookup"><span data-stu-id="b35b6-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="b35b6-121">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="b35b6-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="b35b6-122">sekce > pro  **\<**  **configSections>\<** </span><span class="sxs-lookup"><span data-stu-id="b35b6-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="b35b6-123">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="b35b6-123">Defines a namespace for configuration sections.</span></span> |
