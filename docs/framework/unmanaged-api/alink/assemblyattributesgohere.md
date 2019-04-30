---
title: Assemblyattributesgohere – třída (System.Runtime.CompilerServices)
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 571c2f6723e827a1b385f77724c33703ae970ae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775619"
---
# <a name="assemblyattributesgohere-class"></a><span data-ttu-id="769b5-102">Assemblyattributesgohere – třída</span><span class="sxs-lookup"><span data-stu-id="769b5-102">AssemblyAttributesGoHere Class</span></span>

<span data-ttu-id="769b5-103">Používá ALink jako zástupný symbol pro ukládání informací o vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="769b5-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="769b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="769b5-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a><span data-ttu-id="769b5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="769b5-105">Remarks</span></span>

<span data-ttu-id="769b5-106">Odkazy na tento typ může být vložená do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="769b5-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="769b5-107">Při vytváření manifestu sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, používá ALink informace, které jsou připojené k tyto odkazy vygenerovat reálné vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="769b5-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="769b5-108">V důsledku toho je nikdy vytvořena instance tohoto typu, a odkazy na něj slouží pouze jako součást procesu sestavení a dodávat žádný účel v konečném sestavení.</span><span class="sxs-lookup"><span data-stu-id="769b5-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="769b5-109">Odkazy na tento typ označení vlastní atributy, které nejsou týkající se zabezpečení a nejsou použitelné více.</span><span class="sxs-lookup"><span data-stu-id="769b5-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>

<span data-ttu-id="769b5-110">Tyto typy jsou označeny "vnitřní" v rámci rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="769b5-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="769b5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="769b5-111">Requirements</span></span>

<span data-ttu-id="769b5-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="769b5-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="769b5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="769b5-113">See also</span></span>

- [<span data-ttu-id="769b5-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="769b5-114">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="769b5-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="769b5-115">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="769b5-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="769b5-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
