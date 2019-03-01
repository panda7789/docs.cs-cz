---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74447f52c75ae22e513c6f07950630d37bad191a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969827"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="18348-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="18348-102">AssemblyAttributesGoHereS</span></span>

<span data-ttu-id="18348-103">Používá ALink jako zástupný symbol pro ukládání informací o vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="18348-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="18348-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18348-104">Syntax</span></span>

```
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a><span data-ttu-id="18348-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18348-105">Remarks</span></span>

<span data-ttu-id="18348-106">Odkazy na tento typ může být vložená do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="18348-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="18348-107">Při vytváření manifestu sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, používá ALink informace, které jsou připojené k tyto odkazy vygenerovat reálné vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="18348-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="18348-108">V důsledku toho je nikdy vytvořena instance tohoto typu, a odkazy na něj slouží pouze jako součást procesu sestavení a dodávat žádný účel v konečném sestavení.</span><span class="sxs-lookup"><span data-stu-id="18348-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="18348-109">Odkazy na tento typ označuje vlastních atributů, které se týká zabezpečení a nejsou použitelné více.</span><span class="sxs-lookup"><span data-stu-id="18348-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>

<span data-ttu-id="18348-110">Tyto typy jsou označeny "vnitřní" v rámci rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="18348-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="18348-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18348-111">Requirements</span></span>

<span data-ttu-id="18348-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="18348-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="18348-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18348-113">See also</span></span>

- [<span data-ttu-id="18348-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="18348-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="18348-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="18348-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="18348-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="18348-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
