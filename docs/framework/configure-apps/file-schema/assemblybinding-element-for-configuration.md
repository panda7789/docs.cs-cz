---
title: <assemblyBinding> – element pro <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155476"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="38e02-102">\<assemblyBinding> \<element pro konfigurační></span><span class="sxs-lookup"><span data-stu-id="38e02-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="38e02-103">Určuje zásadu vazby sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="38e02-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="38e02-104">konfigurace &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) **>\<vazby sestavení**</span><span class="sxs-lookup"><span data-stu-id="38e02-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="38e02-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38e02-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="38e02-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="38e02-106">Attribute</span></span>

|           | <span data-ttu-id="38e02-107">Popis</span><span class="sxs-lookup"><span data-stu-id="38e02-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="38e02-108">**Xmlns**</span><span class="sxs-lookup"><span data-stu-id="38e02-108">**xmlns**</span></span> | <span data-ttu-id="38e02-109">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="38e02-109">Required attribute.</span></span><br><br><span data-ttu-id="38e02-110">Určuje obor názvů XML požadovaný pro vazbu sestavení.</span><span class="sxs-lookup"><span data-stu-id="38e02-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="38e02-111">Jako hodnotu použijte řetězec "urn:schemas-microsoft-com:asm.v1".</span><span class="sxs-lookup"><span data-stu-id="38e02-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="38e02-112">Nadřazený prvek</span><span class="sxs-lookup"><span data-stu-id="38e02-112">Parent element</span></span>

|     | <span data-ttu-id="38e02-113">Popis</span><span class="sxs-lookup"><span data-stu-id="38e02-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="38e02-114">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="38e02-114">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="38e02-115">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38e02-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="38e02-116">Podřízený prvek</span><span class="sxs-lookup"><span data-stu-id="38e02-116">Child element</span></span>

|     | <span data-ttu-id="38e02-117">Popis</span><span class="sxs-lookup"><span data-stu-id="38e02-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="38e02-118">**\<linkedKonfigurační>**</span><span class="sxs-lookup"><span data-stu-id="38e02-118">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="38e02-119">Určuje konfigurační soubor, který má být zahrnut.</span><span class="sxs-lookup"><span data-stu-id="38e02-119">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="38e02-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38e02-120">Remarks</span></span>

<span data-ttu-id="38e02-121">Prvek [\*\* \<LinkedConfiguration>\*\*](linkedconfiguration-element.md) zjednodušuje správu sestav součástí tím, že umožňuje konfiguračním souborům aplikací zahrnout konfigurační soubory sestavení do známých umístění, nikoli duplikovat nastavení konfigurace sestavení.</span><span class="sxs-lookup"><span data-stu-id="38e02-121">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="38e02-122">Prvek \*\* \<linkedConfiguration>\*\* není podporován pro aplikace s windows side-by-side manifesty.</span><span class="sxs-lookup"><span data-stu-id="38e02-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="38e02-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="38e02-123">Example</span></span>

<span data-ttu-id="38e02-124">Následující příklad ukazuje, jak zahrnout konfigurační soubor na místní pevný disk:</span><span class="sxs-lookup"><span data-stu-id="38e02-124">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="38e02-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="38e02-125">See also</span></span>

- [<span data-ttu-id="38e02-126">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38e02-126">Configuration file schema for the .NET Framework</span></span>](index.md)
