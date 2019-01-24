---
title: AssemblyAttributesGoHereSM
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereSM
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d47ca3a9134266d1c40447cea6eb8aaf2cc9eb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706294"
---
# <a name="assemblyattributesgoheresm"></a><span data-ttu-id="1f8c5-102">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="1f8c5-102">AssemblyAttributesGoHereSM</span></span>
<span data-ttu-id="1f8c5-103">Používá ALink jako zástupný symbol pro ukládání informací o vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="1f8c5-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f8c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f8c5-104">Syntax</span></span>  
  
```  
AssemblyAttributeGoHereSM  
```  
  
## <a name="remarks"></a><span data-ttu-id="1f8c5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f8c5-105">Remarks</span></span>  
 <span data-ttu-id="1f8c5-106">Odkazy na tento typ může být vložená do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f8c5-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="1f8c5-107">Při vytváření manifestu sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, používá ALink informace, které jsou připojené k tyto odkazy vygenerovat reálné vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="1f8c5-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="1f8c5-108">V důsledku toho je nikdy vytvořena instance tohoto typu, a odkazy na něj slouží pouze jako součást procesu sestavení a dodávat žádný účel v konečném sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f8c5-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="1f8c5-109">Odkazy na tento typ označení vlastních atributů, které jsou související a použití více zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1f8c5-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>  
  
 <span data-ttu-id="1f8c5-110">Tyto typy jsou označeny "vnitřní" v rámci rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="1f8c5-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f8c5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f8c5-111">Requirements</span></span>  
 <span data-ttu-id="1f8c5-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="1f8c5-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f8c5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f8c5-113">See also</span></span>
- [<span data-ttu-id="1f8c5-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="1f8c5-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)
- [<span data-ttu-id="1f8c5-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="1f8c5-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)
- [<span data-ttu-id="1f8c5-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="1f8c5-116">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
