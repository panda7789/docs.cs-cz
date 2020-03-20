---
title: IMetaDataImport::GetInterfaceImplProps – metoda
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175379"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps – metoda
Získá ukazatel na tokeny metadat <xref:System.Type> pro, který implementuje zadanou metodu a pro rozhraní, které deklaruje tuto metodu.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iiImpl`  
 [v] Token metadat představující metodu vrátit tokeny třídy a rozhraní pro.  
  
 `pClass`  
 [out] Token metadat představující třídu, která implementuje metodu.  
  
 `ptkIface`  
 [out] Token metadat představující rozhraní, které definuje implementovanou metodu.  

## <a name="remarks"></a>Poznámky

 Hodnotu získáte `iImpl` voláním metody [EnumInterfaceImpls.](imetadataimport-enuminterfaceimpls-method.md)

 Předpokládejme například, že `mdTypeDef` třída má hodnotu tokenu 0x02000007 a že implementuje tři rozhraní, jejichž typy mají tokeny:

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

Koncepčně jsou tyto informace uloženy do tabulky implementace rozhraní jako:

| Číslo řádku | Token třídy | Token rozhraní |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Odvolání, token je 4bajtová hodnota:

- Dolní 3 bajty drží číslo řádku nebo RID.
- Horní bajt obsahuje typ tokenu – `mdtInterfaceImpl`0x09 pro .

`GetInterfaceImplProps`vrátí informace držené v řádku, jehož `iImpl` token zadáte v argumentu.
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
