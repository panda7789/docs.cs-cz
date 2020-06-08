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
ms.openlocfilehash: 1c9d9647084aa729817eeeb17ee3f5cd320c0d29
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491237"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps – metoda
Získá ukazatel na tokeny metadat pro <xref:System.Type> , který implementuje specifikovanou metodu, a pro rozhraní, které deklaruje tuto metodu.
  
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
 pro Token metadat představující metodu pro návrat třídy a tokeny rozhraní pro.  
  
 `pClass`  
 mimo Token metadat představující třídu, která implementuje metodu.  
  
 `ptkIface`  
 mimo Token metadat představující rozhraní, které definuje implementovanou metodu.  

## <a name="remarks"></a>Poznámky

 Hodnotu pro lze získat `iImpl` voláním metody [enuminterfaceimpls –](imetadataimport-enuminterfaceimpls-method.md) .

 Předpokládejme například, že třída má `mdTypeDef` hodnotu tokenu 0x02000007 a že implementuje tři rozhraní, jejichž typy mají tokeny:

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

V koncepčních případech jsou tyto informace uloženy do tabulky implementace rozhraní jako:

| Číslo řádku | Token třídy | Token rozhraní |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Odvolání tokenu je hodnota o velikosti 4 bajty:

- Dolní 3 bajty obsahují číslo řádku nebo identifikátor RID.
- Horní bajt obsahuje typ tokenu – 0x09 pro `mdtInterfaceImpl` .

`GetInterfaceImplProps`Vrátí informace uchovávané v řádku, jehož token zadáte v `iImpl` argumentu.
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
