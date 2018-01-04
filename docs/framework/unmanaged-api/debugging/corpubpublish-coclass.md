---
title: "CorpubPublish – třída typu coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorpubPublish Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorpubPublish
helpviewer_keywords: CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3dec1175715bdbddc3c975924e91e238fa6d5f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corpubpublish-coclass"></a>CorpubPublish – třída typu coclass
Poskytuje rozhraní pro publikování informací o doménách aplikace a procesy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|[ICorPublish – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|Poskytuje metody pro publikování informací o procesy a aplikační domény v těchto procesů.|  
|[ICorPublishAppDomain – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|Reprezentuje a poskytuje informace o doméně aplikace v procesu.|  
|[ICorPublishAppDomainEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Poskytuje metody, které překračují kolekce aplikační domény, které existují v rámci procesu.|  
|[ICorPublishProcess – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Představuje proces, který běží na počítači.|  
|[ICorPublishProcessEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Poskytuje metody, které překračují kolekce procesy, které jsou spuštěny v počítači.|  
  
## <a name="remarks"></a>Poznámky  
 Typický scénář publikování zahrnuje vývojáři, který chce ladění spravovaného kódu, který běží na počítači v rámci domény aplikace. Hostitelské prostředí může používat více než jedné domény aplikace v rámci procesu. Vývojář se má použít grafické uživatelské rozhraní nebo jiných prostředků k zobrazení seznamu všech procesů, které jsou spuštěné v počítači a vyberte konkrétní proces. Seznam by měly obsahovat všechny domény aplikace v rámci procesy, které běží spravovaného kódu. Vývojář můžete identifikovat specifické aplikační doméně a připojit ladicí program k této doméně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
