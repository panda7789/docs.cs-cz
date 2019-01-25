---
title: AssemblyAttributesGoHere
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHere
api_location:
- alink.dll
api_type:
- COM
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
ms.openlocfilehash: cde96ed9089416fa5febe55e49b4109cfeb11f40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722137"
---
# <a name="assemblyattributesgohere"></a><span data-ttu-id="cfb09-102">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="cfb09-102">AssemblyAttributesGoHere</span></span>
<span data-ttu-id="cfb09-103">Používá ALink jako zástupný symbol pro ukládání informací o vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="cfb09-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfb09-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a><span data-ttu-id="cfb09-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfb09-105">Remarks</span></span>  
 <span data-ttu-id="cfb09-106">Odkazy na tento typ může být vložená do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="cfb09-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="cfb09-107">Při vytváření manifestu sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, používá ALink informace, které jsou připojené k tyto odkazy vygenerovat reálné vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="cfb09-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="cfb09-108">V důsledku toho je nikdy vytvořena instance tohoto typu, a odkazy na něj slouží pouze jako součást procesu sestavení a dodávat žádný účel v konečném sestavení.</span><span class="sxs-lookup"><span data-stu-id="cfb09-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="cfb09-109">Odkazy na tento typ označení vlastní atributy, které nejsou týkající se zabezpečení a nejsou použitelné více.</span><span class="sxs-lookup"><span data-stu-id="cfb09-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="cfb09-110">Tyto typy jsou označeny "vnitřní" v rámci rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="cfb09-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb09-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfb09-111">Requirements</span></span>  
 <span data-ttu-id="cfb09-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="cfb09-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb09-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfb09-113">See also</span></span>
- [<span data-ttu-id="cfb09-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="cfb09-114">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)
- [<span data-ttu-id="cfb09-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="cfb09-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
- [<span data-ttu-id="cfb09-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="cfb09-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
