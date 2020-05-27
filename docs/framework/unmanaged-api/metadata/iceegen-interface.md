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
ms.openlocfilehash: e6cf0aa6f731d0a417e1a2be0ca1d0f8c9299379
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008271"
---
# <a name="iceegen-interface"></a>ICeeGen – rozhraní
Poskytuje metody pro kompilaci dynamického kódu.  
  
 Toto rozhraní je zastaralé a nemělo by se používat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[AddSectionReloc – metoda](iceegen-addsectionreloc-method.md)|Zastaralé. Přidá instrukci. přemístění do základu kódu.|  
|[AllocateMethodBuffer – metoda](iceegen-allocatemethodbuffer-method.md)|Zastaralé. Vytvoří vyrovnávací paměť zadané velikosti pro metodu a získá relativní virtuální adresu metody.|  
|[ComputePointer – metoda](iceegen-computepointer-method.md)|Zastaralé. Určuje vyrovnávací paměť pro zadaný oddíl kódu.|  
|[EmitString – metoda](iceegen-emitstring-method.md)|Zastaralé. Vygeneruje zadaný řetězec do základu kódu.|  
|[GenerateCeeFile – metoda](iceegen-generateceefile-method.md)|Zastaralé. Vygeneruje soubor základní znakové sady, který obsahuje základ kódu, který je aktuálně načten do tohoto `ICeeGen` .|  
|[GenerateCeeMemoryImage – metoda](iceegen-generateceememoryimage-method.md)|Zastaralé. Vygeneruje obrázek v paměti pro základ kódu.|  
|[GetIlSection – metoda](iceegen-getilsection-method.md)|Zastaralé. Získá část základu kódu zprostředkujícího jazyka, na kterou odkazuje zadaný popisovač.|  
|[GetIMapTokenIface – metoda](iceegen-getimaptokeniface-method.md)|Zastaralé. Získá rozhraní, na které odkazuje zadaný token.|  
|[GetMethodBuffer – metoda](iceegen-getmethodbuffer-method.md)|Zastaralé. Načte vyrovnávací paměť odpovídající velikosti pro metodu na zadané relativní virtuální adrese.|  
|[GetSectionBlock – metoda](iceegen-getsectionblock-method.md)|Zastaralé. Získá blok oddílu základu kódu.|  
|[GetSectionCreate – metoda](iceegen-getsectioncreate-method.md)|Zastaralé. Vygeneruje a získá oddíl kódu s použitím zadaných hodnot název a příznak.|  
|[GetSectionDataLen – metoda](iceegen-getsectiondatalen-method.md)|Zastaralé. Získá délku zadaného oddílu.|  
|[GetString – metoda](iceegen-getstring-method.md)|Zastaralé. Získá řetězec uložený na zadané relativní virtuální adrese.|  
|[GetStringSection – metoda](iceegen-getstringsection-method.md)|Zastaralé. Načte řetězcovou reprezentaci oddílu kódu, na který odkazuje zadaný popisovač.|  
|[TruncateSection – metoda](iceegen-truncatesection-method.md)|Zastaralé. Zkrátí zadaný oddíl kódu o zadanou délku.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro metadata](metadata-interfaces.md)
