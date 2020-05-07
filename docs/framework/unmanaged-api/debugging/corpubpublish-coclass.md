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
ms.openlocfilehash: e33029e8244fdfa180a79aa4a5b05b07f594d928
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860906"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish – třída typu coclass
Poskytuje rozhraní pro publikování informací o aplikačních doménách a procesech.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|[ICorPublish – rozhraní](icorpublish-interface.md)|Poskytuje metody pro publikování informací o procesech a doménách aplikace v těchto procesech.|  
|[ICorPublishAppDomain – rozhraní](icorpublishappdomain-interface.md)|Představuje a poskytuje informace o doméně aplikace v procesu.|  
|[ICorPublishAppDomainEnum – rozhraní](icorpublishappdomainenum-interface.md)|Poskytuje metody, které procházejí kolekci aplikačních domén, které aktuálně existují v rámci procesu.|  
|[ICorPublishProcess – rozhraní](icorpublishprocess-interface.md)|Představuje proces, který je spuštěn v počítači.|  
|[ICorPublishProcessEnum – rozhraní](icorpublishprocessenum-interface.md)|Poskytuje metody, které procházejí kolekci procesů, které jsou spuštěny v počítači.|  
  
## <a name="remarks"></a>Poznámky  
 Typický scénář publikování zahrnuje vývojáře, který chce ladit spravovaný kód, který je spuštěný v počítači v doméně aplikace. Hostující prostředí může v rámci procesu používat více než jednu doménu aplikace. Vývojář chce použít grafické uživatelské rozhraní nebo jiné prostředky k zobrazení seznamu všech procesů spuštěných v počítači a vybrat konkrétní proces. Výpis by měl obsahovat všechny domény aplikace v rámci procesů, na kterých běží spravovaný kód. Vývojář pak může identifikovat konkrétní doménu aplikace a připojit ladicí program k této doméně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorPub. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Ladění](index.md)
