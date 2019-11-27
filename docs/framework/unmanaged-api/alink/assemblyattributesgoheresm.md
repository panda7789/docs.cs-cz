---
title: AssemblyAttributesGoHereSM – třída (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
ms.openlocfilehash: 379ba20ebf675bec71e6e5f5bcfc0dc2fbd1f92c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446607"
---
# <a name="assemblyattributesgoheresm-class"></a><span data-ttu-id="858a0-102">AssemblyAttributesGoHereSM – třída</span><span class="sxs-lookup"><span data-stu-id="858a0-102">AssemblyAttributesGoHereSM Class</span></span>

<span data-ttu-id="858a0-103">Používá se nástrojem ALink jako zástupný symbol pro ukládání informací o vlastních atributech.</span><span class="sxs-lookup"><span data-stu-id="858a0-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="858a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="858a0-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a><span data-ttu-id="858a0-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="858a0-105">Remarks</span></span>

<span data-ttu-id="858a0-106">Odkazy na tento typ mohou být vloženy do netmodule, jejichž zdroje obsahují vlastní atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="858a0-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="858a0-107">Při sestavování manifestu sestavení z jednoho nebo více netmodule, které obsahují odkazy na tyto typy, nástroj ALink používá informace připojené k těmto odkazům k vygenerování skutečných uživatelských atributů.</span><span class="sxs-lookup"><span data-stu-id="858a0-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="858a0-108">V takovém případě tento typ není nikdy vytvořen a odkazy na něj jsou používány pouze jako součást procesu sestavení a v konečném sestavení neslouží k žádnému účelu.</span><span class="sxs-lookup"><span data-stu-id="858a0-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="858a0-109">Odkazy na tento typ označují vlastní atributy, které souvisejí se zabezpečením a vícenásobným použitím.</span><span class="sxs-lookup"><span data-stu-id="858a0-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>

<span data-ttu-id="858a0-110">Tyto typy jsou označeny jako "interní" v rámci .NET Framework a jsou umístěny v oboru názvů <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="858a0-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="858a0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="858a0-111">Requirements</span></span>

<span data-ttu-id="858a0-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="858a0-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="858a0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="858a0-113">See also</span></span>

- [<span data-ttu-id="858a0-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="858a0-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="858a0-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="858a0-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="858a0-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="858a0-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
