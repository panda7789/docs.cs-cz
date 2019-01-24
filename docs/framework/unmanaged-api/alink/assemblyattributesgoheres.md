---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereS
api_location:
- alink.dll
api_type:
- COM
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
ms.openlocfilehash: 3506462aaf8d040126d979801460772b3cd47f9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706281"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="2ffc7-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="2ffc7-102">AssemblyAttributesGoHereS</span></span>
<span data-ttu-id="2ffc7-103">Používá ALink jako zástupný symbol pro ukládání informací o vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="2ffc7-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ffc7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ffc7-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a><span data-ttu-id="2ffc7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ffc7-105">Remarks</span></span>  
 <span data-ttu-id="2ffc7-106">Odkazy na tento typ může být vložená do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="2ffc7-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="2ffc7-107">Při vytváření manifestu sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, používá ALink informace, které jsou připojené k tyto odkazy vygenerovat reálné vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="2ffc7-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="2ffc7-108">V důsledku toho je nikdy vytvořena instance tohoto typu, a odkazy na něj slouží pouze jako součást procesu sestavení a dodávat žádný účel v konečném sestavení.</span><span class="sxs-lookup"><span data-stu-id="2ffc7-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="2ffc7-109">Odkazy na tento typ označuje vlastních atributů, které se týká zabezpečení a nejsou použitelné více.</span><span class="sxs-lookup"><span data-stu-id="2ffc7-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="2ffc7-110">Tyto typy jsou označeny "vnitřní" v rámci rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="2ffc7-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ffc7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ffc7-111">Requirements</span></span>  
 <span data-ttu-id="2ffc7-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="2ffc7-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ffc7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ffc7-113">See also</span></span>
- [<span data-ttu-id="2ffc7-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="2ffc7-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)
- [<span data-ttu-id="2ffc7-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="2ffc7-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)
- [<span data-ttu-id="2ffc7-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="2ffc7-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
