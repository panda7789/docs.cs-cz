---
title: Aktivovat funkci (WPF nespravovaná referenční dokumentace rozhraní API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Acrivate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 4e79b74dc8bb7d57125c27e17e8f52d607fffcf1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721950"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Aktivovat funkci (WPF nespravovaná referenční dokumentace rozhraní API)
Toto rozhraní API podporuje infrastrukturu Windows Presentation Foundation (WPF) a není určena pro použití přímo v kódu.  
  
 Používá infrastrukturu Windows Presentation Foundation (WPF) pro správu systému windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a>Parametry  
 pParameters  
 Ukazatel na parametry v okně aktivace.  
  
 ppInner  
 Adresa vyrovnávací paměti jedním prvkem, který obsahuje ukazatel na ukazatel <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [rozhraní .NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 V rozhraní .NET Framework 3.0 a 3.5: PresentationHostDLL.dll  
  
 V rozhraní .NET Framework 4 a novější: PresentationHost_v0400.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Odkaz na nespravované rozhraní API subsystému WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
