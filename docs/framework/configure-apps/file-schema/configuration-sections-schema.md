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
ms.openlocfilehash: 28f936e6fd7c9e7f6f895396df8e8b8d36ab9139
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155320"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="4ad83-102">Schéma konfiguračních oddílů</span><span class="sxs-lookup"><span data-stu-id="4ad83-102">Configuration sections schema</span></span>

<span data-ttu-id="4ad83-103">Schéma konfiguračních oddílů obsahuje prvky, které definují vlastní nastavení v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="4ad83-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="4ad83-104">Obecné informace o konfiguračních souborech a schématech naleznete [v tématu Schéma konfiguračních souborů pro rozhraní .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="4ad83-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="4ad83-105">[**\<konfigurace>** ](configuration-element.md) 
 
 
 
 
 [\*\* \< \*\*](section-element.md) [\*\*configSections>zrušte zaškrtnutí>odebrání oddílu>>oddíluSkupina \< \*\*](configsections-element-for-configuration.md) [\*\* \<>\*\*](sectiongroup-element-for-configsections.md) [\*\* \< \*\*](clear-element-for-configsections.md) [\*\* \< \*\*](remove-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="4ad83-105">[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<clear>**](clear-element-for-configsections.md)
[**\<remove>**](remove-element-for-configsections.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>

|     | <span data-ttu-id="4ad83-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4ad83-106">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4ad83-107">clear>pro \*\* \<\*\* \*\* \<configSections>\*\*</span><span class="sxs-lookup"><span data-stu-id="4ad83-107">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="4ad83-108">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="4ad83-108">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="4ad83-109">**\<jasné>**</span><span class="sxs-lookup"><span data-stu-id="4ad83-109">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="4ad83-110">Vymaže všechny dříve definované oddíly a skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="4ad83-110">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="4ad83-111">**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="4ad83-111">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="4ad83-112">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4ad83-112">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="4ad83-113">odebrat>pro \*\* \<\*\* \*\* \<configSections>\*\*</span><span class="sxs-lookup"><span data-stu-id="4ad83-113">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="4ad83-114">Odebere předdefinovaný oddíl nebo skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="4ad83-114">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="4ad83-115">>oddílu pro \*\* \<>a\*\* \*\* \<oddílySkupina>\*\* \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="4ad83-115">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="4ad83-116">Obsahuje deklaraci oddílu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4ad83-116">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="4ad83-117">sectionGroup>pro \*\* \<\*\* \*\* \<>konfiguračních oddílů\*\*</span><span class="sxs-lookup"><span data-stu-id="4ad83-117">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="4ad83-118">Definuje obor názvů pro oddíly konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4ad83-118">Defines a namespace for configuration sections.</span></span> |
