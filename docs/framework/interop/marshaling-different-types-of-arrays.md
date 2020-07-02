---
title: Zařazování různých typů polí
description: Zařazování různých typů polí, jako jsou celá čísla podle hodnoty nebo odkazu, dvojrozměrné celočíselné hodnoty podle hodnot, řetězců podle hodnot a struktur s celými čísly nebo řetězci.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: f1473c7917189f0b36c96b2adcf20005c5fd6b48
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621493"
---
# <a name="marshaling-different-types-of-arrays"></a>Zařazování různých typů polí
Pole je typ odkazu ve spravovaném kódu, který obsahuje jeden nebo více prvků stejného typu. I když pole jsou odkazové typy, jsou předány jako parametry do nespravovaných funkcí. Toto chování je nekonzistentní, protože spravovaná pole jsou předávána spravovaným objektům, což jsou vstupně-výstupní parametry. Další podrobnosti najdete v tématu [kopírování a připnutí](copying-and-pinning.md).  
  
 Následující tabulka uvádí možnosti zařazování pro pole a popisuje jejich použití.  
  
|Pole|Popis|  
|-----------|-----------------|  
|Celých čísel podle hodnoty.|Předá pole celých čísel jako parametr v parametru.|  
|Celých čísel podle odkazu.|Předá pole celých čísel jako vstupně-výstupní parametr.|  
|Celých čísel podle hodnoty (dvourozměrné).|Předává matici celých čísel jako parametr v parametru.|  
|Řetězců podle hodnoty.|Předá pole řetězců jako parametr v parametru.|  
|Struktury s celými čísly.|Předá pole struktury, které obsahují celá čísla jako parametr in.|  
|Struktury s řetězci.|Předá pole struktur, které obsahují pouze řetězce jako vstupně-výstupní parametr. Členy pole lze změnit.|  
  
## <a name="example"></a>Příklad  
 Tato ukázka předvádí, jak předat následující typy polí:  
  
- Pole celých čísel podle hodnoty.  
  
- Pole celých čísel podle odkazu, které lze změnit.  
  
- Multidimenzionální pole (matice) celých čísel podle hodnoty.  
  
- Pole řetězců podle hodnoty.  
  
- Pole struktur s celými čísly  
  
- Pole struktur s řetězci.  
  
 Pokud není pole explicitně zařazeno pomocí odkazu, výchozí chování zařadí pole jako parametr v parametru. Toto chování můžete změnit použitím <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> atributů a explicitně.  
  
 Ukázka pole používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:  
  
- **TestArrayOfInts** exportovaný z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- **TestRefArrayOfInts** exportovaný z PinvokeLib.dll.  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- **TestMatrixOfInts** exportovaný z PinvokeLib.dll.  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- **TestArrayOfStrings** exportovaný z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- **TestArrayOfStructs** exportovaný z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- **TestArrayOfStructs2** exportovaný z PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace pro dříve uvedené funkce a dvě proměnné struktury, **MYPOINT** a **MYPERSON**. Struktury obsahují následující prvky:  
  
```cpp
typedef struct _MYPOINT  
{  
   int x;
   int y;
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;
   char* last;
} MYPERSON;  
```  
  
 V této ukázce `MyPoint` `MyPerson` struktury a obsahují vložené typy. <xref:System.Runtime.InteropServices.StructLayoutAttribute>Atribut je nastaven tak, aby bylo zajištěno, že jsou členy uspořádány v paměti sekvenčně v pořadí, ve kterém jsou zobrazeny.  
  
 `NativeMethods`Třída obsahuje sadu metod, které jsou volány `App` třídou. Konkrétní podrobnosti o předávání polí naleznete v komentářích v následující ukázce. Pole, které je odkazový typ, je ve výchozím nastavení předáno jako parametr in. Aby volající mohl přijímat výsledky, **atribut** InAttribute a **subattribute** musí být explicitně aplikovány na argument obsahující pole.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Viz také:

- [Datové typy vyvolání platformy](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
