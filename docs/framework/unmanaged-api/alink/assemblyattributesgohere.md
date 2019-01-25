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
# <a name="assemblyattributesgohere"></a>AssemblyAttributesGoHere
Používá ALink jako zástupný symbol pro ukládání informací o vlastní atributy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a>Poznámky  
 Odkazy na tento typ může být vložená do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení. Při vytváření manifestu sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, používá ALink informace, které jsou připojené k tyto odkazy vygenerovat reálné vlastní atributy. V důsledku toho je nikdy vytvořena instance tohoto typu, a odkazy na něj slouží pouze jako součást procesu sestavení a dodávat žádný účel v konečném sestavení.  
  
 Odkazy na tento typ označení vlastní atributy, které nejsou týkající se zabezpečení a nejsou použitelné více.  
  
 Tyto typy jsou označeny "vnitřní" v rámci rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices>.  
  
## <a name="requirements"></a>Požadavky  
 mscorlib.dll  
  
## <a name="see-also"></a>Viz také:
- [AssemblyAttributesGoHereM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
