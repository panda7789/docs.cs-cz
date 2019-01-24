---
title: AssemblyAttributesGoHereM
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereM
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbd5428039144fd38796ed6865c24a605f236ccd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733802"
---
# <a name="assemblyattributesgoherem"></a><span data-ttu-id="e0ddb-102">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="e0ddb-102">AssemblyAttributesGoHereM</span></span>
<span data-ttu-id="e0ddb-103">Používá ALink jako zástupný symbol pro ukládání informací o vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="e0ddb-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0ddb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0ddb-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereM  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0ddb-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0ddb-105">Remarks</span></span>  
 <span data-ttu-id="e0ddb-106">Odkazy na tento typ může být vložená do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0ddb-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="e0ddb-107">Při vytváření manifestu sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, používá ALink informace, které jsou připojené k tyto odkazy vygenerovat reálné vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="e0ddb-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="e0ddb-108">V důsledku toho je nikdy vytvořena instance tohoto typu, a odkazy na něj slouží pouze jako součást procesu sestavení a dodávat žádný účel v konečném sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0ddb-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="e0ddb-109">Odkazy na tento typ označení vlastních atributů, které nejsou týkající se zabezpečení, ale jsou více použití.</span><span class="sxs-lookup"><span data-stu-id="e0ddb-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>  
  
 <span data-ttu-id="e0ddb-110">Tyto typy jsou označeny "vnitřní" v rámci rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="e0ddb-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0ddb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0ddb-111">Requirements</span></span>  
 <span data-ttu-id="e0ddb-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="e0ddb-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ddb-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0ddb-113">See also</span></span>
- [<span data-ttu-id="e0ddb-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="e0ddb-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)
- [<span data-ttu-id="e0ddb-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="e0ddb-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
- [<span data-ttu-id="e0ddb-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="e0ddb-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
