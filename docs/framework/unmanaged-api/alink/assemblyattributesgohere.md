---
title: AssemblyAttributesGoHere
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyAttributesGoHere
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9577ecb1f987d86527a96723f45f09509c55d5cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyattributesgohere"></a>AssemblyAttributesGoHere
Používá ALink jako zástupný znak k uložení informací o vlastní atributy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a>Poznámky  
 Odkazy na tento typ může vložit do netmodules, jejichž zdroje obsahovat vlastní atributy sestavení. Při sestavování manifest sestavení z jednoho nebo více netmodules, které obsahují odkazy na tyto typy, ALink používá informace, které jsou připojené k tyto odkazy pro vydávání skutečných vlastní atributy. Jako takový je nikdy vytvořena instance tohoto typu a na ni odkazují se používají pouze jako součást procesu sestavení a mají žádné účely v posledním sestavení.  
  
 Odkazy na tento typ znamenat vlastních atributů, které nejsou spojených se zabezpečením a nejsou více použití.  
  
 Tyto typy jsou označeny "internal" v rozhraní .NET Framework a jsou umístěny v <xref:System.Runtime.CompilerServices>.  
  
## <a name="requirements"></a>Požadavky  
 mscorlib.dll  
  
## <a name="see-also"></a>Viz také  
 [Assemblyattributesgoherem –](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [Assemblyattributesgoheres –](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [Assemblyattributesgoheresm –](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
