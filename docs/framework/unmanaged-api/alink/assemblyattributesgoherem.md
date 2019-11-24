---
title: AssemblyAttributesGoHereM Class (System.Runtime.CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
ms.openlocfilehash: 15b9445aa3eabbd14541cfe5481bfb553c8c0347
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446629"
---
# <a name="assemblyattributesgoherem-class"></a><span data-ttu-id="29e03-102">AssemblyAttributesGoHereM Class</span><span class="sxs-lookup"><span data-stu-id="29e03-102">AssemblyAttributesGoHereM Class</span></span>

<span data-ttu-id="29e03-103">Used by ALink as a placeholder to store information about custom attributes.</span><span class="sxs-lookup"><span data-stu-id="29e03-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="29e03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29e03-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereM
```

## <a name="remarks"></a><span data-ttu-id="29e03-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29e03-105">Remarks</span></span>

<span data-ttu-id="29e03-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span><span class="sxs-lookup"><span data-stu-id="29e03-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="29e03-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span><span class="sxs-lookup"><span data-stu-id="29e03-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="29e03-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span><span class="sxs-lookup"><span data-stu-id="29e03-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="29e03-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span><span class="sxs-lookup"><span data-stu-id="29e03-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>

<span data-ttu-id="29e03-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span><span class="sxs-lookup"><span data-stu-id="29e03-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="29e03-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29e03-111">Requirements</span></span>

<span data-ttu-id="29e03-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="29e03-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="29e03-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29e03-113">See also</span></span>

- [<span data-ttu-id="29e03-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="29e03-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="29e03-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="29e03-115">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="29e03-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="29e03-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
