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
ms.openlocfilehash: fc43a9c32ba33629b6e89120cf57f6d212ab3a56
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441658"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="c0f4e-102">Schéma konfiguračních oddílů</span><span class="sxs-lookup"><span data-stu-id="c0f4e-102">Configuration sections schema</span></span>

<span data-ttu-id="c0f4e-103">Schéma konfiguračních oddílů obsahuje prvky, které definují vlastní nastavení v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="c0f4e-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="c0f4e-104">Obecné informace o konfiguračních souborech a schématech najdete v tématu [Schéma konfiguračního souboru pro .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="c0f4e-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="c0f4e-105">Popis</span><span class="sxs-lookup"><span data-stu-id="c0f4e-105">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="c0f4e-106">Obsahuje konfigurační oddíl a deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c0f4e-106">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="c0f4e-107">**\<section>** pro **\<configSections>** a**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="c0f4e-107">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="c0f4e-108">Obsahuje deklaraci konfiguračního oddílu.</span><span class="sxs-lookup"><span data-stu-id="c0f4e-108">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="c0f4e-109">**\<sectionGroup>** for**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="c0f4e-109">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="c0f4e-110">Definuje obor názvů pro konfigurační oddíly.</span><span class="sxs-lookup"><span data-stu-id="c0f4e-110">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="c0f4e-111">Neimplementované elementy</span><span class="sxs-lookup"><span data-stu-id="c0f4e-111">Unimplemented elements</span></span>

<span data-ttu-id="c0f4e-112">Následující prvky nemají žádný vliv a neměly by se používat:</span><span class="sxs-lookup"><span data-stu-id="c0f4e-112">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**
