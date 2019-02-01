---
title: <assemblyBinding> – element pro element <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: f5992a6085c32d37f56319cf8b2c361542c441e7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257326"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="3efe6-102">\<assemblybinding – > – element pro \<configuration ></span><span class="sxs-lookup"><span data-stu-id="3efe6-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="3efe6-103">Určuje zásady vazeb sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3efe6-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="3efe6-104">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3efe6-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="3efe6-105">&nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="3efe6-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3efe6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3efe6-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="3efe6-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="3efe6-107">Attribute</span></span>

|           | <span data-ttu-id="3efe6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3efe6-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="3efe6-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="3efe6-109">**xmlns**</span></span> | <span data-ttu-id="3efe6-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3efe6-110">Required attribute.</span></span><br><br><span data-ttu-id="3efe6-111">Určuje obor názvů XML, vyžaduje se pro vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="3efe6-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="3efe6-112">Použijte řetězec "urn: schémata-microsoft-com:asm.v1" jako hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3efe6-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="3efe6-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="3efe6-113">Parent element</span></span>

|     | <span data-ttu-id="3efe6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3efe6-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3efe6-115">**\<Konfigurace >**</span><span class="sxs-lookup"><span data-stu-id="3efe6-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="3efe6-116">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3efe6-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="3efe6-117">Podřízený element.</span><span class="sxs-lookup"><span data-stu-id="3efe6-117">Child element</span></span>

|     | <span data-ttu-id="3efe6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="3efe6-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3efe6-119">**\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="3efe6-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="3efe6-120">Určuje konfigurační soubor, který chcete zahrnout.</span><span class="sxs-lookup"><span data-stu-id="3efe6-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3efe6-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3efe6-121">Remarks</span></span>

<span data-ttu-id="3efe6-122">[  **\<Linkedconfiguration – >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element zjednodušuje správu sestavení komponent tím, že konfigurační soubory v konfiguračních souborech aplikace, které chcete zahrnout sestavení dobře známé umístění, spíše než duplikace nastavení konfigurace sestavení.</span><span class="sxs-lookup"><span data-stu-id="3efe6-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="3efe6-123">**\<Linkedconfiguration – >** element není podporován pro aplikace s Windows manifesty vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="3efe6-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="3efe6-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="3efe6-124">Example</span></span>

<span data-ttu-id="3efe6-125">Následující příklad ukazuje, jak zahrnout konfigurační soubor na místním pevném disku:</span><span class="sxs-lookup"><span data-stu-id="3efe6-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3efe6-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3efe6-126">See also</span></span>

- [<span data-ttu-id="3efe6-127">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3efe6-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
