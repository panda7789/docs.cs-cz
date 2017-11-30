---
title: "ICeeGen – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen
helpviewer_keywords: ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8342c79dd8b7452599af8d9782b0fbec5f83e964
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iceegen-interface"></a>ICeeGen – rozhraní
Poskytuje metody pro dynamický kód kompilace.  
  
 Toto rozhraní je zastaralé a by se neměla používat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Addsectionreloc – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Zastaralé. Přidá instrukce .reloc základu kódu.|  
|[Allocatemethodbuffer – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Zastaralé. Vytvoří vyrovnávací paměti zadaná velikost pro metodu a získá relativní virtuální adresu metody.|  
|[Computepointer – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Zastaralé. Určuje velikost vyrovnávací paměti pro část zadaný kód.|  
|[Emitstring – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Zastaralé. Zadaný řetězec vysílá do základu kódu.|  
|[Generateceefile – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Zastaralé. Generuje soubor základu kódu, který obsahuje kód základní momentálně načtených do této `ICeeGen`.|  
|[Generateceememoryimage – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Zastaralé. Generuje bitovou kopii v paměti pro základu kódu.|  
|[Getilsection – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Zastaralé. Získá části základní převodní jazyk kódu Zadaný popisovač odkazuje.|  
|[Getimaptokeniface – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Zastaralé. Získá rozhraní odkazuje zadaný token.|  
|[Getmethodbuffer – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Zastaralé. Získá odpovídající velikost vyrovnávací paměti pro metodu na zadané adrese relativní virtuální.|  
|[Getsectionblock – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Zastaralé. Získá blok část základu kódu.|  
|[Getsectioncreate – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Zastaralé. Generuje a získá oddíl kód pomocí zadaného názvu a hodnoty příznaku.|  
|[Getsectiondatalen – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Zastaralé. Získá délku zadaný oddíl.|  
|[GetString – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Zastaralé. Získá řetězec uložený na zadané adrese relativní virtuální.|  
|[Getstringsection – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Zastaralé. Získá řetězcovou reprezentaci části kódu, který odkazuje Zadaný popisovač.|  
|[Truncatesection – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Zastaralé. Zkrátí části zadaný kód pomocí zadané délky.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
