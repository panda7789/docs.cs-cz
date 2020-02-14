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
ms.openlocfilehash: b97fea90be301e791bc4109142e6a8b8e1dedaa1
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214768"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="d5a44-102">Schéma konfiguračních oddílů</span><span class="sxs-lookup"><span data-stu-id="d5a44-102">Configuration sections schema</span></span>

<span data-ttu-id="d5a44-103">Schéma konfiguračních oddílů obsahuje prvky, které definují vlastní nastavení v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="d5a44-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="d5a44-104">Obecné informace o konfiguračních souborech a schématech najdete v tématu [Schéma konfiguračního souboru pro .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="d5a44-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="d5a44-105">[**konfigurační >\<** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d5a44-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="d5a44-106">[ **>\<configSections**](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d5a44-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="d5a44-107">[ **\<vymazat >** ](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="d5a44-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="d5a44-108">[ **\<odebrat >** ](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="d5a44-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="d5a44-109">[**oddíl\<>** ](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="d5a44-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="d5a44-110"> **> \<sectionGroup**</span><span class="sxs-lookup"><span data-stu-id="d5a44-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="d5a44-111">Popis</span><span class="sxs-lookup"><span data-stu-id="d5a44-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d5a44-112"> **\<vymazat >** pro **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="d5a44-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="d5a44-113">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="d5a44-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="d5a44-114"> **\<vymazat >** </span><span class="sxs-lookup"><span data-stu-id="d5a44-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="d5a44-115">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="d5a44-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="d5a44-116"> **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="d5a44-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="d5a44-117">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d5a44-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="d5a44-118"> **\<odebrat >** pro **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="d5a44-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="d5a44-119">Odebere předdefinovanou sekci nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="d5a44-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="d5a44-120"> **\<oddíl >** pro **\<configSections >** a **\<oddílů** ></span><span class="sxs-lookup"><span data-stu-id="d5a44-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="d5a44-121">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="d5a44-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="d5a44-122"> **> oddílu\<** pro **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="d5a44-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="d5a44-123">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="d5a44-123">Defines a namespace for configuration sections.</span></span> |
