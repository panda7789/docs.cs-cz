---
title: AssemblyAttributesGoHere Class (System.Runtime.CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
ms.openlocfilehash: 99d7d2bbbb0586db34b5cb7a785b0448a20ab5bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446638"
---
# <a name="assemblyattributesgohere-class"></a><span data-ttu-id="0a27b-102">AssemblyAttributesGoHere Class</span><span class="sxs-lookup"><span data-stu-id="0a27b-102">AssemblyAttributesGoHere Class</span></span>

<span data-ttu-id="0a27b-103">Used by ALink as a placeholder to store information about custom attributes.</span><span class="sxs-lookup"><span data-stu-id="0a27b-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a27b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a27b-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a><span data-ttu-id="0a27b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a27b-105">Remarks</span></span>

<span data-ttu-id="0a27b-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span><span class="sxs-lookup"><span data-stu-id="0a27b-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="0a27b-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span><span class="sxs-lookup"><span data-stu-id="0a27b-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="0a27b-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span><span class="sxs-lookup"><span data-stu-id="0a27b-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="0a27b-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span><span class="sxs-lookup"><span data-stu-id="0a27b-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>

<span data-ttu-id="0a27b-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span><span class="sxs-lookup"><span data-stu-id="0a27b-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a27b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a27b-111">Requirements</span></span>

<span data-ttu-id="0a27b-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="0a27b-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="0a27b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a27b-113">See also</span></span>

- [<span data-ttu-id="0a27b-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="0a27b-114">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="0a27b-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="0a27b-115">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="0a27b-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="0a27b-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
