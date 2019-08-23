---
title: <assemblyBinding> – element pro <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921276"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="459bc-102">\<assemblyBinding element > pro \<konfigurační ></span><span class="sxs-lookup"><span data-stu-id="459bc-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="459bc-103">Určuje zásadu vazby sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="459bc-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="459bc-104">[ **\<> Konfigurace**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="459bc-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="459bc-105">&nbsp;&nbsp; **\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="459bc-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="459bc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="459bc-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="459bc-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="459bc-107">Attribute</span></span>

|           | <span data-ttu-id="459bc-108">Popis</span><span class="sxs-lookup"><span data-stu-id="459bc-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="459bc-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="459bc-109">**xmlns**</span></span> | <span data-ttu-id="459bc-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="459bc-110">Required attribute.</span></span><br><br><span data-ttu-id="459bc-111">Určuje obor názvů XML vyžadovaný pro vazbu sestavení.</span><span class="sxs-lookup"><span data-stu-id="459bc-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="459bc-112">Jako hodnotu použijte řetězec "urn: schemas-microsoft-com: asm. v1".</span><span class="sxs-lookup"><span data-stu-id="459bc-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="459bc-113">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="459bc-113">Parent element</span></span>

|     | <span data-ttu-id="459bc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="459bc-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="459bc-115"> **\<> Konfigurace**</span><span class="sxs-lookup"><span data-stu-id="459bc-115">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="459bc-116">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="459bc-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="459bc-117">Podřízený element</span><span class="sxs-lookup"><span data-stu-id="459bc-117">Child element</span></span>

|     | <span data-ttu-id="459bc-118">Popis</span><span class="sxs-lookup"><span data-stu-id="459bc-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="459bc-119"> **\<linkedConfiguration>** </span><span class="sxs-lookup"><span data-stu-id="459bc-119">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="459bc-120">Určuje konfigurační soubor, který se má zahrnout.</span><span class="sxs-lookup"><span data-stu-id="459bc-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="459bc-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="459bc-121">Remarks</span></span>

<span data-ttu-id="459bc-122">Element [**linkedConfiguration > zjednodušuje správu sestavení komponent tím, že umožňuje aplikačním konfiguračním souborům zahrnout konfigurační soubory sestavení do známých umístění místo duplikace sestavení. \<** ](linkedconfiguration-element.md) nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="459bc-122">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="459bc-123">**\<Linkedconfiguration – >** element není podporován pro aplikace s Windows manifesty vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="459bc-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="459bc-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="459bc-124">Example</span></span>

<span data-ttu-id="459bc-125">Následující příklad ukazuje, jak zahrnout konfigurační soubor na místní pevný disk:</span><span class="sxs-lookup"><span data-stu-id="459bc-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="459bc-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="459bc-126">See also</span></span>

- [<span data-ttu-id="459bc-127">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="459bc-127">Configuration file schema for the .NET Framework</span></span>](index.md)
