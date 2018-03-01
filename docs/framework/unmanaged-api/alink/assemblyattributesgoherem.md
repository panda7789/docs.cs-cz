---
title: AssemblyAttributesGoHereM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be60619077a04784152ece1a64551a1b9e5eb80a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgoherem"></a><span data-ttu-id="28a11-102">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="28a11-102">AssemblyAttributesGoHereM</span></span>
<span data-ttu-id="28a11-103">Používá ALink jako zástupný znak k uložení informací o vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="28a11-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28a11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28a11-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereM  
```  
  
## <a name="remarks"></a><span data-ttu-id="28a11-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28a11-105">Remarks</span></span>  
 <span data-ttu-id="28a11-106">Odkazy na tento typ může vložit do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="28a11-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="28a11-107">Při sestavování manifest sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, ALink používá informace, které jsou připojené k tyto odkazy pro vydávání skutečných vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="28a11-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="28a11-108">Jako takový je nikdy vytvořena instance tohoto typu a na ni odkazují se používají pouze jako součást procesu sestavení a mají žádné účely v posledním sestavení.</span><span class="sxs-lookup"><span data-stu-id="28a11-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="28a11-109">Odkazy na tento typ znamenat vlastních atributů, které nejsou zabezpečení související s ale jsou více použití.</span><span class="sxs-lookup"><span data-stu-id="28a11-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>  
  
 <span data-ttu-id="28a11-110">Tyto typy jsou označeny "internal" v rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="28a11-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28a11-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28a11-111">Requirements</span></span>  
 <span data-ttu-id="28a11-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="28a11-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a11-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="28a11-113">See Also</span></span>  
 [<span data-ttu-id="28a11-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="28a11-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="28a11-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="28a11-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="28a11-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="28a11-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
