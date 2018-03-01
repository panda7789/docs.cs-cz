---
title: AssemblyAttributesGoHereS
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ac8f25632521f2e8abe5209608e42632293feb4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgoheres"></a>AssemblyAttributesGoHereS
Používá ALink jako zástupný znak k uložení informací o vlastní atributy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a>Poznámky  
 Odkazy na tento typ může vložit do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení. Při sestavování manifest sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, ALink používá informace, které jsou připojené k tyto odkazy pro vydávání skutečných vlastní atributy. Jako takový je nikdy vytvořena instance tohoto typu a na ni odkazují se používají pouze jako součást procesu sestavení a mají žádné účely v posledním sestavení.  
  
 Odkazy na tento typ znamenat vlastních atributů, které se týká zabezpečení a nejsou více použití.  
  
 Tyto typy jsou označeny "internal" v rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices>.  
  
## <a name="requirements"></a>Požadavky  
 mscorlib.dll  
  
## <a name="see-also"></a>Viz také  
 [AssemblyAttributesGoHere](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [AssemblyAttributesGoHereM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [AssemblyAttributesGoHereSM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
