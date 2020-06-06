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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155476"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="1de34-102">\<assemblyBinding> – element pro \<configuration></span><span class="sxs-lookup"><span data-stu-id="1de34-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="1de34-103">Určuje zásadu vazby sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1de34-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="1de34-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="1de34-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1de34-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1de34-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="1de34-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="1de34-106">Attribute</span></span>

|           | <span data-ttu-id="1de34-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1de34-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="1de34-108">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="1de34-108">**xmlns**</span></span> | <span data-ttu-id="1de34-109">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="1de34-109">Required attribute.</span></span><br><br><span data-ttu-id="1de34-110">Určuje obor názvů XML vyžadovaný pro vazbu sestavení.</span><span class="sxs-lookup"><span data-stu-id="1de34-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="1de34-111">Jako hodnotu použijte řetězec "urn: schemas-microsoft-com: asm. v1".</span><span class="sxs-lookup"><span data-stu-id="1de34-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="1de34-112">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="1de34-112">Parent element</span></span>

|     | <span data-ttu-id="1de34-113">Description</span><span class="sxs-lookup"><span data-stu-id="1de34-113">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="1de34-114">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1de34-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="1de34-115">Podřízený element</span><span class="sxs-lookup"><span data-stu-id="1de34-115">Child element</span></span>

|     | <span data-ttu-id="1de34-116">Description</span><span class="sxs-lookup"><span data-stu-id="1de34-116">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="1de34-117">Určuje konfigurační soubor, který se má zahrnout.</span><span class="sxs-lookup"><span data-stu-id="1de34-117">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1de34-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1de34-118">Remarks</span></span>

<span data-ttu-id="1de34-119">[**\<linkedConfiguration>**](linkedconfiguration-element.md)Prvek zjednodušuje správu sestavení komponent tím, že umožňuje souborům konfigurace aplikace zahrnout konfigurační soubory sestavení do dobře známých umístění, nikoli duplikovat nastavení konfigurace sestavení.</span><span class="sxs-lookup"><span data-stu-id="1de34-119">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="1de34-120">**\<linkedConfiguration>** Element není podporován pro aplikace s manifesty vedle sebe v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1de34-120">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="1de34-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="1de34-121">Example</span></span>

<span data-ttu-id="1de34-122">Následující příklad ukazuje, jak zahrnout konfigurační soubor na místní pevný disk:</span><span class="sxs-lookup"><span data-stu-id="1de34-122">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1de34-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1de34-123">See also</span></span>

- [<span data-ttu-id="1de34-124">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1de34-124">Configuration file schema for the .NET Framework</span></span>](index.md)
