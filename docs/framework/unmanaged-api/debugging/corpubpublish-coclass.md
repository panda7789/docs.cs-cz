---
title: CorpubPublish – třída typu coclass
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05d9eef36885aee05d88f7da994c8b168c3221b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130530"
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
|[ICorPublishAppDomain – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|Představuje a poskytuje informace o doméně aplikace v procesu.|  
|[ICorPublishAppDomainEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Poskytuje metody, které procházejí kolekci aplikačních doménách, které momentálně existují v rámci procesu.|  
|[ICorPublishProcess – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Představuje proces, který běží na počítači.|  
|[ICorPublishProcessEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Poskytuje metody, které procházejí kolekci procesy, které jsou spuštěny v počítači.|  
  
## <a name="remarks"></a>Poznámky  
 Typický scénář publikování zahrnuje vývojář, který chcete ladit spravovaný kód, který běží na počítači v rámci domény aplikace. Hostitelské prostředí může používat více než jedné domény aplikace v rámci procesu. Vývojář chce použít grafické uživatelské rozhraní nebo jiných prostředků k zobrazení seznamu všechny procesy, které jsou spuštěny v počítači a vybrat konkrétní proces. Seznam by měl obsahovat všechny domény aplikace uvnitř procesy, které jsou spuštěny spravovaného kódu. Vývojář můžete identifikovat specifické aplikační doméně a připojit ladicí program k této doméně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
