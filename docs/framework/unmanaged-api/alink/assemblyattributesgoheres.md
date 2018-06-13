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
ms.openlocfilehash: d68450d05f667851404a009c0984f8722253e71e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402907"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="7d4b1-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="7d4b1-102">AssemblyAttributesGoHereS</span></span>
<span data-ttu-id="7d4b1-103">Používá ALink jako zástupný znak k uložení informací o vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d4b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d4b1-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a><span data-ttu-id="7d4b1-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d4b1-105">Remarks</span></span>  
 <span data-ttu-id="7d4b1-106">Odkazy na tento typ může vložit do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="7d4b1-107">Při sestavování manifest sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, ALink používá informace, které jsou připojené k tyto odkazy pro vydávání skutečných vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="7d4b1-108">Jako takový je nikdy vytvořena instance tohoto typu a na ni odkazují se používají pouze jako součást procesu sestavení a mají žádné účely v posledním sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="7d4b1-109">Odkazy na tento typ znamenat vlastních atributů, které se týká zabezpečení a nejsou více použití.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="7d4b1-110">Tyto typy jsou označeny "internal" v rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="7d4b1-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d4b1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d4b1-111">Requirements</span></span>  
 <span data-ttu-id="7d4b1-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="7d4b1-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d4b1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d4b1-113">See Also</span></span>  
 [<span data-ttu-id="7d4b1-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="7d4b1-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="7d4b1-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="7d4b1-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="7d4b1-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="7d4b1-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
