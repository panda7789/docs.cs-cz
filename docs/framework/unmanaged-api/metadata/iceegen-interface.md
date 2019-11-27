---
title: ICeeGen – rozhraní
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: ae3c372951de00b097d0a8437039a3a85bf3aabf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426150"
---
# <a name="iceegen-interface"></a>ICeeGen – rozhraní
Poskytuje metody pro kompilaci dynamického kódu.  
  
 Toto rozhraní je zastaralé a nemělo by se používat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AddSectionReloc – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Zastaralé. Přidá instrukci. přemístění do základu kódu.|  
|[AllocateMethodBuffer – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Zastaralé. Vytvoří vyrovnávací paměť zadané velikosti pro metodu a získá relativní virtuální adresu metody.|  
|[ComputePointer – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Zastaralé. Určuje vyrovnávací paměť pro zadaný oddíl kódu.|  
|[EmitString – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Zastaralé. Vygeneruje zadaný řetězec do základu kódu.|  
|[GenerateCeeFile – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Zastaralé. Vygeneruje soubor základní znakové sady, který obsahuje základ kódu, který je aktuálně načten do tohoto `ICeeGen`.|  
|[GenerateCeeMemoryImage – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Zastaralé. Vygeneruje obrázek v paměti pro základ kódu.|  
|[GetIlSection – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Zastaralé. Získá část základu kódu zprostředkujícího jazyka, na kterou odkazuje zadaný popisovač.|  
|[GetIMapTokenIface – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Zastaralé. Získá rozhraní, na které odkazuje zadaný token.|  
|[GetMethodBuffer – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Zastaralé. Načte vyrovnávací paměť odpovídající velikosti pro metodu na zadané relativní virtuální adrese.|  
|[GetSectionBlock – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Zastaralé. Získá blok oddílu základu kódu.|  
|[GetSectionCreate – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Zastaralé. Vygeneruje a získá oddíl kódu s použitím zadaných hodnot název a příznak.|  
|[GetSectionDataLen – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Zastaralé. Získá délku zadaného oddílu.|  
|[GetString – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Zastaralé. Získá řetězec uložený na zadané relativní virtuální adrese.|  
|[GetStringSection – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Zastaralé. Načte řetězcovou reprezentaci oddílu kódu, na který odkazuje zadaný popisovač.|  
|[TruncateSection – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Zastaralé. Zkrátí zadaný oddíl kódu o zadanou délku.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
